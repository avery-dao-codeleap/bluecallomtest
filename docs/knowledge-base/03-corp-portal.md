# Corp Portal

**Access:** Authenticated + corp-connected users
**Entry point (pre-corp):** `/app/userProfileEdit` (personal profile)
**Entry point (post-corp):** `/app/manageCorp` (company dashboard)

## Overview

Corp Portal has two distinct faces depending on account state:

1. **Pre-corp-connection** — Corp Portal tile on home leads to `/app/userProfileEdit`. A banner prompts the user to connect with their company. Most corp-admin routes drop the session or redirect.
2. **Post-corp-connection** — Corp Portal tile leads to `/app/manageCorp` ("AgenticBlue Company Dashboard"). Company administration routes become accessible. The user profile page is still available via the tab bar.

This account (`nam.ho@codeleap.de`) is now connected to **CODE LEAP AG**.

---

## Section 1: My AgenticBlue Portal (`/app/userProfileEdit`)

**Section heading:** My AgenticBlue Portal | Profile
**Access:** All authenticated users

### Secondary Navigation (Tab Bar)

Visible on portal pages:

| Tab | Route |
|-----|-------|
| My rewards | `/app/accounting` |
| Settings | `/app/myPreferences` |
| My Portal | `/app/userProfileEdit` |
| Password | `/app/changePwd` |
| Event Registration | `/app/events/eventRegistration` |

### Company Connection Banner (pre-corp)

> *"You are not connected with CODE LEAP AG. If you want to connect with your company, please [Click Here]."*

Clicking "Click Here" initiates the company connection flow. Once connected, this banner is replaced by company data.

### Profile Details Form (14 fields)

| Field | Type | Required | Value |
|-------|------|----------|-------|
| UserName | textbox | Yes | NamHo-presence |
| First Name | textbox | Yes | Nam |
| Last Name | textbox | Yes | Ho |
| City | textbox | Yes | Ho Chi Minh |
| State | textbox | No | — |
| Post Code | textbox | No | — |
| Country | combobox | Yes | Viet Nam |
| Email | textbox | Yes | nam.ho@codeleap.de |
| Title | textbox | No | — |
| Mobile Phone | textbox | No | 8327382432 |
| LinkedIn URL | textbox | Yes | https://www.linkedin.com/in/... |
| Company URL | textbox | Yes | codeleap.de |
| Business email | textbox | Yes | nam.ho@codeleap.de |
| Bio | textbox | No | — (250 chars max) |
| How did you hear about BlueCallom? | combobox | No | — |

**Social connections:**
- LinkedIn: Connected
- Google: Connected
- X (Twitter): Not connected (link to `https://gptblueapi.bluecallom.ai/index.cfm?api=GPTBlueX`)

**Other controls:** "Edit Photo" button, "Save" button

---

## Section 2: Company Dashboard (`/app/manageCorp`)

**Section heading:** AgenticBlue Company Dashboard
**Access:** Corp-connected users
**Nav bar:** C-Portal | Coins

### Layout

- **Left sidebar:** "My Profile" card + "My Messages" panel
- **Main content:** Department list

### Department List

The main content shows a list of company departments. Each department appears as a card/badge.

| Element | Value (CODE LEAP AG) |
|---------|---------------------|
| Department card | "HQ" (shown as badge with label) |

Clicking a department card stays on the same page (no sub-navigation opens in current state).

### Home Dashboard Tile Stats (post-corp)

When the Corp Portal tile is active on the home dashboard it shows:
- 1 Department(s)
- 0 Country(s)
- 0 CC

---

## Section 3: Coin Economy (`/app/orgCoinManagement`)

**Section heading:** Coin Economy
**Access:** Corp-connected users
**Nav bar:** C-Portal | Coins

> **Note:** This is the **organization's** coin ledger — distinct from the personal accounting page at `/app/accounting`. The CC balance shown here is the org's balance (CC 0), not the user's personal balance (CC 10,000).

### Layout

- **Left sidebar:** "My Profile" card (shows CC 0 — org balance) + "My Messages" panel
- **Main content:** Coin ledger with filters and table

### Filters

| Control | Type | Options | Default |
|---------|------|---------|---------|
| Category | Radio buttons | Time \| Prompt \| Agents \| Flights \| Other | Time |
| Period | Combobox | Today \| Last 7 days \| Last 30 days \| Custom | Today |
| Start Date | Date input | YYYY-MM-DD | Current date (disabled unless Custom) |
| End Date | Date input | YYYY-MM-DD | Current date (disabled unless Custom) |

### Transaction Table

**Heading:** Gold Coin

| Column | Description |
|--------|-------------|
| Date | Transaction date |
| Activity | Activity type description |
| Type | Transaction category |
| Coin Spent | CC deducted |
| Coin Added | CC credited |

**Balance display:** `Balance: CC 0`

**Empty state:** "No Records Found"

---

## Corp Admin Routes — Access Map

| Route | Status | Notes |
|-------|--------|-------|
| `/app/userProfileEdit` | accessible | Personal profile (all authenticated users) |
| `/app/manageCorp` | accessible | Company dashboard (corp-connected) |
| `/app/orgCoinManagement` | accessible | Org coin ledger (corp-connected) |
| `/app/manageTeam` | redirect:/home | Requires higher admin role |
| `/app/manageOrg` | redirect:/home | Requires higher admin role |
| `/app/manageLibrary` | redirect:/home | Requires higher admin role |
| `/app/manageCompany` | redirect:/home | Requires higher admin role |

> **Key finding:** `/app/manageCorp` no longer drops the session (it did before corp connection). The session-drop behavior was due to the server-side 401 when accessing corp-admin routes without corp access. After connecting, these routes either load normally or redirect to `/home` (client-side guard for admin-only routes).

---

## Screenshots

| File | Description |
|------|-------------|
| `screenshots/04-corp-portal-overview.png` | My AgenticBlue Portal \| Profile tab (pre-corp) |
| `screenshots/20-corp-portal-home.png` | AgenticBlue Company Dashboard (`/app/manageCorp`) |
| `screenshots/20-corp-org-coins.png` | Coin Economy (`/app/orgCoinManagement`) |
