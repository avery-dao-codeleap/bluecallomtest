# App Flow Discovery & Knowledge Base Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Systematically explore bluecallom.ai using Playwright MCP, document every user flow, and produce a structured knowledge base that future test suites can rely on.

**Architecture:** Use Playwright MCP browser tools to navigate the live app, capture snapshots and screenshots at each state, then synthesize findings into a structured markdown knowledge base under `docs/knowledge-base/`. Each task focuses on one area of the app, ending with a committed documentation artifact.

**Tech Stack:** Playwright MCP (`@playwright/mcp`), Markdown, Claude Code

---

## Prerequisites

- Playwright MCP is configured in `.mcp.json` at project root
- `@playwright/mcp` is available via `npx`
- Valid credentials are available (user provides them when prompted)
- Claude Code session is running from `/Users/namho/Documents/Projects/bluecallom-2`

---

### Task 1: Verify Playwright MCP and Capture Login Page

**Files:**
- Create: `docs/knowledge-base/00-login-page.md`
- Create: `screenshots/01-login-page.png`

**Step 1: Create screenshots directory**

```bash
mkdir -p screenshots
```

**Step 2: Navigate to the login page**

Use Playwright MCP tool:
- `browser_navigate` → `https://bluecallom.ai/login`

**Step 3: Take a screenshot**

Use Playwright MCP tool:
- `browser_screenshot` → save as `screenshots/01-login-page.png`

**Step 4: Take a snapshot to inspect all interactive elements**

Use Playwright MCP tool:
- `browser_snapshot`

Record all visible elements: form fields, buttons, links, error message containers, OAuth providers, etc.

**Step 5: Document the login page**

Create `docs/knowledge-base/00-login-page.md`:

```markdown
# Login Page

**URL:** https://bluecallom.ai/login

## Form Fields
<!-- list each input: label, type, placeholder, required -->

## Actions
<!-- list each button/link and what it does -->

## Login Methods
<!-- e.g. email+password, Google OAuth, SSO -->

## Validation
<!-- client-side rules observed (empty fields, invalid email format) -->

## Error States
<!-- error messages observed for wrong credentials, locked account, etc. -->

## Redirect Behavior
<!-- where does successful login send the user? -->

## Screenshots
- `screenshots/01-login-page.png`
```

**Step 6: Commit**

```bash
git init
git add docs/knowledge-base/00-login-page.md screenshots/01-login-page.png
git commit -m "docs: capture login page structure and elements"
```

---

### Task 2: Execute Login and Document Auth Flow

**Files:**
- Modify: `docs/knowledge-base/00-login-page.md`
- Create: `docs/knowledge-base/01-auth-flow.md`
- Create: `screenshots/02-post-login-landing.png`

**Step 1: Fill in credentials and log in**

Use Playwright MCP tools in sequence:
- `browser_snapshot` → identify email and password field refs
- `browser_fill` (email field ref) → enter test email
- `browser_fill` (password field ref) → enter test password
- `browser_click` (submit button ref)

**Step 2: Wait for navigation and screenshot the landing page**

Use Playwright MCP tools:
- `browser_wait_for_url` or observe URL change in snapshot
- `browser_screenshot` → save as `screenshots/02-post-login-landing.png`

**Step 3: Snapshot the post-login page**

Use Playwright MCP tool:
- `browser_snapshot`

Record the full URL after login, page title, and all top-level navigation items.

**Step 4: Document the auth flow**

Create `docs/knowledge-base/01-auth-flow.md`:

```markdown
# Authentication Flow

## Login Flow
1. User navigates to `/login`
2. User fills email + password
3. User clicks submit
4. On success: redirect to `<url>`
5. On failure: `<error message shown>`

## Session Behavior
- Session token storage: [ ] localStorage [ ] cookie [ ] sessionStorage
- Token key name: <!-- check via browser_evaluate -->
- Session expiry: <!-- if observable -->

## Logout Flow
<!-- document once found -->

## Post-Login Landing
**URL:** <!-- captured -->
**Page Title:** <!-- captured -->

## Screenshots
- `screenshots/01-login-page.png` — login form
- `screenshots/02-post-login-landing.png` — landing after login
```

**Step 5: Inspect session storage for auth tokens**

Use Playwright MCP tool:
- `browser_evaluate` → `JSON.stringify({ls: {...localStorage}, ss: {...sessionStorage}, cookies: document.cookie})`

