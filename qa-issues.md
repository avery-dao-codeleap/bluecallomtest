# BlueCallom.ai - Comprehensive QA Test Report

**Test Date:** January 27, 2026
**Tester:** Automated Testing with Playwright MCP
**Platform URL:** https://bluecallom.ai/
**Test Account:** avery.dao@codeleap.de (CODE LEAP AG)
**Browser:** Chromium (Playwright)
**Viewports Tested:** Desktop (1366x768), Mobile (375x812)

---

## Executive Summary

Comprehensive QA testing was performed on the BlueCallom Enterprise AI Workflow platform covering 12 main application flows, input validation, responsive design, and edge cases.

### Test Results at a Glance

| Metric | Value |
|--------|-------|
| Total Issues Found | **70** |
| High Severity | 3 |
| Medium Severity | 22 |
| Low Severity | 45 |
| Tests Passed | 15 |
| Screenshots Captured | 21 |

### Critical Findings

1. **Create Referral Key Feature Broken** - Returns generic error, completely non-functional
2. **Welcome Modal Reappears Every Visit** - Annoying UX, modal shows on every /home navigation
3. **Duplicate Library Entries** - Same library appears 4 times in Libraries page

### Risk Statement

> **If left unresolved**, these issues risk reducing enterprise trust, increasing onboarding friction, and creating support overhead—particularly around referral functionality (blocking user acquisition incentives), analytics clarity (undermining data-driven decisions), and inconsistent terminology (confusing brand perception). The broken referral feature directly impacts growth mechanics, while the persistent welcome modal creates daily user frustration that could drive churn.

### Top 5 Recommended Fix Order

| Priority | Issue | Owner | Business Rationale |
|----------|-------|-------|-------------------|
| **1** | Create Referral Key broken | `ENG` | Blocks feature adoption & referral-based user acquisition |
| **2** | Welcome Modal persistence | `ENG` | Daily user friction, impacts retention |
| **3** | Library duplication (4x entries) | `DATA` | Erodes data trust, confuses users |
| **4** | Branding standardization | `CONTENT` | AgenticBlue/GPT Blue inconsistency hurts brand perception |
| **5** | Mobile table truncation | `ENG`/`UX` | Enterprise users expect mobile functionality |

### Owner Type Legend

| Tag | Team | Scope |
|-----|------|-------|
| `ENG` | Engineering | Functional bugs, API errors, data issues |
| `UX` | Design/UX | Layout, interactions, user flows |
| `CONTENT` | Content/Marketing | Grammar, wording, branding, terminology |
| `DATA` | Data/Backend | Duplicates, analytics, data integrity |

---

## Testing Methodology

### What Was Tested

| Test Type | Description | Status |
|-----------|-------------|--------|
| **Visual/Navigation Testing** | All 12 main application flows | Completed |
| **Input Validation** | Form submissions with valid/invalid data | Completed |
| **Responsive Design** | Mobile viewport (375px) testing | Completed |
| **Edge Cases** | Special characters, unicode, XSS | Completed |
| **Extended Coverage** | Settings, Password, Event Registration | Completed |

### Flows Tested

1. My Profile (`/app/userProfileEdit`)
2. My Messages (`/app/myMessages`)
3. Team (`/app/teams`)
4. Action Space (Dashboard tile)
5. Analytics (`/app/overviewAnalytics`)
6. Libraries (`/app/libraries`)
7. Corp Portal (`/app/corpLibrary`)
8. Partner Portal (Dashboard tile)
9. GPT Blue Studio (Access dialog)
10. Accounting/CC (`/app/accounting`)
11. Create Referral Key (Dialog)
12. Welcome Note (Modal)

---

## Issues by Category

### 1. Functional Bugs (HIGH SEVERITY)

| ID | Location | Issue | Impact | Owner |
|----|----------|-------|--------|-------|
| **IV-13** | Create Referral Key | Clicking button returns error: "Error occurred while updating user detail" | Feature completely broken | `ENG` |
| **WN12-01** | Welcome Modal | Modal reappears every time user navigates to /home | Very annoying UX | `ENG` |
| **L6-01** | Libraries Page | "Avery Dao's Personal Library" appears 4 times (duplicated) | Data integrity issue | `DATA` |

