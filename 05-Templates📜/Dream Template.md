---
type: dream
domain: 
status: active
priority: medium
target-year: 
created: {{date}}
tags:
  - dream
---

# 🌟 {{title}}

## Vision
*What does this actually look like when it's real? Be specific — picture it.*



## Why this matters to me
*The real reason, not the surface one.*



## Linked Goals
```dataview
TABLE status as "Status", timeframe as "Timeframe", deadline as "Deadline", progress as "Progress %"
FROM "Goals"
WHERE dream and contains(string(dream), this.file.name)
SORT choice(timeframe = "short-term", 1, choice(timeframe = "mid-term", 2, 3)) asc
```

## Bucket List tied to this Dream
```dataview
TASK
FROM "Bucket List"
WHERE contains(tags, "dream/" + this.file.name)
```

## Notes / Reflections
*Anything that shifts how you see this dream — log dated entries below.*

- {{date}}: 
