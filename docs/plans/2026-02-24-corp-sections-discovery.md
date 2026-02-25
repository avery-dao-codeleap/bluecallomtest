# Corp-Connected Sections Discovery Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Now that the account is connected to an organization, explore all previously corp-gated sections using Playwright MCP, document every flow and UI element, and update the knowledge base.

**Architecture:** Playwright MCP browser automation → screenshots + accessibility snapshots → structured markdown docs. Each section gets its own knowledge base file (or updates an existing one). The existing `07-restricted-sections.md` becomes a redirect/changelog doc pointing to the new section files.

**Tech Stack:** Playwright MCP (`browser_navigate`, `browser_snapshot`, `browser_take_screenshot`, `browser_click`, `browser_wait_for`, `browser_evaluate`), git

---

## Sections to Analyze

Previously restricted routes now expected to be accessible:

| Section | Key Routes | Existing Doc |
|---------|-----------|--------------|
| Corp Portal (home) | `/app/manageCorp`, `/app/manageTeam`, `/app/orgCoinManagement`, `/app/manageOrg` | `03-corp-portal.md` (partial) |
| Action Space | `/app/actionSpace`, `/app/flight`, `/app/flightDirector`, `/app/chatMode` | none |
| Analytics | `/app/overviewAnalytics`, `/app/usageAnalytics`, `/app/productivityAnalytics`, `/app/consumptionAnalytics` | none |
| Libraries | `/app/libraries`, `/app/corpLibrary`, `/app/exchangeHome`, `/app/exchangeList` | none |
| GPTBlue Studio sub-features | `/app/promptStudio`, `/app/agentStudio`, `/app/solutionStudio`, `/app/launchpad` | `05-gptblue-studio.md` (dashboard only) |
| Partner Portal | `/app/partnerHome` | none — may still require `partner` role |

---

## Task 1: Verify Session and Probe All Previously Restricted Routes

**Goal:** Confirm the session is active with corp access, then batch-probe all previously restricted routes to build the definitive accessible-vs-redirected map.

**Files:**
- No files to create — results inform subsequent tasks

**Step 1: Confirm logged in and corp connected**

Navigate to `/home`, wait for page load, take screenshot. Verify:
- Corp Portal tile shows `tile-active`
- Other tiles (Team, Action Space, etc.) should now also be `tile-active`
- Screenshot: `screenshots/20-home-corp-connected.png`

**Step 2: Batch probe all corp-gated routes**

Use `browser_run_code` to navigate to each route and record the final URL:

```javascript
async (page) => {
  const routes = [
    '/app/manageCorp',
    '/app/manageTeam',
    '/app/orgCoinManagement',
    '/app/manageOrg',
    '/app/manageLibrary',
    '/app/corpLibrary',
    '/app/corpLibraryList',
    '/app/actionSpace',
    '/app/flight',
    '/app/flightDirector',
    '/app/chatMode',
    '/app/overviewAnalytics',
    '/app/usageAnalytics',
    '/app/productivityAnalytics',
    '/app/consumptionAnalytics',
    '/app/libraries',
    '/app/exchangeHome',
    '/app/exchangeList',
    '/app/promptStudio',
    '/app/agentStudio',
    '/app/solutionStudio',
    '/app/launchpad',
    '/app/partnerHome',
    '/app/partnerProgramsList',
  ];
  const results = {};
  for (const route of routes) {
    await page.goto('https://bluecallom.ai' + route, { waitUntil: 'networkidle' });
    results[route] = page.url().replace('https://bluecallom.ai', '');
    if (page.url().includes('/login')) {
      // Re-login if session dropped — stop and report
      results[route] = 'SESSION_DROPPED → /login';
      break;
    }
  }
  return results;
}
```

> **Warning:** If `/app/manageCorp` drops the session (redirects to `/login`), stop the loop immediately and note it. Re-login before continuing.

**Step 3: Record results**

Create a quick access table in a scratch note (no file needed — just inform subsequent tasks). Mark each route as:
- `accessible` — URL matches the requested route
- `redirect:/home` — redirected to home
- `redirect:/login` — session dropped

**Step 4: Commit**

```bash
git add screenshots/20-home-corp-connected.png
git commit -m "docs: T1 — verify corp-connected home dashboard state"
```

---

## Task 2: Document Corp Portal Home (`/app/manageCorp`)

**Goal:** Fully document the Corporate Portal management page — the main corp admin hub. Update `03-corp-portal.md`.

