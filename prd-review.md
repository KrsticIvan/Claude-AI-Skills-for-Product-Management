---
name: prd-review
description: >
  Use this skill whenever a PM or product team wants to review, critique, audit, stress-test,
  or get feedback on an existing PRD (Product Requirements Document) or spec.
  Triggers on: "review my PRD", "critique this spec", "what's wrong with this PRD",
  "find gaps in my requirements", "stress-test this PRD", "what am I missing",
  "is this PRD ready for engineering", "audit my requirements", "review this feature spec",
  or whenever someone pastes or uploads a PRD and wants analysis rather than drafting.
  Also triggers when someone says "check my acceptance criteria", "are my metrics good",
  "are there any ambiguities", "are my assumptions documented", or "is this ready for review".
  Use this skill even for partial PRDs, one-pagers, or rough specs — the review adapts to
  what is present. Do NOT use for writing or drafting a new PRD from scratch (use prd-drafting instead).
---

# PRD Review Skill

## Purpose

Systematically audit an existing PRD for the five failure modes that most often cause re-work,
engineering misalignment, or shipped features that miss the mark:

1. **Ambiguity** — requirements that can be interpreted more than one way
2. **Missing evidence** — claims or user stories not grounded in discovery
3. **Weak or absent metrics** — success criteria that are unmeasurable or missing baselines
4. **Unclear acceptance criteria** — criteria that a QA engineer cannot write a test for
5. **Unresolved assumptions** — beliefs the PRD depends on that have not been validated or documented

The output is a structured, prioritised critique the PM can act on immediately.

---

## Inputs accepted

- A full or partial PRD (pasted text, uploaded document, or linked content)
- A feature spec, one-pager, or brief
- An existing PRD being prepared for an engineering kickoff or design review
- A PRD that has already received stakeholder feedback and is being revised

Work with whatever is provided. A short or incomplete PRD generates a longer finding list — that is correct behaviour, not a failure.

---

## Review Protocol

Run all five lenses in sequence. For each finding, produce a structured entry (see output format below).
Do not summarise or soften findings. Surface them clearly. The PM decides what to act on.

---

### Lens 1 — Ambiguity Scan

Read every requirement, user story, and acceptance criterion looking for language that two engineers
could reasonably interpret differently.

**Flag when you find:**
- Vague quantifiers: "fast", "easy", "intuitive", "scalable", "simple", "seamless", "robust"
- Undefined scope: "users can manage X" — which users? which actions count as "manage"?
- Conditional requirements with unspecified triggers: "if needed", "where applicable", "as appropriate"
- Pronouns with ambiguous antecedents: "it", "they", "the system" when multiple referents exist
- Missing actor: a requirement that doesn't specify who does what
- Missing constraint: "users can upload files" — what types? what size limits?
- "And/or" in a single requirement (two requirements collapsed into one)
- Requirements written as UI solutions rather than outcomes ("there will be a dropdown" vs "users can select from X options")

For each finding: quote the ambiguous text, explain the two+ interpretations, and suggest a rewrite.

---

### Lens 2 — Evidence Audit

Every user story and desired outcome should be grounded in discovery. Check whether the PRD
cites evidence for the problems it claims to solve.

**Flag when you find:**
- User stories with no discovery source (interview, survey, analytics, support data)
- Problem statements that assert user pain without citing evidence
- Priority decisions (Must-have vs Should-have) that appear arbitrary
- Assumed user behaviour that contradicts common product patterns
- Claims about market size, frequency, or impact with no cited source
- User types defined without a link to research or persona data
- "We know users want X" with no evidence of how that is known

For each finding: identify the claim, note what evidence is missing, and suggest the discovery action
that would fill the gap (e.g., "interview 3 users in this segment", "run a query on event logs").

---

### Lens 3 — Metrics Quality Review

Success metrics must be specific, measurable, tied to a baseline, and linked to the outcomes the PRD claims to deliver.

**Flag when you find:**
- No success metrics section, or a section that is empty / TBD
- Metrics that measure output (feature shipped) rather than outcome (problem solved)
- Vanity metrics: page views, "engagement" without definition, DAU without context
- Missing baseline: a target with no current-state measurement to compare against
- Missing timeframe: "increase retention" with no window specified
- Missing measurement method: how will this metric be tracked?
- All lagging metrics and no leading indicators (or vice versa)
- Metrics disconnected from the stated problem — measuring something that wouldn't confirm the problem is solved
- Thresholds that are too vague to declare success: "improve NPS" vs "increase NPS by 5 points within 90 days"

For each finding: quote the metric or note its absence, explain the gap, and suggest a rewrite or addition.

---

### Lens 4 — Acceptance Criteria Audit

Acceptance criteria must be testable. A QA engineer who has never spoken to the PM should be able to
write a test case from each criterion without asking a question.

