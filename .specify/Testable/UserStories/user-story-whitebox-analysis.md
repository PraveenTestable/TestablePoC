# Testable Landing Page — Confidence Engine Whitebox Analysis

**Figma File**: Confidence Engine - WB-CE
**Generated**: March 27, 2026

---

## Screen 1: PR Confidence Analysis Dashboard

As a developer or QA engineer reviewing code quality,
I want to view whitebox confidence scores and structural analysis metrics,
so that I can assess code quality and identify areas needing improvement before release.

### 1. Acceptance Criteria

1. The PR Confidence Analysis section displays four score cards: Confidence Score, Whitebox Score, Blackbox Score, and Validations Passed
2. Confidence Score displays as X/100 with a progress bar and status badge (HOLD/WARN/GO)
3. Whitebox Score displays as X/50 with weight multiplier (e.g., x 0.60) and subtitle "Structural & code analysis"
4. Blackbox Score displays as X/50 with weight multiplier (e.g., x 0.40) and subtitle "User journey & experience"
5. Validations Passed displays as X/Y with percentage and progress bar
6. Gate Analysis section displays three gate types: Pipeline Gate, Whitebox Confidence, and Blackbox Confidence with respective weights
7. Code Intelligence section displays as a tabbed interface with tabs: Structural Analysis, Code Quality Auditing, Static Code Analysis, Control Flow Testing, Mutation Testing, Data Flow Testing, and More(Please refer attached excel.)
8. Structural Analysis Gate section displays a table with columns: Classification, Value, Execution Status, Result, and Coverage
9. Each classification row displays an icon, name, value with threshold comparison, status badge, result badge, and coverage progress bar
10. Execution Status badges display three states: Completed (green), In Progress (blue with spinner), Not Started (gray)
11. Result badges display three states: Pass (green), Warn (yellow/orange), Fail (red)
12. Clicking on any classification row opens a detail modal/popup for that metric
13. The active tab (Structural Analysis) is highlighted with dark background
14. A download button (icon) is displayed next to each Classification title in the table
15. The download button is enabled (clickable, full opacity) only when the Execution Status is "Completed"
16. The download button is disabled (grayed out, non-clickable) when Execution Status is "In Progress" or "Not Started", other than Completed
17. Clicking the enabled download button triggers download of the classification report (CSV/PDF format)

### 2. Positive Validations

1. Whitebox Score calculates correctly based on structural and code analysis inputs
2. Score weights (60% whitebox, 40% blackbox) apply correctly to final confidence calculation
3. Progress bars animate smoothly when scores update
4. Status badges update dynamically based on score thresholds
5. Tab switching between Code Intelligence categories loads correct content without page refresh
6. Classification table sorts correctly by default order or user-selected sort criteria
7. Clicking on a classification row opens the corresponding detail modal
8. Coverage progress bars display correct percentage and color coding
9. Threshold comparisons display correct operators (≤, ≥, =) and values
10. In Progress indicators show animated spinner for active validations
11. Download button is enabled and clickable when classification status is "Completed"
12. Clicking enabled download button initiates file download successfully
13. Download button is disabled and non-interactive when status is "In Progress" or "Not Started" other than Completed


### 3. Negative Validations

1. Missing score data displays placeholder (e.g., "--" or "N/A") instead of breaking layout
2. Invalid threshold values display error state with appropriate message
3. Failed validations display Fail result badge with red styling
4. Network error during score calculation displays error message with retry option
5. Empty classification table displays "No metrics available" empty state
6. Modal fails to load displays error message and close button remains functional
7. Extremely long classification names truncate with ellipsis without breaking layout
8. Zero coverage displays appropriate visual state (empty or red progress bar)
9. Clicking disabled download button does not trigger any action or download
10. Download failure displays error message with retry option
11. Download button remains disabled during "In Progress" status even if user refreshes page

### 4. Boundary Value Analysis

