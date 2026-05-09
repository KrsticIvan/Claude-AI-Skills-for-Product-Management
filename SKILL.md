---
name: user-testing
description: >
  Use this skill whenever a PM or product team needs to plan, run, or synthesize user testing,
  usability studies, or concept validation sessions. Triggers on: "help me run user testing",
  "write an interview guide", "synthesize usability findings", "map feedback to requirements",
  "summarize test results", "what did users think of the prototype", "did our concept pass
  validation", "analyze test session notes", "create a test script", "does this meet our
  acceptance criteria", "what should we change in the PRD", "did users understand the flow",
  "usability report", "validation report", or any request to extract insight from raw user
  feedback and connect it to product requirements. Also triggers when someone pastes session
  notes, transcripts, or observation logs from a test and wants structured analysis.
  Use even with partial inputs — a single session note still generates useful findings.
---

# User Testing Skill

## Purpose

Plan, structure, and synthesize user testing to validate whether a concept, prototype, or
workflow actually addresses the user problem — and to produce a report the PM can act on
immediately, including evidence-backed PRD change recommendations.

This skill covers the full arc:

1. **Pre-test** — Generate a test script and interview guide from inputs
2. **Synthesis** — Analyze raw session notes, transcripts, or observation logs
3. **Mapping** — Connect feedback to acceptance criteria and requirements
4. **Reporting** — Output a usability and validation report with PRD change recommendations

You may enter at any stage. Work with what is provided.

---

## Inputs accepted

Accept any combination of the following. Work with what is available — missing inputs are noted
as gaps, never blockers.

| Input | How it's used |
|---|---|
| Prototype or feature description | Defines what is being tested |
| PRD or user stories | Source of acceptance criteria and requirements to map against |
| Acceptance criteria | Determines what the test must confirm or refute |
| Target user description | Shapes screener criteria and task framing |
| Hypotheses or assumptions to validate | Focuses the test design on what matters most |
| Raw session notes or transcripts | Primary source for synthesis |
| Observation logs | Supplementary behavioral data |
| Survey or NPS responses | Quantitative signal to pair with qualitative findings |
| Previous test reports | Context for longitudinal comparison |

---

## Step 1: Clarify what is needed

Before producing output, identify which stage(s) to execute:

- **Pre-test only** → user needs a test script or interview guide, not yet having run sessions
- **Synthesis only** → user has session notes/transcripts and needs findings extracted
- **Full flow** → user wants pre-test materials AND post-test synthesis/report

If it is not obvious from context, ask one clarifying question: "Do you need a test script,
synthesis of sessions you've already run, or both?"

Also confirm: are acceptance criteria available? If yes, activate **Step 4: AC Mapping**.
If no, note this and produce a findings report without an AC map.

---

## Step 2: Pre-test — Generate test script and interview guide

Produce these when the user needs to run sessions (or when session design looks incomplete).

### 2a. Screener criteria

Based on the target user description, list 3–6 screener criteria a recruiter could use.
Format: simple qualifying/disqualifying statements a recruiter can check.

Example:
```
INCLUDE: Uses project management software at least weekly
INCLUDE: Has created or assigned tasks for a team of 3+ people
EXCLUDE: Works in software engineering or product management
EXCLUDE: Works at a company with fewer than 10 employees
```

### 2b. Session structure

Recommend a session structure appropriate to what is being tested:

| Session type | When to use | Typical structure |
|---|---|---|
| Concept test | Early-stage idea, no working prototype | Intro → Problem framing → Concept reveal → Reaction probing → Wrap |
| Task-based usability | Working prototype or live product | Intro → Warm-up tasks → Core tasks → Debrief |
| Jobs-to-be-done interview | Understanding existing behavior before building | Intro → Timeline walk → Trigger probing → Outcome probing → Wrap |
| Validation interview | Post-prototype, testing specific hypotheses | Intro → Context calibration → Hypothesis probing → AC verification → Wrap |

State which type is most appropriate given the inputs and why.

### 2c. Interview guide

