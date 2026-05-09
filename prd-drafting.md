---
name: prd-drafting
description: >
  Use this skill whenever a PM needs to write, draft, or review a Product Requirements Document.
  Triggers on: "write a PRD", "draft requirements", "turn this problem into a PRD", "create user
  stories", "write acceptance criteria", "define the requirements for", or any request to move
  from a prioritized problem or insight into a structured spec. Also triggers when a PM shares
  a prioritized problem list, discovery output, or business goal and wants to define what to build.
  Use even if the input is rough — incomplete inputs are surfaced as ambiguities, not blockers.
  After drafting the PRD, always fill the AI-Ready Service Definition Template in assets/.
---

# PRD Drafting Skill

## Purpose

Transform a prioritized problem, discovery evidence, and business context into a structured, complete PRD. Surface ambiguities, flag missing evidence, and identify edge cases the PM may not have considered. After completing the PRD, fill the AI-Ready Service Definition Template.

The PM defines what success looks like. Your job is to make the requirements precise, testable, and ready for engineering and design to act on.

---

## Inputs accepted

Accept any combination of the following. Work with what is provided — flag missing inputs as ambiguities rather than blocking output.

- Prioritized problem list (ideally from the prioritization-customer-problems skill)
- Customer discovery insights or research synthesis
- Business goals, OKRs, or revenue targets
- Technical constraints or platform limitations from engineering
- Stakeholder input or executive mandates
- Competitive context or market requirements
- Existing PRDs or related specs (for consistency reference)

---

## Step 1: Draft the PRD

Produce the PRD in the following structure. Every section is required. If a section cannot be completed from the available input, write a clearly labelled placeholder and explain what information is needed to fill it.

---

### 1. Problem statement

One paragraph (4–6 sentences) that answers:
- What problem exists, for whom, and in what context?
- Why does it matter now — what is the cost of not solving it?
- What evidence supports this problem definition? (cite the discovery source)
- What does "solved" look like at a high level?

Do not describe the solution here. Problem only.

---

### 2. Target users

For each distinct user type affected:
- **User type**: Role or segment name
- **Context**: When and where they encounter this problem
- **Primary goal**: What they are trying to accomplish
- **Pain today**: How the current situation fails them
- **Priority**: Primary / Secondary (primary users drive requirements; secondary users inform edge cases)

Pull from the discovery insight report or prioritization output if available.

---

### 3. Desired outcomes

List 3–6 outcomes the solution must achieve, written from the user's perspective:
- "Users can [do X] without [current friction]"
- "Users know [Y] at the point they need it"
- "The system enables [Z] without requiring [manual step]"

These are not features. They are the conditions that must be true for the problem to be considered solved.

---

### 4. User stories

Write one user story per distinct job or workflow step. Format:

> **As a** [user type], **I want to** [action], **so that** [outcome].

For each story, add:
- **Priority**: Must-have / Should-have / Could-have (MoSCoW)
- **Notes**: Any constraint, edge case, or dependency specific to this story

Group stories by user type if there are multiple.

---

### 5. Acceptance criteria

For each Must-have user story, write acceptance criteria using Given/When/Then format:

> **Given** [precondition], **When** [action], **Then** [expected result].

Write at least 2 criteria per Must-have story — one for the happy path, one for a failure or edge case. Criteria must be testable — avoid words like "fast", "easy", or "intuitive" unless a specific measurable threshold is defined.

---

### 6. Edge cases and failure modes

List scenarios the system must handle that are not covered by the happy-path acceptance criteria. For each:
- **Scenario**: What unusual or adverse condition occurs
- **Expected behaviour**: What the system should do
- **Risk if unhandled**: Low / Medium / High

Include at minimum: empty states, error states, permission edge cases, and high-volume or concurrent-use scenarios relevant to this problem.

---

### 7. Dependencies

List anything this feature depends on that is outside the PM's direct control:
- **Internal dependencies**: Other teams, systems, or features that must exist first
- **External dependencies**: Third-party services, data sources, or APIs
- **Sequencing constraint**: Does this need to ship before or after something else?

Flag any dependency that represents a risk to delivery.

---

### 8. Non-goals

Explicitly state what this PRD does not cover. For each non-goal:
- Name the thing being excluded
- Briefly explain why (out of scope for this cycle, different team, insufficient evidence, future consideration)

Non-goals are as important as goals — they prevent scope creep and set stakeholder expectations.

---

### 9. Assumptions

List the assumptions this PRD is built on. For each:
- **Assumption**: State it clearly
- **Type**: Input / Domain / Operational / Constraint
- **Confidence**: High / Medium / Low
- **Validation needed**: What would confirm or invalidate this assumption, and by when?

---

### 10. Success metrics

