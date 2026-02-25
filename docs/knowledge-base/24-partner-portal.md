# Partner Portal

**URL:** `/app/partnerHome` (entry)
**Access:** Authenticated + corp-connected users
**Home tile:** Partner Portal — shows Partner Manager, 0 Program(s), 0 Partner(s)

## Overview

The Partner Portal allows corp-connected users to manage and browse partner programs and their associated AI assets. The main page and program list are accessible; both are empty for this account (no partner programs configured).

**Common layout:**
- Left sidebar: My Profile card only (no My Messages panel)
- Persistent nav bar: Libraries | Portal | Programs

---

## Sub-Route: Partner Program Dashboard (`/app/partnerHome`)

**Section heading:** Partner Program Dashboard
**Nav bar:** Libraries | Portal | Programs

### Layout

Two panels render on this page:

**Panel 1 (main):** Has nav bar and asset browser
- Slider tabs: Applications | Agents | Prompt
- Empty state: "No partner program is available."

**Panel 2 (secondary):** "Agent or AI Asset Library"
- Empty state: "No partner program is available."

---

## Sub-Route: Partner Program List (`/app/partnerProgramsList`)

**Section heading:** Partner Program List
**Nav bar:** Libraries | Portal | Programs

### Content

Empty state: "No Records Found"

> No partner programs have been set up for this organization.

---

## Route Summary

| Route | Heading | Notes |
|-------|---------|-------|
| `/app/partnerHome` | Partner Program Dashboard | Two panels; empty state |
| `/app/partnerProgramsList` | Partner Program List | "No Records Found" |

---

## Screenshots

| File | Description |
|------|-------------|
| `screenshots/24-partner-home.png` | Partner Program Dashboard (`/app/partnerHome`) |
| `screenshots/24-partner-programs-list.png` | Partner Program List (`/app/partnerProgramsList`) |
