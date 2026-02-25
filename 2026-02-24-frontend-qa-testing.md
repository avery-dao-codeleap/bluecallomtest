# BlueCallom Frontend QA Testing Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Systematically test all accessible flows and components on bluecallom.ai, documenting bugs, inaccessible areas, and UI issues in a structured report.

**Architecture:** Module-by-module sweep — for each module: (1) verify accessibility/navigation, (2) interact with every component and input, (3) immediately log findings to the bug report MD. Pre-auth flows tested first, then all 8 authenticated modules. Concurrently builds a full site structure map (all routes, nav hierarchy, orphaned pages) since the navigation is complex and undocumented.

**Tech Stack:** Playwright MCP (browser automation), Markdown bug report at `docs/qa-report-2026-02-24.md`

**Output:** `docs/qa-report-2026-02-24.md` — continuously updated throughout the run.

---

## Setup

### Task 0: Initialize Bug Report File

**Files:**
- Create: `docs/qa-report-2026-02-24.md`

**Step 1: Create the report file with header**

```markdown
# BlueCallom QA Bug Report — 2026-02-24

**Tester:** Avery Dao (authenticated as self)
**Environment:** https://bluecallom.ai (production)
**Browser:** Playwright/Chromium
**Date:** 2026-02-24

---

## Legend
- 🔴 **Critical** — broken, crashes, data loss
- 🟠 **High** — major flow broken or blocked
- 🟡 **Medium** — component broken but workaround exists
- 🟢 **Low** — cosmetic, minor UX issue
- ✅ **Accessible** — module/flow works
- ❌ **Inaccessible** — cannot reach or broken entry point
- ⚠️ **Partial** — accessible but has issues

---

## Module Accessibility Summary

| Module | Status | Notes |
|--------|--------|-------|
| Login (Google) | | |
| Login (LinkedIn) | | |
| Login (Corporate) | | |
| Forgot Password | | |
| Home Dashboard | | |
| Profile | | |
| Messages | | |
| Accounting | | |
| Team | | |
| Action Space | | |
| Analytics | | |
| Libraries | | |
| Corp Portal | | |
| Partner Portal | | |
| GPTBlue Studio | | |
| Sys Mgmt | | |

---

## Findings

```

**Step 2: Save file and confirm it exists**

---

## Pre-Auth Flows

### Task 1: Login Page — Visual & Layout

**Step 1: Navigate to login page**

Go to: `https://bluecallom.ai/login`

**Step 2: Check all visible elements**
- [ ] BlueCallom logo renders (left panel)
- [ ] "Enterprise AI Workflow Solutions" heading visible
- [ ] 3 bullet points visible and styled correctly
- [ ] Steps 1–4 (numbered onboarding) render correctly
- [ ] Login/Register panel renders on right
- [ ] BlueCallom logo inside login card renders
- [ ] LinkedIn button visible and styled
- [ ] Google button visible and styled
- [ ] "For Corporate Login" link visible
- [ ] Terms of Service link present and correct URL
- [ ] Privacy Policy link present and correct URL
- [ ] "BlueCallom is using Artificial Intelligence" text visible
- [ ] reCAPTCHA badge visible

**Step 3: Check responsive/scroll behavior**

Resize window to 768px wide. Screenshot. Note any layout breakage.

**Step 4: Log findings to report**

Under `## Pre-Auth / Login Page` add results.

---

### Task 2: Login Page — LinkedIn Button

**Step 1: Click "Login/Registration with LinkedIn"**

**Step 2: Observe behavior**
- Does a dialog/confirmation appear?
- Does it redirect to LinkedIn OAuth?
- Does the popup/redirect work or error out?

**Step 3: If redirect opens — note URL and close/back**

Do NOT complete login. Just verify the flow initiates correctly.

**Step 4: Log findings**

---

### Task 3: Login Page — Google Button

**Step 1: Click "Login/Registration with Google"**

**Step 2: Observe the confirmation dialog**
- Does dialog appear with correct text?
- "Abort" and "Ok" buttons present?
- Dialog closeable with X?

**Step 3: Click "Ok"**
- Does it redirect to Google OAuth?
- Does redirect URL look correct?

**Step 4: Back to login, log findings**

---

### Task 4: Login Page — Corporate Login Form

**Step 1: Click "For Corporate Login" link**

**Step 2: Check form appears**
- Email input visible
- Password input visible
- "Forgot Password" link visible
- "Login" button visible