**Flag when you find:**
- Acceptance criteria written in prose rather than Given/When/Then (or equivalent structured format)
- Criteria with no failure/edge case — only happy path covered
- Criteria that use subjective language: "the UI looks correct", "loads quickly", "feels responsive"
- Criteria that describe implementation rather than behaviour: "uses Redis cache" vs "responds within 200ms"
- Must-have user stories with no acceptance criteria
- Acceptance criteria that test the wrong thing (tests the UI component, not the user outcome)
- Missing: empty state criteria, error state criteria, permission boundary criteria
- Criteria that combine multiple conditions in a single Then clause (should be split)
- Acceptance criteria that would pass even if the feature is broken (too loose)

For each finding: quote the criterion, explain why it is not testable, and provide a rewritten version.

---

### Lens 5 — Assumptions Inventory

Every PRD rests on assumptions. Unvalidated, undocumented assumptions are technical debt in the requirements layer.

**Flag when you find:**
- No assumptions section
- Assumptions listed but with no confidence level or validation plan
- Implicit assumptions the PRD depends on but has not stated:
  - User behaviour assumptions ("users will adopt this workflow")
  - Technical assumptions ("this API will be available and performant")
  - Business assumptions ("this segment will pay for this feature")
  - Data availability assumptions ("we have the data to power this")
  - Dependency assumptions ("Team X will deliver Y before we launch")
- Assumptions marked "High confidence" that appear to have no validation evidence
- Assumptions with "validation needed" but no owner or deadline assigned
- Launch decisions that implicitly assume a dependency is resolved (it isn't noted as a risk)

For each finding: state the implicit or weak assumption, identify its type (Input / Domain / Operational / Constraint), rate its risk if wrong (Low / Medium / High), and suggest a validation action.

---

## Output Format

Produce the review in this exact structure:

---

### PRD Review: [Feature or PRD name]

**Review summary**
One paragraph (3–5 sentences): overall assessment of PRD readiness, the two most critical issue categories,
and a recommended next action before engineering kickoff.

**Readiness rating**: Not ready / Needs work / Ready with caveats / Ready
- Not ready: fundamental sections missing, or critical ambiguities that would block engineering
- Needs work: reviewable but requires resolution of several high-priority findings before kickoff
- Ready with caveats: minor gaps; can proceed with documented risks
- Ready: no blocking findings; PRD is complete and testable

---

### Findings

Present findings grouped by lens. Within each lens, order by severity: **Critical → High → Medium → Low**.

For each finding:

```
[LENS] [SEVERITY] Finding #N
Location: [Section name and quoted text, or "Missing — not present"]
Issue: [1–2 sentences explaining the problem]
Risk if unresolved: [What goes wrong during build, test, or launch]
Recommended fix: [Specific, actionable rewrite or addition]
```

Severity definitions:
- **Critical**: Would cause engineering to build the wrong thing, or block QA from signing off
- **High**: Creates significant re-work risk or stakeholder misalignment
- **Medium**: Reduces confidence in the requirement; should be resolved before kickoff
- **Low**: Minor polish; acceptable to defer but worth logging

---

### Finding summary table

| # | Lens | Severity | Location | One-line summary |
|---|------|----------|----------|------------------|
| 1 | Ambiguity | Critical | Section 5, AC #2 | "Fast" is undefined — no latency threshold |
| ... | | | | |

---

### Top 3 actions before engineering kickoff

List the three highest-priority fixes the PM should make before handing to engineering.
Be specific: "Rewrite acceptance criteria for user story 3 using Given/When/Then with a defined error state"
is better than "improve acceptance criteria".

---

## Behaviour rules

**Do not soften findings.** A PRD review that says "this is mostly good, a few small things" when there
are 8 critical ambiguities fails the PM. Be direct.

**Do not rewrite the PRD.** Provide the rewrite only for the specific finding — not the whole section.
The PM owns the document.

**Do not invent requirements.** If something is missing, flag it as missing. Do not assume what the
PM intended and fill it in silently.

**Surface every finding even if the list is long.** A 20-finding review on a weak PRD is correct
and useful. Do not suppress findings to keep the output short.

**Acknowledge what is working.** After the finding table, optionally add a brief "Strengths" note
(2–4 bullet points) for sections that are genuinely well-written. This helps the PM calibrate
which patterns to carry forward.

**Adapt depth to input length.** A 300-word one-pager gets a proportional review. A 3,000-word
full PRD gets exhaustive coverage. Adjust finding count to the complexity of what is present,
not to a fixed target.

---

## When the PRD is very short or informal

If the input is a one-pager, bullet list, or draft with major sections missing:
1. Note upfront which standard PRD sections are absent (this is itself a finding category)
2. Apply all five lenses to what is present
3. Append a "Missing sections" block listing what would need to be added before the document
   could be considered a reviewable PRD — reference the prd-drafting skill for those sections

---

## Integration with prd-drafting skill

If the PM wants to fix the PRD after this review, suggest using the prd-drafting skill to
rewrite the affected sections. The two skills are designed to work in sequence:
prd-drafting produces → prd-review critiques → prd-drafting revises.
