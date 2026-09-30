---
type: dashboard
---

# 🧭 Dashboard

## 🎯 Current Focus (what you're actually working on right now)
```dataview
TABLE dream as "Dream", timeframe as "Timeframe", deadline as "Deadline", progress as "Progress %"
FROM "08-Goals-System/Goals"
WHERE current_focus = true AND achieved != true
SORT deadline asc
```

## 📋 All Active Goals, by date
```dataview
TABLE dream as "Dream", timeframe as "Timeframe", deadline as "Deadline", progress as "Progress %"
FROM "08-Goals-System/Goals"
WHERE achieved != true
SORT deadline asc
```

## 🪣 Open Bucket List Items
```dataview
TASK
FROM "08-Goals-System/Goals"
WHERE !completed
GROUP BY string(file.link) + " — " + string(default(dream, "No dream linked"))
```

## 🏆 Recently Achieved
```dataview
TABLE deadline as "Deadline"
FROM "08-Goals-System/Goals"
WHERE achieved = true
SORT file.mtime desc
LIMIT 5
```
