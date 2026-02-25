# Navigation Map

Discovered via JS bundle analysis + Playwright MCP on 2026-02-24.
Updated 2026-02-25: account connected to CODE LEAP AG — all 7 tiles now `tile-active`.

## Home Dashboard — "My Applications" Module Tiles

Each tile on `/home` navigates to a module section when active.
Tiles have state: `tile-active` (clickable) or `tile-disabled` (account feature not enabled).

**Post-corp-connection state (current):** All 7 tiles are `tile-active`.

| Label | CSS Class | Route | Status |
|-------|-----------|-------|--------|
| Team | `bc-bg-team` | `/app/teams` | tile-active |
| Action Space | `bc-bg-actionSpace` | `/app/actionSpace` | tile-active |
| Analytics | `bc-bg-analytics` | `/app/overviewAnalytics` | tile-active |
| Libraries | `bc-bg-libraries` | `/app/libraries` | tile-active |
| Corp Portal | `bc-bg-corpPortal` | `/app/manageCorp` | tile-active |
| Partner Portal | `bc-bg-partnerPortal` | `/app/partnerHome` | tile-active |
| GPTBlue Studio | `bc-bg-gptStudio` | `/app/actionDeck` | tile-active |

**Home tile stats (post-corp):**

| Tile | Stats |
|------|-------|
| Team | 0 Teammate(s), 0 Team(s), 75% Complete, 0 Badge(s) |
| Action Space | 0 Flight(s), 0 Application(s), 0 Agent(s), 0 Prompt(s) |
| Analytics | Description text only |
| Libraries | 2 Library(s), 0 Application(s), Most Used: Nam Ho's Personal Library |
| Corp Portal | 1 Department(s), 0 Country(s), 0 CC |
| Partner Portal | Partner Manager, 0 Program(s), 0 Partner(s) |
| GPTBlue Studio | 0 Application(s), 0 Agent(s), 0 Prompt(s) |

## Left Sidebar (My Profile Card)

Persistent sidebar visible on all authenticated pages.

### Profile Card — Top Section
| Element | Type | Destination / Action |
|---------|------|----------------------|
| User avatar / name | Clickable | `/app/userProfileEdit` |
| CC balance ("CC 10,000") | Link | `/app/accounting` |
| "Create Referral Key" | Button | Opens referral key modal |
| Join date | Text | — |

### Profile Card — Bottom Icon Bar
| Icon | Purpose |
|------|---------|
| Community/team icon | My Network / community features |
| Help (?) icon | Opens help dialog |
| Home icon | `/home` |
| Layout toggle icon | Toggles sidebar/layout |
| BlueCallom logo | — |

### Messages Card
| Element | Type | Destination |
|---------|------|-------------|
| "My Messages" heading | — | — |
| Message timestamp button | Button | Opens message detail |
| Left/right arrow icons | Buttons | Paginate messages |

## Section Sidebar Navigation Groups

Each section has its own sidebar navigation when active. Extracted from the JS route config.

### My Portal (`/app/userProfileEdit`)
Secondary tab nav visible on profile pages:

| Tab Label | Route |
|-----------|-------|
| My rewards | `/app/accounting` (CC balance / rewards) |
| Settings | `/app/myPreferences` |
| My Portal | `/app/userProfileEdit` |
| Password | `/app/changePwd` |
| Event Registration | `/app/events/eventRegistration` |

Full sidebar nav group (`myPortal`):

| Nav Item | Route |
|----------|-------|
| My Team | `/app/teams` |
| My Network | `/app/myNetwork` |
| My Messages | `/app/myMessages` |
| My Feedback | `/app/myFeedback` |
| Accounting | `/app/accounting` |
| My Badges | `/app/myBadges` |
| My Preferences | `/app/myPreferences` |
| User Profile Edit | `/app/userProfileEdit` |
| Change Password | `/app/changePwd` |
| Event Registration | `/app/events/eventRegistration` |
| Mailbox Config | `/app/mailboxConfig` |

### Corp Portal sidebar (`corporatePortal`)

| Nav Item | Route |
|----------|-------|
| Libraries | `/app/libraries` |
| Corporate Home | `/app/manageCorp` |
| Corp Library | `/app/corpLibrary` |
| Corp Library List | `/app/corpLibraryList` |
| Manage Corp | `/app/manageCorp` |
| Manage Team | `/app/manageTeam` |
| Org Coin Management | `/app/orgCoinManagement` |
| Manage Library | `/app/manageLibrary` |
| System Manager | `/app/manageMailServer` |
| Partner Manager | `/app/managePartner` |

### Analytics sidebar (`analytics`)

| Nav Item | Route |
|----------|-------|
| Overview Analytics | `/app/overviewAnalytics` |
| Usage Analytics | `/app/usageAnalytics` |
| Productivity Analytics | `/app/productivityAnalytics` |
| Consumption Analytics | `/app/consumptionAnalytics` |

### Partner Portal sidebar (`partnerPortal`)

| Nav Item | Route |
|----------|-------|
| Libraries | `/app/libraries` |
| Partner Home | `/app/partnerHome` |
| Partner Programs List | `/app/partnerProgramsList` |

### GPTBlue Studio sidebar (`gptBlueStudio`)

| Nav Item | Route |
|----------|-------|
| GPT Blue | `/app/actionDeck` |
| Prompt Studio | `/app/promptStudio` |
| Agent Studio | `/app/agentStudio` |
| Solution Studio | `/app/solutionStudio` |
| Launchpad | `/app/launchpad` |
| Workspace | `/app/workspace` |