**Step 3: Test empty submission**
- Click "Login" with empty fields
- Note: validation message shown? Browser native or custom?

**Step 4: Test invalid email format**
- Type `notanemail` in email field, any text in password
- Click Login
- Note validation behavior

**Step 5: Test invalid credentials**
- Type `test@test.com` / `wrongpassword`
- Click Login
- Note error message, does it reveal whether email exists?

**Step 6: Test "Forgot Password" link**
- Click it — does it navigate to `/forgotpwd`?
- Does the page load correctly?

**Step 7: Log findings**

---

### Task 5: Forgot Password Page

**Step 1: Navigate to `https://bluecallom.ai/forgotpwd`**

**Step 2: Check page loads (not just redirected back to login)**

**Step 3: Identify and test all components**
- Input field present?
- Submit button present?
- Back to login link?

**Step 4: Test empty submission**
- Note validation behavior

**Step 5: Test invalid email**
- Enter `notanemail@x` — note behavior

**Step 6: Test valid-format email**
- Enter `test@example.com` — note response (success message? error? nothing?)

**Step 7: Log findings + update Accessibility Summary table**

---

## Authenticated Flows

> **Pre-condition:** Already logged in as Avery Dao at `https://bluecallom.ai/home`

### Task 6: Home Dashboard — Layout & Navigation

**Step 1: Navigate to `https://bluecallom.ai/home`**

**Step 2: Check top-level layout**
- BlueCallom logo in header renders
- Left sidebar renders (My Profile card, My Messages card)
- Main grid renders with module cards
- Footer "Powered by BlueCallom" visible

**Step 3: Check My Profile card**
- User name "Avery Dao" visible
- Profile photo renders
- CC balance (CC 7,500) visible and clickable link to /app/accounting
- Referral ID visible with copy icon
- "BlueCallomer Since" date visible
- Bottom nav icons (5 icons) visible and clickable — note where each navigates

**Step 4: Test referral ID copy icon**
- Click copy icon
- Verify some feedback (toast, clipboard, etc.)

**Step 5: Check My Messages card**
- 3 message threads visible
- Each thread clickable
- Timestamp button present
- Navigation arrows present

**Step 6: Check each application card renders**
- Team, Action Space, Analytics, Libraries, Corp Portal, Partner Portal, GPTBlue Studio, Sys Mgmt
- Each has title, help icon, stats, and an illustration

**Step 7: Click each module card — note if it navigates correctly or errors**

**Step 8: Log findings**

---

### Task 7: Profile Module

**Step 1: Navigate to profile (click profile icon or name)**

**Step 2: Document the URL reached**

**Step 3: Check all sections render**
- Personal info section (name, email, etc.)
- Profile completion indicator (currently 70%)
- Badge(s) section (1 badge visible)
- Edit/save controls

**Step 4: Test editable fields**
- Click any editable field — does it become editable?
- Try changing a value and saving — does save work?
- Try saving an empty required field — validation?

**Step 5: Test profile photo upload**
- Is there an upload button?
- Click it — file picker opens?
- Upload an image — preview shown?

**Step 6: Log findings + update Accessibility Summary**

---

### Task 8: Messages Module

**Step 1: Click a message thread in My Messages**

**Step 2: Observe full message view**
- Does message thread open?
- Are messages rendered correctly?
- Is there a reply input?

**Step 3: Test reply input**
- Type a message in the reply box
- Can it be submitted (button or Enter)?
- Do NOT actually send — note if send action is present

**Step 4: Test navigation between threads**

**Step 5: Test "new message" flow if exists**
- Is there a compose button?
- Does it open a form?
- Are recipient, subject, body fields present?
- Test empty submission validation

**Step 6: Log findings + update Accessibility Summary**

---

### Task 9: Accounting Module

**Step 1: Click "CC 7,500" link (navigates to `/app/accounting`)**

**Step 2: Check page loads correctly**
- URL is `/app/accounting`
- Balance displayed
- Transaction history visible?

**Step 3: Test all interactive elements**
- Any filter/date controls?
- Any pagination?
- Any "add credits" or purchase flow?

**Step 4: Log findings + update Accessibility Summary**

---

### Task 10: Team Module

**Step 1: Click Team card on home dashboard**

**Step 2: Note URL and check page loads**

**Step 3: Check all sections**
- Teammates list (currently 0)
- Teams list (currently 0)
- Invite/add teammate button

