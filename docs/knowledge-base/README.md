# BlueCallom Knowledge Base

Systematically explored `https://bluecallom.ai` using Playwright MCP.
Account: `nam.ho@codeleap.de` — connected to CODE LEAP AG (corp-connected since 2026-02-24).

**Exploration sessions:**
- 2026-02-24: Initial exploration (individual account, pre-corp)
- 2026-02-25: Corp-connected exploration (all 7 tiles active)

## Documents

| File | Section | Route(s) | Access |
|------|---------|---------|--------|
| [00-login-page.md](./00-login-page.md) | Login / Registration | `/login` | Public |
| [01-auth-flow.md](./01-auth-flow.md) | Auth Flow (login + logout) | `/login`, `/home` | Public / Authenticated |
| [02-navigation-map.md](./02-navigation-map.md) | Full Route Map | all routes | — |
| [03-corp-portal.md](./03-corp-portal.md) | Corp Portal / Profile | `/app/userProfileEdit`, `/app/manageCorp`, `/app/orgCoinManagement` | Authenticated / Corp |
| [04-accounting.md](./04-accounting.md) | Rewards / CC Coins | `/app/accounting` | Authenticated |
| [05-gptblue-studio.md](./05-gptblue-studio.md) | GPTBlue Studio (Action Deck) | `/app/actionDeck` | Authenticated |
| [06-event-registration.md](./06-event-registration.md) | Event Registration | `/app/events/eventRegistration` | Authenticated |
| [07-restricted-sections.md](./07-restricted-sections.md) | Route Access Map | all sections | — |
| [10-account-settings.md](./10-account-settings.md) | All Portal/Settings Tabs | 11 routes (see file) | Authenticated |
| [20-corp-route-discovery.md](./20-corp-route-discovery.md) | Corp Route Discovery | 13 newly accessible routes | Corp |
| [20-action-space.md](./20-action-space.md) | Action Space | `/app/actionSpace`, `/app/flight`, `/app/chatMode` | Corp |
| [21-analytics.md](./21-analytics.md) | Analytics Dashboards | `/app/overviewAnalytics` + 3 sub-pages | Corp |
| [22-libraries.md](./22-libraries.md) | Libraries | `/app/libraries` + 4 sub-routes | Corp |
| [24-partner-portal.md](./24-partner-portal.md) | Partner Portal | `/app/partnerHome`, `/app/partnerProgramsList` | Corp |

## Access Level Summary

| Level | Description | Routes Accessible |
|-------|-------------|-------------------|
| Public (unauthenticated) | Not logged in | `/login`, `/forgotpwd` |
| `loggedIn` | Authenticated, no corp | `/home`, profile, accounting, preferences, password, events, actionDeck, teams, myNetwork, myMessages, myFeedback, myBadges, mailboxConfig |
| `loggedIn + corp` | Connected to corporate account | All of the above + Action Space, Analytics, Libraries, Corp Portal admin, Partner Portal |
| Admin roles | Org admin / higher tier | `/app/promptStudio`, `/app/agentStudio`, `/app/solutionStudio`, `/app/flightDirector`, `/app/manageTeam`, `/app/manageOrg`, `/app/manageLibrary` |

## Authentication

- **Storage:** `localStorage` only (no cookies, no sessionStorage)
- **Key tokens:** `isLoggedIn`, `refreshToken` (RS256 JWT, ~1yr TTL), `user` object
- **Login methods:** Corporate email+password OR LinkedIn OAuth OR Google OAuth
- **Logout:** Exit icon in profile sidebar → clears all localStorage → redirects to `/login`

## Screenshots Index

All screenshots are in `screenshots/`:

| File | Description |
|------|-------------|
| `01-login-page.png` | Login page (unauthenticated) |
| `02-post-login-landing.png` | Home dashboard after login |
| `03-nav-overview.png` | Home dashboard — all 7 module tiles |
| `04-corp-portal-overview.png` | My AgenticBlue Portal — Profile tab |
| `04-accounting-overview.png` | Rewards / CC Coins page |
| `04-gptblue-studio-overview.png` | GPTBlue Dashboard (actionDeck) |
| `04-preferences-overview.png` | My Preferences page |
| `04-event-registration-overview.png` | Event Registration (empty state) |
| `06-home-pre-logout.png` | Home dashboard with logout button visible |
| `06-logout-button-hover.png` | Logout button tooltip |
| `06-post-logout.png` | Post-logout login page |
| `10-settings-overview.png` | My Portal — profile form |
| `10-settings-preferences.png` | Settings — preferences (top) |
| `10-settings-preferences-2.png` | Settings — preferences (scrolled) |
| `10-settings-password.png` | Change Password tab |
| `10-settings-rewards.png` | My rewards (Accounting) tab |
| `10-settings-event-reg.png` | Event Registration tab (full nav visible) |
| `10-settings-team.png` | Team tab |
| `10-settings-connections.png` | Connections tab |
| `10-settings-messages.png` | Messages tab |
| `10-settings-feedback.png` | Feedback tab |
| `10-settings-badges.png` | Badges tab |
| `10-settings-mailbox.png` | Manage Mailbox Configuration tab |
| `20-home-corp-connected.png` | Home dashboard — all 7 tiles tile-active |
| `20-corp-portal-home.png` | Company Dashboard (`/app/manageCorp`) |
| `20-corp-org-coins.png` | Coin Economy (`/app/orgCoinManagement`) |
| `20-action-space-overview.png` | Action Space — Flights tab |
| `20-action-space-flight.png` | Flight Launchpad (`/app/flight`) |
| `20-action-space-chat.png` | Chat Mode — Mentoha AI (`/app/chatMode`) |
| `21-analytics-overview.png` | Analytics Overview (empty) |
| `21-analytics-usage.png` | Analytics Usage (7 panels) |
| `21-analytics-productivity.png` | Analytics Productivity (bar/pie charts) |
| `21-analytics-consumption.png` | Analytics Consumption |
| `22-libraries-overview.png` | Libraries — Libraries tab |
| `22-libraries-corporate.png` | Libraries — Corporate Library tab |
| `22-libraries-organization.png` | Libraries — Organization Library tab |
| `22-libraries-partner.png` | Libraries — Partner Library tab |
| `22-libraries-exchange.png` | Libraries — Exchange tab |
| `22-corp-library-list.png` | Corporate Solution Library List |
| `22-corp-library.png` | Organization Library asset browser |
| `22-exchange-home.png` | BlueCallom Exchange home |
| `22-exchange-list.png` | Exchange List |
| `23-gptblue-actiondeck.png` | GPTBlue Dashboard — post-corp state |
| `24-partner-home.png` | Partner Program Dashboard |
| `24-partner-programs-list.png` | Partner Program List |
