# Test Ideas

Derived from knowledge base exploration. Organized by section and test type.

---

## Authentication

### Login
- [ ] **Corporate login — happy path**: Submit valid credentials → assert redirect to `/home`, `isLoggedIn` in localStorage = "true"
- [ ] **Corporate login — wrong password**: Submit wrong password → assert error message shown, no redirect
- [ ] **Corporate login — empty fields**: Submit empty email or password → assert validation error shown
- [ ] **Corporate login — invalid email format**: Assert client-side validation
- [ ] **OAuth login — LinkedIn**: Click LinkedIn button → assert OAuth redirect initiated
- [ ] **OAuth login — Google**: Click Google button → assert OAuth redirect initiated
- [ ] **Already authenticated redirect**: Navigate to `/login` while logged in → assert redirect to `/home`
- [ ] **Forgot password link**: Click "Forgot Password" → assert navigation to `/forgotpwd`

### Logout
- [ ] **Logout happy path**: Click exit icon in profile sidebar → assert redirect to `/login`, localStorage empty
- [ ] **Post-logout session cleared**: After logout, navigate to `/home` → assert redirect back to `/login`
- [ ] **Flash alert on logout**: Assert alert text "Your session is expired please re-login again." appears after logout
- [ ] **Logout tooltip**: Hover over exit icon → assert tooltip text "Logs you out. Login to come back."

### Session / Auth Guard
- [ ] **Direct nav to protected route (unauthenticated)**: Navigate to `/app/userProfileEdit` without auth → assert redirect to `/login`
- [ ] **Direct nav to corp-gated route**: Navigate to `/app/teams` without auth → assert redirect to `/login` or `/home`
- [ ] **manageCorp drops session**: Navigate to `/app/manageCorp` while logged in (no corp) → assert redirect to `/login` and localStorage cleared
- [ ] **Session persistence on reload**: Reload page while logged in → assert still on protected page, no re-login required

---

## Home Dashboard

- [ ] **7 module tiles rendered**: Assert all 7 tiles (Team, Action Space, Analytics, Libraries, Corp Portal, Partner Portal, GPTBlue Studio) are visible
- [ ] **Corp-connected: all tiles active**: Assert all 7 tiles have `tile-active` class when account is corp-connected
- [ ] **Pre-corp: 6 tiles disabled**: Assert 6 tiles have `tile-disabled` class (only Corp Portal active) for non-corp account
- [ ] **Tile-disabled click does nothing**: Click a disabled tile → assert no navigation occurs
- [ ] **Corp Portal tile (pre-corp) navigates to profile**: Click Corp Portal tile (pre-corp) → assert navigation to `/app/userProfileEdit`
- [ ] **Corp Portal tile (post-corp) navigates to dashboard**: Click Corp Portal tile (post-corp) → assert navigation to `/app/manageCorp`
- [ ] **GPTBlue Studio tile shows stats**: Assert "0 Application(s) / 0 Agent(s) / 0 Prompt(s)" shown for new account
- [ ] **Libraries tile shows personal library**: Assert "Nam Ho's Personal Library" in most-used list
- [ ] **Team tile shows profile completion**: Assert "75% Complete" shown
- [ ] **Analytics tile shows description text only**: Assert tile has description paragraphs (no numeric stats)
- [ ] **Corp Portal tile shows 1 department**: Assert "1 Department(s)" on tile

---

## Corp Portal / Profile (`/app/userProfileEdit`)

- [ ] **Profile form renders with saved data**: Assert all 14 fields pre-filled with saved values
- [ ] **Required field validation**: Clear a required field (e.g. First Name), submit → assert validation error
- [ ] **Country dropdown populated**: Assert country combobox has options including "Viet Nam" (selected)
- [ ] **Bio character limit**: Type 251 chars in bio → assert counter shows 0 and additional input rejected or warns
- [ ] **Save profile changes**: Edit a field, click Save → assert success feedback and data persists on reload
- [ ] **Edit Photo button present**: Assert "Edit Photo" button visible
- [ ] **LinkedIn Connected badge**: Assert "Connected With LinkedIn" shown
- [ ] **Google Connected badge**: Assert "Connected With Google" shown
- [ ] **X (Twitter) connect link**: Assert "Please connect with X" link present and points to correct URL
- [ ] **Company connection banner**: Assert banner text "You are not connected with CODE LEAP AG..."
- [ ] **CC balance link in banner**: Assert "CC 10,000" links to `/app/accounting`

