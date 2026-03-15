---
tags:
  - status/hub
  - finance
  - cs/dsa
created:
  "{ date }":
---

# 💰 Finance & Business - Master Index

## 🗺️ Topic Hubs
| Topic          | Tag Hub                           | Notes Count                               |
| -------------- | --------------------------------- | ----------------------------------------- |
| Stocks         | [[DSA]]                           | `$= dv.pages('#finance/stocks').length`   |
| Market         | [[3-Tags/Finance/Market]]         | `$= dv.pages('#finance/market').length`   |
| Business Ideas | [[3-Tags/Finance/Business-Ideas]] | `$= dv.pages('#finance/business').length` |
| Startups       | [[3-Tags/Finance/Startups]]       | `$= dv.pages('#finance/startup').length`  |
|                |                                   |                                           |

## 📊 Watchlist
```dataview
TABLE ticker, sector, status
FROM #finance/stocks
WHERE type = "watchlist"
SORT file.mtime DESC
```

## 💡 Active Ideas
```dataview
TABLE stage, potential
FROM #finance/business
WHERE stage != "archived"
SORT potential DESC
```

## 🔗 Related
- [[CS-Index]] - For fintech
- [[Blockchain]] - Crypto/DeFi