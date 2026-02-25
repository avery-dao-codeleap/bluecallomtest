# Analytics

**URL:** `/app/overviewAnalytics` (entry)
**Access:** Authenticated + corp-connected users
**Home tile:** Analytics — description text only (no stats)

## Overview

The Analytics section provides four dashboards tracking AAIS (AI-Assisted Intelligence Solution) performance across the organisation. Each sub-page is a separate route accessible via the shared nav bar. All charts use a year-based period picker (2026/2025/2024/2023). For a new account most charts show "No chart data available for the selected period.", but the productivity/consumption vs cost charts do render with organisational data.

**Common layout across all analytics pages:**
- No sidebar panels (no My Messages, no My Connections — just My Profile card)
- Persistent nav bar: Overview | Usage | Productivity | Consumption
- Persistent tooltip: "Click here to go to Consumption Analytics"
- Each chart panel has a help icon (?) and a "Select Period:" combobox

---

## Sub-Page: Overview (`/app/overviewAnalytics`)

**Section heading:** Analytics Dashboard

### Chart Panels

| Panel | Filter | Empty State |
|-------|--------|-------------|
| AAIS Overview | Select Period: 2026/2025/2024/2023 | "No chart data available for the selected period." |

> The AAIS Overview chart renders an X/Y scatter plot (axes: "Overall Usage →" and "↑ Productivity") when data is present. For this account no data is shown for 2026.

---

## Sub-Page: Usage (`/app/usageAnalytics`)

**Section heading:** Analytics Dashboard - Usage

### Chart Panels (7 total, arranged in pairs)

| Panel | Dimension |
|-------|-----------|
| Monthly Usage by AI Asset | By asset type |
| YTD % of Usage by AI Asset | By asset type (% share) |
| Monthly Usage by Segment | By business segment |
| YTD % of Usage by Segment | By segment (% share) |
| Monthly Usage by Organization | By org unit |
| YTD % of Usage by Organization | By org unit (% share) |
| YTD % of Usage by User | By individual user |

All 7 panels show "No chart data available for the selected period." for 2026.

---

## Sub-Page: Productivity (`/app/productivityAnalytics`)

**Section heading:** Analytics Dashboard - Productivity

### Chart Panels (9 total)

| Panel | Has Data? |
|-------|-----------|
| Monthly Productivity gain by AI Asset | No |
| YTD Productivity gain by AI Asset | No |
| Monthly Productivity gain by Segment | No |
| YTD Productivity gain by Segment | No |
| Monthly Productivity gain by Organization | No |
| YTD Productivity gain by Organization | No |
| Monthly Productivity gain by Flight | No |
| YTD Productivity gain by Flight | No |
| **Monthly Productivity gain vs cost** | **Yes — bar chart** |
| **YTD Productivity gain vs cost** | **Yes — pie/donut chart** |
| YTD Productivity gain by User | No |

### Monthly Productivity Gain vs Cost (bar chart with data)

- **X-axis:** Jan'26, Feb'26
- **Y-axis:** 0k → 200k
- **Legend:** Cost (dark blue bar) | Gain (medium blue bar)
- Jan'26: Cost ~50k, Gain ~0
- Feb'26: Cost ~0, Gain ~200k

### YTD Productivity Gain vs Cost

- Pie/donut chart rendered with one large blue circle

---

## Sub-Page: Consumption (`/app/consumptionAnalytics`)

**Section heading:** Analytics Dashboard - Consumption

### Chart Panels (9 total)

| Panel | Has Data? |
|-------|-----------|
| Monthly Consumption by AI Asset | No |
| YTD Consumption by AI Asset | No |
| Monthly Consumption by Segment | No |
| YTD Consumption by Segment | No |
| Monthly Consumption by Flight | No |
| YTD Consumption by Flight | No |
| Monthly Consumption by Organization | No |
| **Monthly Consumption Vs Productivity** | **Yes — bar chart** |
| YTD Consumption by User | No |

### Monthly Consumption Vs Productivity (bar chart with data)

Same chart structure as Productivity page:
- **X-axis:** Jan'26, Feb'26
- **Y-axis:** 0k → 200k
- **Legend:** Cost | Gain
- Shows identical data to the Productivity gain vs cost chart

---

## Common Controls

| Control | Options | Default |
|---------|---------|---------|
| Select Period | 2026 / 2025 / 2024 / 2023 | 2026 |
| Help icon (?) | Tooltip with chart description | — |

---

## Route Summary

| Route | Heading | Chart Count |
|-------|---------|-------------|
| `/app/overviewAnalytics` | Analytics Dashboard | 1 |
| `/app/usageAnalytics` | Analytics Dashboard - Usage | 7 |
| `/app/productivityAnalytics` | Analytics Dashboard - Productivity | 9 (2 with data) |
| `/app/consumptionAnalytics` | Analytics Dashboard - Consumption | 9 (1 with data) |

---

## Screenshots

| File | Description |
|------|-------------|
| `screenshots/21-analytics-overview.png` | Overview analytics (AAIS Overview, empty) |
| `screenshots/21-analytics-usage.png` | Usage analytics (7 chart panels) |
| `screenshots/21-analytics-productivity.png` | Productivity analytics (full page — bar/pie charts visible) |
| `screenshots/21-analytics-consumption.png` | Consumption analytics (full page — Cost vs Productivity chart visible) |
