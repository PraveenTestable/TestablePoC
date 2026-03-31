Use only MCP tools. No Python code.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 1 — READ SPEC TEMPLATE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Use the filesystem MCP tool to read:
spec-template.md
from the current project folder (Testable_PoC).
This is the STRICT reference for tone, language style,
and section depth. Do not deviate from it.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 2 — READ ALL FIGMA PAGES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Read EVERY page in the Figma file.
For each page and screen extract:
1. Page name and screen/frame name
2. All UI components — inputs, buttons, labels, modals,
   dropdowns, toggles, icons, error states, empty states
3. All visible text — headings, body, placeholders,
   helper text, error messages, tooltips
4. All interaction flows — what happens on click, hover,
   focus, blur, submit, success, failure
5. All navigation — forward, backward, close, skip actions
6. All validation rules visible or implied by the design
7. All accessibility indicators — ARIA labels, focus states,
   tab order, keyboard interactions

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 3 — GENERATE ONE USER STORY FILE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Combine ALL pages and screens into ONE single user story file.
Do NOT create a separate file per screen.

Generate the user story in this EXACT format below.
Every section must use flat numbered lists — no bullets,
no dashes, no asterisks, no sub-numbering like 1.1 or 1.1.1.
Each item is a plain sequential number: 1. 2. 3. 4. ...

══════════════════════════════════════════
OUTPUT FORMAT — FOLLOW EXACTLY
══════════════════════════════════════════

__Testable Landing Page — <Screen Name from Figma>__

Note: Please refer to the attached screenshot in the
comment section.

As a <type of user inferred from the design>,
I want to <action the user is performing on this screen>,
so that <the goal or benefit the user achieves>.

1. Acceptance Criteria
<Screen section name — e.g. "Select Target Environment — Step X of Y">
1. <First acceptance criterion — full sentence, present tense>
2. <Second acceptance criterion>
3. <Continue for all criteria observed in the Figma screen>

2. Positive Validations
1. <Positive scenario — what works correctly when valid input
   or correct action is taken — full sentence>
2. <Continue for all positive validations from the design>

3. Negative Validations
1. <Negative scenario — what happens when invalid input,
   missing data, or wrong action is taken — full sentence>
2. <Continue for all error states visible or implied in Figma>

4. Boundary Value Analysis
1. <Minimum/maximum input boundary — full sentence>
2. <Edge of range behaviour — full sentence>
3. <Continue for all boundary conditions found in the design>

5. UI/UX Validations
1. <Visual/layout/spacing validation — full sentence>
2. <Interaction behaviour validation — full sentence>
3. <Continue for all UI/UX rules observable in the Figma>

6. Accessibility Validations
1. <Keyboard navigation rule — full sentence>
2. <ARIA/screen reader requirement — full sentence>
3. <Contrast, focus ring, label requirement — full sentence>
4. <Continue for all accessibility requirements>

7. Definition of Done
1. All Positive, Negative, Boundary, UI/UX, and
   Accessibility validations listed above have been
   tested and pass across all supported browsers:
   Chrome, Firefox, Safari, and Edge.
2. <Feature-specific done criterion — full sentence>
3. <Continue for all done conditions>

══════════════════════════════════════════
NUMBERING RULES — NON-NEGOTIABLE
══════════════════════════════════════════
1. Every item inside every section uses a flat number only:
   1. 2. 3. 4. — no sub-numbers, no 1.1, no 1.1.1
2. Section headings use top-level numbers: 1. 2. 3. 4. 5. 6. 7.
3. No bullet points ( - * • ) anywhere in the document
4. No dashes as list markers
5. Each numbered item is a complete, standalone sentence
6. Sections must always appear in this order:
   1. Acceptance Criteria
   2. Positive Validations
   3. Negative Validations
   4. Boundary Value Analysis
   5. UI/UX Validations
   6. Accessibility Validations
   7. Definition of Done

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 4 — SAVE TO PROJECT FOLDER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Use the filesystem MCP tool to save the output as ONE file:

  Folder   : Testable_PoC/
  Filename : user-story-<figma-page-name>.md
  Example  : user-story-compliance.md

All screens from all Figma pages go into this single file,
separated by a horizontal rule (---) between each screen.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 5 — CONFIRM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
After saving, display this summary:

  File saved     : Testable_PoC/user-story-compliance.md
  Figma pages    : <count>
  Screens read   : <count>
  Sections/screen: 7 (fixed)
  Total items    :
    Acceptance Criteria  : <count>
    Positive Validations : <count>
    Negative Validations : <count>
    Boundary Analysis    : <count>
    UI/UX Validations    : <count>
    Accessibility        : <count>
    Definition of Done   : <count>

Do NOT push to JIRA yet.
File is saved and ready for your review and approval.