Document token storage mechanism in `01-auth-flow.md`.

**Step 6: Commit**

```bash
git add docs/knowledge-base/01-auth-flow.md screenshots/02-post-login-landing.png
git commit -m "docs: document authentication flow and session behavior"
```

---

### Task 3: Map Top-Level Navigation Structure

**Files:**
- Create: `docs/knowledge-base/02-navigation-map.md`
- Create: `screenshots/03-nav-overview.png`

**Step 1: Snapshot the authenticated app shell**

Use Playwright MCP tool:
- `browser_snapshot`

List every navigation item, sidebar link, header link, and dropdown menu visible.

**Step 2: Screenshot the navigation**

Use Playwright MCP tool:
- `browser_screenshot` → save as `screenshots/03-nav-overview.png`

**Step 3: Build the navigation inventory**

For each nav item found, record:
- Label
- URL/route it navigates to
- Whether it's a top-level page or opens a submenu

**Step 4: Document the navigation map**

Create `docs/knowledge-base/02-navigation-map.md`:

```markdown
# Navigation Map

## Top-Level Routes
| Label | URL | Notes |
|-------|-----|-------|
|       |     |       |

## Sidebar / Secondary Nav
| Label | URL | Notes |
|-------|-----|-------|
|       |     |       |

## User Menu (account dropdown)
| Label | Action | Notes |
|-------|--------|-------|
|       |        |       |

## Breadcrumb Behavior
<!-- does the app use breadcrumbs? document pattern -->

## Screenshots
- `screenshots/03-nav-overview.png`
```

**Step 5: Commit**

```bash
git add docs/knowledge-base/02-navigation-map.md screenshots/03-nav-overview.png
git commit -m "docs: map top-level navigation structure"
```

---

### Task 4: Explore and Document Each Major Section (One Per Section)

> **Repeat this task for every top-level route found in Task 3.**
> Name each doc sequentially: `03-<section-name>.md`, screenshots `04-<section>-*.png`

**Files:**
- Create: `docs/knowledge-base/03-<section-name>.md`
- Create: `screenshots/04-<section-name>-overview.png`
- Create: `screenshots/04-<section-name>-<substate>.png` (as needed)

**Step 1: Navigate to the section**

Use Playwright MCP tool:
- `browser_navigate` → `<section URL>`

**Step 2: Screenshot the section landing**

Use Playwright MCP tool:
- `browser_screenshot` → save as `screenshots/04-<section-name>-overview.png`

**Step 3: Snapshot and enumerate interactive elements**

Use Playwright MCP tool:
- `browser_snapshot`

List: tables, forms, buttons, filters, search bars, modals, tabs, pagination, empty states.

**Step 4: Explore secondary interactions**

For each significant button/action:
- Click it
- Snapshot the resulting state
- Screenshot if it opens a modal, drawer, or new page
- Document the flow

**Step 5: Document the section**

Create `docs/knowledge-base/03-<section-name>.md`:

```markdown
# [Section Name]

**URL:** `<url>`
**Access:** Authenticated users only [ ] / Role-restricted [ ]

## Overview
<!-- one paragraph describing purpose -->

## Key Flows
### Flow 1: [e.g. Create Item]
1. Step 1
2. Step 2
...

### Flow 2: [e.g. Edit Item]
...

## UI Elements
| Element | Type | Purpose |
|---------|------|---------|
|         |      |         |

## Form Fields (if any)
| Field | Type | Required | Validation |
|-------|------|----------|------------|
|       |      |          |            |

## Empty State
<!-- screenshot filename + description -->

## Error States
<!-- what happens when things fail -->

## API Calls Observed
<!-- use browser_evaluate to check network if needed -->

## Screenshots
- `screenshots/04-<section-name>-overview.png`
```

**Step 6: Commit after each section**

```bash
git add docs/knowledge-base/03-<section-name>.md screenshots/04-<section-name>-*.png
git commit -m "docs: document <section-name> flows and UI"
```

---

### Task 5: Document Account & Settings Flows

**Files:**
- Create: `docs/knowledge-base/10-account-settings.md`
- Create: `screenshots/10-settings-*.png`

**Step 1: Navigate to account/settings**

Use Playwright MCP tool:
- `browser_navigate` → settings URL (found in Task 3 user menu)

**Step 2: Snapshot and screenshot all settings sections**

