---
name: prototype-generation
description: >
  Use this skill whenever a PM or product team needs to turn a PRD, user stories, acceptance
  criteria, assumptions, or product concept into a working, testable prototype. Triggers on:
  "build a prototype", "make this clickable", "create a working demo", "turn this PRD into
  something I can test", "build a fake-door test", "create a workflow simulation", "make this
  interactive", "I need something I can show users", "validate this before we build it",
  "prototype this flow", "build a mock of this feature", "create a proof of concept", or any
  request to make a product idea tangible and testable. Also triggers when a PM shares a PRD,
  user story set, acceptance criteria, or hypothesis and says they want to validate it with
  users, stakeholders, or reviewers before committing to full design or engineering.
  Use this skill even with rough or partial inputs — incomplete specs become clearly labelled
  mocked areas, not blockers. Always prefer a working testable artifact over a description of one.
---

# Prototype Generation Skill

## Purpose

Transform product intent — a PRD, user stories, acceptance criteria, assumptions, or key
workflows — into a working prototype that can be tested with real users, stakeholders, or
internal reviewers before full design or engineering begins.

The PM decides what hypothesis matters and whether the fidelity is sufficient. Your job is
to produce the smallest working version that makes the solution tangible and generates useful
feedback.

**Speed, clarity, and testability over production quality. Always.**

---

## Inputs accepted

Accept any combination of the following. Work with what you have — missing inputs become
clearly labelled assumptions or mocked areas, never blockers.

| Input | How it's used |
|---|---|
| PRD | Drives scope, user flows, and must-demonstrate functionality |
| User stories | Maps to prototype screens and interactions |
| Acceptance criteria | Defines what the prototype must prove works |
| Target user | Informs language, UI labels, and testing tasks |
| Key workflow | Shapes the primary user journey to prototype |
| Assumptions to validate | Determines the riskiest thing to make testable |
| Riskiest unknowns | Focuses fidelity and scope on what matters most |
| UI component library | Informs component choices (Tailwind, shadcn, Material, etc.) |
| Brand assets / design system | Applied to visual treatment if provided |
| Example screens or references | Used as aesthetic or layout reference |
| Sample or mocked data | Populates realistic content in the prototype |

---

## Step 1: Understand the prototype intent

Before producing anything, extract and confirm:

1. **What hypothesis or risk is this prototype testing?**
   If not stated: infer the riskiest assumption from the PRD or user stories and state it.

2. **Who will test this prototype, and in what context?**
   (Unmoderated remote session? Moderated interview? Stakeholder walkthrough? Internal review?)

3. **What is the must-demonstrate workflow?**
   Identify the single primary flow that, if testable, generates the most useful signal.

4. **What inputs are missing?**
   List anything that will be mocked, simulated, or assumed in the prototype. Flag it.

If the PM has provided enough context to proceed, proceed. Do not wait for perfect inputs.

---

## Step 2: Prototype fidelity check

Determine the right prototype type before writing a line of code. Use the decision table below.

### Fidelity decision table

| Scenario | Recommended type |
|---|---|
| Testing visual layout, IA, or navigation | Static clickable mock (HTML/CSS) |
| Testing a multi-step user workflow | Interactive UI prototype (React or HTML/JS) |
| Testing a conversational or AI-driven flow | Prompt-flow prototype |
| Testing a data-entry or submission process | Working form or workflow simulation |
| Testing whether users want a feature at all | Fake-door test page |
| Testing a human-in-the-loop process | Concierge prototype |
| Testing an API-backed decision or data display | API-backed demo with mocked data |
| Testing a complex operational workflow | Workflow simulation with state |

### Fidelity definitions

**Static clickable mock** — HTML/CSS with navigation links between screens. No logic.
Best for: Layout, IA, visual hierarchy, first impressions.

**Interactive UI prototype** — React or HTML/JS with state, form handling, and conditional
flows. Data is mocked or hardcoded. Best for: End-to-end user flow validation.

**Prompt-flow prototype** — A structured conversation or AI-powered interaction, either as
a simulated chat UI or a real Claude API call. Best for: AI features, recommendation flows,
conversational UX.

**Working form / workflow simulation** — A functional form or multi-step process with
validation, state transitions, and result screens. Data never leaves the browser.
Best for: Onboarding flows, configuration wizards, submission processes.

**Fake-door test page** — A landing page that presents a feature as if it exists and
captures interest (clicks, sign-ups, wait-list joins) without building it. Best for:
Demand validation before any engineering.

**Concierge prototype** — A human-operated simulation of a product experience, often via
chat, email, or manual workflow. Best for: High-complexity processes where building even
a lightweight prototype is premature.

**API-backed demo** — A lightweight UI connected to a real or mocked API endpoint.
Mocked data replaces real backend data. Best for: Data display, filtering, calculation, or
decision-support features.

**State it explicitly** before producing the prototype: "I'm building a [type] because
[reason tied to the hypothesis being tested]."

---

## Step 3: Scope the prototype

Identify the minimum set of screens, states, and interactions needed to test the hypothesis.

### Scoping rules