---

## Accounting / Rewards (`/app/accounting`)

- [ ] **Page heading**: Assert "Rewards" heading
- [ ] **Transaction table shows initial grants**: Assert 2 rows — "account completion" (7,500 CC) and "your account initialization" (2,500 CC)
- [ ] **Balance is 10,000 CC**: Assert final balance = 10,000
- [ ] **Category filter — Time selected by default**: Assert "Time" radio selected on load
- [ ] **Period filter — Today selected by default**: Assert period combobox = "Today"
- [ ] **Custom date range enables inputs**: Select "Custom" → assert Start Date and End Date inputs become enabled
- [ ] **Pagination renders**: Assert Prev / 1 / Next pagination navigation visible
- [ ] **Filter by Prompt category**: Click "Prompt" radio → assert table updates (empty for new account)

---

## My Preferences / Settings (`/app/myPreferences`)

- [ ] **Execution Alert toggle is ON by default**: Assert toggle checked
- [ ] **Records per page default is 10**: Assert combobox = "10"
- [ ] **Alert Duration default is 7 Seconds**: Assert combobox = "7 Seconds"
- [ ] **Privacy — company users toggle ON by default**: Assert first privacy toggle checked
- [ ] **Privacy — all users toggle OFF by default**: Assert second and third privacy toggles unchecked
- [ ] **Feedback slider at "My" position by default**: Assert slider value = "0" (leftmost)
- [ ] **Coin Visualization toggle ON by default**: Assert checked
- [ ] **Auto Recharge toggle OFF by default**: Assert unchecked
- [ ] **Status banner visible**: Assert "Your status is New Comer." paragraph present

---

## Change Password (`/app/changePwd`)

- [ ] **Page heading**: Assert "Change Password" heading
- [ ] **Three required fields present**: Assert Current Password, New Password, Confirm Password inputs visible
- [ ] **Password complexity hint visible**: Assert hint text about digit/uppercase/special char requirements visible
- [ ] **Update Password button present**: Assert button visible
- [ ] **Weak password validation**: Submit with password lacking uppercase → assert validation error
- [ ] **Passwords don't match validation**: Enter different New and Confirm passwords → assert validation error
- [ ] **Wrong current password**: Submit with incorrect current password → assert server-side error shown

---

## GPTBlue Studio (`/app/actionDeck`)

- [ ] **Page accessible by direct URL**: Navigate to `/app/actionDeck` → assert page loads (no redirect)
- [ ] **Dashboard shows three stat panels**: Assert "Your Prompts", "Your Agents", "Your Applications" panels visible
- [ ] **All metrics are 0 for new account**: Assert all 9 metrics (3 per panel) = 0
- [ ] **Sub-feature routes redirect**: Navigate to `/app/promptStudio` → assert redirect to `/home`
- [ ] **Sub-feature routes redirect (agent)**: Navigate to `/app/agentStudio` → assert redirect to `/home`

---

## Event Registration (`/app/events/eventRegistration`)

- [ ] **Page heading**: Assert "Event Registration List"
- [ ] **Empty state message**: Assert "There are no upcoming events right now. Please check back soon!" shown
- [ ] **Search textbox present**: Assert "Search Event" input with placeholder "Search by name"
- [ ] **Registered Events button present**: Assert "Registered Events" button visible
- [ ] **Table columns rendered**: Assert Name, Location, Event Start Date, Event End Date, Company, Action column headers

---

## Team Tab (`/app/teams`)

- [ ] **Page accessible via tab nav**: Navigate to Event Registration, click Team tab → assert `/app/teams` loads
- [ ] **Page heading**: Assert "AgenticBlue | AAIS Teams and Me"
- [ ] **Table columns**: Assert Name, Company, Email, Phone headers visible
- [ ] **Empty state**: Assert "No Records Found" shown for new account

---

## Connections (`/app/myNetwork`)

- [ ] **Page accessible via tab nav**: Click Connections tab → assert `/app/myNetwork` loads
- [ ] **Page heading**: Assert "My Connections"
- [ ] **Filter label**: Assert "Filter: All|" text visible
- [ ] **Table columns**: Assert Name, Company, Email, Type headers
- [ ] **Empty state**: Assert "No Records Found"

---

## Messages (`/app/myMessages`)