**Files:**
- Modify: `docs/knowledge-base/03-corp-portal.md`
- Screenshots: `screenshots/20-corp-portal-home.png`, `screenshots/20-corp-portal-*.png` (one per sub-section)

**Step 1: Navigate and screenshot Corp Portal home**

```
browser_navigate: https://bluecallom.ai/app/manageCorp
browser_wait_for: text visible (corp section heading)
browser_take_screenshot: screenshots/20-corp-portal-home.png
browser_snapshot: capture all refs
```

**Step 2: Document the page**

Note: heading, sidebar nav items, any stats panels, tables, buttons, forms.

**Step 3: Navigate through corp sidebar sections**

For each sidebar nav item found (from `02-navigation-map.md` — corporatePortal group):
- `/app/manageTeam` — screenshot `screenshots/20-corp-manage-team.png`
- `/app/orgCoinManagement` — screenshot `screenshots/20-corp-org-coins.png`
- `/app/manageLibrary` — screenshot `screenshots/20-corp-manage-library.png`
- `/app/manageOrg` — screenshot `screenshots/20-corp-manage-org.png`
- `/app/manageCompany` — screenshot `screenshots/20-corp-manage-company.png`
- Any other accessible corp-admin routes

For each: snapshot the page, note heading, key UI elements, sub-navigation, table columns, empty states.

**Step 4: Update `03-corp-portal.md`**

Replace the "Access Restriction" section with full documentation of each corp-admin route. Add screenshots list.

**Step 5: Commit**

```bash
git add docs/knowledge-base/03-corp-portal.md screenshots/20-corp-*.png
git commit -m "docs: T2 — document Corp Portal home and admin routes"
```

---

## Task 3: Document Action Space (`/app/actionSpace`)

**Goal:** Document the Action Space section — the main hub for executing AI flights, agents, solutions, and prompts.

**Files:**
- Create: `docs/knowledge-base/20-action-space.md`
- Screenshots: `screenshots/20-action-space-*.png`

**Step 1: Navigate to Action Space**

```
browser_navigate: https://bluecallom.ai/app/actionSpace
browser_wait_for: text visible (section heading)
browser_take_screenshot: screenshots/20-action-space-overview.png
browser_snapshot
```

**Step 2: Document main Action Space page**

Note: heading, sidebar nav, any tabs/filters, main content area, empty states, buttons, table columns.

**Step 3: Navigate Action Space sub-routes**

For each sub-route in the `actionDeck` sidebar group:
- `/app/flight` — screenshot `screenshots/20-action-space-flight.png`
- `/app/flightDirector` — screenshot `screenshots/20-action-space-flight-director.png`
- `/app/chatMode` — screenshot `screenshots/20-action-space-chat.png`
- `/app/launchpad` — screenshot `screenshots/20-action-space-launchpad.png`
- `/app/exchangeHome` — screenshot `screenshots/20-action-space-exchange.png`

For each: snapshot, record heading, sidebar nav items visible, main content, empty state text.

**Step 4: Create `20-action-space.md`**

Structure:
```
# Action Space

**URL:** /app/actionSpace
**Access:** Authenticated + corp connected
**Section heading:** [observed]

## Overview
[description]

## Key Flows
### Flow 1: [name]
[steps]

## Sub-Routes
### Flight (/app/flight)
### Flight Director (/app/flightDirector)
### Chat Mode (/app/chatMode)
### Launchpad (/app/launchpad)

## UI Elements
[table]

## Empty States
[observed messages]

## Screenshots
[list]
```

**Step 5: Commit**

```bash
git add docs/knowledge-base/20-action-space.md screenshots/20-action-space-*.png
git commit -m "docs: T3 — document Action Space section and sub-routes"
```

---

## Task 4: Document Analytics (`/app/overviewAnalytics`)

**Goal:** Document all four Analytics sub-pages.

**Files:**
- Create: `docs/knowledge-base/21-analytics.md`
- Screenshots: `screenshots/21-analytics-*.png`

**Step 1: Navigate to Overview Analytics**

```
browser_navigate: https://bluecallom.ai/app/overviewAnalytics
browser_wait_for: text visible (section heading)
browser_take_screenshot: screenshots/21-analytics-overview.png
browser_snapshot
```

**Step 2: Navigate through all analytics sub-pages**

- `/app/overviewAnalytics` — screenshot `screenshots/21-analytics-overview.png`
- `/app/usageAnalytics` — screenshot `screenshots/21-analytics-usage.png`
- `/app/productivityAnalytics` — screenshot `screenshots/21-analytics-productivity.png`
- `/app/consumptionAnalytics` — screenshot `screenshots/21-analytics-consumption.png`

