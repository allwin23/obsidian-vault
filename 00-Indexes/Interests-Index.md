---
tags:
  - status/hub
  - interest
created:
  "{ date }":
---

---
tags: [status/literature]
created: 2026-02-17
type: book | article | video | course | paper | podcast
title: 
author: 
url: 
area: cs | finance | interest | personal
---

# 📖 Interests-Index

## 📋 Metadata
| | |
|---|---|
| Type | |
| Author | |
| URL | |
| Date Consumed | 2026-02-17 |

## 🎯 Why I Read/Watched This


## 📝 Raw Notes
### Key Points
- 

### Quotes
> 

## 💡 Ideas to Extract
- [ ] Idea 1 → Create: [[]]
- [ ] Idea 2 → Create: [[]]

## 🔗 Connect To
- [[Tag Hub]]
- [[Related Note]] 
# 🎯 Interests - Master Index

## 🗺️ Topic Hubs
| Topic | Tag Hub | Notes Count |
|-------|---------|-------------|
| Books | [[3-Tags/Interests/Books]] | `$= dv.pages('#interest/books').length` |
| Other | [[3-Tags/Interests/Other]] | `$= dv.pages('#interest/other').length` |

## 📚 Reading List
### Currently Reading
```dataview
TABLE author, rating
FROM #interest/books
WHERE reading_status = "reading"
```

### Completed
```dataview
TABLE author, rating, finished
FROM #interest/books
WHERE reading_status = "done"
SORT finished DESC
LIMIT 10
```

### To Read
```dataview
LIST
FROM #interest/books
WHERE reading_status = "todo"
```