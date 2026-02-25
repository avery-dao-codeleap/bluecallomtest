# Libraries

**URL:** `/app/libraries` (entry)
**Access:** Authenticated + corp-connected users
**Home tile:** Libraries — shows Library(s), Application(s), Most Used stats

## Overview

The Libraries section is the hub for discovering and accessing AI asset libraries. The main page (`/app/libraries`) uses a single route with a tab-based nav bar that filters the displayed content. Related sub-routes provide list and detail views for corporate and exchange libraries.

**Common layout:**
- Left sidebar: My Profile card + My Messages panel
- Persistent nav bar: Libraries | Corporate Library | Organization Library | Partner Library | Exchange
- Right column: "Available EAI Applications" (always "No Application Found" for this account)

---

## Main Page (`/app/libraries`) — Tab Views

### Tab: Libraries

**Section heading:** AgenticBlue | EAI Libraries

| Section | Content |
|---------|---------|
| Most Used EAI Libraries | Nam Ho's Personal Library (x2) — Contact: Nam Ho \| `nam.ho@codeleap.de` |
| All EAI Libraries | Nam Ho's Personal Library (x2) — Contact: Nam Ho \| `nam.ho@codeleap.de` |
| Available EAI Applications | "No Application Found" |

> Two identical cards appear due to the account having a single personal library referenced in both slots.

### Tab: Corporate Library

**Section heading:** Corporate Libraries

| Section | Content |
|---------|---------|
| Most Used EAI Libraries | No Libraries Found |
| All EAI Libraries | No Libraries Found |
| Available EAI Applications | No Application Found |

### Tab: Organization Library

**Section heading:** Organization Libraries

| Section | Content |
|---------|---------|
| Most Used EAI Libraries | **Organization Library** — Contact: CODE AG \| `felix.suellwold@codeleap.de` |
| All EAI Libraries | **Organization Library** — Contact: CODE AG \| `felix.suellwold@codeleap.de` |
| Available EAI Applications | No Application Found |

### Tab: Partner Library

**Section heading:** Partner Libraries

| Section | Content |
|---------|---------|
| Most Used EAI Libraries | No Libraries Found |
| All EAI Libraries | No Libraries Found |
| Available EAI Applications | No Application Found |

### Tab: Exchange

**Section heading:** Exchange Libraries

| Section | Content |
|---------|---------|
| Most Used EAI Libraries | BlueCallom Exchange + Innofynd Exchange |
| All EAI Libraries | BlueCallom Exchange + Innofynd Exchange |
| Available EAI Applications | No Application Found |

**Exchange entries:**

| Name | Description | Contact |
|------|-------------|---------|
| BlueCallom Exchange | Professional high-productivity AI prompts library | Dino Smuc (`dino@bluecallom.com`) |
| Innofynd Exchange | Exchange library of innofynd | Leon Pehmer (`leon@innofynd.ai`) |

---

## Sub-Route: Corporate Solution Library List (`/app/corpLibraryList`)

**Section heading:** Corporate Solution Library List
**Nav bar:** Libraries | Corp Home | C-Portal | Manage Corp | Coins
**Sidebar:** My Profile card only (no My Messages panel)

### Controls

| Control | Type | Options |
|---------|------|---------|
| Filter | Text search | "Search by library name" |
| Sort | Toggle | Newest \| Alphabetical |

### Library Entry

| Field | Value |
|-------|-------|
| Name | Organization Library |
| Contact | CODE AG (`felix.suellwold@codeleap.de`) |
| Toggle | "Org" (disabled) |

---

## Sub-Route: Organization Library (`/app/corpLibrary`)

**Section heading:** AgenticBlue | Organization Library
**Nav bar:** C-Portal | Coins
**Sidebar:** My Profile card only (no My Messages panel)

### Layout

Two panels render on this page:

**Panel 1 (main):** Has the nav bar and asset browser
- Slider tabs: Applications | Agents | Prompt
- Empty state: "No application exist."

**Panel 2 (secondary):** "AgenticBlue | Organization Library"
- Empty state: "No application exist."
- Has an "Add User" icon button

---

## Sub-Route: BlueCallom Exchange (`/app/exchangeHome`)

**Section heading:** AgenticBlue | BlueCallom Exchange
**Nav bar:** Libraries | Exchange | More Libraries | Action Space
**Sidebar:** My Profile card only (no My Messages panel)

### Layout

Two panels render on this page:

**Panel 1 (main):** Has the nav bar and asset browser
- Slider tabs: Applications | Agents | Prompt
- Empty state: "No application exist."
- **"More Exchanges" button** (links to exchange list)

**Panel 2 (secondary):** "AI Asset Library | BlueCallom Exchange"
- Empty state: "No application exist."

---

## Sub-Route: Exchange List (`/app/exchangeList`)

**Section heading:** Exchange List
**Nav bar:** Libraries | Exchange | More Libraries | Action Space
**Sidebar:** My Profile card only (no My Messages panel)

### Controls

| Control | Type | Options |
|---------|------|---------|
| Filter | Text search | "Search by library name" |
| Sort | Toggle | Newest \| Alphabetical |

### Exchange Entries

| Name | Description | Contact |
|------|-------------|---------|
| BlueCallom Exchange | Professional high-productivity, high-performance AI prompts library. Prompts by independent Prompt Designers; each provides at least a 10xPPG (Prompt Productivity Gain) | Dino Smuc (`dino@bluecallom.com`) |
| Innofynd Exchange | Exchange library of innofynd | Leon Pehmer (`leon@innofynd.ai`) |

---

## Route Summary

| Route | Heading | Nav Bar |
|-------|---------|---------|
| `/app/libraries` | AgenticBlue \| EAI Libraries (changes per tab) | Libraries \| Corporate Library \| Organization Library \| Partner Library \| Exchange |
| `/app/corpLibraryList` | Corporate Solution Library List | Libraries \| Corp Home \| C-Portal \| Manage Corp \| Coins |
| `/app/corpLibrary` | AgenticBlue \| Organization Library | C-Portal \| Coins |
| `/app/exchangeHome` | AgenticBlue \| BlueCallom Exchange | Libraries \| Exchange \| More Libraries \| Action Space |
| `/app/exchangeList` | Exchange List | Libraries \| Exchange \| More Libraries \| Action Space |

---

## Screenshots

| File | Description |
|------|-------------|
| `screenshots/22-libraries-overview.png` | Libraries tab — personal libraries |
| `screenshots/22-libraries-corporate.png` | Corporate Library tab (empty) |
| `screenshots/22-libraries-organization.png` | Organization Library tab (CODE AG's library) |
| `screenshots/22-libraries-partner.png` | Partner Library tab (empty) |
| `screenshots/22-libraries-exchange.png` | Exchange tab (BlueCallom + Innofynd) |
| `screenshots/22-corp-library-list.png` | Corporate Solution Library List (`/app/corpLibraryList`) |
| `screenshots/22-corp-library.png` | Organization Library asset browser (`/app/corpLibrary`) |
| `screenshots/22-exchange-home.png` | BlueCallom Exchange home (`/app/exchangeHome`) |
| `screenshots/22-exchange-list.png` | Exchange List (`/app/exchangeList`) |