- [ ] **Page accessible via tab nav**: Click Messages tab → assert `/app/myMessages` loads
- [ ] **Page heading**: Assert "My AgenticBlue Portal | Messages"
- [ ] **New message button**: Assert "+ New" button visible
- [ ] **Filter options**: Assert Received, Sent, Starred, Unread filter links present
- [ ] **Sort options**: Assert Date, Sender Name, Subject sort links present
- [ ] **Table columns**: Assert From, Subject, Date, Action column headers
- [ ] **Empty state**: Assert "No Records Found" for new account

---

## Feedback (`/app/myFeedback`)

- [ ] **Page accessible via tab nav**: Click Feedback tab → assert `/app/myFeedback` loads
- [ ] **Page heading**: Assert "My AgenticBlue Portal | Feedback"
- [ ] **Filter options**: Assert "Filter: All|" and slider (My ↔ All Public) visible
- [ ] **Table columns**: Assert Feedback Id, Created By, Title, Type, Date, Priority, Status, Action
- [ ] **Empty state**: Assert "No Records Found"

---

## Badges (`/app/myBadges`)

- [ ] **Page accessible via tab nav**: Click Badges tab → assert `/app/myBadges` loads
- [ ] **Page heading**: Assert "My AgenticBlue Portal | Badges"
- [ ] **Empty state**: Assert "No Badge Assigned" for new account

---

## Mailbox Configuration (`/app/mailboxConfig`)

- [ ] **Page accessible via tab nav**: Click Manage Mailbox Configuration tab → assert `/app/mailboxConfig` loads
- [ ] **Form heading**: Assert "Mailbox Configuration Setup"
- [ ] **Email field present**: Assert Email textbox with 100 char limit
- [ ] **Password field present**: Assert Password textbox with hint "Use your email password or app-specific password"
- [ ] **New button**: Assert "New +" action visible
- [ ] **Sidebar list empty**: Assert "No Mail Configurations Found" in sidebar

---

## Navigation Bar (Portal Section)

- [ ] **Full nav bar on Event Registration page**: Assert all 11 tabs visible (Team through Manage Mailbox Configuration)
- [ ] **Reduced nav on My Portal page**: Assert only 5 tabs (My rewards, Settings, My Portal, Password, Event Registration)
- [ ] **Active tab highlighted**: Assert current tab is visually distinguished in nav bar
- [ ] **Home icon in nav bar**: Assert house icon links to `/home`

---

## Restricted Sections (pre-corp)

- [ ] **Team tile disabled (pre-corp)**: Assert home tile has `tile-disabled` class
- [ ] **Action Space tile disabled (pre-corp)**: Assert `tile-disabled` class
- [ ] **Analytics tile disabled (pre-corp)**: Assert `tile-disabled` class
- [ ] **Libraries tile disabled (pre-corp)**: Assert `tile-disabled` class
- [ ] **Partner Portal tile disabled (pre-corp)**: Assert `tile-disabled` class
- [ ] **Direct nav to /app/teams redirects (pre-corp)**: Navigate without corp account → assert redirect to `/home`
- [ ] **Direct nav to /app/actionSpace redirects (pre-corp)**: Assert redirect to `/home`
- [ ] **Direct nav to /app/overviewAnalytics redirects (pre-corp)**: Assert redirect to `/home`
- [ ] **Direct nav to /app/libraries redirects (pre-corp)**: Assert redirect to `/home`
- [ ] **Direct nav to /app/partnerHome redirects (pre-corp)**: Assert redirect to `/home`
- [ ] **manageCorp terminates session (pre-corp)**: Navigate to `/app/manageCorp` without corp → assert redirect to `/login` AND localStorage cleared

## Restricted Sections (admin-only, even post-corp)

- [ ] **promptStudio redirects**: Navigate to `/app/promptStudio` → assert redirect to `/home`
- [ ] **agentStudio redirects**: Navigate to `/app/agentStudio` → assert redirect to `/home`
- [ ] **solutionStudio redirects**: Navigate to `/app/solutionStudio` → assert redirect to `/home`
- [ ] **flightDirector redirects**: Navigate to `/app/flightDirector` → assert redirect to `/home`
- [ ] **manageTeam redirects**: Navigate to `/app/manageTeam` → assert redirect to `/home`
- [ ] **manageOrg redirects**: Navigate to `/app/manageOrg` → assert redirect to `/home`
- [ ] **manageLibrary redirects**: Navigate to `/app/manageLibrary` → assert redirect to `/home`