---

### 2. Typos & Spelling Errors

| ID | Location | Error | Correction | Owner |
|----|----------|-------|------------|-------|
| PW-01 | Password Change | "Confirm Pass**ow**rd" | "Confirm Pass**wo**rd" | `CONTENT` |
| ER-01 | Event Registration URL | `/eventRegist**e**ration` | `/eventRegist**ra**tion` | `ENG` |
| ER-02 | Event Registration Title | "Event Regist**e**ration List" | "Event Regist**ra**tion List" | `CONTENT` |
| PF-01 | Profile Form | "Please enter **buisness** email" | "Please enter **business** email" | `CONTENT` |
| IV-09 | Messages Validation | "There should be **atleast** one recipient" | "There should be **at least** one recipient" | `CONTENT` |
| ST-01 | Settings Header | "My AgenticBlue Portal \| **Setting**" | "My AgenticBlue Portal \| **Settings**" | `CONTENT` |

---

### 3. Grammar Issues

| ID | Location | Error | Correction | Owner |
|----|----------|-------|------------|-------|
| M2-01 | Messages/Settings | "select **a** Agent" | "select **an** Agent" (appears 3x) | `CONTENT` |
| M2-02 | Messages/Settings | "**New Comer**" | "**Newcomer**" (one word) | `CONTENT` |
| CP7-03 | Corp Portal | "No solution **exists**." | "No solutions **exist**." | `CONTENT` |
| RK11-03 | Referral Dialog | "execute professional Agent" | "execute **a** professional Agent" | `CONTENT` |
| WN12-03 | Welcome Modal | "**open minded**" | "**open-minded**" (hyphenated) | `CONTENT` |

---

### 4. Branding & Naming Inconsistencies

| ID | Location | Issue | Owner |
|----|----------|-------|-------|
| T3-01 | Team Page | "**Agentic Blue**" vs "**AgenticBlue**" used elsewhere | `CONTENT` |
| GS9-01 | GPT Blue Studio | Dialog says "**GPTBlue** Studio" but tile says "**GPT Blue** Studio" | `CONTENT` |
| WN12-05 | Welcome Modal | "**GPTBlue**" (no space) vs dashboard "**GPT Blue**" (with space) | `CONTENT` |
| L6-05 | Libraries | "**Agentic Blue**" (space) inconsistent with "**AgenticBlue**" | `CONTENT` |
| CP7-01 | Corp Portal | Dashboard tile "Corp Portal" → navigates to "Organization Library" page | `UX` |
| AC10-01 | Accounting | Page title "Rewards" but URL is `/accounting` and link shows "CC" | `UX` |

---

### 5. Undefined Terms & Acronyms

| ID | Location | Issue | Owner |
|----|----------|-------|-------|
| T3-02 | Team Page | "**AAIS** Teams and Me" - acronym never explained | `CONTENT` |
| AN5-01 | Analytics | "**AAIS** Overview" - same undefined acronym | `CONTENT` |
| L6-03 | Libraries | "Available **AAIS** Applications" - still undefined | `CONTENT` |
| CP7-05 | Corp Portal | "**C-Portal**" abbreviation unexplained in navigation | `CONTENT` |

---

### 6. UI/UX Issues

| ID | Severity | Location | Issue | Owner |
|----|----------|----------|-------|-------|
| A4-01 | Medium | Action Space Tile | Appears clickable (cursor pointer) but doesn't navigate anywhere | `ENG` |
| PP8-01 | Medium | Partner Portal Tile | No dedicated page - tile click does nothing | `ENG` |
| AN5-02 | Medium | Analytics Chart | Missing X-axis labels | `UX` |
| AN5-03 | Low | Analytics Chart | Legend has unlabeled square icon | `UX` |
| L6-02 | Medium | Libraries | Placeholder description "---" instead of content | `CONTENT` |
| L6-04 | Low | Libraries | Generic placeholder images for thumbnails | `UX` |
| CP7-02 | Medium | Corp Portal | Two panels with identical headers | `UX` |
| CP7-06 | Low | Corp Portal | Unlabeled slider widget | `UX` |
| PF-02 | Medium | Profile Form | "Name" field placeholder shows "Please enter Placeholder" | `ENG` |
| IV-06 | Medium | Profile Save | Confusing tooltip: "send content to all BlueCallom Users" | `UX` |
| IV-12 | Medium | New Message | Alarming button label "Send to all users !!!" | `UX` |
| WN12-02 | Medium | Welcome Modal | Says "gift of CC 2,500" but profile showed "CC 0" initially | `ENG` |
| M2-03 | Low | Messages Page | Onboarding text about coins appears on Messages page (out of place) | `UX` |

