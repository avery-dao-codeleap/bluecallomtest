# Authentication Flow

## Login Flow

### Corporate Login (email + password)
1. User navigates to `/login`
2. User clicks "For Corporate Login" link — reveals an email + password form inline
3. User fills email and password fields
4. User clicks "Login" button
5. On success: immediate redirect to `/home`
6. On failure: (not yet observed — test with wrong credentials in future)

### Social Login (OAuth)
1. User navigates to `/login`
2. User clicks "Login/Registration with LinkedIn" or "Login/Registration with Google"
3. OAuth provider handles authentication
4. On success: redirect back to `/home`

### Form Fields (Corporate Login)
| Field | Type | Placeholder | Required |
|-------|------|-------------|----------|
| Email | textbox | "Please enter email" | Yes |
| Password | textbox | "Enter Password" | Yes |

### Supporting Elements
- "Forgot Password" link → `/forgotpwd`
- reCAPTCHA (Google) embedded for bot protection

## Session Behavior

- **Session token storage:** `localStorage` (not cookies, not sessionStorage)
- **No HTTP-only cookies observed** — `document.cookie` is empty after login
- **SessionStorage:** empty

### localStorage Keys Set on Login

| Key | Value / Description |
|-----|---------------------|
| `isLoggedIn` | `"true"` — boolean flag |
| `refreshToken` | JWT (RS256), audience: `https://www.gptBlueAI.Com/token` |
| `user` | Full user object JSON (see below) |
| `LibraryType` | `"personal"` — default library context |
| `i18nextLng` | `"en"` — i18n language preference |
| `_grecaptcha` | reCAPTCHA token |

### Refresh Token (JWT) Details

- **Algorithm:** RS256
- **Issuer:** `support@bluecallom.com`
- **Audience:** `https://www.gptBlueAI.Com/token`
- **Scope:** `https://www.gptBlueAI.Com`
- **token_type:** `"refresh"`
- **Issued at (iat):** ~Feb 2026
- **Expiry (exp):** ~Feb 2027 (approximately 1 year)
- **userId embedded in token payload**

> Note: No separate access token observed in localStorage or sessionStorage. The access token is likely held in memory (JS variable) and obtained by exchanging the refreshToken server-side.

### `user` Object (localStorage) — Key Fields

| Field | Value |
|-------|-------|
| `userEmail` | nam.ho@codeleap.de |
| `userId` | 201890294 |
| `username` | NamHo-presence |
| `userType` | "Qua" |
| `userlevel` | "Onboarded" |
| `firstName` / `lastName` | Nam Ho |
| `totalCCPoints` / `userCCBalance` | 10,000 CC |
| `orgCCBalance` | 10,000 CC |
| `usrCreatedDate` | 2026-02-24 |
| `betaUser` | true |
| `accId` | 300000001 |
| `orgId` | 4000001 |
| `accountType` | "user" |
| `isProfileComplete` | true |
| `CCtoCHF` | 0.0003 |
| `userCompanyData.companyname` | CODE LEAP AG |
| `userCompanyData.companyCode` | "codeleap" |

## Post-Login Landing

**URL:** `https://bluecallom.ai/home`
**Page Title:** BlueCallom

### Home Page Layout
The home page is a dashboard with two main panels:

**Left sidebar:**
- "My Profile" card — user name, avatar, CC balance, "Create Referral Key" button, join date
- "My Messages" card — message inbox (shows "No Records Found" when empty)
- Bottom: social/help icons, BlueCallom logo, home icon, layout toggle

**Right content area ("My Applications"):**
- Grid of module cards, each clickable:

| Module Card | Key Stats Shown |
|-------------|----------------|
| Team | Teammate(s), Team(s), Profile %, Badges |
| Action Space | Flight(s), Application(s), Agent(s), Prompt(s), Last Used |
| Analytics | Description text only (no counts) |
| Libraries | Library count, Application count, Most Used library |
| Corp Portal | Department(s), Country(s), CC balance |
| Partner Portal | Role (Partner Manager), Program(s), Partner(s) |
| GPTBlue Studio | Application(s), Agent(s), Prompt(s) |

## Logout Flow

### Logout Button Location

The logout button is an icon in the **"My Profile" sidebar panel**, visible on all authenticated pages. It is the 3rd icon in the bottom icon row of the profile card.

**Tooltip on hover:** "Logs you out. Login to come back."

### Logout Flow Steps

1. User hovers over the exit/door icon in the My Profile sidebar — tooltip appears
2. User clicks the icon
3. **Immediate redirect to** `/login`
4. A flash alert appears at the top of the login page: *"Your session is expired please re-login again."*
5. `localStorage` is completely cleared (all keys removed — `isLoggedIn`, `refreshToken`, `user`, `LibraryType`, `i18nextLng`, `_grecaptcha` all gone)
6. The login form is shown (unauthenticated state)

### Post-Logout State

| Aspect | State |
|--------|-------|
| URL | `https://bluecallom.ai/login` |
| localStorage | Empty (all keys cleared) |
| sessionStorage | Empty (unchanged — was already empty) |
| Alert shown | "Your session is expired please re-login again." |
| Login page | Shows standard OAuth + Corporate login options |

### Session Cleanup Mechanism

Logout clears all auth state from `localStorage` client-side. There is no observed server-side session invalidation call (no logout API endpoint observed). The JWT refresh token is simply removed from localStorage, making it inaccessible to the app.

### Screenshots
- `screenshots/06-home-pre-logout.png` — home dashboard with logout button visible
- `screenshots/06-logout-button-hover.png` — tooltip "Logs you out. Login to come back."
- `screenshots/06-post-logout.png` — post-logout login page

## Session Expiry / Persistence

- Refresh token has ~1 year TTL.
- `isLoggedIn: "true"` flag in localStorage persists across page reloads.
- Clearing localStorage (via JS or browser DevTools) breaks the session — navigating to `/login` then shows the login form instead of redirecting.

## Screenshots

- `screenshots/01-login-page.png` — login form (unauthenticated state)
- `screenshots/02-post-login-landing.png` — home dashboard after login