Write a full interview guide with:

**Introduction script** (verbatim, ~100 words)
Cover: purpose of session, no right/wrong answers, thinking aloud encouraged, recording consent,
no performance pressure.

**Warm-up questions** (3–5 questions)
Open-ended, build rapport, calibrate user context. Do not reveal the concept yet.

**Core task or probing section**
For task-based tests: write 3–6 tasks in second-person present tense ("You need to...")
with clear success criteria the observer can track.

For concept/validation tests: write 5–10 probing questions that move from open
("What's your first reaction?") to specific ("Where would you look to do X?").

**Hypothesis probing** (if hypotheses provided)
For each hypothesis: write 1–2 questions that would surface confirming or disconfirming evidence.
Label them clearly: `[HYP-1]`, `[HYP-2]`, etc.

**Wrap-up questions** (3–5 questions)
Summary impressions, likelihood to use, what they'd change, anything they want to add.

**Observer note-taking template**
A simple table or tick-sheet the observer fills in per participant:

```
Participant ID: ___    Date: ___    Moderator: ___

Task / Question | Observed behavior | Quote (verbatim) | Pass / Fail / Partial | Severity
```

---

## Step 3: Synthesis — Analyze session notes and transcripts

When raw session data is provided, produce structured findings.

### 3a. Evidence inventory

Before synthesizing, note:
- Number of sessions provided
- Format of data (notes, transcript, video summary, etc.)
- Any sessions with unusually sparse data (flag as low-confidence)

### 3b. Finding extraction

Read all session data and extract every distinct observation: a behavior, quote, reaction,
confusion, failure, success, or objection that a user exhibited.

Tag each observation:
- **Type**: Confusion / Failure / Objection / Delight / Workaround / Suggestion / Success
- **Frequency**: how many participants exhibited this (N=X out of Y)
- **Severity** (for usability issues): Critical / High / Medium / Low
  - Critical: blocked task completion
  - High: caused frustration or significant deviation; reduced confidence
  - Medium: caused hesitation or a wrong first attempt; user recovered
  - Low: minor friction; user noticed but continued

### 3c. Pattern clustering

Group related observations into themes. Each theme is a named finding:

```
FINDING [#]: [Short descriptive name]
Type: [Usability issue / Validation signal / Objection / Positive signal]
Frequency: N=X/Y participants
Severity: [Critical / High / Medium / Low / N/A]
Description: [2–3 sentences describing what was observed across participants]
Supporting quotes:
  - "[Verbatim quote]" — P[#]
  - "[Verbatim quote]" — P[#]
Evidence strength: [Strong / Moderate / Weak]
  Strong = 3+ participants, consistent behavior, unprompted
  Moderate = 2 participants, or 3+ but only when prompted
  Weak = 1 participant, or inconsistent across sessions
```

### 3d. Recurring objections

List any objection, concern, or resistance that appeared in 2+ sessions.
Format: objection statement → frequency → whether it was resolved in session or remained open.

---

## Step 4: Map findings to acceptance criteria

Only execute this step if acceptance criteria are available.

For each acceptance criterion in the PRD, evaluate it against the session findings:

```
AC [#]: [Acceptance criterion text]
Status: CONFIRMED / REFUTED / INCONCLUSIVE / NOT TESTED
Evidence: [Finding #s and quotes that support this status]
Confidence: High / Medium / Low
Notes: [Any nuance — e.g., confirmed for power users but not novices]
```

Status definitions:
- **CONFIRMED**: At least 3 participants demonstrated the criterion was met; no contradicting evidence
- **REFUTED**: At least 2 participants failed to meet the criterion, or expressed direct contradiction
- **INCONCLUSIVE**: Mixed evidence across participants; cannot call it either way
- **NOT TESTED**: The test did not surface data relevant to this criterion

Produce a summary table at the end of this section:

| AC # | Summary | Status | Confidence |
|------|---------|--------|------------|
| AC-1 | Users can complete checkout without help | CONFIRMED | High |
| AC-2 | Users understand pricing tier differences | REFUTED | High |
| ... | | | |

