# Test Cases: Email/Password Sign-In

## Test Case 1: TC-001 - Successful Sign-In with Valid Email and Password

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com" in the email/username field
3. Enter valid password: "SecurePass123!" in the password field
4. Click the "Authenticate →" button

**Expected Result:**
- System validates credentials successfully
- User is redirected to /dashboard
- Welcome toast notification displays: "Welcome back, {UserName}!"
- JWT tokens are issued and stored correctly

---

## Test Case 2: TC-002 - Successful Sign-In with Valid Username and Password

**Steps:**
1. Navigate to /signin page
2. Enter valid username: "johndoe" in the email/username field
3. Enter valid password: "SecurePass123!" in the password field
4. Click the "Authenticate →" button

**Expected Result:**
- System validates credentials successfully
- User is redirected to /dashboard
- Welcome toast notification displays: "Welcome back, {UserName}!"

---

## Test Case 3: TC-003 - Email Field Required Validation

**Steps:**
1. Navigate to /signin page
2. Leave email/username field empty
3. Enter valid password: "SecurePass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Email or username is required"
- Email/username field border turns red
- Form does not submit
- Focus moves to email/username field

---

## Test Case 4: TC-004 - Password Field Required Validation

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com"
3. Leave password field empty
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Password is required"
- Password field border turns red
- Form does not submit
- Focus moves to password field

---

## Test Case 5: TC-005 - Invalid Email Format Validation

**Steps:**
1. Navigate to /signin page
2. Enter invalid email: "userexample.com" (missing @)
3. Enter valid password: "SecurePass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Please enter a valid email address"
- Email field border turns red
- Form does not submit

---

## Test Case 6: TC-006 - Invalid Email Format (Missing Domain)

**Steps:**
1. Navigate to /signin page
2. Enter invalid email: "user@"
3. Enter valid password: "SecurePass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Please enter a valid email address"
- Form does not submit

---

## Test Case 7: TC-007 - Invalid Email Format (Missing TLD)

**Steps:**
1. Navigate to /signin page
2. Enter invalid email: "user@domain"
3. Enter valid password: "SecurePass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Please enter a valid email address"
- Form does not submit

---

## Test Case 8: TC-008 - Invalid Username Format (Too Short)

**Steps:**
1. Navigate to /signin page
2. Enter invalid username: "jo" (2 characters)
3. Enter valid password: "SecurePass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Please enter a valid username (3-50 characters, letters, numbers, underscore, hyphen)"
- Form does not submit

---

## Test Case 9: TC-009 - Invalid Username Format (Special Characters)

**Steps:**
1. Navigate to /signin page
2. Enter invalid username: "__john" (starts with special char)
3. Enter valid password: "SecurePass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Please enter a valid username (3-50 characters, letters, numbers, underscore, hyphen)"
- Form does not submit

---

## Test Case 10: TC-010 - Email with Spaces Validation

**Steps:**
1. Navigate to /signin page
2. Enter email with spaces: "user @example.com"
3. Enter valid password: "SecurePass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Email/username must not contain spaces"
- Form does not submit

---

## Test Case 11: TC-011 - Auto-Trim Leading/Trailing Whitespace

**Steps:**
1. Navigate to /signin page
2. Enter email with leading/trailing spaces: "  user@example.com  "
3. Enter valid password: "SecurePass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- System auto-trims whitespace before submission
- Form submits successfully with trimmed email
- User is redirected to dashboard

---

## Test Case 12: TC-012 - Case Insensitive Email Login

**Steps:**
1. Navigate to /signin page
2. Enter email with mixed case: "USER@EXAMPLE.COM"
3. Enter valid password: "SecurePass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- System converts email to lowercase before lookup
- Authentication succeeds if credentials match
- User is redirected to dashboard

---

## Test Case 13: TC-013 - Password Too Short Validation

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com"
3. Enter short password: "Pass1" (5 characters)
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Password must be at least 8 characters"
- Password field border turns red
- Form does not submit

---

## Test Case 14: TC-014 - Password Missing Uppercase Letter

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com"
3. Enter password without uppercase: "password123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Password must contain at least one uppercase letter"
- Form does not submit

---

## Test Case 15: TC-015 - Password Missing Lowercase Letter

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com"
3. Enter password without lowercase: "PASSWORD123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Password must contain at least one lowercase letter"
- Form does not submit

---

## Test Case 16: TC-016 - Password Missing Number

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com"
3. Enter password without number: "Password!!!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Password must contain at least one number"
- Form does not submit

---