For each: note heading, chart/dashboard widgets visible, date filters, dropdowns, empty state behavior, any navigation.

**Step 3: Create `21-analytics.md`**

Structure:
```
# Analytics

**URL:** /app/overviewAnalytics (entry)
**Access:** Authenticated + corp connected

## Overview
[description]

## Sub-Pages
### Overview Analytics (/app/overviewAnalytics)
### Usage Analytics (/app/usageAnalytics)
### Productivity Analytics (/app/productivityAnalytics)
### Consumption Analytics (/app/consumptionAnalytics)

## UI Elements / Filters
[table of common controls]

## Screenshots
[list]
```

**Step 4: Commit**

```bash
git add docs/knowledge-base/21-analytics.md screenshots/21-analytics-*.png
git commit -m "docs: T4 — document Analytics section (all 4 sub-pages)"
```

---

## Task 5: Document Libraries (`/app/libraries`)

**Goal:** Document personal library, corporate library, and exchange/marketplace.

**Files:**
- Create: `docs/knowledge-base/22-libraries.md`
- Screenshots: `screenshots/22-libraries-*.png`

**Step 1: Navigate to Libraries**

```
browser_navigate: https://bluecallom.ai/app/libraries
browser_wait_for: text visible (section heading)
browser_take_screenshot: screenshots/22-libraries-overview.png
browser_snapshot
```

**Step 2: Navigate through library sub-routes**

- `/app/libraries` — screenshot `screenshots/22-libraries-overview.png`
- `/app/corpLibrary` — screenshot `screenshots/22-libraries-corp.png`
- `/app/corpLibraryList` — screenshot `screenshots/22-libraries-corp-list.png`
- `/app/exchangeHome` — screenshot `screenshots/22-libraries-exchange-home.png`
- `/app/exchangeList` — screenshot `screenshots/22-libraries-exchange-list.png`
- `/app/manageLibrary` — screenshot `screenshots/22-libraries-manage.png`

For each: note heading, sidebar nav, filters, asset list table columns, search box, any "Create" / "Add" buttons.

**Step 3: Create `22-libraries.md`**

Structure:
```
# Libraries

**URL:** /app/libraries (entry)
**Access:** Authenticated + corp connected

## Overview
[description]

## Sub-Routes
### Personal Library (/app/libraries)
### Corporate Library (/app/corpLibrary)
### Corporate Library List (/app/corpLibraryList)
### Exchange Home (/app/exchangeHome)
### Exchange List (/app/exchangeList)
### Manage Library (/app/manageLibrary)

## Asset Types
[prompts / agents / solutions — as observed]

## UI Elements
[table]

## Screenshots
[list]
```

**Step 4: Commit**

```bash
git add docs/knowledge-base/22-libraries.md screenshots/22-libraries-*.png
git commit -m "docs: T5 — document Libraries section and exchange/marketplace"
```

---

## Task 6: Document GPTBlue Studio Sub-Features

**Goal:** Document all sub-features that were previously redirecting to `/home` — Prompt Studio, Agent Studio, Solution Studio, Launchpad.

**Files:**
- Modify: `docs/knowledge-base/05-gptblue-studio.md`
- Screenshots: `screenshots/23-gptblue-*.png`

**Step 1: Navigate to each GPTBlue sub-feature**

- `/app/promptStudio` — screenshot `screenshots/23-gptblue-prompt-studio.png`
- `/app/agentStudio` — screenshot `screenshots/23-gptblue-agent-studio.png`
- `/app/solutionStudio` — screenshot `screenshots/23-gptblue-solution-studio.png`
- `/app/launchpad` — screenshot `screenshots/23-gptblue-launchpad.png`
- `/app/workspace` — screenshot `screenshots/23-gptblue-workspace.png`

For each: take snapshot, note heading, sidebar nav, main content, forms/wizards, empty states, create/add buttons.

**Step 2: Update `05-gptblue-studio.md`**

Add a full section for each newly accessible sub-feature. Update the "Access Restriction" section to reflect that sub-features are now accessible with corp connection.

**Step 3: Commit**

```bash
git add docs/knowledge-base/05-gptblue-studio.md screenshots/23-gptblue-*.png
git commit -m "docs: T6 — document GPTBlue Studio sub-features (Prompt/Agent/Solution Studio, Launchpad)"
```

---

## Task 7: Check Partner Portal Access

**Goal:** Determine if Partner Portal is accessible with current account (corp-connected but not necessarily `partner` role). Document result.

