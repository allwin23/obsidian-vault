# Efficiency Vault — Setup

## 1. Install required plugins
Community plugins → confirm these are installed and enabled:
- **Dataview** (with "Enable JavaScript Queries" turned on in Dataview settings)
- **Templater**

Meta Bind is no longer needed — every input field is now a real HTML input rendered directly by Dataview, so there's no bracket syntax (`INPUT[...]`, `VIEW[...]`) showing anywhere.

## 2. Copy the folder
Drop the whole `Efficiency` folder into your vault root (so paths match: `Efficiency/Dashboard.md`, `Efficiency/Time Efficiency/`, `Efficiency/Work Efficiency/`, `Efficiency/Templates/`, `Efficiency/Assets/`).

## 3. Enable the CSS snippet
Settings → Appearance → CSS snippets → copy `Assets/efficiency-style.css` into your vault's `.obsidian/snippets/` folder → toggle it on.

## 4. Point Templater at the templates
Settings → Templater → Template folder location → set to `Efficiency/Templates`.

## 5. Using it day to day

**Time Efficiency** — `Efficiency/Time Efficiency/2026-09.md` is one real table, one row per date, with two plain number boxes (placeholder text "hrs") for Planned and Worked. Type a value and the two efficiency columns on the same row update instantly:
- **Required Efficiency** = Worked ÷ 12
- **Actual Efficiency** = Worked ÷ Planned

Values save automatically the moment you click or tab out of the box (no separate save step). Nothing but the table itself is visible — no code, no brackets.

**Work Efficiency** — `Efficiency/Work Efficiency/2026-09.md` still uses one card per day (a checklist doesn't fit a table row). Fill in your planned tasks each morning, check them off — efficiency (completed ÷ planned) is calculated automatically.

**New month** — run the Templater template (`Time Efficiency - Month` or `Work Efficiency - Month`) from the command palette on or after the 1st. Time Efficiency needs no prompt at all — it detects the current month and files itself. Work Efficiency will still ask how many task slots per day, since that's a personal preference.

**Dashboard** — `Efficiency/Dashboard.md`. Pick a date with the date box at the top (any day in the week you want); the weekly table (Required / Actual / Work) and averages update right below it. Monthly averages and the full daily log are further down, always current.

## Notes
- Everything renders as an actual form/table — nothing shows as code in Reading or Live Preview. You'd only see the underlying script in Source Mode.
- September 2026 is pre-built and ready to use right away.
