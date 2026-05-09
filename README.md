# Claude-AI-Skills-for-Product-Management
Structured instruction sets that automate PM tasks in Claude -- covering discovery, prioritisation, PRD drafting, prototyping, and user testing.

What This Is
This repository contains a growing library of Claude AI Skills built for product managers. Each skill is a structured instruction set stored as a SKILL.md file. When placed in Claude's skills directory, it activates automatically when Claude detects a matching PM task -- producing consistent, high-quality outputs without manual prompting or lengthy prompt templates.
Skills encode the way we do things as a repeatable process. They reduce onboarding friction, ensure output quality is consistent across the team, and make AI assistance genuinely reliable for high-stakes PM deliverables.

The PM Job Landscape
A product manager's work spans eleven core Jobs to be Done, from early discovery through to post-launch iteration. This repository currently covers the first five.
#Job to be DoneSkill Available1Customer Discovery & ResearchYes2Problem PrioritizationYes3Problem Framing & PRD CreationYes4Experiment Design & PrototypingYes5Quick Testing & LearningYes6Design Collaboration & UX RefinementComing soon7Technical Scoping & FeasibilityComing soon8Delivery & Scope ManagementComing soon9QA & Acceptance TestingComing soon10Launch & Go-to-Market ReadinessComing soon11Post-Launch Analysis & IterationComing soon

Skills
01 -- Customer Discovery & Research
File: skills/user/customer-discovery-research/SKILL.md
Transforms raw, unstructured customer research into a structured insight report a PM can act on immediately. Accepts interview notes, survey responses, support tickets, sales transcripts, NPS comments, and analytics exports in any format.
Output: Prioritised pain points with evidence counts, Jobs to be Done, behavioural patterns, strategic opportunities, and representative quotes.
Trigger phrases: "synthesize research", "what are users telling us", "summarize feedback", "find patterns in these notes"

02 -- Prioritisation of Customer Problems
File: skills/user/prioritization-customer-problems/SKILL.md
Scores and stack-ranks candidate customer problems against a multi-factor framework covering customer impact, business value, strategic fit, and effort. Missing context is treated as a confidence penalty rather than a blocker -- uncertainty is made explicit, not hidden.
Output: Scored priority table, tradeoff analysis, opportunity narrative, and deprioritisation rationale.
Trigger phrases: "prioritize", "score", "stack rank", "compare tradeoffs", "build a roadmap", "what should we work on next"

03 -- PRD Drafting
File: skills/user/prd-drafting/SKILL.md
Turns a prioritised problem, discovery evidence, or business goal into a complete Product Requirements Document. Incomplete inputs are surfaced as flagged ambiguities rather than blockers. Also populates an AI-Ready Service Definition Template to support downstream implementation handoffs.
Output: Full PRD including problem statement, user stories, acceptance criteria, success metrics, edge cases, and open questions.
Trigger phrases: "write a PRD", "draft requirements", "create user stories", "write acceptance criteria", "define requirements for"

04 -- PRD Review
File: skills/user/prd-review/SKILL.md
Systematically audits an existing PRD across five failure modes: ambiguity, missing evidence, weak or absent metrics, untestable acceptance criteria, and unresolved assumptions. Every finding is categorised by severity and linked to a concrete fix recommendation.
Output: Structured critique with prioritised findings by severity, fix recommendations, and an engineering-readiness verdict.
Trigger phrases: "review my PRD", "critique this spec", "find gaps", "is this ready for engineering", "audit my requirements"

05 -- Prototype Generation
File: skills/user/prototype-generation/SKILL.md
Converts a PRD, user stories, or product concept into a working interactive prototype -- clickable demos, fake-door tests, and workflow simulations -- that can be tested with real users or stakeholders before engineering begins. Incomplete specs become clearly labelled placeholder areas, not blockers.
Output: Working interactive prototype (HTML/React), test tasks, known limitations, and suggested validation questions.
Trigger phrases: "build a prototype", "make this clickable", "create a demo", "turn this PRD into something I can test", "validate before we build"

06 -- User Testing
File: skills/user/user-testing/SKILL.md
Supports the full user testing lifecycle: generating test scripts and interview guides before sessions, synthesising raw session notes and transcripts after, and producing a structured validation report that maps findings directly to PRD requirements. Can be entered at any stage.
Output: Test script and interview guide (pre-test); usability report, requirement mapping, and PRD change recommendations (post-test).
Trigger phrases: "run user testing", "write an interview guide", "synthesize usability findings", "did users understand the flow", "usability report"

How Skills Chain Together
Skills are designed to feed into each other naturally, but each can also be used independently.
Customer Discovery & Research
        |
        v
Prioritisation of Customer Problems
        |
        v
PRD Drafting  <-->  PRD Review
        |
        v
Prototype Generation
        |
        v
User Testing
Output from one skill becomes natural input to the next. A full run through the chain takes a PM from raw research notes to a validated, tested product concept ready for engineering.

What Stays Human-Owned
Skills handle information processing and structure. The following decisions always remain with the PM:

Strategic bets -- choosing which market or user segment to focus on, and why now.
Prioritisation calls -- the final ranking of problems when tradeoffs involve values, politics, or incomplete data that a scoring model cannot resolve.
Success criteria -- deciding what good enough means for a given product bet and what metrics the team will live by.
Stakeholder alignment -- navigating organisational dynamics, managing expectations, and building buy-in.
Scope and trade-off judgments -- deciding what to cut, delay, or simplify when time and resources are constrained.
Ethical and commercial risk -- identifying where a product decision could harm users, create regulatory exposure, or damage trust.

Skills surface options, evidence, and structure. Accountability sits with the PM.

Repository Structure
skills/
  user/
    customer-discovery-research/
      SKILL.md
    prioritization-customer-problems/
      SKILL.md
    prd-drafting/
      SKILL.md
      assets/
    prd-review/
      SKILL.md
    prototype-generation/
      SKILL.md
      assets/
      references/
    user-testing/
      SKILL.md

Using a Skill
Skills activate automatically in Claude when the skill files are present in the configured skills directory. No additional setup is required beyond placing the SKILL.md file in the correct location.
To use a skill manually, paste the contents of the relevant SKILL.md into your Claude system prompt, or reference it in your project configuration.

Contributing
To add a new skill:

Create a new directory under skills/user/your-skill-name/
Add a SKILL.md following the structure of existing skills (purpose, inputs accepted, output format, step-by-step protocol)
Update this README with the new skill entry and mark the corresponding Job to be Done in the landscape table
Open a pull request with a short description of what the skill does and what triggered the need for it

May 2026
