<%*
// Prompts for a month, then builds day-by-day task cards.
const input = await tp.system.prompt("Month to create (YYYY-MM)", tp.date.now("YYYY-MM"));
const [y, m] = input.split("-").map(Number);
const daysInMonth = new Date(y, m, 0).getDate();
const monthName = new Date(y, m - 1, 1).toLocaleString('default', { month: 'long' });
const numTasks = Number(await tp.system.prompt("Task slots per day", "6"));

let body = `# Work Efficiency — ${monthName} ${y}\n\n`;
body += "Plan each day's tasks at the start of the day. Efficiency is calculated automatically as completed ÷ planned tasks.\n\n";

for (let d = 1; d <= daysInMonth; d++) {
  const wd = new Date(y, m - 1, d).toLocaleDateString('default', { weekday: 'long' });
  body += `> [!card] ${wd} · ${d} ${monthName}\n`;
  for (let i = 0; i < numTasks; i++) {
    body += `> - [ ] \n`;
  }
  body += "\n";
}

body += "---\n\n## Month Summary\n\n";
body += "```dataviewjs\n";
body += "const file = dv.current();\n";
body += "const content = await app.vault.read(app.vault.getAbstractFileByPath(file.file.path));\n";
body += "const lines = content.split('\\n');\n";
body += "const dayRegex = /^> \\[!card\\] (.+)$/;\n";
body += "const taskRegex = /^> - \\[( |x|X)\\] ?(.*)$/;\n";
body += "const rows = [];\n";
body += "let currentDay = null, planned = 0, done = 0;\n";
body += "let total = 0, count = 0;\n";
body += "function flush() {\n";
body += "  if (currentDay && planned > 0) {\n";
body += "    const eff = (done / planned) * 100;\n";
body += "    rows.push([currentDay, `${done}/${planned}`, eff.toFixed(1) + '%']);\n";
body += "    total += eff; count++;\n";
body += "  }\n";
body += "}\n";
body += "for (const line of lines) {\n";
body += "  const dm = line.match(dayRegex);\n";
body += "  if (dm) { flush(); currentDay = dm[1]; planned = 0; done = 0; continue; }\n";
body += "  const tm = line.match(taskRegex);\n";
body += "  if (tm && tm[2].trim() !== '') {\n";
body += "    planned++;\n";
body += "    if (tm[1].toLowerCase() === 'x') done++;\n";
body += "  }\n";
body += "}\n";
body += "flush();\n";
body += "dv.table(['Day','Completed','Efficiency'], rows);\n";
body += "if (count > 0) {\n";
body += "  dv.paragraph(`**Month average efficiency: ${(total/count).toFixed(1)}%** (based on ${count} planned days)`);\n";
body += "} else {\n";
body += "  dv.paragraph('No tasks planned yet.');\n";
body += "}\n";
body += "```\n";

tR += body;

await tp.file.move("/Efficiency/Work Efficiency/" + input);
-%>
