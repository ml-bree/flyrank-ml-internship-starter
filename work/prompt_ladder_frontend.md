# Prompt Ladder: Writing Frontend Code (Login Page)

**Voice Card:** Build things, deliver results, have fun, be direct

---

## Baseline Prompt (Version 0)

**Prompt:**
Write frontend code for a login page.

**Output (excerpt):**
[Claude gave a polished login page with split layout, dark theme, console animation, client-side validation, mobile responsive]

**What's wrong with it:**
Too generic. No tech stack specified. No mention of state management, error handling beyond client validation, loading states, tests, or production considerations. API endpoints hardcoded.

---

## Version 1: Defined Audience

**Layer Added:** Defined audience

**Prompt:**
Write frontend code for a login page for a production React application used by a team of engineers. The code should be production-ready, maintainable, and follow React best practices.

**Output (excerpt):**
[Claude gave 12 files, TypeScript, separated concerns (API layer, validation, state logic, UI), security comments, trade-offs explained]

**What changed in the prompt:**
Added audience (production React app for a team of engineers).

**What improved in the output:**
Now it's properly structured with separated concerns (12 files instead of one), TypeScript for type safety, security footguns called out (session cookie vs bearer token, user-enumeration leak, useReducer vs useState), and clear trade-offs documented.

**What still failed:**
Still missing: tech stack specifics (Tailwind? React Hook Form? Zod?), API integration, loading states, accessibility details, rate-limiting UX, CSRF handling, MFA, i18n.

**What I would try next:**
Add real context (tech stack + product details).

---

## Version 2: Real Context

**Layer Added:** Real context

**Prompt:**
Write frontend code for a login page for a production React application used by a team of engineers. The app uses React with TypeScript, Tailwind CSS, and React Hook Form for validation. It's for an internal ML platform where engineers authenticate to access dashboards and data. The login should call a real API endpoint and handle loading and error states properly.

**Output (excerpt):**
[Claude gave complete React component with TypeScript, Zod schema, React Hook Form, API integration, loading states, error handling, password visibility toggle]

**What changed in the prompt:**
Added tech stack (React, TypeScript, Tailwind, React Hook Form, Zod) + product context (internal ML platform).

**What improved in the output:**
Complete form validation with Zod schema. API integration with proper error handling. Loading states with spinner. Password visibility toggle. SessionStorage token storage.

**What still failed:**
No tests. No README. No i18n. Some hardcoded strings. Limited accessibility details.

**What I would try next:**
Specify output format (tests + README).

---

## Version 3: Specified Format

**Layer Added:** Specified format

**Prompt:**
Write frontend code for a login page for a production React application used by a team of engineers. The app uses React with TypeScript, Tailwind CSS, and React Hook Form with Zod for validation. It's for an internal ML platform where engineers authenticate to access dashboards and data. The login should call a real API endpoint and handle loading and error states properly.

Structure the output as:
1. The full Login component
2. Unit tests for the form validation
3. A README explaining the component's decisions and trade-offs

**Output (excerpt):**
[Claude gave full component + comprehensive unit tests + detailed README with architecture decisions, security considerations, accessibility features]

**What changed in the prompt:**
Added specified format (component + tests + README).

**What improved in the output:**
Now includes complete test suite (form validation, API integration, UI interactions, accessibility) and a professional README explaining decisions, trade-offs, and usage.

**What still failed:**
No i18n support. Some TypeScript `any` types. Missing WCAG compliance details. Rate limiting not fully implemented. No request timeout handling.

**What I would try next:**
Add quality criteria (TypeScript coverage, accessibility, i18n).

---

## Version 4: Constraints + Quality

**Layer Added:** Constraints + Quality criteria

**Prompt:**
Write frontend code for a login page for a production React application used by a team of engineers. The app uses React with TypeScript, Tailwind CSS, and React Hook Form with Zod for validation. It's for an internal ML platform where engineers authenticate to access dashboards and data. The login should call a real API endpoint and handle loading and error states properly.

Structure the output as:
1. The full Login component
2. Unit tests for the form validation
3. A README explaining the component's decisions and trade-offs

Quality Criteria:
- 100% accessibility compliance (WCAG 2.1 AA)
- Complete TypeScript coverage (no `any` types)
- Mobile-responsive design
- Loading states for all async operations
- Comprehensive error handling (network, validation, API)
- Rate limiting with user feedback
- Secure token storage with expiration

Constraints:
- Under 300 lines for the main component
- All strings must be in a separate locale file (i18n ready)
- Include proper ARIA attributes and keyboard navigation
- No console warnings or errors
- All tests must pass