1. Confidence Score minimum displays as 0/100 with appropriate styling
2. Confidence Score maximum displays as 100/100 with GO status
3. Whitebox Score minimum displays as 0/50
4. Whitebox Score maximum displays as 50/50
5. Score thresholds at boundary (e.g., exactly 10 for cyclomatic complexity) display correct Pass/Warn status
6. Coverage at 0% displays empty progress bar with red or gray styling
7. Coverage at 100% displays full progress bar with green styling
8. Classification values at threshold boundary display correct comparison result
9. Modal opens correctly when clicking anywhere on the classification row
10. Very large value numbers display without breaking layout (e.g., 10000+)

### 5. UI/UX Validations

1. Score cards maintain consistent height and width across all four cards
2. Progress bar colors match status (brown/red for low, green for high)
3. Status badges use consistent color coding across the interface
4. Tab buttons display clear active/inactive states with visual distinction
5. Classification table rows have adequate padding and hover states
6. Icons are consistent in size and alignment within table cells
7. Modal overlay dims background content appropriately
8. Modal close button (X) is visible and positioned in top-right corner
9. Value comparisons display operators (≤, ≥) clearly with proper spacing
10. Coverage progress bars align consistently across all rows
11. Typography hierarchy distinguishes headers from content
12. Gate weights display as percentages with clear labeling
13. Download button icon is positioned to the right of the Classification name
14. Enabled download button displays with full opacity and pointer cursor
15. Disabled download button displays grayed out with not-allowed cursor
16. Download button hover state shows visual feedback (slight color change or scale)
17. Tooltip on disabled download button displays message like "Download available when status is Completed"
18. Download button is vertically aligned with the Classification name

### 6. Accessibility Validations

1. All score cards have appropriate ARIA labels describing the metric
2. Progress bars have aria-valuenow, aria-valuemin, and aria-valuemax attributes
3. Status badges have aria-label describing the state (e.g., "Hold", "Warning", "Go")
4. Tab navigation works correctly with keyboard (Tab, Enter, Arrow keys)
5. Active tab is indicated with aria-selected="true"
6. Classification table has proper table structure with th and td elements
7. Table rows are keyboard navigable with Enter key to open modal
8. Modal traps focus correctly when opened
9. Modal close button is keyboard accessible
10. Pressing Escape key closes the modal
11. Focus returns to triggering element when modal closes
12. Color contrast ratio meets WCAG 2.1 Level AA requirement of 4.5:1 for all text
13. Screen readers announce status changes dynamically via live regions
14. Download button has aria-label describing the action (e.g., "Download Static Analysis Metric report")
15. Disabled download button has aria-disabled="true" attribute
16. Tooltip content is accessible to screen readers via aria-describedby
17. Download button is keyboard accessible with Enter and Space keys to trigger

### 7. Definition of Done

1. All Positive, Negative, Boundary, UI/UX, and Accessibility validations listed above have been tested and pass across all supported browsers: Chrome, Firefox, Safari, and Edge
2. Whitebox Score calculation is accurate and matches backend computation
3. Tab switching between Code Intelligence categories works without errors
4. Classification table displays all metrics with correct data binding
5. Modal opens correctly for each classification type with appropriate data
6. Real-time updates reflect correctly when validation status changes
7. Performance testing confirms dashboard loads within 2 seconds
8. Security review completed with zero critical or high vulnerabilities
9. QA testing completed with no open critical or high severity bugs
10. Download button correctly enables/disables based on execution status
11. Download functionality generates and downloads reports in correct format

---

## Screen 2: Static Analysis Metric Detail Modal

As a developer reviewing code quality metrics,
I want to view detailed breakdown of a specific classification metric,
so that I can understand the cumulative metrics and sub-metrics contributing to the overall score.

### 1. Acceptance Criteria

