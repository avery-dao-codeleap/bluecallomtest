# Account & Settings Flows

**Section:** My AgenticBlue Portal
**Access:** All authenticated users
**Entry route:** `/app/userProfileEdit` (via Corp Portal tile on home dashboard)

## Overview

The "My AgenticBlue Portal" is the central hub for all personal account management. It spans 11 tabs accessible via the secondary navigation bar. The full navigation bar is only visible on certain pages (Event Registration, Messages, Feedback, Badges, Manage Mailbox Configuration); simpler pages (Team, Connections) show a reduced set.

## Navigation Bar Variants

**Full nav bar** (visible on: Messages, Feedback, Badges, Event Registration, Manage Mailbox Configuration):
```
Team | Connections | Messages | Feedback | My rewards | Badges | Settings | My Portal | Password | Event Registration | Manage Mailbox Configuration
```

**Portal-subset nav bar** (visible on: Settings, My Portal, Password, My rewards):
```
My rewards | Settings | My Portal | Password | Event Registration
```

**Team-subset nav bar** (visible on: Team, Connections):
```
Team | Connections | My Portal
```

## Status Banner

Appears on all portal pages (when user is "New Comer" status and not connected to corp):

> "Your status is New Comer. Maybe you just select an Agent or AI Asset from the library and get a feel for the Agent or AI Asset in GPTBlue. Whenever you execute an Agent or AI Asset, coins will be deducted from your account. To start with you received free coins to experience the new AI Asset Economy."

## My Profile Sidebar Panel

Present on all portal pages (left column):

| Element | Value |
|---------|-------|
| Profile photo | Circular photo |
| Name | Nam Ho |
| CC Balance | CC 10,000 (link → `/app/accounting`) |
| "Create Referral Key" button | Generates referral key |
| Member since | BlueCallomer Since - Feb 24, 2026 |

The sidebar context panel (lower left) varies by page:
- **My Connections** panel on: My Portal, Settings, Password, Feedback, Badges pages
- **My Messages** panel on: My rewards, Team, Connections pages

## Tab: My Portal (`/app/userProfileEdit`)

**Section heading:** My AgenticBlue Portal | Profile

### Sub-sections

**Balance card:**
- Shows: `Balance: CC 10,000`

**Company connection banner:**
- *"You are not connected with CODE LEAP AG. If you want to connect with your company, please [Click Here]."*
- "Click Here" initiates the company connection flow (not yet captured)

**Profile Details form (14 fields):**

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
| LinkedIn URL | textbox | Yes | https://www.linkedin.com/in/kiet-huynh-25934b220 |
| Company URL | textbox | Yes | codeleap.de |
| Business email | textbox | Yes | nam.ho@codeleap.de |
| Bio | textbox | No | — (250 chars max) |
| How did you hear about BlueCallom? | combobox | No | — |

**Social connections:**
- LinkedIn: Connected
- Google: Connected
- X (Twitter): Not connected (link to connect via `https://gptblueapi.bluecallom.ai/index.cfm?api=GPTBlueX`)

**Edit Photo** button (expected to open upload dialog).

**Save** button submits profile changes.

### Screenshots
- `screenshots/10-settings-overview.png` — Profile tab (My Portal)

---

## Tab: Settings (`/app/myPreferences`)

**Section heading:** My AgenticBlue Portal | Settings

### My Preferences Form

| Setting | Control | Default |
|---------|---------|---------|
| Execution Alert | Toggle | ON |
| Records per page | Select (10 / 50 / 100 / 200) | 10 |
| Alert Duration | Select (3 / 5 / 7 / 10 Seconds) | 7 Seconds |
| Show contact to company users | Toggle | ON (recommended) |
| Show contact to all BlueCallom users | Toggle | OFF |
| Show contact to public | Toggle | OFF |
| Feedback visibility | Slider (My ↔ All Public) | My |
| Coin Visualization | Toggle | ON |
| Auto Recharge | Toggle | OFF |

**Auto Recharge helper text:** "Automatically recharge my card when my credit balance falls below a threshold"

### Screenshots
- `screenshots/10-settings-preferences.png` — Settings page (top)
- `screenshots/10-settings-preferences-2.png` — Settings page (scrolled to full preferences)

---

## Tab: Password (`/app/changePwd`)

**Section heading:** My AgenticBlue Portal | Change Password

### Change Password Form

| Field | Type | Required |
|-------|------|----------|
| Current Password | password textbox | Yes |
| New Password | password textbox | Yes |
| Confirm Password | password textbox | Yes |

**Password requirements:** "Password must contain at least one digit, one lowercase letter, one uppercase letter, one special character, and be between 8 and 16 characters in length."

**"Update Password" button** — submits the form.

### Screenshots
- `screenshots/10-settings-password.png` — Change Password tab

---

## Tab: My rewards (`/app/accounting`)