## Test Case 17: TC-017 - Password Missing Special Character

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com"
3. Enter password without special char: "Password123"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Password must contain at least one special character"
- Form does not submit

---

## Test Case 18: TC-018 - Show/Hide Password Toggle

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com"
3. Enter password: "SecurePass123!"
4. Click the eye icon (show/hide toggle) in password field

**Expected Result:**
- Password text becomes visible (plain text)
- Eye icon changes to eye-slash icon
- Clicking again hides password (shows dots/asterisks)

---

## Test Case 19: TC-019 - Invalid Credentials Error

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com"
3. Enter wrong password: "WrongPass123!"
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Invalid email or password. Please try again."
- Both fields highlighted in red
- Button re-enabled for retry
- Failed attempt counter incremented

---

## Test Case 20: TC-020 - Account Locked After 5 Failed Attempts

**Steps:**
1. Navigate to /signin page
2. Enter valid email but wrong password 5 times consecutively
3. Attempt 6th login with correct credentials

**Expected Result:**
- After 5th failure: Error displays "Too many failed attempts. Please try again after {X} minutes."
- Button disabled during lockout period
- Email notification sent to account holder
- 6th attempt blocked even with correct password

---

## Test Case 21: TC-021 - Network Error Handling

**Steps:**
1. Navigate to /signin page
2. Enter valid email and password
3. Disconnect internet
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Unable to connect. Please check your internet connection and try again."
- Button re-enabled for retry
- Form fields retain values

---

## Test Case 22: TC-022 - Server Error Handling (500)

**Steps:**
1. Navigate to /signin page
2. Enter valid email and password
3. Simulate server 500 error
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Something went wrong. Please try again later."
- Button re-enabled for retry
- Error logged to monitoring system

---

## Test Case 23: TC-023 - Forgot Password Link Navigation

**Steps:**
1. Navigate to /signin page
2. Click "Forgot Password?" link

**Expected Result:**
- User is redirected to /forgot-password page
- No form validation triggered
- Current form state preserved

---

## Test Case 24: TC-024 - Register Link Navigation

**Steps:**
1. Navigate to /signin page
2. Click "Register" link in footer

**Expected Result:**
- User is redirected to /signup or /register page
- No form validation triggered

---

## Test Case 25: TC-025 - Enter Key Submits Form

**Steps:**
1. Navigate to /signin page
2. Enter valid email: "user@example.com"
3. Enter valid password: "SecurePass123!"
4. Press Enter key while focus is in password field

**Expected Result:**
- Form submits as if "Authenticate" button was clicked
- User is redirected to dashboard on success

---

## Test Case 26: TC-026 - Tab Order Navigation

**Steps:**
1. Navigate to /signin page
2. Press Tab key repeatedly

**Expected Result:**
- Focus moves in order: Email field → Password field → Forgot Password link → Authenticate button → Register link
- Each focused element has visible focus indicator

---

## Test Case 27: TC-027 - Loading State During Authentication

**Steps:**
1. Navigate to /signin page
2. Enter valid email and password
3. Click the "Authenticate →" button

**Expected Result:**
- Button shows loading spinner
- Button text changes to "Signing in..." or spinner only
- Button is disabled (no double-submit)
- Arrow icon hidden during loading

---

## Test Case 28: TC-028 - Authenticated User Redirected from Sign-In

**Steps:**
1. User is already logged in (has valid session)
2. Navigate to /signin page

**Expected Result:**
- User is automatically redirected to /dashboard
- Sign-in page does not display

---

## Test Case 29: TC-029 - Unauthenticated User Redirected to Sign-In

**Steps:**
1. Ensure user is not logged in (no valid session)
2. Navigate to protected route: /dashboard

**Expected Result:**
- User is redirected to /signin page
- Original intended URL may be preserved for post-login redirect

---

## Test Case 30: TC-030 - Email Length Validation (Max 254 chars)

**Steps:**
1. Navigate to /signin page
2. Enter email exceeding 254 characters
3. Enter valid password
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Email must not exceed 254 characters"
- Form does not submit

---

## Test Case 31: TC-031 - Username Length Validation (Max 50 chars)

**Steps:**
1. Navigate to /signin page
2. Enter username exceeding 50 characters
3. Enter valid password
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Username must not exceed 50 characters"
- Form does not submit

---

## Test Case 32: TC-032 - Password Too Long Validation (Max 128 chars)

**Steps:**
1. Navigate to /signin page
2. Enter valid email
3. Enter password exceeding 128 characters
4. Click the "Authenticate →" button

**Expected Result:**
- Error message displays: "Password must not exceed 128 characters"
- Form does not submit

