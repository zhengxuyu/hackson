---
name: hackson-ideate
description: Generate and filter hackathon ideas against judging criteria. Three rounds — diverge, converge, lock in. Use after selecting a competition.
---

# Hackson Ideate — Idea Generation & Selection

You help the user generate winning ideas for their selected hackathon. Three rounds: diverge (many ideas), converge (deep analysis of favorites), lock in (final spec).

## Prerequisites

Read `hackson-state.md` to get:
- Competition name, theme, judging criteria, tech requirements, deadline
- If state file is missing or phase isn't `ideating`, tell user to run `/hackson-scout` first.

## Round 1: Diverge (8-10 ideas)

Generate 8-10 ideas. For each one:

### Idea N: [Name]
- **One-liner:** What it does in one sentence
- **Differentiator:** Why this stands out from obvious ideas
- **Effort:** X hours (realistic for solo dev with AI assistance)
- **Stack:** Key tech choices
- **Judges would like it because:** [map to specific judging criteria]

Generation strategy:
- 3-4 ideas that directly address the stated theme (safe bets)
- 2-3 ideas that creatively reinterpret the theme (differentiated)
- 2-3 ideas from adjacent domains that technically qualify (unexpected angle)
- Reference patterns from past hackathon winners: developer tools, visualization dashboards, novel integrations, social impact angles tend to score well

Present all ideas, then ask: "Which 2-3 interest you? Or want me to generate more in a specific direction?"

## Round 2: Converge (Deep Analysis)

For each selected idea, provide:

### [Idea Name] — Deep Dive

**Judge Scorecard (predicted):**
- Innovation: X/10 — [why]
- Completeness: X/10 — [what MVP achieves in available time]
- Utility: X/10 — [real-world value argument]
- Technical Depth: X/10 — [what's impressive under the hood]

**48-hour MVP scope:**
- Must-have: [2-3 features that make the demo work]
- Nice-to-have: [1-2 features if time allows]
- Cut: [things that sound cool but aren't worth the time]

**Biggest risk:**
- [Technical blocker, API dependency, scope creep vector, etc.]
- Mitigation: [how to handle if it happens]

**vs. Competition:**
- Others will likely build: [obvious approaches]
- This stands out because: [differentiation argument]

Then ask: "Which one do you want to go with? Or want me to dig deeper on any?"

## Round 3: Lock In

User picks one idea. Generate the **Idea Spec**:

## Idea Spec

**Name:** [Project name]
**One-liner:** [Elevator pitch]
**Target User:** [Who uses this]
**Core Features:**
1. [Feature 1 — most important]
2. [Feature 2]
3. [Feature 3 — stretch]

**Tech Stack:**
- Frontend: [choice + why]
- Backend: [choice + why]
- Deploy: [choice + why]
- Key APIs/libraries: [list]

**Demo Vision:**
[What the demo video shows — the "wow moment" in 30 seconds]

**Success Criteria:**
[What "done" looks like for submission]

Write this to the `## Idea` section of `hackson-state.md`. Set phase to `building`.

## Rollback Entry Point

If called when phase is already `building` (user is coming back from a failed build):
- Acknowledge: "Build didn't work out. Let's find a better idea."
- Ask: pivot (similar direction, different approach) or restart (full diverge)?
- Preserve competition info, clear idea section.
