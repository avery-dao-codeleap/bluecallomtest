# Corp-Connected Route Discovery

**Account:** `nam.ho@codeleap.de` connected to **CODE LEAP AG**
**Date:** 2026-02-24
**Status:** Account upgraded from individual → corp-connected

## Overview

After connecting the account to a corporate organization, 13 previously restricted routes became accessible. 8 routes remain restricted (redirect to `/home`) — these appear to require a higher admin or special role.

## Two Distinct Restriction Behaviors

| Behavior | Redirect Target | Meaning |
|----------|----------------|---------|
| **Auth-guard redirect** | → `/login` then back to intended URL | Route IS accessible; just needed re-auth |
| **Client-side block** | → `/home` (no redirect back) | Route is genuinely restricted at this access level |

## Complete Route Probe Results

### Now Accessible (corp-connected)

| Route | Page Heading | Nav Bar |
|-------|-------------|---------|
| `/app/manageCorp` | Corp Portal | C-Portal \| Coins |
| `/app/orgCoinManagement` | Coin Economy | C-Portal \| Coins |
| `/app/actionSpace` | Action Space | (see Action Space section) |
| `/app/overviewAnalytics` | Analytics Dashboard | Overview \| Usage \| Productivity \| Consumption |
| `/app/libraries` | AgenticBlue \| EAI Libraries | Libraries \| Corporate Library \| Organization Library \| Partner Library \| Exchange |
| `/app/partnerHome` | Partner Program Dashboard | Libraries \| Portal \| Programs |
| `/app/partnerProgramsList` | Partner Program List | Libraries \| Portal \| Programs |
| `/app/flight` | AgenticBlue Flight Launchpad | (home icon only) |
| `/app/chatMode` | Chat | AI Assets \| Action Space \| Agents \| Chat \| BLC Exchange |
| `/app/corpLibrary` | AgenticBlue \| Organization Library | C-Portal \| Coins |
| `/app/corpLibraryList` | Corporate Solution Library List | Libraries \| Corp Home \| C-Portal \| Manage Corp \| Coins |
| `/app/exchangeHome` | AgenticBlue \| BlueCallom Exchange | Libraries \| Exchange \| More Libraries \| Action Space |
| `/app/exchangeList` | Exchange List | Libraries \| Exchange \| More Libraries \| Action Space |

### Still Restricted (→ `/home`)

| Route | Notes |
|-------|-------|
| `/app/promptStudio` | GPTBlue sub-feature — requires higher tier |
| `/app/agentStudio` | GPTBlue sub-feature — requires higher tier |
| `/app/flightDirector` | Flight builder — requires higher role |
| `/app/launchpad` | Launchpad — requires higher role |
| `/app/solutionStudio` | Solution builder — requires higher tier |
| `/app/manageOrg` | Org admin — requires org admin role |
| `/app/manageLibrary` | Library admin — requires admin role |
| `/app/manageTeam` | Team admin — requires admin role |

## Key Page Summaries

### `/app/manageCorp` — Corp Portal Home

Entry point for corporate administration.
- **Nav:** C-Portal | Coins
- Leads to organizational settings and coin management

### `/app/orgCoinManagement` — Coin Economy

Corporate CC coin ledger (distinct from personal accounting at `/app/accounting`).
- **Heading:** Coin Economy
- **Table columns:** Gold Coin transactions
- **Nav:** C-Portal | Coins

### `/app/corpLibraryList` — Corporate Solution Library List

Lists all solution libraries accessible to the organization.
- **Nav:** Libraries | Corp Home | C-Portal | Manage Corp | Coins
- **Controls:** Filter (search by library name), Sort: Newest | Alphabetical
- **Card shown:** "Organization Library" — Contact: CODE AG (`felix.suellwold@codeleap.de`)

### `/app/corpLibrary` — Organization Library

Browse AI assets in the organization's library.
- **Heading:** AgenticBlue | Organization Library
- **Nav:** C-Portal | Coins
- **Slider tabs:** Applications | Agents | Prompt
- **Empty state:** "No application exist."

