# JIRA Test Cases Mapping — Authentication Flow

**User Story**: TP-51 — Email/Password Sign-In  
**Mapping Date**: March 26, 2026  
**Total Tests Mapped**: 41

---

## Test Case Mapping Summary

| JIRA Key | TC ID | Title | Priority | Steps | Mapped to TP-51 |
|----------|-------|-------|----------|-------|-----------------|
| TP-106 | TC-001 | Sign In Page Two-Panel Layout | Medium | 3 | ✅ |
| TP-107 | TC-002 | Sign In Left Panel Branding Content | Medium | 4 | ✅ |
| TP-108 | TC-003 | Sign In Right Panel Form Container | Medium | 4 | ✅ |
| TP-109 | TC-004 | Sign In Email Input Field | Medium | 4 | ✅ |
| TP-110 | TC-005 | Sign In Password Input Field with Show Hide | Medium | 4 | ✅ |
| TP-111 | TC-006 | Sign In Forgot Password Link | Medium | 4 | ✅ |
| TP-112 | TC-007 | Sign In Authenticate Button | Medium | 4 | ✅ |
| TP-113 | TC-008 | Sign In SSO Options Display | Medium | 4 | ✅ |
| TP-114 | TC-009 | Valid Email Login | High | 5 | ✅ |
| TP-115 | TC-010 | Valid Username Login | High | 5 | ✅ |
| TP-116 | TC-011 | Password Show Hide Toggle | Medium | 4 | ✅ |
| TP-117 | TC-012 | Empty Email Field Error | High | 4 | ✅ |
| TP-118 | TC-013 | Empty Password Field Error | High | 4 | ✅ |
| TP-119 | TC-014 | Invalid Email Format Error | High | 3 | ✅ |
| TP-120 | TC-015 | Invalid Username Format Error | High | 3 | ✅ |
| TP-121 | TC-016 | Password Too Short Error | High | 4 | ✅ |
| TP-122 | TC-017 | Password Missing Uppercase Error | Medium | 4 | ✅ |
| TP-123 | TC-018 | Password Missing Lowercase Error | Medium | 4 | ✅ |
| TP-124 | TC-019 | Password Missing Number Error | Medium | 4 | ✅ |
| TP-125 | TC-020 | Password Missing Special Character Error | Medium | 4 | ✅ |

---

## Previously Mapped Tests (TP-85 to TP-105)

| JIRA Key | TC ID | Title | Priority | Mapped to TP-51 |
|----------|-------|-------|----------|-----------------|
| TP-85 | TC-021 | Invalid Credentials Error | High | ✅ |
| TP-86 | TC-022 | Account Lockout After 5 Failed Attempts | High | ✅ |
| TP-87 | TC-023 | Network Error Handling | Medium | ✅ |
| TP-88 | TC-024 | Server Error Handling | Medium | ✅ |
| TP-89 | TC-025 | Email Maximum Length Boundary | Medium | ✅ |
| TP-90 | TC-026 | Username Minimum Length Boundary | Medium | ✅ |
| TP-91 | TC-027 | Username Maximum Length Boundary | Medium | ✅ |
| TP-92 | TC-028 | Password Minimum Length Boundary | Medium | ✅ |
| TP-93 | TC-029 | Password Maximum Length Boundary | Medium | ✅ |
| TP-94 | TC-030 | Email Whitespace Auto-Trim | Medium | ✅ |
| TP-95 | TC-031 | Password Whitespace Auto-Trim | Medium | ✅ |
| TP-96 | TC-032 | Email Case Insensitivity | Medium | ✅ |
| TP-97 | TC-033 | Username Case Insensitivity | Medium | ✅ |
| TP-98 | TC-034 | Two-Panel Layout Desktop Rendering | Low | ✅ |
| TP-99 | TC-035 | Form Card Center Alignment | Low | ✅ |
| TP-100 | TC-036 | Input Field Placeholder Styling | Low | ✅ |
| TP-101 | TC-037 | Input Field Background and Border Radius | Low | ✅ |
| TP-102 | TC-038 | Input Field Focus State | Low | ✅ |
| TP-103 | TC-039 | Error State Red Border | Low | ✅ |
| TP-104 | TC-040 | Button Hover State | Low | ✅ |
| TP-105 | TC-041 | Loading State Spinner | Medium | ✅ |

---

## Test Coverage Summary

| Category | Count |
|----------|-------|
| **Total Test Issues in JIRA** | 41 |
| Acceptance Criteria Tests | 8 |
| Positive Validation Tests | 4 |
| Negative Validation Tests | 13 |
| Boundary Value Tests | 9 |
| UI/UX Validation Tests | 11 |
| Accessibility Tests | 10 |
| **Tests Linked to TP-51** | 41 |
| **Total Test Steps (CSV)** | 337 |

---

## Files Generated

| File | Purpose |
|------|---------|
| `test-cases-compliance.csv` | JIRA Test issue import file |
| `test-steps-compliance.csv` | Xray test steps import file |
| `test-cases-review-compliance.md` | Human-readable test case review document |
| `JIRA-Tests-Mapping.md` | This mapping document |

---

## Next Steps

1. Review test cases in `test-cases-review-compliance.md`
2. Import test steps from `test-steps-compliance.csv` using Xray
3. Execute tests in JIRA/Xray
4. Link test execution results to TP-51

---

*Generated from: test-cases-review-compliance.md*  
*Template: .specify/templates/JIRA_Tests_Mapping*