See `04-accounting.md` for full documentation.

**Summary:** CC coin ledger with transaction history. Filter by category (Time / Prompt / Agents / Flights / Other) and period (Today / Last 7 days / Last 30 days / Custom).

### Screenshots
- `screenshots/10-settings-rewards.png` — My rewards tab (Accounting)

---

## Tab: Team (`/app/teams`)

**Section heading:** AgenticBlue | AAIS Teams and Me

Accessible via this tab navigation even though the home dashboard tile is `tile-disabled`.

### Team List Table

| Column | Description |
|--------|-------------|
| Name | Team member name (sortable) |
| Company | Member's company |
| Email | Member's email |
| Phone | Member's phone |

**Empty state:** "No Records Found"

### Screenshots
- `screenshots/10-settings-team.png` — Team tab

---

## Tab: Connections (`/app/myNetwork`)

**Section heading:** My Connections

### Connections List

**Filter:** All (filterable by connection type)

| Column | Description |
|--------|-------------|
| Name | Connection name (sortable) |
| Company | Connection's company (sortable) |
| Email | Connection's email (sortable) |
| Type | Connection type (sortable) |

**Empty state:** "No Records Found"

### Screenshots
- `screenshots/10-settings-connections.png` — Connections tab

---

## Tab: Messages (`/app/myMessages`)

**Section heading:** My AgenticBlue Portal | Messages

### My Messages

| Control | Purpose |
|---------|---------|
| "+ New" button | Compose a new message |
| Filter: Received | Show received messages (default) |
| Filter: Sent | Show sent messages |
| Filter: Starred | Show starred messages |
| Filter: Unread | Show unread messages |
| Sort: Date | Sort by date (default) |
| Sort: Sender Name | Sort by sender |
| Sort: Subject | Sort by subject |

**Table columns:** From | Subject | Date | Action

**Empty state:** "No Records Found"

### Screenshots
- `screenshots/10-settings-messages.png` — Messages tab

---

## Tab: Feedback (`/app/myFeedback`)

**Section heading:** My AgenticBlue Portal | Feedback

### Feedback List

| Control | Purpose |
|---------|---------|
| Filter: All | Show all feedback |
| Slider (My ↔ All Public) | Toggle between personal and public feedback |

**Table columns:** Feedback Id | Created By | Title | Type | Date | Priority | Status | Action

**Empty state:** "No Records Found"

### Screenshots
- `screenshots/10-settings-feedback.png` — Feedback tab

---

## Tab: Badges (`/app/myBadges`)

**Section heading:** My AgenticBlue Portal | Badges

### My Badges

**Empty state:** "No Badge Assigned"

Badges are earned through platform activities (referenced in the rewards tooltip: "Your Status Rewards for various actions. Learn more at bluecallom.com/rewards").

### Screenshots
- `screenshots/10-settings-badges.png` — Badges tab

---

## Tab: Event Registration (`/app/events/eventRegistration`)

See `06-event-registration.md` for full documentation.

**Summary:** Browse and register for BlueCallom events. Empty state when no events scheduled.

### Screenshots
- `screenshots/10-settings-event-reg.png` — Event Registration tab

---

## Tab: Manage Mailbox Configuration (`/app/mailboxConfig`)

**Section heading:** Mailbox Configuration Setup

Two-panel layout:
- **Left sidebar:** "Mailbox Configuration List" — lists saved email configs ("No Mail Configurations Found" when empty)
- **Right panel:** Form to add a new mailbox configuration

### Mailbox Configuration Form

| Field | Type | Required | Constraint |
|-------|------|----------|------------|
| Email | textbox | Yes | 100 chars max |
| Password | textbox | Yes | 50 chars max |

**Password hint:** "Use your email password or app-specific password"

**"New +" button** — appears to add/save the configuration.

**Empty state:** "No Mail Configurations Found"

### Screenshots
- `screenshots/10-settings-mailbox.png` — Manage Mailbox Configuration tab

---

## Access Notes

| Route | Status |
|-------|--------|
| `/app/userProfileEdit` | Accessible |
| `/app/myPreferences` | Accessible |
| `/app/changePwd` | Accessible |
| `/app/accounting` | Accessible |
| `/app/events/eventRegistration` | Accessible |
| `/app/teams` | Accessible via tab nav (tile-disabled on home dashboard) |
| `/app/myNetwork` | Accessible via tab nav |
| `/app/myMessages` | Accessible via tab nav |
| `/app/myFeedback` | Accessible via tab nav |
| `/app/myBadges` | Accessible via tab nav |
| `/app/mailboxConfig` | Accessible via tab nav |

> **Key finding:** The Team, Connections, Messages, Feedback, Badges, and Mailbox pages are all accessible via tab navigation from the portal section, even though the "Team" home tile is `tile-disabled`. The access restriction only prevents direct navigation from the home dashboard tile.
