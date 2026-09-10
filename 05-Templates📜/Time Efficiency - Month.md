<%*
// Prompts for a month, then builds the full day-by-day card layout.
const input = await tp.system.prompt("Month to create (YYYY-MM)", tp.date.now("YYYY-MM"));
const [y, m] = input.split("-").map(Number);
const daysInMonth = new Date(y, m, 0).getDate();
const monthName = new Date(y, m - 1, 1).toLocaleString('default', { month: 'long' });

let front = "---\n";
front += `month: ${input}\n`;
for (let d = 1; d <= daysInMonth; d++) {
  const dd = String(d).padStart(2, '0');
  front += `planned_${dd}: \n`;
  front += `worked_${dd}: \n`;
}
front += "---\n\n";

let body = `# Time Efficiency — ${monthName} ${y}\n\n`;
body += "Enter planned and worked hours for each day. Efficiency is calculated automatically as Worked ÷ 12 hrs.\n\n";

for (let d = 1; d <= daysInMonth; d++) {
  const dd = String(d).padStart(2, '0');
  const wd = new Date(y, m - 1, d).toLocaleDateString('default', { weekday: 'long' });
  body += `> [!card] ${wd} · ${d} ${monthName}\n`;
  body += `> **Planned Hrs** \`INPUT[number:planned_${dd}]\`&nbsp;&nbsp;&nbsp;&nbsp;**Worked Hrs** \`INPUT[number:worked_${dd}]\`\n`;
  body += `>\n`;
  body += `> Efficiency: \`VIEW[round(({worked_${dd}} / 12) * 100, 1)][text]\`%\n\n`;
}

body += "---\n\n## Month Summary\n\n";
body += "```dataviewjs\n";
body += "const p = dv.current();\n";
body += "const rows = [];\n";
body += "let total = 0, count = 0;\n";
body += `for (let d = 1; d <= ${daysInMonth}; d++) {\n`;
body += "  const dd = String(d).padStart(2, '0');\n";
body += "  const planned = p['planned_' + dd];\n";
body += "  const worked = p['worked_' + dd];\n";
body += "  if (worked === undefined || worked === null || worked === '') continue;\n";
body += "  const eff = (worked / 12) * 100;\n";
body += "  total += eff; count++;\n";
body += "  rows.push([dd, planned ?? '—', worked, eff.toFixed(1) + '%']);\n";
body += "}\n";
body += "dv.table(['Day','Planned','Worked','Efficiency'], rows);\n";
body += "if (count > 0) {\n";
body += "  dv.paragraph(`**Month average efficiency: ${(total/count).toFixed(1)}%** (based on ${count} logged days)`);\n";
body += "} else {\n";
body += "  dv.paragraph('No days logged yet.');\n";
body += "}\n";
body += "```\n";

tR += front + body;

// Move this file into the right folder and rename it to the month
await tp.file.move("/Efficiency/Time Efficiency/" + input);
-%>
