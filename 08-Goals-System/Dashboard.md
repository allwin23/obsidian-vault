---
type: dashboard
---

# 🧭 Dashboard

## 🎯 Current Focus (what you're actually working on right now)
```dataview
TABLE domain as "Domain", dream as "Dream", deadline as "Deadline", progress as "Progress %"
FROM "Goals"
WHERE current-focus = true AND status != "done"
SORT deadline asc
```

## 📋 All Active Goals, by timeframe
```dataview
TABLE domain as "Domain", timeframe as "Timeframe", status as "Status", deadline as "Deadline"
FROM "Goals"
WHERE status = "in-progress" OR status = "not-started"
SORT timeframe asc, deadline asc
```

## 🪣 Open Bucket List Items
```dataview
TASK
FROM "Bucket List"
WHERE !completed
```

## 🏆 Recently Achieved
```dataview
TABLE domain as "Domain", dream as "Dream"
FROM "Goals"
WHERE status = "done"
SORT file.mtime desc
LIMIT 5
```