---

## Test Case 33: TC-033 - Whitespace-Only Email Validation

**Steps:**
1. Navigate to /signin page
2. Enter only spaces in email field: "   "
3. Enter valid password
4. Click the "Authenticate →" button

**Expected Result:**
- After trim, treated as empty
- Error message displays: "Email or username is required"
- Form does not submit

---

## Test Case 34: TC-034 - Whitespace-Only Password Validation

**Steps:**
1. Navigate to /signin page
2. Enter valid email
3. Enter only spaces in password field: "   "
4. Click the "Authenticate →" button

**Expected Result:**
- After trim, treated as empty
- Error message displays: "Password is required"
- Form does not submit

---

## Test Case 35: TC-035 - Error Clears on Retype

**Steps:**
1. Navigate to /signin page
2. Enter invalid email: "invalid"
3. Click submit to trigger error
4. Start typing again in email field

**Expected Result:**
- Error message clears when user starts retyping
- Field border returns to normal state

---

## Test Case 36: TC-036 - Two-Panel Layout Rendering

**Steps:**
1. Navigate to /signin page on desktop (1440px width)

**Expected Result:**
- Left panel displays marketing/branding content
- Right panel displays sign-in form
- Form card centered vertically and horizontally
- All text styles match Figma specifications

---

## Test Case 37: TC-037 - Responsive Layout on Mobile

**Steps:**
1. Navigate to /signin page on mobile viewport (375px width)

**Expected Result:**
- Layout adapts to mobile screen
- All elements remain accessible
- Touch targets are ≥ 44x44px
- No horizontal scrolling

---

## Test Case 38: TC-038 - Cross-Browser Compatibility (Chrome)

**Steps:**
1. Open /signin page in Chrome (latest version)
2. Complete sign-in flow with valid credentials

**Expected Result:**
- All functionality works correctly
- No console errors
- Styling renders correctly

---

## Test Case 39: TC-039 - Cross-Browser Compatibility (Firefox)

**Steps:**
1. Open /signin page in Firefox (latest version)
2. Complete sign-in flow with valid credentials

**Expected Result:**
- All functionality works correctly
- No console errors
- Styling renders correctly

---

## Test Case 40: TC-040 - Cross-Browser Compatibility (Safari)

**Steps:**
1. Open /signin page in Safari (latest version)
2. Complete sign-in flow with valid credentials

**Expected Result:**
- All functionality works correctly
- No console errors
- Styling renders correctly

---

## Test Case 41: TC-041 - WCAG Color Contrast Compliance

**Steps:**
1. Navigate to /signin page
2. Use color contrast analyzer tool
3. Check all text elements against background

**Expected Result:**
- All text has contrast ratio ≥ 4.5:1
- Meets WCAG 2.1 Level AA requirements

---

## Test Case 42: TC-042 - Screen Reader Compatibility

**Steps:**
1. Enable screen reader (NVDA/VoiceOver/JAWS)
2. Navigate through sign-in form using keyboard
3. Submit form with invalid data

**Expected Result:**
- Form fields announced with labels
- Error messages announced when they appear
- Button states (loading, disabled) announced

---

## Test Case 43: TC-043 - Keyboard Navigation Complete

**Steps:**
1. Navigate to /signin page
2. Use only keyboard (Tab, Enter, Escape)
3. Complete sign-in flow

**Expected Result:**
- All interactive elements accessible via keyboard
- Tab order is logical
- Enter key submits form
- Focus indicators are visible

---

## Test Case 44: TC-044 - Rate Limiting (10 req/min per IP)

**Steps:**
1. Use API testing tool (Postman/curl)
2. Send 11 sign-in requests within 1 minute from same IP

**Expected Result:**
- First 10 requests processed normally
- 11th request returns 429 status code
- Error message: "Too many requests. Please try again later."

---

## Test Case 45: TC-045 - JWT Token Issued on Success

**Steps:**
1. Navigate to /signin page
2. Enter valid credentials
3. Click "Authenticate →"
4. Inspect network response

**Expected Result:**
- Response contains accessToken (JWT format)
- Response contains refreshToken
- Token expiry set correctly (30 minutes for access token)

---

## Test Case 46: TC-046 - Refresh Token Stored in HttpOnly Cookie

**Steps:**
1. Navigate to /signin page
2. Enter valid credentials
3. Complete authentication
4. Inspect browser cookies

**Expected Result:**
- Refresh token stored in cookie
- Cookie has HttpOnly flag set
- Cookie has Secure flag set
- Cookie has SameSite=Strict attribute

