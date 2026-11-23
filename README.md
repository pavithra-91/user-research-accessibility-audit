# user-research-accessibility-audit
User research findings, personas/user flows, and WCAG accessibility audit for UI/UX internship milestone
# User Research & Accessibility Audit: IRCTC Train Ticket Booking Flow

## 1. Project Overview
* **Product Audited:** IRCTC Next Generation eTicketing System (Web & Mobile Web)
* **Focus Area:** Train Search, Availability Check, and Passenger Details Flow
* **Objective:** Identify key usability bottlenecks through user research and evaluate the interface against **WCAG 2.1 Level AA** accessibility standards to propose actionable UI/UX improvements.

---

## 2. User Research

### Research Methodology
* **Task-Based Usability Testing:** Observed 5 users (3 frequent travelers, 2 first-time users) attempting to search for a train between two stations and reach the passenger details screen.
* **Contextual Inquiry & Feedback:** Collected post-task feedback on visual clutter, navigation clarity, and error recovery.

### User Persona
* **Name:** Karthik S., 24 | Final-Year Engineering Student
* **Goals:** Book Tatkal or regular sleeper/3AC tickets quickly on mobile without losing session progress.
* **Frustrations:**
  * Distracted by overlapping banner ads and pop-ups during time-sensitive bookings.
  * Confusing quota and class abbreviations (`GN`, `TQ`, `SS`, `3E`) without inline explanations.
  * Form resets or session timeouts when correcting minor input mistakes.

### Key Research Findings & Pain Points
1. **High Cognitive Load:** Promotional banners, alerts, and dense navigation menus compete with the primary "Book Ticket" card.
2. **Unclear Information Hierarchy:** Train availability status (`AVAILABLE`, `WL`, `RAC`) and fare breakdowns require excessive horizontal scrolling or extra clicks on smaller screens.
3. **Poor Error Feedback:** CAPTCHA and login validation errors clear previously entered fields, forcing users to re-type information.

---

## 3. WCAG 2.1 Accessibility Audit

| # | Area / Component | WCAG Criterion | Severity | Issue Description | Recommended Fix |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | **Color Contrast** (Secondary labels & disabled dates) | 1.4.3 Contrast (Minimum) | High | Light gray placeholder text and inactive calendar dates fall below the 4.5:1 contrast ratio against white/light-blue backgrounds. | Darken secondary text to at least `#595959` and increase contrast on interactive calendar states. |
| **2** | **CAPTCHA Verification** | 1.1.1 Non-text Content | Critical | Image-based CAPTCHA lacks a reliable audio alternative on several modal prompts, blocking screen-reader and low-vision users. | Provide an accessible audio CAPTCHA button with clear ARIA labels or migrate to an accessible challenge mechanism. |
| **3** | **Form Labels & Inputs** (Station From/To & Quota) | 3.3.2 Labels or Instructions | High | Inputs rely heavily on placeholder text that disappears once typing starts, hurting users with cognitive or memory impairments. | Add persistent, visible `<label>` elements above every input field and include helper text for quota codes. |
| **4** | **Keyboard Navigation** (Date Picker & Dropdowns) | 2.1.1 Keyboard | High | Tabbing through the search widget skips custom dropdown options or traps focus inside promotional modals. | Enforce logical `tabindex` order, visible focus outlines (`2px solid`), and `Esc` key dismissal for all modals. |
| **5** | **Touch Targets** (Mobile Class Tabs & Modify Search) | 2.5.5 Target Size | Medium | Adjacent class filter tabs (`SL`, `3A`, `2A`) and close (`X`) buttons on pop-ups are smaller than `44x44px`, causing mis-taps. | Increase clickable padding to a minimum of `44x44px` with at least `8px` spacing between targets. |
| **6** | **Status Indicators** (Seat Availability Colors) | 1.4.1 Use of Color | Medium | Availability relies primarily on green/orange/red text color to convey booking likelihood. | Pair colors with clear status icons and descriptive text badges (e.g., `[✓] Available`, `[!] Waitlist`). |

---

## 4. Summary of Recommendations
1. **Declutter the Hero Section:** Isolate the primary train search widget from third-party advertisements and non-essential links.
2. **Standardize Accessible Forms:** Use persistent labels, high-contrast text (`>= 4.5:1`), and inline validation that preserves user input on error.
3. **Improve Mobile Ergonomics & Keyboard Support:** Enlarge touch targets to `44x44px` minimum and ensure full keyboard/screen-reader compatibility across modals and date pickers.
