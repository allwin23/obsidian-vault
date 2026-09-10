---
selected_week: 2026-09-11
---

# Efficiency Dashboard

**Select a week (any date in that week — week runs Monday to Sunday):**

```dataviewjs
const fm = dv.current();
const file = app.vault.getAbstractFileByPath(fm.file.path);
const wrap = dv.el('div', '', { cls: 'eff-week-pick' });
const input = document.createElement('input');
input.type = 'date';
input.value = fm.selected_week ?? '';
input.addEventListener('change', async () => {
  await app.fileManager.processFrontMatter(file, (frontmatter) => {
    frontmatter.selected_week = input.value;
  });
});
wrap.appendChild(input);
```

---

## Weekly Efficiency

```dataviewjs
const p = dv.current();
if (!p.selected_week) {
  dv.paragraph("Pick a date above to see that week's efficiency.");
} else {
  const picked = new Date(p.selected_week);
  const day = picked.getDay();
  const diffToMonday = (day === 0 ? -6 : 1 - day);
  const monday = new Date(picked);
  monday.setDate(picked.getDate() + diffToMonday);

  const weekDates = [];
  for (let i = 0; i < 7; i++) {
    const d = new Date(monday);
    d.setDate(monday.getDate() + i);
    weekDates.push(d);
  }

  async function readTaskEfficiency(y, m, day) {
    const path = `09-Efficiency/Work Efficiency/${y}-${String(m).padStart(2,'0')}.md`;
    const file = app.vault.getAbstractFileByPath(path);
    if (!file) return null;
    const content = await app.vault.read(file);
    const lines = content.split('\n');
    const dayRegex = /^> \[!card\] (.+) · (\d+) /;
    const taskRegex = /^> - \[( |x|X)\] ?(.*)$/;
    let planned = 0, done = 0, found = false, capturing = false;
    for (const line of lines) {
      const dm = line.match(dayRegex);
      if (dm) {
        if (capturing) break;
        if (Number(dm[2]) === day) { capturing = true; found = true; }
        continue;
      }
      if (capturing) {
        const tm = line.match(taskRegex);
        if (tm && tm[2].trim() !== '') {
          planned++;
          if (tm[1].toLowerCase() === 'x') done++;
        } else if (line.trim() === '' || line.startsWith('---')) {
          break;
        }
      }
    }
    if (!found || planned === 0) return null;
    return (done / planned) * 100;
  }

  function readTimeEfficiency(y, m, day) {
    const page = dv.page(`09-Efficiency/Time Efficiency/${y}-${String(m).padStart(2,'0')}.md`);
    if (!page) return { req: null, act: null };
    const dd = String(day).padStart(2, '0');
    const worked = page['worked_' + dd];
    const planned = page['planned_' + dd];
    const req = (worked !== undefined && worked !== null && worked !== '') ? (worked / 12) * 100 : null;
    const act = (req !== null && planned !== undefined && planned !== null && planned !== '' && planned > 0) ? (worked / planned) * 100 : null;
    return { req, act };
  }

  const rows = [];
  let reqTotal = 0, reqCount = 0, actTotal = 0, actCount = 0, workTotal = 0, workCount = 0;

  for (const d of weekDates) {
    const y = d.getFullYear(), m = d.getMonth() + 1, day = d.getDate();
    const label = d.toLocaleDateString('default', { weekday: 'short', day: 'numeric', month: 'short' });
    const { req, act } = readTimeEfficiency(y, m, day);
    const workEff = await readTaskEfficiency(y, m, day);
    if (req !== null) { reqTotal += req; reqCount++; }
    if (act !== null) { actTotal += act; actCount++; }
    if (workEff !== null) { workTotal += workEff; workCount++; }
    rows.push([
      label,
      req !== null ? req.toFixed(1) + '%' : '—',
      act !== null ? act.toFixed(1) + '%' : '—',
      workEff !== null ? workEff.toFixed(1) + '%' : '—'
    ]);
  }

  dv.table(['Day', 'Required Eff.', 'Actual Eff.', 'Work Efficiency'], rows);

  const reqAvg = reqCount ? (reqTotal / reqCount).toFixed(1) + '%' : '—';
  const actAvg = actCount ? (actTotal / actCount).toFixed(1) + '%' : '—';
  const workAvg = workCount ? (workTotal / workCount).toFixed(1) + '%' : '—';
  dv.paragraph(`**Week average — Required: ${reqAvg} · Actual: ${actAvg} · Work: ${workAvg}**`);
}
```

---

## Monthly Efficiency