**Step 4: Test "Invite Teammate" flow**
- Click invite button
- Form appears? Required fields?
- Test empty submission
- Test invalid email format

**Step 5: Test "Create Team" flow if present**
- Click create team
- Form fields present?
- Test validation

**Step 6: Test Help icon (?) on Team card**
- Click it — tooltip or help modal appears?

**Step 7: Log findings + update Accessibility Summary**

---

### Task 11: Action Space Module

**Step 1: Click Action Space card on home dashboard**

**Step 2: Note URL and check page loads**

**Step 3: Identify all sub-sections**
- Flights (0)
- Applications (0)
- Agents (0)
- Prompts (0)

**Step 4: Test "Create/Add" for each sub-section**
- Is there a create button for Flights?
- Is there a create button for Applications?
- Is there a create button for Agents?
- Is there a create button for Prompts?

**Step 5: For each create flow that exists:**
- Open it
- Check all fields render
- Test required field validation (empty submission)
- Test field-level validation (invalid inputs)
- Note any dropdowns/selects — do options load?
- Note any rich text editors — do they function?

**Step 6: Test navigation/tabs within Action Space**

**Step 7: Log findings + update Accessibility Summary**

---

### Task 12: Analytics Module

**Step 1: Click Analytics card on home dashboard**

**Step 2: Note URL and check page loads**

**Step 3: Check all sections render**
- Are charts/graphs visible or just empty state?
- Filter controls present (date range, etc.)?
- Export options?

**Step 4: Test any interactive controls**
- Date pickers — do they open and work?
- Dropdowns — do they load options?
- Any chart interactions (hover tooltips, click-through)?

**Step 5: Log findings + update Accessibility Summary**

---

### Task 13: Libraries Module

**Step 1: Click Libraries card on home dashboard**

**Step 2: Note URL and check page loads**

**Step 3: Check library list (2 libraries present)**
- Both "Avery Dao's Personal Library" entries visible
- Clickable? Navigate correctly?