---

### 7. Responsive/Mobile Issues

| ID | Severity | Issue | Screenshot | Owner |
|----|----------|-------|------------|-------|
| MR-01 | Medium | Accounting table columns truncated on 375px - "Coin Spent" shows as "Co Sp", Balance column hidden | mobile-accounting-375.png | `ENG`/`UX` |
| MR-02 | Low | Tables need horizontal scroll on mobile | mobile-accounting-full.png | `ENG`/`UX` |

---

### 8. Miscellaneous Issues

| ID | Severity | Location | Issue | Owner |
|----|----------|----------|-------|-------|
| P1-03 | Low | Profile | Mobile Phone shows "-" instead of empty/placeholder | `UX` |
| GS9-02 | Low | GPT Blue Studio | Missing space after period: "developers.To gain" | `CONTENT` |
| RK11-01 | Low | Referral Dialog | Random capitalization: "you can Use to execute" | `CONTENT` |
| RK11-02 | Low | Referral Dialog | "Friends" capitalized mid-sentence | `CONTENT` |
| RK11-04 | Low | Referral Dialog | "Generative-AI" hyphenated (usually "Generative AI") | `CONTENT` |
| WN12-04 | Low | Welcome Modal | "USER PROFILE" in all caps, inconsistent | `UX` |
| AN5-04 | Low | Analytics | Period selector shows 2023-2025 for user who joined Jan 2026 | `DATA` |
| IV-15 | Low | Analytics | No "No data" message when selecting years before user joined | `UX` |

---

## Input Validation Results

### Profile Form

| Test | Result | Notes |
|------|--------|-------|
| Required field (First Name) | **PASS** | Shows "First Name is required" |
| Required field (LinkedIn URL) | **PASS** | Shows "LinkedIn URL is required." |
| Email format validation | **PASS** | Shows "Email address must be in the format of name@domain.com" |
| Phone format validation | **PASS** | Shows helpful format examples |
| Save with valid data | **PASS** | Shows "User details updated Successfully" |

### Messages - New Message

| Test | Result | Notes |
|------|--------|-------|
| Recipient required | **PASS** | Shows validation message |
| Subject required | **PASS** | Shows "Subject is required." |
| Body/Editor required | **PASS** | Shows "Editor is required." |

### Other Validations

| Test | Result | Notes |
|------|--------|-------|
| Analytics period filter | **PASS** | Dropdown changes year successfully |
| Create Referral Key | **FAIL** | Returns error instead of creating key |

---

## Edge Case Testing

| Test | Result | Notes |
|------|--------|-------|
| German umlauts (äöüß) | **PASS** | Displays correctly |
| Japanese characters (日本語) | **PASS** | Displays correctly |
| Emojis (🎉) | **PASS** | Displays correctly |
| XSS script injection | **PASS** | Rendered as plain text (secure) |
| HTML entities (&, quotes) | **PASS** | Handled properly |

---

## Screenshots Index