```dataviewjs
const timeFiles = dv.pages('"09-Efficiency/Time Efficiency"');
const rows = [];

for (const page of timeFiles) {
  const month = page.file.name;
  if (!month) continue;
  let reqTotal = 0, reqCount = 0, actTotal = 0, actCount = 0;
  for (const key in page) {
    if (key.startsWith('worked_')) {
      const dd = key.split('_')[1];
      const w = page[key];
      const pl = page['planned_' + dd];
      if (w !== undefined && w !== null && w !== '') {
        reqTotal += (w / 12) * 100;
        reqCount++;
        if (pl !== undefined && pl !== null && pl !== '' && pl > 0) {
          actTotal += (w / pl) * 100;
          actCount++;
        }
      }
    }
  }
  rows.push([
    month,
    reqCount ? (reqTotal / reqCount).toFixed(1) + '%' : '—',
    actCount ? (actTotal / actCount).toFixed(1) + '%' : '—'
  ]);
}

rows.sort((a, b) => a[0].localeCompare(b[0]));
dv.header(3, "Time Efficiency by Month");
dv.table(['Month', 'Avg Required', 'Avg Actual'], rows);
```

```dataviewjs
async function monthWorkAverage(path) {
  const file = app.vault.getAbstractFileByPath(path);
  if (!file) return null;
  const content = await app.vault.read(file);
  const lines = content.split('\n');
  const dayRegex = /^> \[!card\] /;
  const taskRegex = /^> - \[( |x|X)\] ?(.*)$/;
  let planned = 0, done = 0, capturing = false;
  let total = 0, count = 0;

  function flush() {
    if (planned > 0) {
      total += (done / planned) * 100;
      count++;
    }
  }

  for (const line of lines) {
    if (dayRegex.test(line)) {
      flush();
      planned = 0; done = 0; capturing = true;
      continue;
    }
    if (capturing) {
      const tm = line.match(taskRegex);
      if (tm && tm[2].trim() !== '') {
        planned++;
        if (tm[1].toLowerCase() === 'x') done++;
      }
    }
  }
  flush();
  return count ? (total / count) : null;
}

const workFiles = dv.pages('"09-Efficiency/Work Efficiency"');
const rows = [];
for (const page of workFiles) {
  const avg = await monthWorkAverage(page.file.path);
  rows.push([page.file.name, avg !== null ? avg.toFixed(1) + '%' : '—']);
}
rows.sort((a, b) => a[0].localeCompare(b[0]));
dv.header(3, "Work Efficiency by Month");
dv.table(['Month', 'Avg Efficiency'], rows);
```

---

## Every Day

```dataviewjs
async function readTaskEfficiency(y, m, day) {
  const path = `09-Efficiency/Work Efficiency/${y}-${String(m).padStart(2,'0')}.md`;
  const file = app.vault.getAbstractFileByPath(path);
  if (!file) return null;
  const content = await app.vault.read(file);
  const lines = content.split('\n');
  const dayRegex = /^> \[!card\] (.+) · (\d+) /;
  const taskRegex = /^> - \[( |x|X)\] ?(.*)$/;
  let planned = 0, done = 0, found = false, capturing = false;
  for (const line of lines) {
    const dm = line.match(dayRegex);
    if (dm) {
      if (capturing) break;
      if (Number(dm[2]) === day) { capturing = true; found = true; }
      continue;
    }
    if (capturing) {
      const tm = line.match(taskRegex);
      if (tm && tm[2].trim() !== '') {
        planned++;
        if (tm[1].toLowerCase() === 'x') done++;
      } else if (line.trim() === '' || line.startsWith('---')) {
        break;
      }
    }
  }
  if (!found || planned === 0) return null;
  return (done / planned) * 100;
}

const timeFiles = dv.pages('"09-Efficiency/Time Efficiency"').sort(p => p.file.name);
const rows = [];

for (const page of timeFiles) {
  const [y, m] = page.file.name.split('-').map(Number);
  const daysInMonth = new Date(y, m, 0).getDate();
  for (let day = 1; day <= daysInMonth; day++) {
    const dd = String(day).padStart(2, '0');
    const worked = page['worked_' + dd];
    const planned = page['planned_' + dd];
    const req = (worked !== undefined && worked !== null && worked !== '') ? (worked / 12) * 100 : null;
    const act = (req !== null && planned !== undefined && planned !== null && planned !== '' && planned > 0) ? (worked / planned) * 100 : null;
    const workEff = await readTaskEfficiency(y, m, day);
    if (req === null && workEff === null) continue;
    const label = new Date(y, m - 1, day).toLocaleDateString('default', { day: 'numeric', month: 'short', year: 'numeric' });
    rows.push([
      label,
      req !== null ? req.toFixed(1) + '%' : '—',
      act !== null ? act.toFixed(1) + '%' : '—',
      workEff !== null ? workEff.toFixed(1) + '%' : '—'
    ]);
  }
}

dv.table(['Date', 'Required Eff.', 'Actual Eff.', 'Work Efficiency'], rows);
```
