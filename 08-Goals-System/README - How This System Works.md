---
type: readme
---

# 🧭 How This System Works

This vault is organized in **4 layers**. Each layer is its own kind of note, linked to the one above it.

```
DOMAIN  (a life area — doesn't get its own note, it's just a tag/heading)
  └── DREAM   (the big 10+ year vision in that domain — 1 note per dream)
        └── GOAL   (a concrete, time-bound step toward the dream — 1 note per goal)
              └── BUCKET LIST ITEM   (a single tick-able experience/milestone)
```

### The four layers, in plain terms

1. **Domains** — the fixed buckets of your life: Career, Financial, Personal, Health, Relationships, Growth, Travel/Experience (edit this list to whatever fits you). You don't make a note for a domain — it's just a property (`domain:`) every Dream carries, so you can filter/group by it.

2. **Dreams** — the "big picture" per domain. One dream note = one long-term vision (e.g. "Financial: Fully financially independent by 40"). This rarely changes.

3. **Goals** — the building blocks of a Dream. Each goal links back to its parent dream (`dream:: [[...]]`), has a `timeframe` (short/mid/long), a `status`, and a `progress` %. **This is the layer that updates constantly** — that's expected and good.

4. **Bucket List** — single tick-off items/experiences, each tagged to the dream they belong to (or standalone, no dream needed). Lives in one running file: `Bucket List.md`.

### Folders
```
📁 Dreams/       one file per dream (use Templates/Dream Template.md)
📁 Goals/        one file per goal  (use Templates/Goal Template.md)
📁 Templates/    the two templates above
📄 Dashboard.md  the single page you open daily — pulls everything together
📄 Bucket List.md  your full bucket list, grouped by domain
```

### Daily use
Open **`Dashboard.md`** every day. That's the "manifest it" page — it auto-shows:
- Your Dreams, one line each, by priority
- Your **Current Focus** goals (the short-term ones you flagged `current-focus: true`)
- Your open Bucket List items

You only ever *edit* Goal notes (update status/progress) and tick Bucket List checkboxes. Dreams stay mostly static; Dashboard never needs manual editing — it queries live.

### Setup (2 minutes)
1. Install the **Dataview** community plugin (Settings → Community plugins → Browse → search "Dataview" → Install & Enable). This is what makes Dashboard.md and the Dream notes auto-populate.
2. Drop all these folders/files into your vault, keeping the folder names (`Dreams`, `Goals`, `Templates`) — the queries reference these paths.
3. In Settings → Templates, set the template folder to `Templates/` so you can insert them with `Ctrl/Cmd + P → Insert Template`.
4. Duplicate the example Dream + Goal I've included, rename them, delete the example content, and start filling in your real ones.

### The status/field vocabulary (keep it consistent — this is what makes filtering work)

**Dream `status`**: `active` · `achieved` · `paused` · `dropped`
**Goal `timeframe`**: `short-term` · `mid-term` · `long-term`
**Goal `status`**: `not-started` · `in-progress` · `done` · `dropped`
**Goal `current-focus`**: `true` / `false` — flip this on for whatever you're actively working on *right now* (keep this to ~3-5 goals max across your whole life, or "current focus" stops meaning anything)
**Priority** (on Dreams): `high` · `medium` · `low`

Keep these exact spellings — Dataview queries filter on exact text.
