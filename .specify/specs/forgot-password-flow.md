# Feature Specification: Forgot Password Flow

**Feature Branch**: `887-forgot-password-flow`
**Created**: March 26, 2026
**Status**: Draft
**Input**: Figma Design - Forgot Password Flow (Node: 887:3053)

---

## User Story

**As a** registered user who has forgotten my password,
**I want to** reset my password using my email address,
**So that** I can regain access to my account securely.

**Story Type**: `AUTH`
**Layout Type**: `SINGLE-STEP`

---

## Page Layout

Upon launching the `/forgot-password` page, the user is directed to the Forgot Password page, which consists of the following:

- **Left Panel**: Branding/Marketing Panel (597px width)
- **Right Panel**: Form Panel (843px width, centered with 150px padding)

---

### Left Panel (Branding/Marketing)

1. Shall display the product logo (Container with shield icon) at the top
2. Shall display the tagline "Ship with confidence." in bold (Title-2, 64px, Bold, #171717)
3. Shall display the subtext: "AI-powered testing that understands your codebase and validates every change against your user stories." (Label-1, 16px, Regular, #A3A3A3)
4. Shall display key metrics/stats with labels:
   - "14,864" - TESTS RUN TODAY
   - "99.2%" - PASS RATE
   - "1.2s" - AVG SPEED
5. Shall display a product preview or terminal/code snippet mockup at bottom (code preview panel with syntax highlighting)
6. Panel shall be non-scrollable and fully visible on load (597px x 900px fixed)

### Right Panel (Forgot Password Form)

1. Shall display a "Back" link with ArrowRight icon (rotated 180°) at top left
2. Shall display the heading "Forgot Password?" in bold (H4, 32px, Semi Bold, #0A0A0A)
3. Shall display the subtext: "Enter your email to reset your password. If it's correct, we'll send you an email with OTP" (Label-1, 16px, Regular, #A3A3A3)
4. Shall display an email input field with placeholder "Email" (background #F5F5F5, border-radius 16px)
5. Shall display a full-width primary "Send Email →" button (background #0A0A0A, text white, border-radius 16px)
6. Shall display inline validation messages on the email field
7. Shall display button loading/disabled state during submission

---

## Business Logic

1. System MUST validate email format before sending OTP
2. System MUST NOT reveal whether an email exists in the database (security best practice)
3. System MUST generate a time-limited OTP (One-Time Password) for password reset
4. System MUST invalidate any existing password reset tokens when a new one is requested
5. System MUST rate-limit password reset requests per email address
6. System MUST log all password reset requests for security monitoring

## Data Rules

- Email field MUST accept valid email addresses only (max 254 characters)
- OTP MUST be stored as a hashed value in the database
- OTP MUST have an expiry timestamp (e.g., 10 minutes from generation)
- Password reset tokens MUST be single-use only
- All password reset events MUST be audited with timestamp and IP address

---

## Positive Validations — Email Field

### Field Requirements

**FR-001**: Field MUST accept valid email addresses only

### Validation Rules

1. **Required Field**
   - Empty submission → Error: "Email is required"
   - Triggered on: Form submit, field blur

2. **Format Validation**
   - Must contain exactly one `@` symbol
   - Must have valid local part (before @): 1-64 characters
   - Must have valid domain part (after @): 1-255 characters
   - Domain MUST contain at least one `.` character
   - Domain MUST have valid TLD (2+ characters)
   - Invalid format → Error: "Please enter a valid email address"
   - Examples valid: `user@example.com`, `john.doe@company.co.uk`
   - Examples invalid: `@example.com`, `user@`, `user@domain`, `userdomain.com`

3. **Length Validation**
   - Email: Maximum 254 characters total
   - Too long → Error: "Email must not exceed 254 characters"

4. **Whitespace Handling**
   - No leading/trailing whitespace (auto-trimmed before validation)
   - No spaces within email
   - Spaces within → Error: "Email must not contain spaces"

5. **Case Handling**
   - Email: Case-insensitive (converted to lowercase before lookup)
   - `User@Example.com` = `user@example.com`

### Real-Time Feedback

- Validation triggered on field blur (when user leaves the field)
- Error message displayed inline below field in red (#DC3545 or similar)
- Field border turns red on error
- Error cleared when user starts typing again
- Valid state: Green checkmark (optional), border returns to normal

---

## Negative Validations

1. **Empty Email**
   - Scenario: User submits form without entering email
   - Display: "Email is required"
   - Focus moves to email field

2. **Invalid Email Format**
   - Scenario: User enters invalid email format (e.g., `user@`, `@example.com`, `userdomain.com`)
   - Display: "Please enter a valid email address"
   - Field highlighted in red

3. **Whitespace-Only Input**
   - Scenario: User enters only spaces in email field
   - After trim: Treated as empty
   - Display: "Email is required"

4. **Non-Existent Email**
   - Scenario: User enters email that doesn't exist in database
   - Display: "If an account exists with this email, we've sent password reset instructions."
   - Generic message (doesn't reveal if email exists)

5. **Rate Limit Exceeded**
   - Scenario: User requests multiple password reset emails within short period
   - Display: "Too many requests. Please wait {X} minutes before trying again."
   - Button disabled during cooldown period

6. **Network Error**
   - Scenario: No internet connection, API unreachable
   - Display: "Unable to connect. Please check your internet connection and try again."
   - Button re-enabled for retry

7. **Server Error**
   - Scenario: 500 Internal Server Error from API
   - Display: "Something went wrong. Please try again later."
   - Button re-enabled for retry

---

## Button Behaviour

### Send Email Button

**FR-002**: Send Email button MUST validate email and trigger password reset flow

#### Initial State
- Button enabled when email field has valid value (optional enhancement)
- Button always enabled (validate on click) — **Recommended**
- Background: `#0A0A0A` (black)
- Text: "Send Email" with arrow icon
- Cursor: pointer on hover

#### Loading State
- Triggered on: Form submit (after validation passes)
- Button disabled (no double-submit)
- Text replaced with spinner or "Sending..."
- Spinner: 16-20px, white color, rotating
- Arrow icon hidden during loading
- Minimum display time: 500ms (prevents flash)

#### Success State
- Triggered on: 200 OK response from API
- Display: "If an account exists with this email, we've sent password reset instructions."
- Email input field cleared and disabled
- Button hidden or replaced with "Back to Sign In" link
- Success message displayed above form

#### Error State
- Triggered on: 4XX / 5XX response from API
- Button re-enabled for retry
- Loading spinner replaced with original text
- Error message displayed above form or inline
- Email field retains value (user doesn't retype)

#### Validation Flow
```
User clicks "Send Email"
  ↓
Client-side validation (email format)
  ↓
If invalid: Display errors, stop
  ↓
If valid: Show loading state, disable button
  ↓
POST /api/v1/auth/forgot-password
  ↓
On 200 OK: Display success message
On 4XX/5XX: Display error, re-enable button
```

### Back Link

- Location: Top left of form card, left-aligned
- Text: "Back" with left arrow icon (ArrowRight rotated 180°)
- Style: Link color (#0A0A0A or similar), underlined on hover
- Click action: Navigate to `/signin`
- No form validation triggered
- No state change on current page

---

## Definition of Done

### Functional Validations

1. ✅ Email field accepts only valid email addresses
2. ✅ Email format validated client-side before submission
3. ✅ All inline validation messages display correctly on error
4. ✅ Send Email button shows loading state during API call
5. ✅ Success message displayed after email sent (generic, doesn't reveal if email exists)
6. ✅ Back link navigates to `/signin` page
7. ✅ Rate limiting enforced (e.g., max 3 requests per hour per email)
8. ✅ API returns correct response structure for all scenarios
9. ✅ Password reset token generated and emailed correctly
10. ✅ Existing tokens invalidated when new one is requested

### UI / UX Validations

1. ✅ Two-panel layout renders correctly on desktop (1440px+)
2. ✅ Form card centered vertically and horizontally in right panel
3. ✅ All text styles match Figma (font family, size, weight, color, line-height)
4. ✅ Input field has correct placeholder text and styling (#F5F5F5 background)
5. ✅ Input field focus states implemented (border highlight)
6. ✅ Error states display red border and inline error message
7. ✅ Button hover states implemented (slight lighten/darken)
8. ✅ Loading spinner centered in button during API call
9. ✅ Enter key submits form when focus in email field
10. ✅ Error messages clear when user starts retyping
11. ✅ Form auto-trims whitespace from inputs before submission
12. ✅ Back link positioned correctly at top left

### Performance & Reliability

1. ✅ Password reset API responds within 500ms (p95) under normal load
2. ✅ System handles 1000 concurrent password reset requests
3. ✅ Page loads and becomes interactive within 2 seconds (3G network)
4. ✅ No layout shift (CLS < 0.1) during page load
5. ✅ Graceful degradation if JavaScript disabled (basic form submission)

### Security Validations

1. ✅ All password reset traffic over HTTPS/TLS 1.3
2. ✅ Password reset tokens are cryptographically secure (minimum 128-bit entropy)
3. ✅ Tokens expire after 10 minutes (configurable)
4. ✅ Tokens are single-use only (invalidated after successful password reset)
5. ✅ Rate limiting applied on API endpoint (e.g., 3 requests per hour per email)
6. ✅ Generic success/error messages (don't reveal if email exists)
7. ✅ All password reset attempts logged (without exposing sensitive data)
8. ✅ SQL injection prevention (parameterized queries)
9. ✅ Timing attack prevention (constant-time comparison for tokens)
10. ✅ Email sent contains secure, expiring reset link with OTP

### Compatibility & Accessibility

1. ✅ Responsive layout on desktop (1440px+), tablet (768px-1024px), mobile (375px-767px)
2. ✅ Cross-browser tested: Chrome (latest 2), Firefox (latest 2), Safari (latest 2), Edge (latest 2)
3. ✅ No console errors in browser DevTools
4. ✅ WCAG 2.1 Level AA compliance:
   - ✅ Color contrast ratio ≥ 4.5:1 for all text
   - ✅ All interactive elements keyboard accessible
   - ✅ Focus indicators visible (2px outline minimum)
   - ✅ Email field has associated `<label>` element (visually hidden if needed)
   - ✅ Error messages associated with field via `aria-describedby`
   - ✅ Invalid field marked with `aria-invalid="true"`
   - ✅ Live regions for dynamic error announcements
5. ✅ Screen reader tested (NVDA, VoiceOver, JAWS):
   - ✅ Email field announced with label
   - ✅ Errors announced when they appear
   - ✅ Button states (loading, disabled) announced
6. ✅ Keyboard navigation:
   - ✅ Tab through email field, back link, and button in logical order
   - ✅ Enter key submits form
   - ✅ Back link accessible via keyboard
7. ✅ Touch targets ≥ 44x44px on mobile devices

### Sign-off

1. ✅ Unit tests written and passing (Jest, Vitest, etc.)
2. ✅ Integration tests written and passing (API testing)
3. ✅ E2E tests written and passing (Cypress, Playwright)
4. ✅ Security review completed (OWASP Top 10 checked)
5. ✅ Code review completed and approved
6. ✅ QA testing completed with no open critical/high bugs
7. ✅ Product Owner has reviewed and accepted the feature
8. ✅ Documentation updated (API docs, user guides)

---

## Edge Cases

1. **Email Already Verified but User Forgot**
   - Scenario: User has verified account but forgot password
   - Handling: Normal password reset flow proceeds

2. **Email Not Verified / Account Not Created**
   - Scenario: User enters email that was never registered or not verified
   - Handling: Display generic success message (doesn't reveal account status)

3. **Network Failure Mid-Request**
   - Scenario: User clicks Send Email, network disconnects during API call
   - Handling: Timeout after 30 seconds, display: "Unable to connect. Please check your internet connection.", re-enable button

4. **Multiple Rapid Form Submissions**
   - Scenario: User clicks Send Email button multiple times rapidly
   - Handling: Debounce button clicks (300ms); ignore duplicate requests; loading state prevents visual double-click

5. **Browser Cookies Disabled**
   - Scenario: User has third-party or all cookies disabled
   - Handling: Password reset still works (token sent via email, not stored in cookie)

6. **OTP Link Tampered**
   - Scenario: User modifies reset link/OTP in email
   - Handling: Token validation fails; display: "This reset link is invalid. Please request a new password reset."

7. **Token Expires Mid-Flow**
   - Scenario: User clicks reset link after token expiry (10 minutes)
   - Handling: Display: "This reset link has expired. Please request a new password reset."

8. **Token Already Used**
   - Scenario: User tries to use same reset link twice
   - Handling: Display: "This reset link has already been used. Please request a new password reset."

9. **Copy-Paste with Leading/Trailing Spaces**
   - Scenario: User copy-pastes email with invisible spaces
   - Handling: Auto-trim whitespace before validation and submission

10. **Email Service Unavailable**
    - Scenario: SMTP/email service is down when trying to send reset email
    - Handling: Display: "Unable to send reset email. Please try again later." Log error for monitoring

11. **User Navigates Away After Success**
    - Scenario: User closes browser after seeing success message, before checking email
    - Handling: Token remains valid until expiry; user can use link from email later

12. **Autofill Conflict**
    - Scenario: Browser autofill populates incorrect email
    - Handling: Allow user to edit field before submit; validate on submit, not on input change

13. **Account Suspended/Disabled**
    - Scenario: User requests password reset for suspended account
    - Handling: Display generic success message; do not reveal account status

14. **Concurrent Reset Requests**
    - Scenario: User requests multiple password resets in quick succession
    - Handling: Invalidate previous tokens, generate new one; rate limit applies

15. **Time Zone / Clock Skew**
    - Scenario: User's device clock is significantly off
    - Handling: Use server timestamp for token expiry validation

---

## Functional Requirements

**FR-001**: System MUST accept only valid email addresses in the email field

**FR-002**: System MUST validate email format client-side before submitting to API

**FR-003**: System MUST send password reset request to `POST /api/v1/auth/forgot-password` endpoint

**FR-004**: System MUST generate a secure, time-limited OTP for password reset

**FR-005**: System MUST send password reset email with OTP link to user's email address

**FR-006**: System MUST display generic success message regardless of whether email exists

**FR-007**: System MUST implement rate limiting (max 3 requests per hour per email)

**FR-008**: System MUST invalidate existing password reset tokens when new one is requested

**FR-009**: System MUST log all password reset requests for security monitoring

**FR-010**: System MUST auto-trim whitespace from email before validation

**FR-011**: System MUST use case-insensitive email lookup

**FR-012**: System MUST provide "Back" link to navigate to `/signin` page

*Assumptions made:*

- **A-001**: User accounts are pre-created via registration flow
- **A-002**: Email verification is handled separately (not part of this flow)
- **A-003**: SMTP/email service is configured and available
- **A-004**: Backend API for password reset is implemented and available
- **A-005**: Password reset token expiry is configurable (default 10 minutes)
- **A-006**: Create New Password flow is implemented as a separate story

---

## Success Criteria

**SC-001**: Users can request password reset in under 5 seconds (from button click to success message)

**SC-002**: 95% of users successfully complete password reset request on first attempt (no validation errors)

**SC-003**: Password reset API maintains 99.9% uptime with <500ms response time (p95)

**SC-004**: Zero critical or high security vulnerabilities in password reset flow (per security audit)

**SC-005**: WCAG 2.1 Level AA compliance verified via automated (axe, Lighthouse) and manual testing

**SC-006**: Password reset emails delivered within 60 seconds (p95)

**SC-007**: Rate limiting prevents >99% of abuse attempts in penetration testing

**SC-008**: <1% of password reset requests result in support tickets (usability metric)
