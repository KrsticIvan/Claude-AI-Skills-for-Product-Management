---
name: customer-discovery-research
description: >
  Use this skill whenever a PM or product team needs to make sense of raw customer research.
  Triggers on: interview notes, survey responses, support tickets, sales call transcripts, 
  customer success notes, analytics exports, NPS comments, or any mix of unstructured 
  customer input. Also triggers when someone says "synthesize research", "what are users 
  telling us", "summarize feedback", "find the patterns in these notes", or "turn this into 
  insights". Even if the user only shares a few notes or a single source, use this skill — 
  partial data still deserves structured synthesis. The goal is to transform raw, messy 
  input into a structured insight report a PM can act on.
---

# Customer Discovery & Research Synthesis

## Purpose

Transform raw, unstructured customer research into a structured insight report. The PM's job is to decide which insights matter strategically — your job is to make sure they have the clearest possible picture to decide from.

## Inputs accepted

Accept any combination of the following. Never ask the user to reformat their data first.

- Interview notes (verbatim or summarised)
- Survey responses (open-ended or structured)
- Support tickets or helpdesk threads
- Sales call transcripts or CRM notes
- Customer success check-in notes
- Analytics events or funnel data (described in text)
- NPS or CSAT comments
- Market signals (competitor reviews, social mentions, analyst notes)

If the input source is unclear, infer it from context. Do not ask the user to label their data.

## Output: Synthesized Insight Report

Produce the report in the following structure. Use every section — if a section has no data, say so briefly rather than omitting it.

---

### 1. Summary (3–5 sentences)
What is this research about, who participated, and what is the single most important thing the data is saying? Write this as if briefing a VP who has 30 seconds.

---

### 2. Validated pain points

For each pain point:
- **Pain point**: One clear sentence naming the problem
- **Evidence**: Number of sources or mentions (e.g. "7 of 12 interviewees", "mentioned in 4 support tickets")
- **Severity**: Low / Medium / High — based on emotional language, frequency, and workarounds described
- **Representative quote**: One verbatim or near-verbatim quote that best captures it
- **User segment**: Which user type or persona this pain primarily affects (if determinable)

Order pain points from most to least evidenced.

---

### 3. Jobs to be Done (JTBD)

For each distinct job identified in the data:
- **Job statement**: "When [situation], I want to [motivation], so I can [outcome]" — write in the user's voice
- **Job type**: Functional / Emotional / Social
- **Importance**: Low / Medium / High — based on how often users mention it and how much effort they invest in accomplishing it
- **How well it is currently served**: Not served / Poorly served / Partially served / Well served
- **Opportunity signal**: Flag as high opportunity if importance is High and current serving is Poor or Partial

Order by opportunity signal (highest first).

If the data does not contain enough signal to write proper job statements, list candidate jobs as hypotheses and flag them for validation.

---

### 4. Current solution landscape

For each current solution or workaround identified:

- **Solution**: What users are doing today (tool, process, or workaround)
- **User segment**: Who uses it
- **Importance of the job it serves**: Low / Medium / High
- **Satisfaction with current solution**: Rate 1–5, where 1 = deeply frustrated, 5 = fully satisfied. Base this on language used (e.g. "it works fine" ≠ "it's the best we have")
- **Opportunity gap**: Importance minus satisfaction — higher gap = stronger opportunity
- **Barrier to change**: What would stop this user from switching? (e.g. switching cost, habit, lack of awareness, contractual lock-in, fear of disruption)

Include a one-line summary of where the biggest opportunity gap sits across all solutions reviewed.

---

### 5. Behavioral patterns

List 3–6 recurring behaviors, workarounds, or decision patterns observed across sources. Each pattern should be:
- Described in one sentence
- Tied to at least 2 data points
- Labelled with the segment it applies to (if specific)

---

### 6. User segments identified

If the data reveals distinct user types with meaningfully different needs, describe each:
- Segment name (descriptive, not a persona label)
- Defining characteristics (role, context, goal, or constraint)
- Their dominant pain point(s)
- How they differ from other segments

If the data is too thin to segment reliably, say so.

---

### 7. Draft personas (optional — include only if 3+ interviews or rich qualitative data exists)

For each persona:
- Name and role archetype
- Primary goal
- Key frustrations
- How they currently cope (workarounds or alternatives)
- Quote that captures their mindset

Mark these clearly as **drafts** — they should be validated, not shipped.

---

### 8. Contradictions and tensions

Surface any findings that conflict with each other, or that contradict common assumptions. For example: users say they want X but behave in a way that suggests Y. Do not smooth these over — contradictions are often where the most valuable insight lives.

---

### 9. Confidence level

Rate the overall confidence in these findings:

| Factor | Assessment |
|---|---|
| Sample size | e.g. "12 interviews — adequate for qualitative themes" |
| Source diversity | e.g. "All enterprise segment — missing SMB perspective" |
| Recency | e.g. "Interviews conducted within last 30 days" |
| Consistency | e.g. "High — themes repeated across source types" |
| **Overall confidence** | Low / Medium / High |

---

### 10. Open questions

List 3–7 questions this research raises but does not answer. Phrase each as a testable hypothesis or a specific thing to learn next. Flag which are highest priority.

---

## Synthesis principles

Follow these when processing any input:

**Cluster before concluding.** Group raw data points into themes first, then derive the insight from the cluster — not the other way around. Never start with a conclusion and fit data to it.

**Preserve the user's voice.** Keep at least one direct quote per major pain point. Do not paraphrase away the emotion or specificity of what users said.

**Separate observation from interpretation.** State what users said or did, then separately state what that might mean. Use language like "this may indicate…" or "a possible explanation is…" for interpretations.

**Weight by recurrence, not recency.** A pain mentioned by one articulate user last week is weaker signal than the same pain mentioned by five users over three months, unless the context has clearly changed.

**Flag thin data honestly.** If a section cannot be completed reliably given the input, say so. A PM making decisions on thin data should know it is thin.

**Never invent.** Do not extrapolate beyond what the data supports. If a user segment or persona is not supported by the data, do not create one.

---

## Formatting rules

- Use the section structure above exactly — PMs will use these as a recurring template
- Bold pain point names and segment names for scannability
- Use tables for the confidence assessment
- Keep the summary under 100 words
- Total report length: aim for 600–1200 words depending on data richness
- If the input is very sparse (e.g. 3–5 short notes), produce a shorter version and note what additional data would strengthen it