---

## Step 5: PRD change recommendations

For every REFUTED or INCONCLUSIVE acceptance criterion, and for every Critical or High
severity finding without an existing AC, produce a concrete PRD change recommendation:

```
REC [#]: [Short title]
Trigger: [Finding #s or AC #s that motivate this change]
Recommended PRD change:
  Section affected: [PRD section name]
  Type of change: [Add / Modify / Remove / Clarify]
  Proposed text: [Specific language to add or replace — be concrete]
Priority: [Must-fix before launch / Should-fix before launch / Defer to v2]
Evidence basis: [1–2 sentences on the user evidence supporting this change]
```

---

## Step 6: Produce the usability and validation report

Assemble all outputs into this report structure:

---

### User Testing Report: [Feature / Concept Name]

**Test summary**
- Sessions conducted: N
- Participant profile: [Brief description of who was tested]
- Prototype / concept tested: [1 sentence]
- Test type: [Concept test / Task-based usability / Validation / Jobs-to-be-done]
- Date range: [if known]

**Top-line verdict** (3–5 sentences)
Did the concept address the user problem? What is the strongest signal from the sessions?
What is the most important thing the team needs to know before proceeding?

**Validation status**
- Hypothesis [#]: VALIDATED / REFUTED / INCONCLUSIVE (repeat for each)
- Overall readiness: Ready to build / Needs iteration / Concept requires rethink

---

#### What worked

List 3–7 positive findings with frequency and evidence strength. Be specific — not "users liked
the design" but "7/8 participants completed the core task without prompting (Finding #3)".

#### What failed

List all Critical and High severity findings with AC mapping, frequency, and severity.
Ordered by severity.

#### Open questions

List unresolved questions the test surfaced but did not answer. These are candidates for
the next round of research or a targeted follow-up study.

#### Evidence quality summary

| Finding # | Description | Frequency | Severity | Evidence strength |
|-----------|-------------|-----------|----------|-------------------|
| F-1 | ... | N=5/8 | High | Strong |
| ... | | | | |

---

#### AC Status Summary

[Output from Step 4 summary table]

---

#### Recommended PRD changes

[Output from Step 5, ordered by Priority]

---

#### Recommended next step

One clear action the team should take based on this report. Options:
- Proceed to engineering with the noted PRD changes
- Run a second round of testing on the refuted or inconclusive criteria
- Return to PRD and rework the affected user stories before building
- Escalate a critical finding to stakeholders before proceeding

---

## Behaviour rules

**Do not soften findings.** A finding that says "some users had minor trouble" when 6/8
participants failed the task is a misrepresentation. Use the frequency data.

**Do not invent quotes.** Only use verbatim text that appears in the provided session data.
If the input is sparse, note that quotes are paraphrased and flag low evidence confidence.

**Do not over-interpret weak evidence.** A finding from 1 participant is a signal, not a
pattern. Label it Weak. Do not recommend PRD changes from a single data point unless the
severity is Critical.

**Do not collapse nuanced findings.** If behavior differed between user segments (e.g.,
new users vs power users, mobile vs desktop), preserve that distinction in the finding.
Collapsing it loses signal.

**Surface the open questions.** A test rarely answers every question. Explicitly listing
what remains unresolved is as valuable as confirming what works.

**Adapt depth to input.** 2 session notes → shorter synthesis with explicit low-confidence
flags. 10 transcripts → full pattern analysis. Never fabricate findings to fill out a report.

---

## Integration with other PM skills

This skill works in sequence with the other PM skills:

```
prd-drafting → prototype-generation → [user-testing] → prd-review → prd-drafting (revise)
```

- If acceptance criteria are missing, reference **prd-drafting** to produce them before testing
- If a prototype does not yet exist, reference **prototype-generation** to build one
- After this report, use **prd-review** to validate the PRD changes before engineering kickoff
- If the concept needs a full rethink, return to **prd-drafting** with the findings as input
