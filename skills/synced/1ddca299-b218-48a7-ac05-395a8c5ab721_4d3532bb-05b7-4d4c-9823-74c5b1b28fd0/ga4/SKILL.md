---
name: ga4
description: "Comprehensive guide and workflow for Google Analytics 4 (GA4) reporting and traffic analysis. Covers selecting GA4 accounts/properties, querying metrics (sessions, active users, engagement rate, conversions, total revenue) and dimensions (source/medium, channel group, page path, date), filtering, period-over-period comparisons, generating CSV exports, and plotting visualization charts. Use for any GA4 task: traffic analysis, acquisition reports, audience breakdown, or conversion analytics."
---

# GA4 Analytics & Reporting Skill Guide

This skill provides step-by-step instructions for querying, analyzing, and visualizing Google Analytics 4 (GA4) data within Markifact.

---

## Core Execution Pattern

When performing any GA4 analytics or reporting task:
1. **Discover**: Confirm available tools via `find_operations` if not already loaded.
2. **Inspect**: Always check input schemas using `get_operation_inputs` before executing an operation for the first time.
3. **Execute**: Run operations via `run_operation` (`ga4_select_accounts`, `ga4_get_report`).

---

## 1. Account Discovery & Selection

Before fetching GA4 reports:
1. Call `ga4_select_accounts` with `selection_mode: 'all'` or `selection_mode: 'filter'` to retrieve available GA4 properties and property IDs.
2. If the user specifies a website or account name, filter or select the matching property value/label.

---

## 2. Running GA4 Reports (`ga4_get_report`)

Use `ga4_get_report` to query metrics and dimensions across selected GA4 properties.

### Standard Inputs
- `accounts`: List of account/property objects or property ID strings returned from `ga4_select_accounts`.
- `metrics`: Array of metric IDs (e.g. `['sessions', 'activeUsers', 'engagementRate', 'views', 'totalRevenue']`).
- `dimensions`: Array of dimension IDs (e.g. `['sessionSourceMedium', 'sessionDefaultChannelGroup', 'pagePath', 'date']`).
- `date_range`:
  - Presets: `LAST_7_DAYS`, `LAST_14_DAYS`, `LAST_30_DAYS`, `THIS_MONTH_TO_DATE`, `LAST_MONTH`.
  - Fixed range: `preset: 'FIXED'`, `start: 'YYYY-MM-DD'`, `end: 'YYYY-MM-DD'`.
- `filters`: Array of filter objects with `field`, `operator` (`EQUALS`, `CONTAINS`, `REGEXP_MATCH`, etc.), and `value`.
- `orders`: Sort settings, e.g. `[{'field': 'sessions', 'direction': 'DESC'}]`.
- `limit`: Maximum rows to return.

### Period-Over-Period Comparison
To compare current period against a prior period:
- Set `date_range.compare` object:
  - `preset`: `'previous_period'`, `'previous_month_same_dates'`, or `'previous_year'`.
  - `comparison_format`: `'rows'` or `'columns'`.

---

## 3. Data Visualization & Reporting Workflow

### 1. Data Processing
- Save returned JSON data or CSV previews into `/workspace/files/file-ga4-report.csv`.
- Clean, group, or calculate percentage shares using Python scripts executed via `shell`.

### 2. Creating Visual Charts
- Use Python (`pandas` + `matplotlib` / `seaborn`) to create clear, modern charts.
- Save charts in `/workspace/files/file-ga4-chart.png`.
- Obtain safe file URLs with `get_file_url("file-ga4-chart.png")`.
- Display images in your final response using Markdown: `![GA4 Chart](URL)`.

### 3. Key Metrics Reference
Refer to `references/ga4_metrics_dimensions.md` for exact naming conventions of GA4 metrics and dimensions.
