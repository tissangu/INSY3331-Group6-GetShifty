---
name: getshifty-quality
description: >-
  Shared quality, scheduling, UI, privacy, and testing standards for the INSY 3331
  AI for Business Shark Tank project: GetShifty. All four team members and Google
  Antigravity sessions must adhere to these rules when designing, implementing,
  refactoring, or verifying features for the GetShifty employee scheduling application.
---

# GetShifty Quality Standards & Team Skill
**Course:** INSY 3331 — Artificial Intelligence for Business  
**Project:** GetShifty (Shark Tank Project)  
**Target Users:** Small-business managers (restaurants, cafés, retail)  
**Core Purpose:** Shared engineering instructions, scheduling rules, interface standards, privacy protocols, and collaboration workflows for all four team members when using Google Antigravity.

---

## 1. Technical Requirements

- **Single-File Architecture:** Keep the entire web application inside a single `index.html` file containing HTML, CSS (in `<style>` tags), and JavaScript (in `<script>` tags). Do not split into external `.js` or `.css` files unless explicitly assigned.
- **GitHub Pages Compatibility:** Ensure all code, paths, and inline assets run seamlessly as a static site hosted on GitHub Pages.
- **Zero-Dependency Constraint:** Do not introduce servers (Node.js, Express, Python backends), API keys, paid cloud services, external databases (Firebase, Supabase, SQL), external package installs (`npm`, `yarn`, `pip`), or bundlers/build tools (Webpack, Vite, Tailwind CLI).
- **Client-Side Persistence:** Store all employee rosters, shift requirements, preferences, and generated schedules locally using browser `localStorage`. Always provide fallback initialization data so the application never starts blank or crashes on empty cache.
- **Tool Discipline:** Do not execute Git commands (commits, pushes, branch creation) or open external browsers unless explicitly instructed by the team member in their prompt.

---

## 2. Scheduling Rules

Every scheduling algorithm or manual adjustment must strictly satisfy these hard constraints:

1. **Availability Adherence:** Never schedule an employee on days or shift intervals (morning, afternoon, evening) where they have marked themselves unavailable.
2. **Zero Overlapping Shifts:** Never assign an employee to overlapping shifts or multiple shifts on the same calendar day.
3. **Maximum Weekly Hours Cap:** Never exceed an employee's declared maximum weekly working hours cap ($e.\text{assignedHours} + \text{duration} \le e.\text{maxHours}$).
4. **Qualification & Role Matching:** Only assign employees to shift slots matching roles and qualifications they are verified to perform (e.g., Manager, Barista, Cashier, Server).
5. **Time-Off & Absence Respect:** Strictly honor recorded time-off requests, call-outs, and blacked-out dates.
6. **Explicit Shortage Flagging:** If a required shift cannot be filled due to constraint conflicts, clearly flag and highlight it as an "Uncovered Shift" rather than silently leaving it empty or violating a hard constraint.

---

## 3. Scheduling Optimization and Fairness

When multiple candidates satisfy all hard constraints, the scheduling engine must optimize assignments using these soft heuristics:

- **Fair Hours Distribution:** Distribute weekly hours equitably based on each employee's preferred hours target and declared availability, avoiding situations where one worker is overloaded while another gets zero hours.
- **Prioritize Complete Coverage:** Prioritize filling every open shift slot without compromising or relaxing hard constraints.
- **Proactive Conflict & Shortage Identification:** Continuously audit the weekly matrix to identify understaffed roles, single points of failure, and bottleneck shifts.
- **Schedule Stability on Regeneration:** When regenerating schedules (such as during an employee call-out or schedule adjustment), preserve existing valid shift assignments to avoid ripple disruptions across the team.
- **Transparent Diagnostic Explanations:** For every unfilled or conflict shift, provide a human-readable explanation of why the slot could not be filled (e.g., "All qualified Managers exceed their 40h cap or are unavailable on Saturday Morning").

---

## 4. User Interface Standards

- **Brand Identity:** Maintain the official product name **GetShifty** and tagline **"Smarter Scheduling. Happier Teams."**
- **Modern & Professional Aesthetic:** Use a clean, polished design system featuring a cohesive color palette (slate neutrals, indigo primary, emerald success, amber warning, rose alert), modern card elevations, and clean typography.
- **Cross-Device Responsiveness:** Ensure the user interface renders and functions cleanly across mobile smartphones, tablets, and desktop laptops.
- **Visual Consistency:** Maintain uniform border radii, button hierarchies (primary, secondary, danger, ghost), form field styling, modal backdrops, and table layouts throughout the application.
- **Comprehensive Visual Dashboards:** Display:
  - An interactive weekly schedule grid (Monday through Sunday across shifts).
  - Employee rosters with real-time hours tracking (scheduled vs. preferred vs. max).
  - Clear staffing coverage indicators and real-time KPI metrics.