Define how the PM will know the problem is solved. For each metric:
- **Metric**: What is being measured
- **Baseline**: Current state (if known)
- **Target**: What "success" looks like, with a timeframe
- **Measurement method**: How it will be tracked (event, query, survey, etc.)
- **Leading or lagging**: Leading indicators (early signal) vs lagging indicators (confirmed outcome)

Include at least one leading and one lagging metric. Flag any metric where baseline data does not yet exist.

---

### 11. Decision log

Track key decisions made during PRD drafting. Start with any decisions implied by the inputs provided.

| Decision | Options considered | Rationale | Date | Owner |
|---|---|---|---|---|

Add a row for every significant scope, design, or priority choice made in this PRD. This log is the PM's audit trail.

---

### 12. Ambiguities and missing evidence

List every open question, gap in evidence, or unresolved decision that could affect implementation. For each:
- **Ambiguity**: State the question clearly
- **Impact if unresolved**: What breaks or becomes risky?
- **Recommended action**: Who should answer this, and by when?
- **Priority**: Resolve before build / Can be resolved during build / Post-launch

This section should never be empty on a first draft. If everything seems clear, look harder.

---

## Step 2: Fill the AI-Ready Service Definition Template

After completing the PRD, fill the template at `assets/AI-Ready_Service_Definition_Template.xlsx`.

The template has two sheets: **Spoke Definition** and **Assumptions & Constraints**.

### Spoke Definition sheet — field mapping

| Template field | Where to pull it from in the PRD |
|---|---|
| Service Name | Feature or problem name from the problem statement |
| Service Type | Infer from solution type: Info Page / Data Selection / Predictive Tool |
| High-Level Description | Condense the problem statement (2–3 sentences, capability summary, no mechanics) |
| Foundational Capabilities | Derived from Must-have user stories — list as discrete capability statements |
| Expected Tools Called | From dependencies — list internal systems, APIs, or data sources |
| System Behavior (Conceptual) | Write as a brief flow: Input → Process → Output, max 1 line |
| Customer Intent / Context | Pull from Target Users — what they are trying to achieve and in what context |
| Questions Answered | Rewrite user stories as the literal questions a user would ask |
| Customer Inputs | What the user provides — from user stories and acceptance criteria |
| System Outputs | What the system returns — from desired outcomes and acceptance criteria |
| Required Capabilities or External Dependencies | From the Dependencies section |
| Likely Errors | From Edge Cases and Failure Modes — list as brief failure mode names |
| Failure Impact | From edge case risk ratings — translate to plain language consequence |
| Error Detectability | Assess per failure mode: Low (error looks plausible) / Medium / High (obvious) |
| Owner / Submitter | Leave blank for PM to fill |

### Assumptions & Constraints sheet — field mapping

| Template field | Where to pull it from in the PRD |
|---|---|
| Input Assumptions | From PRD Assumptions where Type = Input |
| Domain Assumptions | From PRD Assumptions where Type = Domain |
| Operational Constraints | From PRD Assumptions where Type = Operational or Constraint |
| Out-of-Scope | From Non-Goals section |
| Known Limitations | From Ambiguities section — items flagged as "can be resolved post-launch" or unresolvable |

Use openpyxl to write values into the `Product Team Entry` column of the Spoke Definition sheet and the `Description` column of Assumptions & Constraints. Preserve all existing formatting, column widths, and structure — do not reformat the template. Save to `/mnt/user-data/outputs/prd-drafting/` with the filename format `PRD_[FeatureName]_ServiceDefinition.xlsx`.

---

## Drafting principles

**Write requirements, not solutions.** The PRD defines what must be true — not how engineering should build it. Avoid implementation language unless a constraint genuinely requires it.

**Make every acceptance criterion testable.** If a QA engineer cannot write a test case from the criterion, rewrite it until they can.

**Ambiguity is a first-class output.** A PRD that surfaces 8 real ambiguities is more valuable than one that papers over them. The PM resolves ambiguities; the skill surfaces them.

**Flag thin evidence explicitly.** If a user story or requirement is based on limited discovery data, note it. Requirements built on weak evidence should be marked for validation before engineering begins.

**Non-goals protect the PM.** Every excluded scope item that is not written down will come back as a stakeholder expectation. Be thorough.

**Decision log from day one.** Every scope choice, priority call, or tradeoff made during drafting should be logged. The PM should be able to explain any decision in a review.

---

## Formatting rules

- Use the section structure and numbering above exactly
- Acceptance criteria: always Given/When/Then, never prose
- User stories: always As a / I want to / So that format
- Tables for: success metrics, dependencies, decision log, edge cases
- Total PRD length: 1,000–2,500 words depending on problem complexity
- Template fill: always produce the filled .xlsx as a separate output file