Use Playwright MCP tools:
- `browser_snapshot`
- `browser_screenshot` → `screenshots/10-settings-overview.png`

**Step 3: Document all settings flows**

Flows to capture:
- Profile update (name, avatar, etc.)
- Password change
- Email change
- Notification preferences
- Billing / subscription (if present)
- Team / org management (if present)
- API keys / integrations (if present)
- Delete account

**Step 4: Create the settings doc**

Follow the same template as Task 4 section doc.

**Step 5: Commit**

```bash
git add docs/knowledge-base/10-account-settings.md screenshots/10-settings-*.png
git commit -m "docs: document account and settings flows"
```

---

### Task 6: Document Logout Flow

**Files:**
- Modify: `docs/knowledge-base/01-auth-flow.md`
- Create: `screenshots/20-logout.png`

**Step 1: Find and trigger logout**

Use Playwright MCP tools:
- `browser_snapshot` → find logout button/link
- `browser_click` → logout element ref

**Step 2: Screenshot post-logout state**

Use Playwright MCP tool:
- `browser_screenshot` → `screenshots/20-logout.png`

**Step 3: Verify redirect**

Observe URL after logout. Attempt to navigate back to a protected URL and confirm redirect to login.

**Step 4: Update auth flow doc**

Add Logout Flow section to `docs/knowledge-base/01-auth-flow.md`:

```markdown
## Logout Flow
1. User clicks logout (location: `<where found>`)
2. Session cleared: [ ] localStorage [ ] cookie [ ] sessionStorage
3. Redirect to: `<url>`
4. Accessing protected URL after logout: redirect to `<url>`
```

**Step 5: Commit**

```bash
git add docs/knowledge-base/01-auth-flow.md screenshots/20-logout.png
git commit -m "docs: document logout flow and session teardown"
```

---

### Task 7: Synthesize Master Knowledge Base Index

**Files:**
- Create: `docs/knowledge-base/README.md`
- Create: `docs/knowledge-base/99-test-ideas.md`

**Step 1: Create the README index**

Create `docs/knowledge-base/README.md`:

```markdown
# BlueCallom App — Knowledge Base

Discovered via Playwright MCP on YYYY-MM-DD.
**App URL:** https://bluecallom.ai

## Documents

| File | Description |
|------|-------------|
| [00-login-page.md](00-login-page.md) | Login page structure and elements |
| [01-auth-flow.md](01-auth-flow.md) | Login, logout, session behavior |
| [02-navigation-map.md](02-navigation-map.md) | All routes and nav structure |
| [03-*.md](.) | Individual section flows |
| [10-account-settings.md](10-account-settings.md) | Account and settings flows |
| [99-test-ideas.md](99-test-ideas.md) | Suggested E2E test cases |

## App Summary
<!-- fill in after exploration: what does the app do? -->

## Key User Roles
<!-- e.g. Admin, Standard User, Viewer -->

## Critical Flows (highest test priority)
1. <!-- e.g. Login / Logout -->
2.
3.
```

**Step 2: Create the test ideas doc**

Create `docs/knowledge-base/99-test-ideas.md` based on all flows discovered:

```markdown
# Suggested E2E Test Cases

Derived from flow discovery. Prioritized by risk.

## Critical (must have)
- [ ] Login with valid credentials → lands on dashboard
- [ ] Login with invalid credentials → shows error
- [ ] Session persists on page reload
- [ ] Logout clears session and redirects
- <!-- add more based on discovered flows -->

## High Priority
- <!-- CRUD flows for main entities -->

## Medium Priority
- <!-- edge cases, validation -->

## Low Priority
- <!-- cosmetic, nice-to-have -->
```

**Step 3: Commit**

```bash
git add docs/knowledge-base/README.md docs/knowledge-base/99-test-ideas.md
git commit -m "docs: add knowledge base index and test ideas"
```

---

## Output Summary

After completing all tasks, the project will contain:

```
docs/
  knowledge-base/
    README.md                    # master index
    00-login-page.md             # login page elements
    01-auth-flow.md              # auth + session + logout
    02-navigation-map.md         # all routes
    03-<section>.md              # one file per major section
    10-account-settings.md       # settings flows
    99-test-ideas.md             # prioritized test cases
screenshots/
    01-login-page.png
    02-post-login-landing.png
    03-nav-overview.png
    04-<section>-*.png
    ...
```

This knowledge base becomes the source of truth for writing the Playwright E2E test suite.
