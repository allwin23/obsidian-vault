# Daily Hours & Outcome Tracker (Aug 31 – Oct 15)

  

```dataviewjs

const entries = {

  "2026-08-31": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-01": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-02": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-03": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-04": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-05": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-06": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-07": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-08": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-09": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-10": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-11": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-12": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-13": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-14": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-15": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-16": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-17": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-18": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-19": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-20": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-21": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-22": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-23": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-24": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-25": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-26": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-27": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-28": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-29": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-09-30": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-01": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-02": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-03": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-04": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-05": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-06": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-07": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-08": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-09": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-10": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-11": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-12": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-13": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-14": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },

  "2026-10-15": { planned: 0, completed: 0, totalPlannedOutcome: 0, completedOutcome: 0 },};

  

const REQUIRED_BASE_HRS = 12; // Required Hr % = completed / 12 * 100

  

const rows = Object.entries(entries).map(([dateStr, d]) => {

  const hasPlanned = d.planned > 0;

  const hasCompleted = d.completed > 0;

  const hasOutcome = d.totalPlannedOutcome > 0;

  

  const todayEffPct = hasPlanned

    ? ((d.completed / d.planned) * 100).toFixed(1) + "%"

    : "-";

  

  const requiredHrPct = hasCompleted

    ? ((d.completed / REQUIRED_BASE_HRS) * 100).toFixed(1) + "%"

    : "-";

  

  const completedOutcomeEffPct = hasOutcome

    ? ((d.completedOutcome / d.totalPlannedOutcome) * 100).toFixed(1) + "%"

    : "-";

  

  return [

    dateStr,

    d.planned,

    d.completed,

    todayEffPct,

    requiredHrPct,

    d.totalPlannedOutcome,

    d.completedOutcome,

    completedOutcomeEffPct

  ];

});

  

dv.table(

  [

    "Date",

    "Planned Hrs",

    "Completed Hrs",

    "Today Eff %",

    "Required Hr %",

    "Total Planned Outcome",

    "Completed Outcome",

    "Completed Outcome Eff %"

  ],

  rows

);

```

  

## Column logic reference

| Column | Type | Formula |

|---|---|---|

| Today Planned Hrs | Entered | manual number |

| Completed Hrs | Entered | manual number |

| Today Eff % | Auto | `completed / planned * 100` |

| Required Hr % | Auto | `completed / 12 * 100` |

| Total Planned Outcome | Entered | manual number |

| Completed Outcome | Entered | manual number |

| Completed Outcome Eff % | Auto | `completedOutcome / totalPlannedOutcome * 100` |