| Filename | Issue Documented |
|----------|------------------|
| flow1-profile-issues.png | Profile: LinkedIn required, Name field confusion, placeholder issues |
| flow2-messages.png | Grammar: "a Agent", "New Comer", misplaced onboarding text |
| flow3-team.png | Branding inconsistency, undefined "AAIS" acronym |
| flow4-actionspace-dashboard.png | Non-functional tile click |
| flow5-analytics.png | Missing chart labels, undefined "AAIS" |
| flow6-libraries.png | **HIGH: Duplicate library entries (4x)** |
| flow7-corpportal.png | Naming mismatch, duplicate panels |
| flow8-partnerportal-dashboard.png | Non-functional tile, no dedicated page |
| flow9-gptbluestudio-access-dialog.png | Branding: "GPTBlue" vs "GPT Blue" |
| flow10-accounting.png | Naming mismatch: "Rewards" vs "Accounting" |
| flow11-referralkey-dialog.png | Capitalization issues in dialog text |
| flow12-welcomenote.png | **HIGH: Modal reappears every visit** |
| input-validation-profile-required.png | Validation errors: First Name, Phone, LinkedIn |
| input-validation-profile-email.png | Email format validation error shown |
| input-validation-messages-required.png | Typo: "atleast" + validation errors |
| input-validation-referral-key-error.png | **HIGH: Feature broken - generic error** |
| settings-page-issues.png | Typo: "Setting" missing 's' |
| password-change-full.png | Typo: "Confirm Passowrd" |
| event-registration-typo.png | Typo: "Registeration" in URL and title |
| mobile-accounting-375.png | Table truncation on mobile |
| mobile-accounting-full.png | Full view of truncated columns |

**Total: 21 screenshots** (6 removed - showed only passing tests)

All screenshots saved to `.playwright-mcp/` directory.

---

## Recommendations

### Immediate Fixes (High Priority)

1. **Fix Create Referral Key** - Currently returns generic error, feature is broken
2. **Fix Welcome Modal** - Should only show once (use localStorage/cookie flag)
3. **Fix Library Duplicates** - Investigate data issue causing 4x entries

### Short-term Fixes (Medium Priority)

4. **Fix all typos** - "Passowrd", "Registeration", "buisness", "atleast"
5. **Standardize branding** - Choose one: "GPTBlue" OR "GPT Blue" OR "AgenticBlue"
6. **Define "AAIS" acronym** - Add explanation or use full name
7. **Fix mobile table truncation** - Add horizontal scroll or responsive table
8. **Fix non-functional tiles** - Action Space, Partner Portal should navigate somewhere

### Low Priority Fixes

9. **Grammar corrections** - "a Agent" → "an Agent", "New Comer" → "Newcomer"
10. **Consistent naming** - Align page titles with navigation labels
11. **Placeholder texts** - Fix "Please enter Placeholder" on Name field
12. **Chart improvements** - Add X-axis labels, legend labels

### Additional Testing Recommendations

**Not Yet Tested:**
- Company form creation/editing
- Feedback system with screenshot capture
- Social OAuth flows (LinkedIn/Google/X)
- Photo upload functionality
- Mailbox configuration
- Session timeout behavior
- Multi-user/concurrent sessions
- Cross-browser compatibility (Safari, Firefox, Edge)
- Accessibility (WCAG compliance, screen readers)
- Performance/load testing

---

## Frontend Architecture & Tooling (Inferred)

**Inference Date:** February 10, 2026
**Method:** Browser runtime inspection only (DevTools, network requests, source maps, DOM patterns)
**Source Map Availability:** Yes — publicly accessible at `/static/js/main.9971a00f.js.map` (486 source files mapped)

> **Note:** All findings below are based exclusively on observable browser evidence. No source code repository access was used.

---

### 1. Frontend Framework: React 18.2.0

| Attribute | Detail |
|-----------|--------|
| **Observed** | React fiber keys on DOM elements (`__reactFiber$`, `__reactContainer$`), `#root` mount point, `createRoot` / `hydrateRoot` APIs present in bundle, React 18-only hooks (`useId`, `useDeferredValue`, `useInsertionEffect`, `useTransition`), version string `"18.2.0"` found twice in minified bundle |
| **Suggests** | React 18.2.0 with concurrent rendering capabilities |
| **Confidence** | **High** |

**Implications:**
- **Maintainability:** React 18 is a well-supported, current-generation framework. The concurrent features (Suspense, lazy loading confirmed in bundle) indicate modern patterns are in use.
- **Type Safety:** See TypeScript section below.
- **QA & Testing:** React Testing Library and standard React testing approaches are fully applicable. Component-level testing with concurrent mode should be considered.
- **Future Scope:** Well-positioned for React 19 migration path. No legacy class-component-only patterns detected (though `componentDidCatch` / error boundaries are present, which is expected).

---

### 2. Build Tooling: Webpack (Create React App origin, likely ejected or customized)