---

## Corp Portal (post-corp)

- [ ] **manageCorp loads without session drop**: Navigate to `/app/manageCorp` (corp-connected) → assert page loads, no redirect to `/login`
- [ ] **Company Dashboard heading**: Assert "AgenticBlue Company Dashboard" heading
- [ ] **HQ department badge shown**: Assert "HQ" department card/badge visible
- [ ] **Nav bar: C-Portal and Coins**: Assert nav shows C-Portal and Coins links

### Coin Economy (`/app/orgCoinManagement`)

- [ ] **Page heading**: Assert "Coin Economy"
- [ ] **Org balance is CC 0**: Assert "Balance: CC 0" shown (separate from personal CC 10,000)
- [ ] **Gold Coin table visible**: Assert Date, Activity, Type, Coin Spent, Coin Added columns
- [ ] **Empty state**: Assert "No Records Found" for new org
- [ ] **Category filter defaults to Time**: Assert "Time" radio selected
- [ ] **Period filter defaults to Today**: Assert "Today" combobox value
- [ ] **Custom date range enables inputs**: Select "Custom" → assert Start/End Date inputs become enabled

---

## Action Space

### `/app/actionSpace`

- [ ] **Flights tab active by default**: Assert "Flight Space" heading on load
- [ ] **Nav: Flights | Agents | Applications | Prompts**: Assert all 4 nav tabs visible
- [ ] **Flights tab — Active AAIS Flights empty**: Assert "Currently there are no active flights"
- [ ] **Flights tab — Available AAIS Flights empty**: Assert "No Flights Found"
- [ ] **Agents tab heading**: Click Agents tab → assert "Agent Space" heading
- [ ] **Agents tab empty state**: Assert "No Agents Found" in both sections
- [ ] **Applications tab heading**: Click Applications tab → assert "Solution Space" heading
- [ ] **Applications tab empty state**: Assert "No Application Found"
- [ ] **Prompts tab heading**: Click Prompts tab → assert "Prompt Space" heading
- [ ] **Prompts tab empty state**: Assert "No Prompts Found"
- [ ] **Sidebar: My Profile + My Messages**: Assert both sidebar panels present

### Flight Launchpad (`/app/flight`)

- [ ] **Page heading**: Assert "AgenticBlue Flight Launchpad"
- [ ] **Open Items list present**: Assert Review Response, Review 4 leads, 8 follow up calls, 2 visits items shown
- [ ] **gainValue spinbutton present**: Assert spinbutton with name "gainValue" visible
- [ ] **Gain display shows NaN initially**: Assert "A NaN x Gain" text before entering value
- [ ] **Save button present**: Assert Save button visible
- [ ] **Sidebar: My Messages + Flight Team slider**: Assert slider tab toggle between My Messages and Flight Team

### Chat Mode (`/app/chatMode`)

- [ ] **Page heading**: Assert "Chat"
- [ ] **AI assistant greeting**: Assert "What can I do for you ?" text visible
- [ ] **AI assistant name**: Assert "Mentoha" name shown
- [ ] **Message input placeholder**: Assert "Send a message..." placeholder
- [ ] **Chat History empty state**: Assert "There is no previous chat history"
- [ ] **New Chat button**: Assert "New Chat" button visible
- [ ] **Nav includes Chat tab**: Assert AI Assets, Action Space, Agents, Chat, BLC Exchange tabs visible

---

## Analytics

- [ ] **Overview nav tab visible**: Assert Overview | Usage | Productivity | Consumption nav bar
- [ ] **Period picker defaults to 2026**: Assert "2026" selected in combobox
- [ ] **Period picker options**: Assert 2026, 2025, 2024, 2023 options available
- [ ] **Help (?) icon on each chart panel**: Assert each panel has a help icon

### Overview (`/app/overviewAnalytics`)

- [ ] **Page heading**: Assert "Analytics Dashboard"
- [ ] **AAIS Overview panel present**: Assert chart panel for "AAIS Overview"
- [ ] **Empty state for 2026**: Assert "No chart data available for the selected period."

### Usage (`/app/usageAnalytics`)

