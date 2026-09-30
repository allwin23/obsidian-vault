---
type: bucketlist
---

# 🪣 Bucket List

*Every goal has its own Bucket List section. This page pulls every bucket item from every goal, grouped under the goal it belongs to (with the dream it serves), so you can see what's left to complete without opening each note.*

```dataview
TASK
FROM "08-Goals-System/Goals"
GROUP BY string(file.link) + " — " + string(default(dream, "No dream linked"))
```