1. The modal displays with header showing the classification name (e.g., "Static Analysis Metric")
2. The modal header displays the parent category subtitle (e.g., "Cyclomatic Complexity")
3. The modal displays a close button (X) in the top-right corner
7. Cumulative Metrics section displays four cards: Value, Threshold, Status, and Coverage
8. Value card displays the metric value prominently
9. Threshold card displays the threshold with comparison operator (e.g., "≥ 70" or "≤ 10")
10. Status card displays Pass/Warn/Fail badge
11. Coverage card displays percentage with progress bar
12. A detailed metrics table displays columns: Metric, Threshold, Result, and Coverage
13. Each sub-metric row displays the metric name, threshold comparison, result badge, and coverage bar
14. The modal has a white background with subtle shadow overlay on dimmed background
15. Clicking outside the modal or on the X button closes the modal

### 2. Positive Validations

1. Modal opens centered on screen with appropriate dimensions
2. Cumulative metrics display correct aggregated values from sub-metrics
3. Status badge correctly reflects whether value meets threshold
4. Coverage progress bar displays correct percentage and fills proportionally
5. Sub-metrics table displays all child metrics for the classification
6. Result badges display correct Pass/Warn/Fail status based on threshold comparison
7. Modal content scrolls if content exceeds viewport height
8. Close button (X) closes modal and returns focus to triggering element
9. Clicking on overlay background closes modal
10. Escape key closes modal

### 3. Negative Validations

1. Missing metric data displays placeholder instead of breaking layout
2. Invalid threshold configuration displays error state with message
3. Empty sub-metrics table displays "No sub-metrics available" message
4. Modal content overflow displays scrollbar without cutting off content
5. Network error during data fetch displays error message with retry option
6. Extremely long metric names truncate with ellipsis
7. Very large numeric values display without breaking layout
8. Modal remains functional even if some data fails to load

### 4. Boundary Value Analysis

1. Value at exact threshold boundary displays correct Pass/Warn status
2. Coverage at 0% displays empty progress bar
3. Coverage at 100% displays full progress bar
4. Single sub-metric displays correctly without extra spacing
5. Many sub-metrics (10+) display with appropriate scrolling
6. Minimum threshold values (e.g., 0) display correctly
7. Maximum threshold values (e.g., 1000+) display without overflow
8. Decimal values display with consistent precision (e.g., 4.2)

### 5. UI/UX Validations

1. Modal overlay dims background to 50-70% opacity
2. Modal has rounded corners and subtle drop shadow
3. Cumulative metrics cards have consistent size and spacing
4. Card labels display in uppercase or smaller font for hierarchy
5. Values display in large, bold typography for emphasis
6. Progress bars use consistent color scheme (green for pass, yellow for warn, red for fail)
7. Table has clear header row with distinct styling
8. Table rows have adequate padding and hover states
9. Close button has hover state indicating interactivity
10. Modal animation (fade/slide in) is smooth and not jarring
11. Typography is consistent with overall design system
12. Icons and badges align consistently within cells

### 6. Accessibility Validations

1. Modal has role="dialog" and aria-modal="true" attributes
2. Modal has aria-labelledby pointing to the header title
3. Focus is trapped within modal when open
4. All interactive elements are keyboard accessible
5. Close button has aria-label="Close modal"
6. Pressing Escape key closes modal
7. Focus returns to triggering element when modal closes
8. Cumulative metric cards have appropriate ARIA labels
9. Progress bars have aria-valuenow, aria-valuemin, aria-valuemax
10. Table has proper structure with scope attributes on headers
11. Color contrast ratio meets WCAG 2.1 Level AA requirement of 4.5:1
12. Screen readers announce modal opening and closing

### 7. Definition of Done

1. All Positive, Negative, Boundary, UI/UX, and Accessibility validations listed above have been tested and pass across all supported browsers: Chrome, Firefox, Safari, and Edge
2. Modal opens correctly when clicking any classification row
3. Cumulative metrics calculate and display accurately
4. Sub-metrics table displays all child metrics with correct data
5. Close functionality works via X button, overlay click, and Escape key
6. Focus management works correctly for keyboard users
7. Modal displays correctly on various screen sizes and resolutions
8. Performance testing confirms modal opens within 500ms
9. Security review completed with zero critical or high vulnerabilities
10. QA testing completed with no open critical or high severity bugs