---

## Test Case 47: TC-047 - Access Token Stored in Memory

**Steps:**
1. Navigate to /signin page
2. Enter valid credentials
3. Complete authentication
4. Check localStorage and sessionStorage

**Expected Result:**
- Access token NOT in localStorage
- Access token NOT in sessionStorage
- Access token stored in JavaScript memory only

---

## Test Case 48: TC-048 - HTTPS/TLS Enforcement

**Steps:**
1. Attempt to access /signin page via HTTP (not HTTPS)

**Expected Result:**
- Connection redirected to HTTPS
- Or connection refused with security error

---

## Test Case 49: TC-049 - CSRF Protection on Form Submit

**Steps:**
1. Navigate to /signin page
2. Inspect form submission headers
3. Verify CSRF token presence

**Expected Result:**
- CSRF token included in request headers or form data
- Request without CSRF token is rejected

---

## Test Case 50: TC-050 - XSS Protection Headers

**Steps:**
1. Navigate to /signin page
2. Inspect response headers

**Expected Result:**
- Content-Security-Policy header present
- X-Content-Type-Options: nosniff
- X-Frame-Options: DENY or SAMEORIGIN
- X-XSS-Protection: 1; mode=block

---

## Test Case 51: TC-051 - Multiple Rapid Submissions Debounced

**Steps:**
1. Navigate to /signin page
2. Enter valid credentials
3. Click "Authenticate →" button multiple times rapidly

**Expected Result:**
- Only one API request sent
- Subsequent clicks ignored during loading state
- No duplicate submissions

---

## Test Case 52: TC-052 - Session Already Active Detection

**Steps:**
1. User already logged in on current browser
2. Navigate to /signin page

**Expected Result:**
- User redirected to dashboard, OR
- Message displays: "You are already signed in."
- Option to "Sign out and sign in again" or "Go to Dashboard"

---

## Test Case 53: TC-053 - Valid Email Formats Accepted

**Steps:**
1. Navigate to /signin page
2. Test with various valid email formats:
   - user@example.com
   - john.doe@company.co.uk
   - user+tag@example.com
3. Enter valid password for each
4. Submit form

**Expected Result:**
- All valid email formats accepted
- Authentication proceeds normally

---

## Test Case 54: TC-054 - Account Suspended Error Handling

**Steps:**
1. Navigate to /signin page
2. Enter credentials for suspended account
3. Click "Authenticate →"

**Expected Result:**
- Error message displays: "Your account has been suspended. Please contact support at support@testable.io"
- Support email is clickable (mailto: link)

---

## Test Case 55: TC-055 - Unverified Email Error Handling

**Steps:**
1. Navigate to /signin page
2. Enter credentials for account with unverified email
3. Click "Authenticate →"

**Expected Result:**
- Error message displays: "Please verify your email address before signing in. Check your inbox for the verification link."
- Option to "Resend verification email" displayed

---

## Test Case 56: TC-056 - Concurrent Session Limit (5 Sessions)

**Steps:**
1. User already has 5 active sessions on different devices
2. Attempt to sign in from 6th device with valid credentials

**Expected Result:**
- Error message displays: "You have reached the maximum number of active sessions (5). Please sign out from another device or contact support."
- Option to "View active sessions" provided

---

## Test Case 57: TC-057 - Paste Email into Username Field

**Steps:**
1. Navigate to /signin page
2. Copy email: "user@example.com"
3. Paste into email/username field
4. Enter valid password
5. Submit form

**Expected Result:**
- System detects @ symbol
- Validates as email format
- Authentication proceeds normally

---

## Test Case 58: TC-058 - Password Manager Auto-Fill

**Steps:**
1. Navigate to /signin page
2. Use password manager to auto-fill credentials
3. Submit form (may auto-submit)

**Expected Result:**
- Credentials populated correctly
- Form submits successfully
- No validation errors from auto-fill

---

## Test Case 59: TC-059 - Copy-Paste with Leading/Trailing Spaces

**Steps:**
1. Navigate to /signin page
2. Copy email with spaces: "  user@example.com  "
3. Paste into email field
4. Enter valid password
5. Submit form

**Expected Result:**
- System auto-trims whitespace
- Authentication proceeds with trimmed email
- Login succeeds

---

## Test Case 60: TC-060 - Right-Click Paste in Password Field

**Steps:**
1. Navigate to /signin page
2. Enter valid email
3. Right-click in password field
4. Select Paste from context menu

**Expected Result:**
- Paste operation allowed
- Password field accepts pasted value
- No blocking of paste functionality
