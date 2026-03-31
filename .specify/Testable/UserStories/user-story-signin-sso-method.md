# Testable Landing Page — Sign In with SSO

**Figma File**: 2 Compliance
**Node ID**: 895:14567
**Generated**: March 26, 2026

---

## Screen: Sign In — SSO Authentication

As an enterprise user with organizational SSO credentials,
I want to sign in using my company's SSO provider,
so that I can securely access my workspace using my existing corporate identity.

### 1. Acceptance Criteria

1. The sign-in page displays a Google OAuth button with Google icon and "Google" label
2. The sign-in page displays a Microsoft OAuth button with Microsoft icon and "Microsoft" label
3. The sign-in page displays a "Sign in with SSO" button with dropdown indicator (chevron)
4. Clicking the "Sign in with SSO" button expands a dropdown menu showing available SSO providers
5. The SSO dropdown displays provider options: Okta, Azure AD, OneLogin, and Auth0
6. Each SSO provider option displays the provider name in the dropdown list
7. Selecting an SSO provider initiates authentication redirect to that provider's login page
8. A divider with "or" text separates SSO authentication from email/password section
9. The SSO dropdown closes when user clicks outside the dropdown or presses Escape key
10. The SSO button displays loading state during redirect initiation

### 2. Positive Validations

1. Clicking "Sign in with SSO" button expands dropdown menu smoothly
2. Selecting Okta from dropdown redirects to Okta login page for authentication
3. Selecting Azure AD from dropdown redirects to Microsoft Azure AD login page
4. Selecting OneLogin from dropdown redirects to OneLogin authentication page
5. Selecting Auth0 from dropdown redirects to Auth0 authentication page
6. Successful SSO authentication redirects user to workspace dashboard
7. Welcome message displays after successful SSO login
8. SSO dropdown closes when user clicks outside the dropdown area
9. Pressing Escape key closes the SSO dropdown without initiating authentication
10. User can switch between different SSO providers by reopening dropdown
11. SSO session is created with appropriate user permissions from identity provider

### 3. Negative Validations

1. SSO provider unavailable displays error message indicating provider is temporarily unavailable
2. User cancels SSO authentication displays no error and returns to sign-in page
3. SSO authentication failure displays generic error message "Authentication failed. Please try again."
4. Network error during SSO redirect displays error "Unable to connect. Please check your internet connection."
5. SSO session timeout displays error "Session expired. Please sign in again."
6. User account not provisioned for SSO displays error "Your account is not configured for SSO. Please contact your administrator."
7. SSO email domain does not match organization displays error "Email domain does not match your organization's SSO domain."
8. Popup blocker prevents SSO window displays message with alternative sign-in option
9. Invalid SSO response from provider displays error "Unable to process authentication response."
10. Multiple rapid SSO attempts triggers rate limiting message "Too many attempts. Please wait before trying again."

### 4. Boundary Value Analysis

1. SSO dropdown supports minimum 1 and maximum 10 configured providers
2. SSO redirect timeout is set to 30 seconds before displaying timeout error
3. SSO session token expiry matches organizational policy (typically 8-12 hours)
4. SAML assertion must be received within 5 minutes of issuance
5. Maximum concurrent SSO sessions allowed per user is 5
6. SSO authentication must complete within 60 seconds or timeout
7. Dropdown menu maximum height is 300px with scroll for additional providers
8. SSO provider metadata refresh occurs every 24 hours for certificate updates

### 5. UI/UX Validations

1. Sign-in form is displayed as a white card with 16px border radius on right panel
2. "Welcome Back," heading is displayed in 32px Inter Semi-Bold font
3. Subtext is displayed in 16px Inter Regular font with gray color (#A3A3A3)
4. Google and Microsoft buttons are displayed side-by-side in two-column layout
5. "Sign in with SSO" button spans full width of form container
6. SSO button displays chevron icon that rotates 180 degrees when dropdown expands
7. Dropdown menu appears directly below SSO button with consistent spacing
8. Dropdown has white background with subtle shadow for depth
9. Each SSO provider option has hover state with light gray background
10. Divider with "or" text is centered with horizontal lines on both sides
11. Loading state displays spinner on SSO button during provider redirect
12. Error messages display in toast notification or inline below relevant field

### 6. Accessibility Validations

1. "Sign in with SSO" button has aria-label "Sign in with Single Sign-On"
2. SSO button has aria-expanded attribute indicating dropdown state (true/false)
3. SSO button has aria-haspopup attribute set to "menu"
4. Dropdown menu has role="menu" for screen reader announcement
5. Each SSO provider option has role="menuitem" with provider name announced
6. Keyboard Tab navigation moves focus through all interactive elements in logical order
7. Arrow Down/Up keys navigate between SSO provider options in dropdown
8. Enter key selects focused SSO provider and initiates authentication
9. Escape key closes dropdown and returns focus to SSO button
10. Focus indicator displays visible outline (minimum 2px) on all focused elements
11. Color contrast ratio meets WCAG 2.1 Level AA (4.5:1 for text, 3:1 for UI components)
12. Screen readers announce "Sign in with SSO button, expands to show provider options"
13. Screen readers announce each provider as selectable menu item
14. Dropdown open/close state changes are announced via aria-live region
15. All interactive elements have minimum touch target of 44x44px
16. Focus trap is implemented within dropdown when open to prevent focus loss

### 7. Definition of Done

1. All Positive, Negative, Boundary, UI/UX, and Accessibility validations listed above have been tested and pass across all supported browsers: Chrome, Firefox, Safari, and Edge
2. SSO authentication works end-to-end with all four configured providers (Okta, Azure AD, OneLogin, Auth0)
3. SSO dropdown expands and collapses correctly with proper animation
4. Keyboard navigation works correctly for dropdown and provider selection
5. Error handling displays appropriate messages for all failure scenarios
6. Successful SSO authentication redirects to dashboard with welcome message
7. Session tokens are issued correctly with appropriate expiry
8. Multiple concurrent SSO sessions are supported per user
9. Security review completed with zero critical or high vulnerabilities in SSO flow
10. SSO audit logging captures all authentication attempts (success and failure)
11. WCAG 2.1 Level AA compliance verified via automated and manual testing
12. QA testing completed with no open critical or high severity bugs
13. Product Owner has reviewed and accepted the SSO authentication feature

---

*Generated from Figma: https://www.figma.com/design/BXMaoyXQzDwRZ2yaUa5iNP/2-Compliance?node-id=895:14567*
*Template: .specify/Testable/Template/UserStoryCreation-1*