### Action Space sidebar (`actionDeck`)

| Nav Item | Route |
|----------|-------|
| Prompts (PROMPTIO) | `/app/assetIo/` |
| Action Space | `/app/actionSpace` |
| Agents (AGENTIO) | `/app/assetIo/` |
| Launchpad | `/app/launchpad` |
| Chat Mode | `/app/chatMode` |
| AI Libraries | `/app/exchangeHome` |
| GPT Blue | `/app/actionDeck` |

## Complete Route Inventory

All routes defined in the JS bundle (`/static/js/main.c2037c05.js`):

### User / Profile
| Route | Description |
|-------|-------------|
| `/home` | Dashboard home |
| `/app/userProfileEdit` | Edit profile (name, photo, LinkedIn, company URL, bio) |
| `/app/myNetwork` | My Network / connections |
| `/app/myMessages` | Message inbox |
| `/app/myFeedback` | My feedback |
| `/app/accounting` | CC coin accounting / balance |
| `/app/myBadges` | Badges earned |
| `/app/myPreferences` | User preferences |
| `/app/changePwd` | Change password |
| `/app/teams` | My team |
| `/app/events/eventRegistration` | Event registration |
| `/app/mailboxConfig` | Mailbox configuration |
| `/app/autoRecharge` | Auto-recharge settings |
| `/app/payout` | Payout |

### Action Space / AI
| Route | Description |
|-------|-------------|
| `/app/actionSpace` | Action Space (flights, agents, solutions, prompts) |
| `/app/actionDeck` | GPT Blue / Action Deck |
| `/app/flight` | Flight execution |
| `/app/flightDirector` | Flight Director |
| `/app/flightDirector/:id` | Flight Director edit |
| `/app/launchpad` | Launchpad |
| `/app/chatMode` | Chat mode |
| `/app/agentStudio` | Agent Studio |
| `/app/agentStudio/version` | Agent Studio version |
| `/app/solutionStudio` | Solution Studio |
| `/app/solutionStudio/version` | Solution Studio version |
| `/app/promptStudio` | Prompt Studio |
| `/app/workspace` | Workspace |
| `/app/assetIo/` | Asset IO (prompt/agent/solution import-export) |

### Libraries / Exchange
| Route | Description |
|-------|-------------|
| `/app/libraries` | Libraries overview |
| `/app/corpLibrary` | Corporate library |
| `/app/corpLibraryList` | Corporate library list |
| `/app/exchangeHome` | AI Libraries / Exchange home |
| `/app/exchangeList` | Exchange list |
| `/app/manageLibrary` | Manage libraries |

### Analytics
| Route | Description |
|-------|-------------|
| `/app/overviewAnalytics` | Overview analytics |
| `/app/usageAnalytics` | Usage analytics |
| `/app/productivityAnalytics` | Productivity analytics |
| `/app/consumptionAnalytics` | Consumption analytics |

### Corporate Portal
| Route | Description |
|-------|-------------|
| `/app/manageCorp` | Corporate home / manage corp |
| `/app/corpLibrary` | Corp library |
| `/app/manageTeam` | Manage team |
| `/app/orgCoinManagement` | Org coin management |
| `/app/manageOrg` | Manage organization |
| `/app/manageCompany` | Manage company |
| `/app/requestCompany` | Request company connection |
| `/app/themes` | Themes |
| `/app/systemMgmt` | System management overview |
| `/app/manageMailServer` | Mail server config |
| `/app/manageCustomModel` | Custom LLM model management |
| `/app/manageFunction` | Function management |
| `/app/manageEvents` | Event management |
| `/app/manageDBConnection` | DB connection management |
| `/app/manageDBQueryFunction` | DB query function management |

### Partner Portal
| Route | Description |
|-------|-------------|
| `/app/partnerHome` | Partner home |
| `/app/partnerProgramsList` | Partner programs list |
| `/app/managePartner` | Partner manager |

### Admin (BlueCallom internal)
| Route | Description |
|-------|-------------|
| `/app/admin/salesOps` | Sales Ops / BLC Portal |
| `/app/admin/approveAccRequest` | Company request approval |
| `/app/admin/adminLibraryApproval` | Exchange request approval |
| `/app/admin/adminAccTransSummary` | Account transaction summary |
| `/app/admin/translationList` | Translation list |
| `/app/admin/adminMessages` | Admin messages |
| `/app/admin/manageFeedback` | Manage feedback |
| `/app/admin/manageSegments` | Manage segments |
| `/app/admin/assetExecutionReport` | Asset execution report |
| `/app/admin/adminPayoutApproval` | Payout approval |
| `/app/admin/adminBadges` | Admin badges |
| `/app/admin/manageRoles` | Roles & permissions |
| `/app/admin/manageCurrency` | Manage currency |
| `/app/admin/assignCoins` | Assign coins |
| `/app/admin/manageLLMModels` | Manage LLM models |
| `/app/admin/adminManageUsers` | Admin manage users |
| `/app/admin/adminUpgradeRequest` | Admin upgrade requests |
| `/app/BlueCallom` | Internal BlueCallom users |

### Billing / Payments
| Route | Description |
|-------|-------------|
| `/app/PaymentNewCard` | Add new payment card |
| `/app/purchaseConfirmation` | Purchase confirmation |

## Breadcrumb Behavior

No breadcrumb navigation observed. The app uses a persistent left sidebar as the primary navigation pattern. Page heading (e.g., "My AgenticBlue Portal | Profile") serves as the section indicator.

## Screenshots

- `screenshots/03-nav-overview.png` — Home dashboard showing all module tiles
