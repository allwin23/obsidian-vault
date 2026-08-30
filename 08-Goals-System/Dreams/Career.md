---
type: dream
domain: Career
status: active
priority: high
target-year: 2032
created: 2026-08-28
tags:
  - dream
---

# 🌟 Career - Example Dream (rename this file to your real dream)

## Vision
*Example: "I lead a small, sharp engineering team building something I actually believe in — I'm known for judgment, not just output."*

## Why this matters to me
*Example: "I've spent years executing other people's vision. I want the next chapter to be mine to shape."*

## Linked Goals
```dataview
TABLE status as "Status", timeframe as "Timeframe", deadline as "Deadline", progress as "Progress %"
WHERE type = "goal" and dream and contains(string(dream), this.file.name)
SORT choice(timeframe = "short-term", 1, choice(timeframe = "mid-term", 2, 3)) asc
```


## Bucket List tied to this Dream
```dataview
TASK
FROM "Bucket List"
WHERE contains(tags, "dream/" + this.file.name)
```

## Notes / Reflections
- 2026-08-28: Dream created — delete this example once you've made your real ones.