- [ ] **Page heading**: Assert "Analytics Dashboard - Usage"
- [ ] **7 chart panels rendered**: Assert Monthly/YTD panels for AI Asset, Segment, Organization, and YTD by User
- [ ] **All panels empty for 2026**: Assert "No chart data available for the selected period." in all panels

### Productivity (`/app/productivityAnalytics`)

- [ ] **Page heading**: Assert "Analytics Dashboard - Productivity"
- [ ] **Monthly Productivity gain vs cost has data**: Assert bar chart with Jan'26 and Feb'26 bars rendered
- [ ] **Bar chart legend**: Assert "Cost" and "Gain" legend items visible
- [ ] **YTD Productivity gain vs cost has data**: Assert pie/donut chart rendered
- [ ] **Other panels are empty**: Assert "No chart data available for the selected period." for remaining panels

### Consumption (`/app/consumptionAnalytics`)

- [ ] **Page heading**: Assert "Analytics Dashboard - Consumption"
- [ ] **Monthly Consumption Vs Productivity has data**: Assert bar chart with Jan'26 and Feb'26 rendered
- [ ] **Other panels are empty**: Assert empty state for all other panels

---

## Libraries

### Main page (`/app/libraries`)

- [ ] **Libraries tab active by default**: Assert heading includes "EAI Libraries"
- [ ] **Nav: 5 tabs**: Assert Libraries, Corporate Library, Organization Library, Partner Library, Exchange tabs
- [ ] **Libraries tab — personal library shown**: Assert "Nam Ho's Personal Library" cards visible
- [ ] **Organization Library tab — CODE AG library shown**: Assert "Organization Library" card with CODE AG contact
- [ ] **Exchange tab — 2 exchanges shown**: Assert BlueCallom Exchange and Innofynd Exchange cards
- [ ] **Corporate Library tab — empty**: Assert "No Libraries Found"
- [ ] **Partner Library tab — empty**: Assert "No Libraries Found"
- [ ] **Available EAI Applications always empty**: Assert "No Application Found" in right column

### Corporate Solution Library List (`/app/corpLibraryList`)

- [ ] **Page heading**: Assert "Corporate Solution Library List"
- [ ] **Filter input present**: Assert "Search by library name" textbox
- [ ] **Sort options**: Assert Newest | Alphabetical toggle
- [ ] **Organization Library entry**: Assert "Organization Library" card with CODE AG contact
- [ ] **Org toggle disabled**: Assert "Org" checkbox/toggle is disabled

### Organization Library (`/app/corpLibrary`)

- [ ] **Page heading**: Assert "AgenticBlue | Organization Library"
- [ ] **Slider tabs**: Assert Applications, Agents, Prompt tabs on slider
- [ ] **Empty state**: Assert "No application exist."
- [ ] **Two panels render**: Assert both main panel (with nav) and secondary panel visible

### BlueCallom Exchange (`/app/exchangeHome`)

- [ ] **Page heading**: Assert "AgenticBlue | BlueCallom Exchange"
- [ ] **Slider tabs**: Assert Applications, Agents, Prompt
- [ ] **More Exchanges button**: Assert "More Exchanges" button visible
- [ ] **Empty state**: Assert "No application exist."
- [ ] **AI Asset Library secondary panel**: Assert "AI Asset Library | BlueCallom Exchange" panel rendered

### Exchange List (`/app/exchangeList`)

- [ ] **Page heading**: Assert "Exchange List"
- [ ] **BlueCallom Exchange listed**: Assert BlueCallom Exchange entry with Dino Smuc contact
- [ ] **Innofynd Exchange listed**: Assert Innofynd Exchange entry with Leon Pehmer contact
- [ ] **Filter input present**: Assert "Search by library name" textbox
- [ ] **Sort options**: Assert Newest | Alphabetical

---

## Partner Portal

### Partner Program Dashboard (`/app/partnerHome`)

- [ ] **Page heading**: Assert "Partner Program Dashboard"
- [ ] **Nav: Libraries | Portal | Programs**: Assert all 3 nav tabs
- [ ] **Slider tabs**: Assert Applications, Agents, Prompt tabs
- [ ] **Main panel empty state**: Assert "No partner program is available."
- [ ] **Secondary panel**: Assert "Agent or AI Asset Library" panel with empty state

### Partner Program List (`/app/partnerProgramsList`)

- [ ] **Page heading**: Assert "Partner Program List"
- [ ] **Empty state**: Assert "No Records Found"