**Step 4: Click into a library**
- Documents/items listed?
- Upload button present?
- Test upload flow (open file picker, cancel — don't upload)

**Step 5: Test "Create New Library" flow**
- Create button present?
- Name field, type selection?
- Empty submission validation?

**Step 6: Test search/filter within Libraries if present**

**Step 7: Log findings + update Accessibility Summary**

---

### Task 14: Corp Portal Module

**Step 1: Click Corp Portal card on home dashboard**

**Step 2: Note URL and check page loads**

**Step 3: Check all sections**
- Departments (1 department present)
- Countries (0)
- CC balance (0)

**Step 4: Click into the existing Department**
- Detail view loads?
- Edit controls present?

**Step 5: Test "Add Department" flow**
- Form present?
- Required fields?
- Validation on empty/invalid submission?

**Step 6: Test "Add Country" flow if present**

**Step 7: Log findings + update Accessibility Summary**

---

### Task 15: Partner Portal Module

**Step 1: Click Partner Portal card on home dashboard**

**Step 2: Note URL and check page loads**

**Step 3: Check all sections**
- Partner Manager role indicated
- Programs (0)
- Partners (0)

**Step 4: Test "Create Program" flow**
- Form fields?
- Validation?

**Step 5: Test "Add Partner" flow**
- Invite by email?
- Validation?

**Step 6: Log findings + update Accessibility Summary**

---

### Task 16: GPTBlue Studio Module

**Step 1: Click GPTBlue Studio card on home dashboard**

**Step 2: Note URL and check page loads**

**Step 3: Check all sections**
- Applications (0)
- Agents (0)
- Prompts (0)

**Step 4: Test "Create Application" flow**
- All form fields render?
- Required field validation?
- AI model selection dropdown — options load?

**Step 5: Test "Create Agent" flow**
- Form fields present?
- Configuration options (model, temperature, etc.)?
- Test validation

**Step 6: Test "Create Prompt" flow**
- Prompt editor present?
- Variable injection UI?
- Save flow works?

**Step 7: Log findings + update Accessibility Summary**

---

### Task 17: Sys Mgmt Module

**Step 1: Click Sys Mgmt card on home dashboard**

**Step 2: Note URL and check page loads**

**Step 3: Check all sub-sections**
- Function Calls (0)
- Mail Servers (0)
- Model Sets (0)
- System Functions (0)

**Step 4: Test "Add Function Call" flow**
- Form present?
- Fields (name, endpoint, method, etc.)?
- Validation?

**Step 5: Test "Add Mail Server" flow**
- SMTP fields present?
- Test connection button?
- Validation?

**Step 6: Test "Add Model Set" flow**
- Model selection?
- Provider fields?
- Validation?

**Step 7: Log findings + update Accessibility Summary**

---

## Site Structure Mapping

### Task 18: Discover & Document All Routes

**Goal:** Build a complete map of every URL, navigation path, and how modules connect — because the nav structure is unclear.

**Step 1: Record every URL visited during testing**

As you go through Tasks 6–17, log every URL you land on in this format in the report:

```markdown
## Site Structure Map

### Routes Discovered
| URL | Reached Via | Module | Auth Required |
|-----|-------------|--------|---------------|
| /login | direct | Login | No |
| /forgotpwd | Login → "Forgot Password" | Auth | No |
| /home | post-login redirect | Home Dashboard | Yes |
| /app/accounting | Home → CC balance link | Accounting | Yes |
| ... | ... | ... | ... |
```

**Step 2: Map the left sidebar / global nav icons**

On the home dashboard, there are 5 nav icons in the profile card. Click each one:
- Note the icon (describe visually)
- Note the URL it navigates to
- Note what the page/section is

**Step 3: Map entry points for each module**

For each of the 8 module cards, record:
- Does clicking the card navigate to a new URL?
- Or does it open a modal/panel in-place?
- What is the exact URL?

**Step 4: Map sub-routes within each module**

For each module that loads a new page, record all tabs, sub-sections, and drill-down URLs discovered during testing. Example:

```markdown
### Action Space
- /app/action-space (main)
  - /app/action-space/flights
  - /app/action-space/agents
  - /app/action-space/prompts
```

**Step 5: Identify orphaned or dead-end pages**

Pages that:
- Have no back button or breadcrumb
- Cannot be reached from the main nav
- Have broken links (404s, blank screens)

**Step 6: Draw the navigation hierarchy**

After all modules tested, add this section to the report:

```markdown
### Navigation Hierarchy
Home (/home)
├── Profile
│   └── Edit Profile
├── Messages
│   └── Thread View
├── Accounting (/app/accounting)
├── Team (/app/team)
│   ├── Teammates
│   └── Teams
├── Action Space (/app/...)
│   ├── Flights
│   ├── Applications
│   ├── Agents
│   └── Prompts
├── Analytics (/app/...)
├── Libraries (/app/...)
│   └── Library Detail
├── Corp Portal (/app/...)
│   └── Department Detail
├── Partner Portal (/app/...)
├── GPTBlue Studio (/app/...)
│   ├── Applications
│   ├── Agents
│   └── Prompts
└── Sys Mgmt (/app/...)
    ├── Function Calls
    ├── Mail Servers
    ├── Model Sets
    └── System Functions
```

Fill in actual URLs and add any missing nodes discovered.

**Step 7: Note structural issues**

Document any of these:
- Modules that share the same URL pattern but do different things
- Navigation that doesn't match what the card labels say
- Modules reachable multiple ways with inconsistent behavior
- Missing breadcrumbs, broken back navigation, confusing hierarchy

---

## Cross-Cutting Checks

### Task 19: Global UI / Navigation

**Step 1: Check header across all pages**
- Logo always present and links home?
- Consistent across all modules?

**Step 2: Check footer on all pages**
- "Powered by BlueCallom" present?

**Step 3: Test Help icons (?) throughout app**
- Click each one — tooltip or modal appears?
- Content is meaningful?

**Step 4: Test Share icons throughout app**
- Click share icons — what happens?

**Step 5: Test browser back/forward navigation**
- Navigate between 3+ modules
- Use browser back — correct page loads?

**Step 6: Test logout flow**
- Find logout option (profile menu?)
- Log out — redirected to login?
- Back button after logout — properly blocked?

**Step 7: Log findings**

---

### Task 20: Finalize Bug Report

**Step 1: Complete Accessibility Summary table** with ✅ / ❌ / ⚠️ for each module

**Step 2: Add Executive Summary section at top of report**

```markdown
## Executive Summary

- **Total issues found:** N
- **Critical:** N
- **High:** N
- **Medium:** N
- **Low:** N
- **Inaccessible modules:** [list]
- **Fully functional modules:** [list]
```

**Step 3: Review report for completeness**
- Every module has an entry
- Every finding has severity, steps to reproduce, and expected vs actual behavior

**Step 4: Save final report**

File: `docs/qa-report-2026-02-24.md`