**Files:**
- Create: `docs/knowledge-base/24-partner-portal.md` (if accessible)
- Screenshots: `screenshots/24-partner-*.png`

**Step 1: Navigate to Partner Portal**

```
browser_navigate: https://bluecallom.ai/app/partnerHome
browser_wait_for: networkidle (or redirect)
browser_take_screenshot: screenshots/24-partner-home-attempt.png
```

**Step 2: Record outcome**

- If accessible: snapshot, screenshot, document heading, sidebar, stats panels
- If redirect to `/home`: note that `partner` role is still required; document the redirect behavior
- If redirect to `/login`: session dropped; note and re-login

**Step 3a (if accessible): Navigate sub-routes**

- `/app/partnerProgramsList` — screenshot `screenshots/24-partner-programs.png`
- `/app/managePartner` — screenshot `screenshots/24-partner-manage.png`

**Step 3b (if not accessible): Update `07-restricted-sections.md`**

Note Partner Portal still requires `partner` role even with corp connection.

**Step 4: Create or update Partner Portal doc**

If accessible: create `24-partner-portal.md` with full flow documentation.
If not: update `07-restricted-sections.md` to narrow the scope to Partner Portal only.

**Step 5: Commit**

```bash
git add docs/knowledge-base/24-partner-portal.md screenshots/24-partner-*.png
# OR
git add docs/knowledge-base/07-restricted-sections.md
git commit -m "docs: T7 — check Partner Portal access; [accessible|still restricted]"
```

---

## Task 8: Update Navigation Map and Restricted Sections Doc

**Goal:** Bring `02-navigation-map.md` and `07-restricted-sections.md` up to date with the corp-connected state.

**Files:**
- Modify: `docs/knowledge-base/02-navigation-map.md`
- Modify: `docs/knowledge-base/07-restricted-sections.md`

**Step 1: Update `02-navigation-map.md`**

Update the "Home Dashboard — Module Tiles" table:
- Change `tile-active`/`tile-disabled` status based on observed state
- Update the "Active for this account" column with correct values

**Step 2: Update `07-restricted-sections.md`**

- Change the title/overview to reflect that most sections are now accessible
- Keep only the remaining restricted section(s) (Partner Portal if still restricted)
- Add a note: "As of corp connection on [date], the following were unlocked"

**Step 3: Commit**

```bash
git add docs/knowledge-base/02-navigation-map.md docs/knowledge-base/07-restricted-sections.md
git commit -m "docs: T8 — update nav map and restricted sections for corp-connected account"
```

---

## Task 9: Update README and Test Ideas

**Goal:** Update the master index and add new test cases for all newly documented sections.

**Files:**
- Modify: `docs/knowledge-base/README.md`
- Modify: `docs/knowledge-base/99-test-ideas.md`

**Step 1: Update `README.md`**

- Add links for new docs (20-action-space.md, 21-analytics.md, 22-libraries.md, 24-partner-portal.md if created)
- Update the access level table to show which routes are now accessible
- Update the screenshot index

**Step 2: Update `99-test-ideas.md`**

Add new test sections for each newly documented section:
- Corp Portal Home (manageCorp): tile is active, corp admin sub-routes load, stats displayed
- Action Space: main page loads, sub-routes accessible, flight execution UI present
- Analytics: all 4 sub-pages load, filters/controls visible
- Libraries: personal and corp library accessible, exchange/marketplace browsable
- GPTBlue Studio sub-features: Prompt/Agent/Solution Studio load with correct headings, Launchpad accessible

**Step 3: Commit**

```bash
git add docs/knowledge-base/README.md docs/knowledge-base/99-test-ideas.md
git commit -m "docs: T9 — update README index and test ideas for corp-connected sections"
```

---

## Summary

| Task | Section | Output |
|------|---------|--------|
| T1 | Route probe | Access map, home screenshot |
| T2 | Corp Portal home + admin routes | Updated `03-corp-portal.md` |
| T3 | Action Space | New `20-action-space.md` |
| T4 | Analytics | New `21-analytics.md` |
| T5 | Libraries | New `22-libraries.md` |
| T6 | GPTBlue Studio sub-features | Updated `05-gptblue-studio.md` |
| T7 | Partner Portal | New `24-partner-portal.md` or update to `07-restricted-sections.md` |
| T8 | Nav map + restricted sections | Updated `02-navigation-map.md`, `07-restricted-sections.md` |
| T9 | README + test ideas | Updated `README.md`, `99-test-ideas.md` |
