# Login Page

**URL:** https://bluecallom.ai/login

## Form Fields

No traditional email/password form fields exist. Authentication is exclusively OAuth-based (see Login Methods below).

## Actions

| Element | Type | Label | Behavior |
|---------|------|-------|----------|
| Login/Registration with LinkedIn | Button | "Login/Registration with LinkedIn" | Initiates LinkedIn OAuth flow |
| Login/Registration with Google | Button | "Login/Registration with Google" | Initiates Google OAuth flow |
| For Corporate Login | Link | "For Corporate Login" | href="#" — likely opens a corporate SSO modal or separate flow |
| Share icon | Button (icon) | (no label) | Top-right of login card; shares the page |
| Left/Right nav arrows | Buttons (icon) | (no label) | Navigation within the login card (carousel or multi-step) |
| Terms of Service | Link | "Terms of Service" | https://bluecallom.com/terms/ |
| Privacy Policy | Link | "Privacy Policy" | https://bluecallom.com/privacy/ |

## Login Methods

1. **LinkedIn OAuth** — "Login/Registration with LinkedIn" button
2. **Google OAuth** — "Login/Registration with Google" button
3. **Corporate Login** — "For Corporate Login" link (href="#"); specific flow TBD

> No username/password fields. All authentication is social or corporate OAuth.

## Validation

- No client-side form validation applicable (no text input fields).
- reCAPTCHA (Google) is embedded via iframe for bot protection.
- Page displays: "BlueCallom is using Artificial Intelligence"

## Error States

- Not directly observable on the login page itself (OAuth errors would surface after OAuth redirect).
- No inline error message containers observed in the snapshot.

## Redirect Behavior

- **Unauthenticated:** Stays on `/login`, shows login card.
- **Already authenticated:** Navigating to `/login` immediately redirects to `/home`.
- **After successful OAuth login:** Redirects to `/home` (confirmed by session behavior — see `01-auth-flow.md`).

## Page Layout

The login page is split into two panels:

**Left panel (marketing):**
- Heading: "Enterprise AI Workflow Solutions"
- Description paragraph about cross-functional AI solutions
- Bullet list of capabilities (innovation, compliance, order processing)
- 4-step onboarding overview:
  1. Register with social login
  2. Complete your profile
  3. Select an agent or solution
  4. Invite your Team and Partners

**Right panel (login card):**
- BlueCallom logo
- LinkedIn OAuth button
- Google OAuth button
- "For Corporate Login" link
- Legal disclaimer (Terms of Service + Privacy Policy)
- "BlueCallom is using Artificial Intelligence" notice
- reCAPTCHA (iframe, bottom right of viewport)

## Screenshots

- `screenshots/01-login-page.png` — Login page (unauthenticated state)