- **One primary flow only.** Choose the journey that most directly tests the key assumption.
  Additional flows are out of scope unless explicitly required by the acceptance criteria.

- **Mock everything not directly tested.** If a screen isn't part of the test flow,
  replace it with a placeholder. Label it clearly: `[MOCKED — not in scope for this test]`.

- **Hardcode realistic data.** Use plausible names, numbers, and content. Avoid
  "Lorem ipsum", "Test User", or "123". Realistic data reduces noise in user sessions.

- **Mark simulation clearly.** Any simulated behaviour (fake API call, hardcoded result,
  pre-filled state) must be commented in code and labelled in the UI if visible to testers.

- **No production features.** No auth, no real data persistence, no error handling beyond
  what the test scenario requires. Build only what the test needs.

### Scope checklist (confirm before building)

- [ ] Primary flow identified (start → end)
- [ ] Number of screens / steps scoped
- [ ] Mocked data defined
- [ ] Simulated states identified (success, error, empty, loading if relevant)
- [ ] Out-of-scope areas noted

---

## Step 4: Build the prototype

Follow the active prototype type from Step 2. Build in a single self-contained artifact
unless multiple files are genuinely required.

### All prototype types — universal rules

1. **Single file when possible.** React: one `.jsx` file. HTML: one `.html` with inline CSS and JS.
   Multi-file only when complexity requires it — explain why.

2. **Realistic mocked data.** Define a clear `MOCK_DATA` block or constant at the top of
   the file. Make data plausible for the target user and domain.

3. **Clearly mark mocked areas** in comments: `// MOCKED: replace with real API call`

4. **Navigation that works.** Every button and link that a user would click in a test
   session must do something — even if it's just advancing to the next screen.

5. **No dead ends.** Every screen must have an obvious way forward. If a path is out of
   scope, show a `[This section is not part of this prototype]` placeholder screen.

6. **Mobile-first layout.** Default to a responsive layout unless the product is
   desktop-only. Use `max-width: 480px` for mobile-focused flows.

7. **Loading states for async simulation.** If the prototype simulates an API call or
   data fetch, include a brief loading state (500–1500ms timeout) to make the interaction
   feel realistic.

---

### Type-specific build guidance

#### Interactive UI prototype (React)

```jsx
// PROTOTYPE — Not production code
// Hypothesis being tested: [STATE IT]
// Mocked areas: [LIST THEM]

const MOCK_DATA = { ... };  // All fake data lives here

export default function Prototype() {
  const [step, setStep] = useState('start');
  // ... minimal state only
}
```

- Use Tailwind utility classes for layout and styling
- Import from `react` only: `useState`, `useEffect` if needed
- Use `lucide-react` for icons
- No external API calls — all data from `MOCK_DATA`
- Include a `PROTOTYPE_CONFIG` object at the top for easy test customisation:
  ```js
  const PROTOTYPE_CONFIG = {
    userName: "Sarah",
    scenario: "First-time onboarding",
    simulateError: false
  };
  ```

#### HTML/CSS/JS clickable mock

```html
<!-- PROTOTYPE — Static clickable mock -->
<!-- Hypothesis: [STATE IT] -->
<!-- Navigation: All links use onclick to show/hide screen divs -->
<script>
  function showScreen(id) {
    document.querySelectorAll('.screen').forEach(s => s.style.display = 'none');
    document.getElementById(id).style.display = 'block';
  }
</script>
```

- One `<div class="screen">` per screen, all in the same file
- Only one screen visible at a time via JS toggle
- Style inline or with a `<style>` block — no external CSS
- Every interactive element must call `showScreen()` or show feedback

#### Fake-door test page

Must include:
- A clear value proposition (what the feature does for the user)
- A primary CTA (e.g. "Join waitlist", "Request early access", "Get started")
- A capture mechanism (form field or button that records intent — even if just an alert)
- A thank-you / confirmation state after CTA click
- Optional: a secondary CTA for users who want to learn more

```js
// Fake-door capture — no real submission
function handleSignup(email) {
  // MOCKED: In production, POST to /api/waitlist
  console.log('Captured intent:', email);
  showScreen('thank-you');
}
```

#### Prompt-flow prototype

Build a chat-like UI that simulates an AI-powered or structured conversational flow.
Either:
- **Simulated**: Hardcode a decision tree of responses triggered by user input matching
- **Live**: Use the Anthropic API (`/v1/messages`) with a tightly scoped system prompt

For live prompt-flow prototypes:
```js
const response = await fetch("https://api.anthropic.com/v1/messages", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    model: "claude-sonnet-4-20250514",
    max_tokens: 1000,
    system: `[PROTOTYPE PERSONA]: You are simulating [feature name].
             Scope: [NARROW SCOPE — only respond to X, Y, Z].
             Always stay in character. Never break the simulation.`,
    messages: conversationHistory
  })
});
```

Label the prototype clearly: `[AI-POWERED — responses are generated live]`

#### Workflow simulation

- Model the workflow as explicit state: `idle → step1 → step2 → complete → error`
- Show clear progress indicators (step counter, progress bar, or breadcrumb)
- Simulate async transitions with `setTimeout`
- Include at least one error/rejection path if the acceptance criteria require it

