---
name: prioritization-customer-problems
description: >
  Use this skill whenever a PM needs to decide which customer problems are worth solving now.
  Triggers on: a list of candidate problems, features, or opportunities to compare and rank;
  requests to "prioritize", "score", "stack rank", "compare tradeoffs", or "build a roadmap";
  situations where a PM has insights from research and needs to decide what to work on next.
  Also triggers when someone shares a mix of strategic context (revenue goals, segment value,
  competitive pressure, roadmap commitments, technical constraints) alongside a problem list.
  Even with incomplete context, use this skill — missing inputs become explicit confidence
  penalties, not blockers. The PM makes the final call; this skill makes the tradeoffs visible.
---

# Prioritization of Customer Problems

## Purpose

Score and compare candidate customer problems so a PM can make a defensible, well-reasoned prioritization decision. Surface tradeoffs, expose weak evidence, and show what is being given up when a problem is chosen — or deprioritized.

The PM decides. Your job is to make the decision as clear and honest as possible.

## Inputs accepted

Accept any combination of the following. Work with what is provided; flag what is missing as a confidence penalty rather than blocking output.

- Customer insight report or research synthesis (ideally from the customer-discovery-research skill)
- List of candidate problems or opportunity areas (can be rough)
- Company strategy or OKRs
- Revenue goals or commercial targets
- Customer segment value or ICP definition
- Competitive context or market signals
- Current roadmap commitments or in-flight work
- Technical constraints or effort signals from engineering
- Stakeholder priorities or executive mandates

If none of the strategic context is provided, note it clearly and proceed with customer signal only — but flag that strategic fit scores will be low-confidence.

---

## Output: Prioritized Problem List

Produce the output in the following structure. Every section is required. If a section cannot be completed reliably, say so briefly and explain why.

---

### 1. Prioritization summary (3–5 sentences)

What problems rose to the top, why, and what is the most important tradeoff the PM is accepting by choosing them? Write this as a briefing for a leadership review — direct and opinionated, but grounded in the evidence below.

---

### 2. Scoring table

Score each candidate problem across all dimensions. Use a 1–5 scale for each factor unless stated otherwise. Present as a table.

| Problem | Impact | Frequency | Strategic fit | Revenue relevance | Urgency | Effort (inverse) | Confidence | Total | Rank |
|---|---|---|---|---|---|---|---|---|---|

**Factor definitions:**

- **Impact** (1–5): How significantly does solving this improve the user's life or workflow? Base on severity language in research, workaround complexity, and JTBD importance scores if available.
- **Frequency** (1–5): How many users are affected, how often? Base on recurrence counts from research. If no data, score 1 and flag.
- **Strategic fit** (1–5): How directly does solving this advance the company's stated strategy, OKRs, or ICP focus? If no strategy context provided, score 2 for all and flag.
- **Revenue relevance** (1–5): Does solving this unlock, protect, or expand revenue? Consider: expansion in high-value segments, churn risk, new market access, or sales blockers.
- **Urgency** (1–5): Is there a time constraint — competitive threat, contractual commitment, seasonal window, or regulatory deadline?
- **Effort** (inverse, 1–5): 5 = low effort, 1 = very high effort. Use engineering signals if provided; otherwise estimate based on problem scope and flag as uncertain.
- **Confidence** (1–5): How well-evidenced is this problem? 5 = validated by multiple sources with strong signal. 1 = single mention or assumption. Pull from the insight report's confidence level where available.
- **Total**: Sum of all scores. Do not weight factors unless the PM has provided weights — use equal weighting by default and note this.

Below the table, note if any factor was scored with low data and should be treated as provisional.

---

### 3. Rationale per problem

For each candidate problem, write 2–4 sentences explaining:
- Why it scored as it did
- What evidence drives the score (quote the insight report or data source)
- Any factor where the score is uncertain and why

Keep rationale factual. Do not advocate — surface the signal, let the PM judge.

---

### 4. Framework views (run at least 2)

Apply established prioritization frameworks to cross-check the scoring table. Use whichever frameworks fit the inputs best. Always include RICE or ICE if effort data is available.

**Available frameworks:**

- **RICE** (Reach × Impact × Confidence ÷ Effort): Best when effort estimates exist
- **ICE** (Impact × Confidence × Ease): Lighter version when effort is unknown
- **Opportunity scoring** (Importance − Satisfaction): Best when JTBD and satisfaction data exist from the insight report
- **Value vs. Effort 2×2**: Visual quadrant — plot each problem and describe which quadrant it falls in (Quick wins / Big bets / Fill-ins / Time sinks)
- **Strategic alignment matrix**: Map each problem against the company's top 2–3 strategic priorities and mark fit as High / Medium / Low / None

For each framework, state whether the ranking it produces agrees or disagrees with the scoring table, and why any disagreement exists.

---

### 5. Sensitivity analysis

Identify the 2–3 factors where a small change in score would most change the overall ranking. For each:
- State the factor and the problem it most affects
- Describe what would need to be true for the ranking to shift (e.g. "If engineering confirms this is a 2-week build rather than a quarter, Problem B moves from rank 4 to rank 1")
- Flag whether that information is worth gathering before committing

This section exists to show the PM where the decision is fragile and where more data would actually change the outcome.

---

### 6. Opportunity cost statement

For the top 2–3 ranked problems, state explicitly what is being deprioritized and what that means:
- Which lower-ranked problems are being set aside
- What user segment or use case goes unserved as a result
- What risk that creates (churn, competitive exposure, missed revenue)

Do not soften this. The PM needs to see the cost of the choice, not just the benefit.

---

### 7. Weak evidence flags

List any problems where the scoring is built on thin or unvalidated data. For each:
- Name the problem
- Identify which factor(s) are low-confidence
- Recommend the minimum validation needed before committing (e.g. "3 customer interviews", "engineering spike", "review churn data for this segment")

---

### 8. Recommended next step

One sentence per top-ranked problem: what should the PM do next to either validate the prioritization or begin scoping? This is not a roadmap — it is the single most useful next action.

---

## Scoring principles

**Equal weights by default.** Do not apply custom factor weights unless the PM has explicitly provided them. If weights are provided, show both the weighted and unweighted totals so the PM can see the effect.

**Penalize missing data explicitly.** A factor with no supporting evidence scores 1–2, not a generous middle score. Low-confidence scores must be visible in the table — do not hide uncertainty inside an average.

**Do not collapse tradeoffs.** A problem that scores high on impact but low on confidence is not the same as one that scores medium on both. Keep the factor-level detail visible.

**Never advocate.** Present what the data says. If asked "which should we pick?", redirect to the tradeoffs and ask the PM what they want to optimize for.

**Flag strategic assumptions.** If no strategy context is provided, note that strategic fit scores are assumptions and the PM should validate them against actual company priorities before using the table in a review.

---

## Formatting rules

- Scoring table must be a markdown table — never prose
- Framework views can be prose or tables depending on framework type; the 2×2 should be described in text if a visual is not possible
- Rationale per problem: use bold problem name, then prose — no sub-bullets
- Total report length: 800–1,500 words depending on number of candidate problems
- If fewer than 3 candidate problems are provided, note that prioritization is most useful with 4+ options and offer to help the PM identify more candidates