- **Navigation & Error Feedback:** Provide intuitive navigation, accessible modal dialogs with escape/close handlers, and friendly toast/banner notifications for user feedback.

---

## 5. Privacy and Responsible AI

- **Synthetic & Fictional Data:** Exclusively use fictional employee names, mock contact details, and synthetic store scenarios in demonstrations, test fixtures, and demo datasets.
- **Zero Sensitive Data Collection:** Never request, collect, or store confidential personal identification (e.g., Social Security Numbers, banking details, personal medical records, home addresses).
- **Local Data Custody:** All data must remain strictly on the user's local machine inside browser `localStorage`. Never transmit user data to external endpoints or third-party tracking services.
- **Human-in-the-Loop Decision Making:** Present AI scheduling outputs as recommendations for managerial review and approval; always permit managers to review, override, manually edit, or reject automated assignments.
- **Legal & Compliance Transparency:** Never represent automated scheduling recommendations as legal guarantees of compliance with federal, state, or municipal labor regulations (e.g., Fair Workweek laws, predictive scheduling ordinances, OSHA rules). Managers remain the ultimate authority.
- **Statistical Integrity:** Never fabricate test outcomes, fairness indices, or performance metrics. All metrics must accurately reflect the real mathematical state of the underlying schedule.

---

## 6. Testing and Quality Assurance

Every code change must be rigorously verified before handoff:

- **Interactive Verification:** Verify that every interactive element (buttons, tabs, dropdowns, modal triggers, print/export actions) performs its intended function without console errors.
- **Mathematical Accuracy:** Ensure that total assigned hours, fairness percentages, and variance metrics reflect actual employee inputs and slot durations.
- **Constraint Regression Testing:** Validate that employee availability boundaries and weekly maximum hour caps remain unbroken across all test cases.
- **Regeneration Integrity:** Verify that recording an absence or triggering schedule regeneration correctly recalculates assignments, updates diffs, and highlights replacement staff.
- **Zero Regression Principle:** Never break existing features, persistence flows, or visual layouts when adding new capabilities.
- **Manual Verification Instructions:** After completing any change, provide the teammate with clear, step-by-step manual testing instructions explaining how to verify the updated feature in the browser.

---

## 7. Team Collaboration Protocols

All four INSY 3331 Group 6 team members must adhere to this collaboration workflow:

1. **Pre-Change Review & Explanation:** Before modifying any code, the AI agent and the team member must review this skill and explicitly explain the planned modification, identifying which section of `index.html` will be touched.
2. **Feature Scoping:** Keep changes tightly focused on the specific assigned feature or bug fix for that iteration. Avoid unsolicited refactoring of unrelated code.
3. **Change Summarization:** Conclude each build iteration with a concise summary detailing:
   - What was added or updated.
   - Any limitations or known edge cases.
   - Clear next steps for subsequent iterations.
4. **Clean Code & Readability:** Write clean, well-commented HTML, CSS, and JavaScript so any of the other three teammates can immediately understand and extend the implementation.
5. **Iteration Documentation:** Remind team members to capture screenshots of their build iteration (e.g., feature in action, conflict resolution, console tests) for their Shark Tank project deliverable and presentation slide deck.

---

## 8. Skill Evolution & Improvement Log

*Note: INSY 3331 course guidelines require at least one documented, professor-reviewed skill improvement throughout the project lifecycle.*

### How to Update This Skill
When professor feedback, user testing, or team retrospectives identify areas to improve:
1. Identify the relevant section in this file (`.agents/skills/getshifty-quality/SKILL.md`).
2. Add or refine the specific rule, heuristic, or constraint.
3. Document the update in the **Revision History** table below, noting the date, author, change description, and rationale.

### Revision History
| Version | Date | Author | Summary of Improvement / Rationale |
|:---:|:---:|:---:|:---|
| **v1.0** | Current | INSY 3331 Group 6 | Initial baseline shared team skill: technical constraints, scheduling heuristics, UI standards, privacy, testing, and team protocols for Shark Tank project. |
| **v1.1** | *Pending* | *Assigned Member* | *Document professor-requested improvement here (e.g., overtime threshold constraints, employee fatigue/clopening rules, or multi-skill matching).* |