**Output (excerpt):**
[Claude gave full WCAG 2.1 AA compliant component with i18n support, TypeScript with no `any`, complete accessibility features, rate limiting, proper ARIA attributes]

**What changed in the prompt:**
Added quality criteria (TypeScript coverage, WCAG compliance, i18n) and constraints (line limit, locale files, accessibility).

**What improved in the output:**
Full i18n support with locale files. 100% TypeScript coverage (no `any`). WCAG 2.1 AA compliance with proper ARIA attributes. Rate limiting with user feedback. Mobile-responsive design. Request timeout handling.

**What still failed:**
No self-review or verification step. Potential issues like memory leaks from timers, missing input sanitization, incomplete error types.

**What I would try next:**
Add verification (self-review after writing).

---

## Version 5: Verification

**Layer Added:** Verification

**Prompt:**
Write frontend code for a login page for a production React application used by a team of engineers. The app uses React with TypeScript, Tailwind CSS, and React Hook Form with Zod for validation. It's for an internal ML platform where engineers authenticate to access dashboards and data. The login should call a real API endpoint and handle loading and error states properly.

Structure the output as:
1. The full Login component
2. Unit tests for the form validation
3. A README explaining the component's decisions and trade-offs

Quality Criteria:
- 100% accessibility compliance (WCAG 2.1 AA)
- Complete TypeScript coverage (no `any` types)
- Mobile-responsive design
- Loading states for all async operations
- Comprehensive error handling (network, validation, API)
- Rate limiting with user feedback
- Secure token storage with expiration

Constraints:
- Under 300 lines for the main component
- All strings must be in a separate locale file (i18n ready)
- Include proper ARIA attributes and keyboard navigation
- No console warnings or errors
- All tests must pass

After writing the code, review it against the criteria above. Identify any weaknesses, security concerns, or gaps. If you find issues, revise the code and explain what you changed.

**Output (excerpt):**
[Claude gave code + self-review identifying 10 issues: missing timeout handling, memory leak risk, incomplete token storage, no input sanitization, missing focus management, incomplete error types, form not reset on rate limit, no AbortController cleanup, inconsistent storage, missing mobile padding. All were fixed.]

**What changed in the prompt:**
Added verification step (Claude reviews its own code).

**What improved in the output:**
Self-review caught 10 issues that were then fixed: timeout handling with AbortController, memory leak prevention with useRef, token + user storage, email sanitization, focus management on error, TIMEOUT_ERROR added, form reset on rate limit, proper cleanup, consistent storage, mobile padding.

**What still failed:**
Could still benefit from real-world testing and server-side rate limiting validation.

**What I would try next:**
Add real user testing and server-side integration validation.

---

## Final Reusable Prompt
Write frontend code for a login page for a production React application used by a team of engineers. The app uses React with TypeScript, Tailwind CSS, and React Hook Form with Zod for validation. It's for an internal ML platform where engineers authenticate to access dashboards and data. The login should call a real API endpoint and handle loading and error states properly.

Structure the output as:
1. The full Login component
2. Unit tests for the form validation
3. A README explaining the component's decisions and trade-offs

Quality Criteria:
- 100% accessibility compliance (WCAG 2.1 AA)
- Complete TypeScript coverage (no `any` types)
- Mobile-responsive design
- Loading states for all async operations
- Comprehensive error handling (network, validation, API)
- Rate limiting with user feedback
- Secure token storage with expiration

Constraints:
- Under 300 lines for the main component
- All strings must be in a separate locale file (i18n ready)
- Include proper ARIA attributes and keyboard navigation
- No console warnings or errors
- All tests must pass

After writing the code, review it against the criteria above. Identify any weaknesses, security concerns, or gaps. If you find issues, revise the code and explain what you changed.


---

## Summary Table

| Version | Layer Added | What Improved |
|---------|-------------|---------------|
| 0 | Baseline | N/A |
| 1 | Defined audience | React instead of vanilla HTML; separated concerns; security comments |
| 2 | Real context | Complete validation with Zod; API integration; loading states; password toggle |
| 3 | Specified format | Comprehensive tests; detailed README with architecture decisions |
| 4 | Constraints + Quality | i18n support; WCAG 2.1 AA compliance; 100% TypeScript coverage; rate limiting |
| 5 | Verification | Self-review caught 10 issues: timeouts, memory leaks, sanitization, accessibility, focus management |

**Most valuable layer:** Verification (Version 5) — it caught the most issues and led to the most improvements. Adding a self-review step transformed good code into production-ready code.

**What I learned:** Prompt engineering is iterative. Each layer builds on the previous one. The verification layer (self-review) was the most impactful because it forced the AI to think critically about its own output and catch issues that weren't obvious from the initial prompt.
