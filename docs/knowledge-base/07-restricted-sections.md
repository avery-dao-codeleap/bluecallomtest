# Restricted Sections

**Account:** `nam.ho@codeleap.de` connected to CODE LEAP AG (corp-connected since 2026-02-24)

## Overview

After connecting to a corporate account, all 7 home tiles became `tile-active` and 13 routes became accessible. 8 routes remain restricted (→ `/home`) — these require a higher admin or special role beyond basic corp membership.

## Currently Accessible (post-corp-connection)

| Route | Section |
|-------|---------|
| `/app/teams` | Team |
| `/app/actionSpace` | Action Space |
| `/app/flight` | Action Space — Flight Launchpad |
| `/app/chatMode` | Action Space — Chat |
| `/app/overviewAnalytics` | Analytics — Overview |
| `/app/usageAnalytics` | Analytics — Usage |
| `/app/productivityAnalytics` | Analytics — Productivity |
| `/app/consumptionAnalytics` | Analytics — Consumption |
| `/app/libraries` | Libraries |
| `/app/corpLibrary` | Libraries — Org Library |
| `/app/corpLibraryList` | Libraries — Corp Library List |
| `/app/exchangeHome` | Libraries — Exchange Home |
| `/app/exchangeList` | Libraries — Exchange List |
| `/app/manageCorp` | Corp Portal |
| `/app/orgCoinManagement` | Corp Portal — Coin Economy |
| `/app/partnerHome` | Partner Portal |
| `/app/partnerProgramsList` | Partner Portal — Programs List |
| `/app/actionDeck` | GPTBlue Studio — Dashboard |

## Still Restricted (→ `/home`)

These routes require a higher role (org admin, flight builder, or higher subscription tier):

| Route | Reason |
|-------|--------|
| `/app/promptStudio` | GPTBlue sub-feature — requires higher tier |
| `/app/agentStudio` | GPTBlue sub-feature — requires higher tier |
| `/app/solutionStudio` | GPTBlue sub-feature — requires higher tier |
| `/app/flightDirector` | Flight builder — requires elevated role |
| `/app/launchpad` | Launchpad — requires elevated role |
| `/app/manageOrg` | Org admin — requires org admin role |
| `/app/manageLibrary` | Library admin — requires admin role |
| `/app/manageTeam` | Team admin — requires admin role |
| `/app/manageCompany` | Company admin — requires admin role |

## Required Access Levels (from JS bundle `pageSecurity`)

| Access Level | Description |
|-------------|-------------|
| `loggedIn` | Basic authenticated user |
| `corp` | Connected to a corporate account |
| `partner` | Partner role (for Partner Portal) |

Corp-gated routes require `["loggedIn", "corp"]`. Admin routes require additional role flags beyond `corp`.

## Two Restriction Behaviors

| Behavior | Redirect Target | Meaning |
|----------|----------------|---------|
| Auth-guard redirect | → `/login` then back to intended URL | Route accessible; JWT expired |
| Client-side block | → `/home` (no redirect back) | Route genuinely restricted for this access level |

## How to Unlock Remaining Restricted Routes

Routes still blocked (→ `/home`) require org admin or elevated account roles. These are granted by a BlueCallom administrator, not by connecting to a corporate account.
