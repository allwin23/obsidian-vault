---
tags: [status/hub, personal]
created: {{date}}
---

# 🧘 Personal - Master Index

## 🗺️ Areas
| Area | Tag Hub | Latest |
|------|---------|--------|
| Journal | [[3-Tags/Personal/Journal]] | [[{{date:YYYY-MM-DD}}]] |
| Mental Health | [[3-Tags/Personal/Mental-Health]] | - |
| Goals | [[3-Tags/Personal/Goals]] | - |

## 📅 Recent Journal Entries
```dataview
TABLE mood, energy
FROM #personal/journal
SORT file.name DESC
LIMIT 7
```

## 🎯 Active Goals
```dataview
TABLE status, deadline
FROM #personal/goals
WHERE status != "done"
SORT deadline ASC
```

## 🧠 Mental Health Trends
```dataview
TABLE mood_score, anxiety, energy
FROM #personal/mental
SORT file.name DESC
LIMIT 7
```