### `/app/exchangeHome` — BlueCallom Exchange

Public marketplace for AI assets.
- **Heading:** AgenticBlue | BlueCallom Exchange
- **Nav:** Libraries | Exchange | More Libraries | Action Space
- **Slider tabs:** Applications | Agents | Prompt
- **Button:** "More Exchanges"
- **Empty state:** "No application exist."
- **Right column:** "AI Asset Library | BlueCallom Exchange"

### `/app/exchangeList` — Exchange List

Browsable list of all available exchanges.
- **Nav:** Libraries | Exchange | More Libraries | Action Space
- **Controls:** Filter (search by library name), Sort: Newest | Alphabetical
- **Exchanges listed:**
  - **BlueCallom Exchange** — Professional high-productivity AI prompts. Contact: Dino Smuc (`dino@bluecallom.com`)
  - **Innofynd Exchange** — Exchange library of innofynd. Contact: Leon Pehmer (`leon@innofynd.ai`)

### `/app/flight` — AgenticBlue Flight Launchpad

View and interact with active AAIS flights.
- **Heading:** AgenticBlue Flight Launchpad
- **Content:** "Active AAIS Flight" section with open items list, instruction block, and AI asset productivity tracker
- **Sidebar:** "My Messages" panel with "Flight Team" slider tab
- **Open Items (sample data):** Review Response, Review 4 leads, 8 follow up calls, 2 visits
- **Controls:** "gainValue" spinbutton (manual hours), Save button

### `/app/chatMode` — Chat

AI-powered chat interface for interacting with agents.
- **Heading:** Chat
- **AI assistant:** "Mentoha" — greeting: "What can I do for you?"
- **Nav:** AI Assets | Action Space | Agents | Chat | BLC Exchange
- **Left sidebar:** "Chat History" panel with "New Chat" button (empty: "There is no previous chat history")
- **Input:** "Send a message..." text box

### `/app/partnerHome` — Partner Program Dashboard

Overview of partner programs.
- **Heading:** Partner Program Dashboard
- **Nav:** Libraries | Portal | Programs
- **Slider tabs:** Applications | Agents | Prompt
- **Empty state:** "No partner program is available."

### `/app/partnerProgramsList` — Partner Program List

List of all partner programs.
- **Nav:** Libraries | Portal | Programs
- **Empty state:** "No Records Found"

### `/app/overviewAnalytics` — Analytics Dashboard

Performance analytics overview.
- **Heading:** Analytics Dashboard
- **Nav tabs:** Overview | Usage | Productivity | Consumption

## Home Dashboard — Corp-Connected State

All 7 tiles now have `tile-active` class:

| Tile | Route | Stats Shown |
|------|-------|-------------|
| Team | `/app/teams` | 0 Teammate(s), 0 Team(s), 75% Complete, 0 Badge(s) |
| Action Space | `/app/actionSpace` | 0 Flight(s), 0 Application(s), 0 Agent(s), 0 Prompt(s) |
| Analytics | `/app/overviewAnalytics` | (description text only) |
| Libraries | `/app/libraries` | 2 Library(s), 0 Application(s), Most Used: Nam Ho's Personal Library |
| Corp Portal | `/app/manageCorp` | 1 Department(s), 0 Country(s), 0 CC |
| Partner Portal | `/app/partnerHome` | Partner Manager, 0 Program(s), 0 Partner(s) |
| GPTBlue Studio | `/app/actionDeck` | 0 Application(s), 0 Agent(s), 0 Prompt(s) |

## Screenshots

| File | Description |
|------|-------------|
| `screenshots/20-home-corp-connected.png` | Home dashboard — all 7 tiles tile-active |
| `screenshots/20-probe-orgCoinManagement.png` | Coin Economy page |
| `screenshots/20-probe-partnerHome.png` | Partner Program Dashboard |