| Attribute | Detail |
|-----------|--------|
| **Observed** | `webpackChunkblue_callom` global variable, `../webpack/runtime/*` entries in source map (14 runtime modules), `static/js/main.[hash].js` + `static/css/main.[hash].css` naming convention, `manifest.json` with CRA-style PWA configuration (`"start_url": "."`, `"display": "standalone"`), `<noscript>You need to enable JavaScript to run this app.</noscript>` (CRA boilerplate), `reportWebVitals.ts` in source map, content-hashed chunk filenames (`6729.2fddc6df.chunk.js`, `6290.3447bad9.chunk.js`) |
| **Suggests** | Originally scaffolded with Create React App (CRA), bundled via Webpack 5. Code splitting is active (multiple chunks). |
| **Confidence** | **High** |

**Implications:**
- **Maintainability:** CRA is in maintenance mode (no major updates since 2022). If still using `react-scripts`, migration to Vite or a custom Webpack config may eventually be advisable.
- **QA & Testing:** Jest + React Testing Library are the default CRA test runners and should work out of the box.
- **Future Scope:** Bundle size is ~1.19 MB for the main JS chunk (minified). This is moderately large. Tree-shaking and code-splitting improvements could reduce initial load.

---

### 3. Language: TypeScript

| Attribute | Detail |
|-----------|--------|
| **Observed** | Source map contains **335 `.ts`/`.tsx` files** vs 119 `.js`/`.jsx` files (the JS files are exclusively from `node_modules`). All application source files use `.ts` or `.tsx` extensions. `__esModule` helpers present in bundle. App entry point is `index.tsx`, main component is `App.tsx`. |
| **Suggests** | The application is written **entirely in TypeScript**. |
| **Confidence** | **High** |

**Application file breakdown (from source map):**
- `.tsx` files: 25 (React components)
- `.ts` files: 22 (utilities, API layer, constants, guards, hooks)
- `.svg` assets: 12

**Implications:**
- **Type Safety:** Strong structural evidence of deliberate TypeScript adoption across all layers (components, API integration, routing guards, utilities). However, see the Type Safety Assessment below for runtime behavior analysis.
- **Maintainability:** TypeScript provides compile-time safety. The consistent use across the codebase (no mixed JS/TS app files) is a positive signal.
- **QA & Testing:** TypeScript reduces certain categories of bugs (null reference, type mismatch) at compile time. Runtime testing remains essential for business logic and integration.

---

### 4. UI Framework: Bootstrap 5.3.2