#### API-backed demo

```js
// MOCKED API — replace with real endpoint before production
async function fetchData(params) {
  await new Promise(r => setTimeout(r, 800)); // simulate latency
  return MOCK_DATA.filter(/* apply params */);
}
```

Never make real external API calls in a prototype unless the PM explicitly requests it
and provides credentials/keys.

---

## Step 5: Produce the prototype outputs

Deliver all of the following with the prototype artifact.

### Output 1: The working prototype

A complete, runnable artifact. State clearly at the top:
- Prototype type
- Hypothesis being tested
- Mocked areas
- How to run it (if applicable)

### Output 2: Setup and usage instructions

Short (3–5 steps). Include:
- How to open or run the prototype
- Any required environment (browser, Node, etc.)
- Which scenario the tester should follow first

### Output 3: What this prototype tests

A plain-language summary (3–5 sentences) of:
- What user behaviour or assumption is being validated
- What a successful test looks like
- What a failed test looks like

### Output 4: Requirements-to-prototype mapping

A table linking PRD requirements or acceptance criteria to prototype behaviour.

| Requirement / AC | Prototype behaviour | Mocked / Live |
|---|---|---|
| AC-1: User can submit request | Submit button advances to confirmation screen | Live |
| AC-2: System validates input | Inline error shown on empty required fields | Live |
| AC-3: Email confirmation sent | Alert shown — no real email sent | Mocked |

### Output 5: Known limitations and mocked areas

A bulleted list of everything the prototype does not do, simulate accurately, or represent
faithfully. Be explicit. Testers should not discover surprises mid-session.

Examples:
- Authentication is skipped — prototype opens directly to the main flow
- API responses are hardcoded — no real data processing occurs
- Error states show a generic message — real error handling not implemented
- Mobile responsiveness not tested on iOS — only desktop Chrome

### Output 6: Suggested user testing tasks

Write 3–5 tasks in the format a test facilitator would actually read aloud:

> "You've just received an invitation to [scenario context]. Please [specific task].
> Think out loud as you go."

Tasks must:
- Avoid telling the user what to click or look for
- Be scenario-based, not feature-based
- Correspond to the primary flow in the prototype

### Output 7: Questions to ask users during testing

Write 5–8 debrief questions targeting the hypothesis being tested:

**During the task:**
- "What would you expect to happen next?"
- "What's going through your mind right now?"

**After the task:**
- "What felt unclear or confusing?"
- "Did the result match what you expected?"
- Questions specific to the assumption being tested

---

## Prototype quality checklist

Before delivering the prototype, verify:

- [ ] Every button and link does something (no dead UI)
- [ ] Primary flow is completable start to finish without breaking
- [ ] All mocked areas are clearly labelled
- [ ] Realistic data is used (no Lorem ipsum, no "Test User")
- [ ] The prototype opens without a build step if HTML/CSS/JS
- [ ] The hypothesis being tested is stated in the prototype itself
- [ ] Output 1–7 are all present

---

## Principles

**The smallest thing that tests the thing.** Do not build features that aren't in the test
flow. Scope ruthlessly. Every screen that isn't tested is a screen that delayed the learning.

**Mock confidently, label clearly.** Mocking is not cutting corners — it's the point.
A prototype that clearly marks its simulation boundaries is more trustworthy than one that
hides them. PMs, facilitators, and stakeholders deserve to know what's real.

**Realistic data changes everything.** Users respond differently to "Sarah Chen, 3 invoices
overdue" than "User 1, test data". Use names, numbers, and content that feel authentic to
the target user's world.

**Testability over aesthetics.** A prototype with 60% of the visual polish but 100% of the
interactive flow is better than a beautiful mock no one can click through. Prioritise
navigability.

**Make the hypothesis visible.** The riskiest assumption being tested should be stated
somewhere in the prototype header, a sticky label, or setup instructions. Everyone in the
test session should know what question they're trying to answer.

**The PM owns the hypothesis. You own the artifact.** Never substitute your judgment for
the PM's about what to test or what fidelity is sufficient. Surface options, state tradeoffs,
build what's asked.

---

## Failure modes to avoid

| Anti-pattern | Problem | Correct behaviour |
|---|---|---|
| Building the full product | Over-engineered, too slow, tests the wrong things | Scope to one flow |
| No mocked data labels | Testers don't know what's real | Label everything mocked |
| Dead UI elements | Testers get stuck, lose trust in prototype | Every control does something |
| Abstract testing tasks | Testers don't know what to do | Write scenario-based tasks |
| Missing limitations doc | Stakeholders treat prototype as spec | Always deliver Output 5 |
| Perfect visual fidelity | Tester feedback focuses on colours not flows | Embrace intentional roughness |
| No stated hypothesis | Prototype generates data but no insight | State hypothesis in Output 3 |

---

## Reference files

- `references/prototype-patterns.md` — Examples and code templates for each prototype type
- `references/testing-task-writing.md` — Guide to writing effective usability testing tasks
- `assets/mock-data-examples.md` — Sample realistic mocked data for common product domains
