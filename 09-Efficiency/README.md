# Efficiency Vault — Setup

## 1. Install required plugins
Community plugins → confirm these are installed and enabled:
- **Dataview**
- **Templater**
- **Meta Bind**

## 2. Copy the folder
Drop the whole `Efficiency` folder into your vault root (so paths match: `Efficiency/Dashboard.md`, `Efficiency/Time Efficiency/`, `Efficiency/Work Efficiency/`, `Efficiency/Templates/`, `Efficiency/Assets/`).

## 3. Enable the CSS snippet
Settings → Appearance → CSS snippets → copy `Assets/efficiency-style.css` into your vault's `.obsidian/snippets/` folder → toggle it on. Styles the Time Efficiency table and the Work Efficiency cards.

## 4. Point Templater at the templates
Settings → Templater → Template folder location → set to `Efficiency/Templates`.

## 5. Using it day to day

**Time Efficiency** — `Efficiency/Time Efficiency/2026-09.md` is one table, each row a date. Two plain number inputs per row (Planned Hrs, Worked Hrs), two efficiency columns fill in automatically as you type:
- **Required Efficiency** = Worked Hrs ÷ 12 — how you're doing against a fixed 12-hour standard
- **Actual Efficiency** = Worked Hrs ÷ Planned Hrs — how you're doing against what you actually planned for that day

**Work Efficiency** — `Efficiency/Work Efficiency/2026-09.md` still uses one card per day (a checklist doesn't fit a table row). Fill in your planned tasks each morning, check them off — efficiency (completed ÷ planned) is computed automatically, no card edits needed to change the calculation.

**New month** — no prompts to fill in. Just run the Templater template (`Time Efficiency - Month` or `Work Efficiency - Month`) from the command palette on or after the 1st, and it detects the current month itself and files the new note in the right folder. (Work Efficiency will still ask how many task slots per day, since that's a personal preference, not derivable from the date.)

**Dashboard** — `Efficiency/Dashboard.md`. Pick any date in the target week with the date picker at the top; the weekly table (Required / Actual / Work) and averages update immediately below. Monthly averages and the full daily log are further down, always current.

## Notes
- None of the calculation logic is visible when reading a note — it renders as plain input boxes and numbers, like a web form. You'd only see the underlying code in Source Mode.
- September 2026 is pre-built and ready to use right away.