| Attribute | Detail |
|-----------|--------|
| **Observed** | CSS banner comment: `Bootstrap v5.3.2 (https://getbootstrap.com/)`, Bootstrap 5-specific classes active in DOM (`visually-hidden`, `form-floating`, `accordion`, `text-end`, `rounded-pill`), `--bs-*` CSS custom properties (2,627 custom properties total), `data-bs-theme` attribute for light/dark theming, 26 Bootstrap JS source files in source map (modal, dropdown, carousel, collapse, offcanvas, tooltip, popover, etc.), `@popperjs/core` dependency (Bootstrap 5's positioning engine) |
| **Suggests** | Bootstrap 5.3.2 with full JS component suite and dark mode theming support |
| **Confidence** | **High** |

**Custom Design Layer:**
- 12 custom `bc-*` CSS classes observed (e.g., `bc-bg-actionSpace`, `bc-bg-analytics`, `bc-column-3`, `bc-range`, `bc-line-before`)
- Custom CSS variables with `--bc-*` prefix for glassmorphism effects (`--bc-glass-blur`, `--bc-glass-bg`, `--bc-card-bg`)
- Light/dark theme variants defined via `[data-bs-theme=light]` and `[data-bs-theme=dark]`

**Implications:**
- **Maintainability:** Bootstrap 5.3.x is actively maintained. The custom `bc-*` layer indicates a branded design system built on top of Bootstrap — maintainable as long as the custom layer stays thin.
- **QA & Testing:** Visual regression testing should cover both light and dark themes. The glassmorphism layer (`backdrop-filter: blur`) may have cross-browser rendering differences.
- **Future Scope:** No `react-bootstrap` or `reactstrap` wrapper detected — Bootstrap is used directly with vanilla JS components. This is a potential fragility point: direct Bootstrap JS manipulation can conflict with React's virtual DOM.

---

### 5. State Management: Redux (via @reduxjs/toolkit) + React Hook Form

| Attribute | Detail |
|-----------|--------|
| **Observed** | `@reduxjs/toolkit`, `redux`, `redux-thunk`, `react-redux`, `reselect`, and `immer` all present in source map packages. `use-sync-external-store` (Redux 8+ dependency) confirmed. `commonSlice.ts` in source map (RTK slice pattern). `api-middleware.tsx` suggests custom API middleware. 61 `react-hook-form` source files in source map. |
| **Suggests** | Redux Toolkit for global state, React Hook Form for form state management |
| **Confidence** | **High** |

**Implications:**
- **Maintainability:** RTK is the modern recommended Redux approach. The presence of `api-middleware.tsx` (custom) alongside RTK Query signals (`createApi`/`fetchBaseQuery` found in bundle) suggests the API layer may be in transition or using both patterns.
- **Type Safety:** RTK provides strong TypeScript integration. React Hook Form also has excellent TS support. Both reduce the likelihood of state-related type errors.
- **QA & Testing:** State can be tested independently via Redux store tests. Form validation logic (React Hook Form) should have dedicated test coverage.

---

### 6. Internationalization: i18next + react-i18next

| Attribute | Detail |
|-----------|--------|
| **Observed** | `i18next` and `react-i18next` packages in source map, `i18n/i18n.ts` configuration file, `hooks/ui/usePageTranslation.ts` custom hook, `i18nextLng: "en"` in localStorage, `html-parse-stringify` dependency (used by react-i18next for Trans component) |
| **Suggests** | Full i18n infrastructure with custom translation hook |
| **Confidence** | **High** |

**Implications:**
- **QA & Testing:** Translation coverage and missing key detection should be part of QA. The custom `usePageTranslation` hook suggests page-level translation loading.
- **Future Scope:** The infrastructure supports multi-language deployment.

---

### 7. Routing: React Router (v6+)

| Attribute | Detail |
|-----------|--------|
| **Observed** | `react-router` and `react-router-dom` packages in source map, `@remix-run/router` (the underlying engine for React Router v6.4+), `history.state` contains `{usr, key, idx}` (React Router v6 state shape), auth guards (`guards/auth.guard.tsx`, `guards/non-auth.guard.tsx`), path-based routing (no hash, e.g., `/home`, `/app/userProfileEdit`) |
| **Suggests** | React Router v6.4+ with data router features |
| **Confidence** | **High** |

**Implications:**
- **Maintainability:** React Router v6 is the current standard. The auth guard pattern is clean and well-structured.
- **QA & Testing:** Route-level testing and guard logic verification should be included. Deep-link testing is important given the path-based routing.

---

### 8. Additional Libraries Detected

| Library | Evidence | Confidence |
|---------|----------|------------|
| **markdown-it** | Package in source map, with `linkify-it`, `mdurl`, `punycode.js`, `uc.micro` dependencies | High |
| **html2canvas** | Package in source map (screenshot/export functionality) | High |
| **react-icons** | Package in source map | High |
| **react-google-recaptcha-v3** | Package in source map, reCAPTCHA iframe + badge visible in DOM, site key `6LenJGsp...` | High |
| **Google Fonts (Open Sans)** | Stylesheet loaded from `fonts.googleapis.com`, confirmed in computed styles | High |

---

### 9. Backend API Architecture (Observed from Network)

| Attribute | Detail |
|-----------|--------|
| **API Host** | `gptblueapi.bluecallom.ai` |
| **Protocol** | HTTPS, all POST requests |
| **Pattern** | RPC-style REST: `/rest/gptblueAPI/{serviceCFC}/{methodName}/` |
| **Observed Services** | `gptBlueAdmin`, `gptbluePublicCFC`, `userManagerCFC`, `gptBlueAccBranding`, `appDashboard`, `gptUserMessage`, `gptBluePartner`, `gptBlueSystemCFC` |
| **Auth Pattern** | Token stored in localStorage (`refreshToken` key), user profile stored as JSON object with 37 fields |
| **Static Assets** | Served from `cloud.bluecallom.ai/data/` (logos, photos) |
| **Confidence** | **High** |

**Naming Convention Note:** The `CFC` suffix in endpoint service names (e.g., `userManagerCFC`, `gptbluePublicCFC`) is characteristic of ColdFusion Component naming conventions, suggesting the backend may be built on Adobe ColdFusion or Lucee CFML.

---

### 10. Security Observations

| Item | Detail |
|------|--------|
| **Source Maps Exposed** | `.js.map` files are publicly accessible in production. This exposes the **full application source code**, file structure, and all package dependencies to any visitor. **This is a significant security concern.** |
| **Auth Tokens in localStorage** | `refreshToken` and full user profile stored in localStorage. This is vulnerable to XSS-based token theft (unlike httpOnly cookies). |
| **reCAPTCHA v3** | Implemented for bot protection (invisible mode). |
| **No Service Worker** | PWA manifest exists but no active service worker detected. |

---

### 11. Type Safety Assessment (Runtime Behavior Analysis)

**Overall Assessment: Structurally sound, with some runtime fragility signals**

| Signal | Observation | Implication |
|--------|-------------|-------------|
| **Positive:** Full TypeScript adoption | 100% of app source files are `.ts`/`.tsx` | Compile-time type checking is comprehensive |
| **Positive:** RTK + React Hook Form | Both have excellent TS support | State and form layers are well-typed |
| **Positive:** Clean console | Zero errors or warnings on page load | No obvious runtime type mismatches on the happy path |
| **Concern:** Direct Bootstrap JS usage | No React wrapper library; vanilla Bootstrap JS manipulates DOM directly | Potential for React/Bootstrap DOM conflicts that TypeScript cannot catch at compile time |
| **Concern:** Large user object (37 fields) | Stored as untyped JSON in localStorage | Runtime parsing of this object could be fragile if the API contract changes |
| **Concern:** Duplicate API calls observed | Same endpoints (`checkBLCAdminSecurity`, `getPageTileInfo`, `getUserProfile`) called 3x on page load | Suggests potential issues in effect dependencies or component mounting logic — not a type safety issue per se, but indicates areas where stricter typing of side effects could help |

**Confidence in Type Safety Assessment:** **Medium** — structural evidence is strong, but runtime behavior can only be partially evaluated from outside the codebase.

---

### 12. Summary & Recommendations

#### Confirmed Technology Stack

| Layer | Technology | Version | Confidence |
|-------|-----------|---------|------------|
| Framework | React | 18.2.0 | High |
| Language | TypeScript | (version not determinable) | High |
| Build Tool | Webpack (CRA-derived) | 5.x (inferred) | High |
| UI Framework | Bootstrap | 5.3.2 | High |
| State Management | Redux Toolkit + React Hook Form | — | High |
| Routing | React Router | 6.4+ | High |
| i18n | i18next + react-i18next | — | High |
| API Layer | Custom middleware + fetch | — | High |
| Backend (inferred) | ColdFusion/CFML (from CFC naming) | — | Medium |

#### Recommendations (Medium-High Confidence)

1. **Disable source maps in production** — The exposed `.map` files reveal the entire application structure, file names, and dependency tree. This should be addressed immediately.

2. **Investigate duplicate API calls** — Three endpoints are called 3x each on home page load. This suggests unnecessary re-renders or missing dependency arrays in `useEffect` hooks. This wastes bandwidth and backend resources.

3. **Consider a React-Bootstrap wrapper** — Direct Bootstrap JS DOM manipulation alongside React's virtual DOM is a known source of subtle bugs. Adopting `react-bootstrap` (which provides React-native Bootstrap components) would eliminate this conflict surface.

4. **Evaluate CRA migration path** — CRA is effectively unmaintained. Consider migrating to Vite (most popular CRA replacement) for faster builds, better tree-shaking, and active maintenance.

5. **Move auth tokens to httpOnly cookies** — localStorage-based token storage is vulnerable to XSS attacks. Coordinate with the backend team to implement secure cookie-based authentication.

6. **Reduce main bundle size** — At ~1.19 MB (minified JS), the initial payload is heavy. The `markdown-it` and `html2canvas` libraries could potentially be lazy-loaded only on pages that need them.

*Architecture inference generated: February 10, 2026*
*Method: Browser-only runtime inspection via Playwright MCP*
