/* Efficiency vault — styling
   Enable via Settings → Appearance → CSS snippets → "efficiency-style" */

/* Time Efficiency input table (rendered by dataviewjs as real <table>/<input>) */
.eff-time-wrap {
  margin: 10px 0 18px 0;
  overflow-x: auto;
}

.eff-table {
  border-collapse: collapse;
  width: 100%;
}

.eff-table th {
  text-align: left;
  font-weight: 600;
  background: var(--background-secondary);
  padding: 6px 12px;
  border-bottom: 2px solid var(--background-modifier-border);
  white-space: nowrap;
}

.eff-table td {
  padding: 5px 12px;
  border-bottom: 1px solid var(--background-modifier-border);
  white-space: nowrap;
}

.eff-table input[type="number"] {
  width: 64px;
  text-align: center;
  border-radius: 6px;
  border: 1px solid var(--background-modifier-border);
  padding: 3px 4px;
  background: var(--background-primary);
}

.eff-table td.eff-value {
  font-weight: 600;
}

/* Dashboard week picker */
.eff-week-pick {
  margin: 6px 0 16px 0;
}

.eff-week-pick input[type="date"] {
  border-radius: 6px;
  border: 1px solid var(--background-modifier-border);
  padding: 4px 8px;
  background: var(--background-primary);
}

/* Work Efficiency day-jump picker */
.eff-day-jump {
  margin: 6px 0 16px 0;
}

.eff-day-jump input[type="date"] {
  border-radius: 6px;
  border: 1px solid var(--background-modifier-border);
  padding: 4px 8px;
  background: var(--background-primary);
  margin-right: 8px;
}

.eff-day-jump button {
  border-radius: 6px;
  padding: 4px 10px;
}

.eff-highlight {
  transition: background-color 0.3s ease;
  background-color: var(--text-selection) !important;
}

/* Work Efficiency day cards */
.callout[data-callout="card"] {
  border: 1px solid var(--background-modifier-border);
  border-radius: 10px;
  background: var(--background-secondary);
  padding: 14px 18px 16px 18px;
  margin: 14px 0;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.06);
}

.callout[data-callout="card"] .callout-icon {
  display: none;
}

.callout[data-callout="card"] .callout-title {
  font-weight: 600;
  font-size: 1em;
  letter-spacing: 0.01em;
  color: var(--text-normal);
  padding-bottom: 6px;
  margin-bottom: 8px;
  border-bottom: 1px solid var(--background-modifier-border);
}

.callout[data-callout="card"] .callout-title-inner {
  color: var(--text-normal);
}

.callout[data-callout="card"] .task-list-item {
  margin: 4px 0;
}

/* dataview-rendered result tables (month summaries, dashboard rollups) */
.dataview.table-view-table {
  border-collapse: collapse;
  width: 100%;
  margin: 8px 0 16px 0;
}

.dataview.table-view-table th {
  text-align: left;
  font-weight: 600;
  border-bottom: 2px solid var(--background-modifier-border);
  padding: 6px 10px;
}

.dataview.table-view-table td {
  padding: 6px 10px;
  border-bottom: 1px solid var(--background-modifier-border);
}