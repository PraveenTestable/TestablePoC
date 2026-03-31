# Testable Landing Page — Authentication Flow

**Figma File**: 2 Compliance  
**Node ID**: 887:3053  
**Generated**: March 26, 2026

---

## Screen 1: Sign In

As a registered user with email credentials,  
I want to sign in using my email and password,  
so that I can securely access my workspace and continue my work.

### 1. Acceptance Criteria

1. The sign-in page displays a two-panel layout with branding on the left and form on the right
2. The left panel displays the product logo, tagline "Ship with confidence.", and key metrics (14,864 tests run today, 99.2% pass rate, 1.2s avg speed)
3. The right panel displays a white card container with "Welcome Back," heading and "Sign in to continue to your workspace" subtext
4. The form contains an email input field with placeholder text "Email"
5. The form contains a password input field with placeholder text "Password" and a show/hide eye icon
6. The form displays a "Forgot Password?" link positioned below the password field
7. The form displays an "Authenticate" button with full width and dark background (#0A0A0A)
8. The form displays SSO options including Google and Microsoft buttons with respective icons
9. The form displays a divider with "or" text separating SSO and email/password options
10. The form displays a "Sign in with SSO" button for enterprise authentication

### 2. Positive Validations

1. Email field accepts valid email addresses (user@example.com) and usernames (john_doe)
2. Password field accepts passwords meeting complexity requirements (8+ characters, uppercase, lowercase, number, special character)
3. Show/hide password toggle correctly switches between masked dots and plain text visibility
4. Authenticate button becomes clickable when both email and password fields contain values
5. Form submission triggers client-side validation before sending to API
6. Successful authentication redirects user to dashboard with welcome toast message
7. SSO buttons initiate OAuth flow when clicked
8. Forgot Password link navigates to password reset page without validation

### 3. Negative Validations

1. Empty email field displays error message "Email or username is required" on submit
2. Empty password field displays error message "Password is required" on submit
3. Invalid email format displays error message "Please enter a valid email address"
4. Invalid username format displays error message "Please enter a valid username (3-50 characters, letters, numbers, underscore, hyphen)"
5. Password less than 8 characters displays error message "Password must be at least 8 characters"
6. Password missing uppercase letter displays error message "Password must contain at least one uppercase letter"
7. Password missing lowercase letter displays error message "Password must contain at least one lowercase letter"
8. Password missing number displays error message "Password must contain at least one number"
9. Password missing special character displays error message "Password must contain at least one special character"
10. Invalid credentials display generic error message "Invalid email or password. Please try again."
11. Account locked after 5 failed attempts displays error message "Too many failed attempts. Please try again after {X} minutes."
12. Network error displays error message "Unable to connect. Please check your internet connection and try again."
13. Server error displays error message "Something went wrong. Please try again later."

### 4. Boundary Value Analysis

1. Email field accepts maximum 254 characters and rejects input exceeding this limit
2. Username field accepts minimum 3 characters and rejects input with fewer characters
3. Username field accepts maximum 50 characters and rejects input exceeding this limit
4. Password field accepts minimum 8 characters and rejects input with fewer characters
5. Password field accepts maximum 128 characters and rejects input exceeding this limit
6. Email field auto-trims leading and trailing whitespace before validation
7. Password field auto-trims leading and trailing whitespace before validation
8. Email field treats input as case-insensitive (User@Example.com equals user@example.com)
9. Username field treats input as case-insensitive for lookup purposes

### 5. UI/UX Validations

1. Two-panel layout renders correctly on desktop screens (1440px width and above)
2. Form card is centered vertically and horizontally in the right panel
3. All text styles match Figma specifications for font family, size, weight, color, and line-height
4. Input fields display correct placeholder text in light gray color (#A3A3A3)
5. Input fields have light gray background (#F5F5F5) with border-radius of 16px
6. Input field focus state displays border highlight to indicate active field
7. Error state displays red border (#DC3545) and inline error message below the field
8. Button hover state displays slight color change to indicate interactivity
9. Loading state displays centered spinner with "Signing in..." text and disabled button
10. Tab order follows logical sequence: Email, Password, Forgot Password link, Authenticate button, SSO buttons
11. Enter key submits form when focus is in email or password field
12. Error messages clear when user starts retyping in the field
13. SSO buttons are visually separated from email/password form with divider
14. Back navigation from Forgot Password returns to Sign In page

### 6. Accessibility Validations

1. All interactive elements are keyboard accessible via Tab key navigation
2. Email input field has associated label element with aria-label "Email or username"
3. Password input field has associated label element with aria-label "Password"
4. Invalid fields are marked with aria-invalid="true" attribute
5. Error messages are associated with fields via aria-describedby attribute
6. Dynamic error announcements are made via live regions for screen readers
7. Focus indicators are visible with minimum 2px outline on all interactive elements
8. Color contrast ratio meets WCAG 2.1 Level AA requirement of 4.5:1 for all text
9. Show/hide password toggle button has aria-label "Show password" or "Hide password" based on state
10. Authenticate button state changes (loading, disabled) are announced to screen readers
11. All touch targets meet minimum 44x44px size requirement on mobile devices
12. Screen readers announce form fields with their labels when focused

### 7. Definition of Done

1. All Positive, Negative, Boundary, UI/UX, and Accessibility validations listed above have been tested and pass across all supported browsers: Chrome, Firefox, Safari, and Edge
2. Email and password authentication works end-to-end with successful redirect to dashboard
3. All error states display appropriate messages and allow user recovery
4. Loading and disabled states prevent duplicate form submissions
5. Rate limiting is enforced at 5 failed attempts per 15 minutes per account
6. JWT tokens are issued correctly on successful authentication
7. Refresh token is stored in HttpOnly, Secure, SameSite=Strict cookie
8. Access token is stored in memory only, not in localStorage or sessionStorage
9. Security review completed with zero critical or high vulnerabilities
10. QA testing completed with no open critical or high severity bugs

---

## Screen 2: Forgot Password — Send Email

As a user who forgot my password,  
I want to request a password reset email,  
so that I can regain access to my account.

### 1. Acceptance Criteria

1. The Forgot Password page displays a Back link with arrow icon at the top left
2. The page displays "Forgot Password?" heading in bold (H4, 32px, Semi Bold)
3. The page displays subtext "Enter your email to reset your password. If it's correct, we'll send you an email with OTP"
4. The form contains an email input field with placeholder text "Email"
5. The form displays a "Send Email" button with full width and dark background
6. The Back link navigates to the Sign In page without triggering validation
7. The email field accepts valid email addresses only
8. The Send Email button triggers password reset flow on click

### 2. Positive Validations

1. Email field accepts valid email addresses in standard format (user@example.com)
2. Send Email button becomes clickable when email field contains a valid value
3. Form submission triggers client-side email format validation before API call
4. Successful request displays message "If an account exists with this email, we've sent password reset instructions."
5. Email input field is cleared and disabled after successful submission
6. Send Email button is replaced with "Back to Sign In" link on success
7. Back link correctly navigates to Sign In page preserving any entered data

### 3. Negative Validations

1. Empty email field displays error message "Email is required" on submit
2. Invalid email format displays error message "Please enter a valid email address"
3. Email exceeding 254 characters displays error message "Email must not exceed 254 characters"
4. Email with spaces displays error message "Email must not contain spaces"
5. Non-existent email displays generic message "If an account exists with this email, we've sent password reset instructions."
6. Rate limit exceeded displays error message "Too many requests. Please wait {X} minutes before trying again."
7. Network error displays error message "Unable to connect. Please check your internet connection and try again."
8. Server error displays error message "Something went wrong. Please try again later."

### 4. Boundary Value Analysis

1. Email field accepts maximum 254 characters and rejects input exceeding this limit
2. Email field auto-trims leading and trailing whitespace before validation
3. Email field treats input as case-insensitive for lookup (User@Example.com equals user@example.com)
4. Rate limiting allows maximum 3 password reset requests per hour per email address
5. Password reset token expires after 10 minutes from generation time

### 5. UI/UX Validations

1. Two-panel layout matches Sign In page for visual consistency
2. Form card is centered vertically and horizontally in the right panel
3. All text styles match Figma specifications for font family, size, weight, color, and line-height
4. Input field displays correct placeholder text in light gray color (#A3A3A3)
5. Input field has light gray background (#F5F5F5) with border-radius of 16px
6. Input field focus state displays border highlight to indicate active field
7. Error state displays red border (#DC3545) and inline error message below the field
8. Button hover state displays slight color change to indicate interactivity
9. Loading state displays centered spinner with "Sending..." text and disabled button
10. Success message displays in green or neutral color above the form
11. Back link is positioned at top left with left-pointing arrow icon
12. Back link does not trigger form validation when clicked

### 6. Accessibility Validations

1. All interactive elements are keyboard accessible via Tab key navigation
2. Email input field has associated label element with aria-label "Email"
3. Invalid fields are marked with aria-invalid="true" attribute
4. Error messages are associated with fields via aria-describedby attribute
5. Dynamic error announcements are made via live regions for screen readers
6. Focus indicators are visible with minimum 2px outline on all interactive elements
7. Color contrast ratio meets WCAG 2.1 Level AA requirement of 4.5:1 for all text
8. Send Email button state changes (loading, disabled) are announced to screen readers
9. Success message is announced to screen readers via live region
10. Back link has descriptive text "Back to Sign In" for screen reader users

### 7. Definition of Done

1. All Positive, Negative, Boundary, UI/UX, and Accessibility validations listed above have been tested and pass across all supported browsers: Chrome, Firefox, Safari, and Edge
2. Password reset email is sent successfully when valid email is submitted
3. Generic success message is displayed regardless of whether email exists in database
4. Rate limiting is enforced at 3 requests per hour per email address
5. Password reset token is generated with minimum 128-bit entropy
6. Password reset token expires after 10 minutes from generation
7. All password reset requests are logged for security monitoring
8. Security review completed with zero critical or high vulnerabilities

---

## Screen 3: Forgot Password — OTP Verification

As a user who received a password reset email,  
I want to verify my identity with the OTP code,  
so that I can proceed to create a new password.

### 1. Acceptance Criteria

1. The OTP Verification page displays a Back link with arrow icon at the top left
2. The page displays "Enter Verification Code" heading in bold (H4, 32px, Semi Bold)
3. The page displays subtext "We've sent a 6-digit code to your email. Enter it below to verify your identity."
4. The form contains 6 individual OTP input boxes arranged horizontally
5. The form displays a "Verify" button with full width and dark background
6. The form displays a "Resend code" link with countdown timer
7. Auto-focus moves to the next input box after each digit is entered
8. Backspace key moves focus to the previous input box
9. Paste of 6-digit code auto-fills all input boxes
10. The Verify button triggers OTP validation on click

### 2. Positive Validations

1. OTP field accepts exactly 6 numeric digits (0-9)
2. Each input box accepts only a single digit character
3. Auto-focus correctly moves to next box after digit entry
4. Backspace correctly moves focus to previous box and clears the digit
5. Paste of 6-digit code correctly fills all boxes in sequence
6. Verify button becomes enabled when all 6 digits are entered
7. Valid OTP redirects to Create New Password screen
8. Resend code link becomes enabled after 60 second countdown completes

### 3. Negative Validations

1. Empty OTP submission displays error message "Verification code is required"
2. OTP with fewer than 6 digits displays error message "Please enter a valid 6-digit code"
3. OTP with non-numeric characters displays error message "Please enter a valid 6-digit code"
4. Invalid OTP displays error message "Invalid verification code. Please try again."
5. Expired OTP displays error message "This verification code has expired. Please request a new one."
6. Already used OTP displays error message "This verification code has already been used. Please request a new one."
7. Maximum resend attempts exceeded displays error message "Maximum resend attempts reached. Please try again later."
8. Network error displays error message "Unable to connect. Please check your internet connection and try again."

### 4. Boundary Value Analysis

1. OTP field accepts exactly 6 digits and rejects input with fewer digits
2. OTP field accepts exactly 6 digits and rejects input with more digits
3. Each input box accepts only single character (0-9)
4. OTP expires after 10 minutes from generation time
5. Maximum 3 resend attempts allowed per password reset request
6. Resend countdown timer starts at 60 seconds after each send

### 5. UI/UX Validations

1. Two-panel layout matches previous pages for visual consistency
2. Form card is centered vertically and horizontally in the right panel
3. All text styles match Figma specifications for font family, size, weight, color, and line-height
4. OTP input boxes have light gray background (#F5F5F5) with border-radius of 8px
5. OTP input boxes are evenly spaced with consistent gap between them
6. Active input box displays border highlight to indicate focus
7. Error state displays red border (#DC3545) on all OTP boxes
8. Button hover state displays slight color change to indicate interactivity
9. Loading state displays centered spinner with "Verifying..." text and disabled button
10. Resend code link displays countdown "Resend code in 60s" when disabled
11. Resend code link displays enabled state with link color after countdown
12. Pasted content is automatically distributed across input boxes

### 6. Accessibility Validations

1. All interactive elements are keyboard accessible via Tab key navigation
2. Each OTP input box has associated aria-label "Verification code digit 1" through "digit 6"
3. Invalid input boxes are marked with aria-invalid="true" attribute
4. Error messages are associated with input group via aria-describedby attribute
5. Dynamic error announcements are made via live regions for screen readers
6. Focus indicators are visible with minimum 2px outline on all input boxes
7. Color contrast ratio meets WCAG 2.1 Level AA requirement of 4.5:1 for all text
8. Verify button state changes (loading, disabled) are announced to screen readers
9. Resend countdown timer is announced to screen readers at appropriate intervals
10. Success message is announced to screen readers via live region

### 7. Definition of Done

1. All Positive, Negative, Boundary, UI/UX, and Accessibility validations listed above have been tested and pass across all supported browsers: Chrome, Firefox, Safari, and Edge
2. OTP verification works end-to-end with valid 6-digit code
3. Auto-focus and backspace navigation works correctly across all input boxes
4. Paste functionality correctly distributes 6-digit code across boxes
5. Resend code functionality generates new OTP and invalidates previous code
6. Rate limiting is enforced at maximum 3 resend attempts per request
7. OTP expires correctly after 10 minutes from generation
8. Security review completed with zero critical or high vulnerabilities

---

## Screen 4: Create New Password

As a user who verified identity with OTP,  
I want to create a new password for my account,  
so that I can regain access with updated credentials.

### 1. Acceptance Criteria

1. The Create New Password page displays "Create New Password" heading in bold (H4, 32px, Semi Bold)
2. The page displays subtext "Your new password must be different from your previous password"
3. The form contains a New Password input field with placeholder text "New Password"
4. The form contains a Confirm Password input field with placeholder text "Confirm Password"
5. Both password fields display show/hide eye icons for visibility toggle
6. The form displays a password strength indicator below the New Password field
7. The form displays a checklist showing password requirements with real-time checkmarks
8. The form displays a "Reset Password" button with full width and dark background
9. The Reset Password button is disabled until all requirements are met
10. The Reset Password button triggers password reset on click

### 2. Positive Validations

1. New Password field accepts passwords meeting all complexity requirements
2. Confirm Password field accepts input matching the New Password exactly
3. Show/hide password toggle correctly switches between masked and plain text for both fields
4. Password strength indicator updates in real-time as user types
5. Requirement checklist shows green checkmark as each criterion is met
6. Reset Password button becomes enabled when all requirements are satisfied
7. Matching passwords and valid complexity triggers successful submission
8. Successful reset displays message "Password reset successful. Redirecting to sign in..."
9. User is redirected to Sign In page after 2 seconds on success

### 3. Negative Validations

1. Empty New Password field displays error message "New password is required" on submit
2. Empty Confirm Password field displays error message "Please confirm your password" on submit
3. Password less than 8 characters displays error message "Password must be at least 8 characters"
4. Password missing uppercase letter displays error message "Password must contain at least one uppercase letter"
5. Password missing lowercase letter displays error message "Password must contain at least one lowercase letter"
6. Password missing number displays error message "Password must contain at least one number"
7. Password missing special character displays error message "Password must contain at least one special character"
8. Password exceeding 128 characters displays error message "Password must not exceed 128 characters"
9. Passwords not matching displays error message "Passwords do not match"
10. Password same as current password displays error message "New password must be different from your current password"
11. Network error displays error message "Unable to connect. Please check your internet connection and try again."
12. Server error displays error message "Something went wrong. Please try again later."

### 4. Boundary Value Analysis

1. Password field accepts minimum 8 characters and rejects input with fewer characters
2. Password field accepts maximum 128 characters and rejects input exceeding this limit
3. Password field auto-trims leading and trailing whitespace before validation
4. Internal spaces within password are allowed if other requirements are met
5. Confirm Password must match New Password character-for-character including case
6. Password strength is calculated in real-time as user types each character

### 5. UI/UX Validations

1. Two-panel layout matches previous pages for visual consistency
2. Form card is centered vertically and horizontally in the right panel
3. All text styles match Figma specifications for font family, size, weight, color, and line-height
4. Input fields display correct placeholder text in light gray color (#A3A3A3)
5. Input fields have light gray background (#F5F5F5) with border-radius of 16px
6. Input field focus state displays border highlight to indicate active field
7. Error state displays red border (#DC3545) and inline error message below the field
8. Button hover state displays slight color change to indicate interactivity
9. Loading state displays centered spinner with "Resetting..." text and disabled button
10. Password strength indicator displays visual feedback (weak/medium/strong)
11. Requirement checklist displays below New Password field with clear labels
12. Checkmarks turn green as requirements are satisfied in real-time
13. Show/hide eye icons are positioned on the right side of each password field

### 6. Accessibility Validations

1. All interactive elements are keyboard accessible via Tab key navigation
2. New Password input field has associated label with aria-label "New Password"
3. Confirm Password input field has associated label with aria-label "Confirm Password"
4. Invalid fields are marked with aria-invalid="true" attribute
5. Error messages are associated with fields via aria-describedby attribute
6. Dynamic error announcements are made via live regions for screen readers
7. Focus indicators are visible with minimum 2px outline on all interactive elements
8. Color contrast ratio meets WCAG 2.1 Level AA requirement of 4.5:1 for all text
9. Show/hide password toggle buttons have appropriate aria-label based on state
10. Reset Password button state changes (loading, disabled) are announced to screen readers
11. Password strength changes are announced to screen readers via live region
12. Requirement checklist updates are announced as checkmarks appear

### 7. Definition of Done

1. All Positive, Negative, Boundary, UI/UX, and Accessibility validations listed above have been tested and pass across all supported browsers: Chrome, Firefox, Safari, and Edge
2. Password reset works end-to-end with valid new password meeting all requirements
3. Real-time password strength indicator updates correctly as user types
4. Requirement checklist shows accurate checkmarks for each satisfied criterion
5. Password complexity validation matches backend requirements exactly
6. Password is hashed with bcrypt (cost >= 12) before database storage
7. All existing sessions are invalidated after password reset
8. Password reset confirmation email is sent to user's registered email address
9. Security review completed with zero critical or high vulnerabilities
10. QA testing completed with no open critical or high severity bugs


---

*Generated from Figma: https://www.figma.com/design/BXMaoyXQzDwRZ2yaUa5iNP/2-Compliance?node-id=887-3053*  
*Template: .specify/templates/spec-template.md*
