# Hackson Skill Suite Design

## Overview

A Claude Code skill suite for solo hackers to systematically win hackathons on DoraHacks (and other platforms). Covers the full lifecycle: scout → ideate → build → ship. Architecture follows a Hub + Spoke model with a central controller dispatching phase-specific sub-skills.

## Core Interaction Model

Every phase follows the same loop:
1. AI does heavy lifting (research, generation, coding)
2. AI presents structured output with options
3. User reviews, picks, or redirects
4. AI iterates until user signs off
5. Output saved to state file, advance to next phase

User is the decision-maker. AI is the executor.

## Architecture: Hub + Spoke

```
/hackson (hub)
  ├── /hackson-scout   (调研选赛)
  ├── /hackson-ideate  (Idea 生成与筛选)
  ├── /hackson-build   (MVP 快速搭建)
  └── /hackson-ship    (提交打包)
```

### State Management

All state persisted in `hackson-state.md` at project root. Contains:
- Selected competition metadata (name, URL, deadline, judging criteria, tech requirements)
- Current phase: `scouting | ideating | building | shipping | submitted`
- Idea list + selected idea spec
- Build progress (modules, status, deploy URL)
- Submission checklist

State flow:
```
scouting → ideating → building → shipping → submitted
               ↑___________|  (rollback allowed)
```

### Hub: `/hackson`

- On entry: report current state (one line), suggest 2-3 next actions
- Commands: `/hackson` (main), `/hackson status` (overview), `/hackson reset` (start over)
- New competition: initialize state file, enter scouting
- Resume: read state file, pick up where left off

---

## Phase 1: `/hackson-scout` (调研选赛)

**Purpose:** Find the highest-ROI hackathon to compete in.

**Process:**
1. Fetch active hackathon listings from DoraHacks via web search/fetch
2. Extract structured info per competition:
   - Theme/track, prize pool, judging criteria, deadline, entry requirements
   - Tech constraints (chain, language, platform)
   - Registration count / historical winner quality
3. Generate ROI assessment table, ranked by win probability:
   - Prize / time investment ratio
   - Track crowdedness (more participants = harder)
   - Tech stack match to user's strengths
   - Deadline feasibility
4. Present Top 3 recommendations with reasoning

**User action:** Pick a competition or request another batch.

**Output:** Selected competition profile written to `hackson-state.md`. Phase → `ideating`.

---

## Phase 2: `/hackson-ideate` (Idea 生成与筛选)

**Purpose:** Generate and filter ideas optimized for the selected competition's judging criteria.

**Round 1 — Diverge:**
- Generate 8-10 ideas based on competition profile
- Each idea includes: one-line pitch, core differentiator, estimated effort (hours), tech stack
- Reference historical winning project patterns

**Round 2 — Converge:**
- User selects 2-3 favorites
- Deep analysis on each:
  - Score against judging dimensions (innovation, completeness, utility, technical depth)
  - What MVP looks like within 48 hours
  - Biggest risk (tech blockers, API dependencies, etc.)
  - Differentiation vs likely competitor projects

**Round 3 — Lock in:**
- User picks one idea
- AI outputs idea spec: target user, core features (max 3), tech stack recommendation, demo vision

**Output:** Idea spec written to `hackson-state.md`. Phase → `building`.

---

## Phase 3: `/hackson-build` (MVP 快速搭建)

**Purpose:** Go from idea spec to deployable demo as fast as possible.

### Hard Rule: Zero Scheduling

All code is AI-implemented. There is no "estimated X days." When the user says build something, AI starts immediately. Module granularity is scoped to "deliverable in one conversation turn." If complexity is too high, downgrade the approach — never delay.

### Sub-phases:

**Phase 3a — Scaffold:**
1. Generate project structure from idea spec's tech stack
2. Pick deployment target (Vercel/Railway/Netlify — whichever ships fastest)
3. List feature modules, priority-sorted: must-have / bonus / cut

**Phase 3b — Module-by-module implementation:**
4. For each module:
   - AI proposes implementation approach (technical detail level)
   - User confirms or adjusts
   - AI writes code
   - Run and verify
5. Update progress in state file after each module

**Phase 3c — Live demo:**
6. Deploy to public URL
7. Smoke test: core path works end to end

**Key principles:**
- Time-box thinking: each module has a budget, if exceeded → downgrade, don't delay
- Demo-driven: only build what judges can see or interact with
- Dead-end detection: if stuck, proactively suggest rolling back to `/hackson-ideate`

**User action:** Confirm each module's approach, test the demo, decide continue or rollback.

**Output:** Live MVP URL + feature checklist in `hackson-state.md`. Phase → `shipping`.

---

## Phase 4: `/hackson-ship` (提交打包)

**Purpose:** Package everything for submission, maximizing score against judging criteria.

### 1. Project Description
- Generate DoraHacks BUIDL submission copy from idea spec + actual MVP
- Structure: problem statement, solution, tech architecture, roadmap
- Align content to each judging criterion explicitly

### 2. Demo Materials
- Demo video script: step-by-step screen recording instructions + voiceover text
- Pitch deck outline + per-slide content (if needed)
- Screenshot/GIF shot list for key highlights

### 3. Technical Documentation
- README (judge-facing, not developer-facing)
- Architecture diagram description
- If open-source required: clean repo, add license

### 4. Pre-submission Checklist
- Cross-check against competition's submission requirements item by item
- Deadline warning with time buffer

**User action:** Review copy, record demo video (following script), hit submit.

**Output:** Complete submission package. State → `submitted`.

---

## Skill File Structure

```
skills/
  hackson.md              # Hub controller
  hackson-scout.md        # Phase 1: research & select
  hackson-ideate.md       # Phase 2: idea generation & filtering
  hackson-build.md        # Phase 3: MVP implementation
  hackson-ship.md         # Phase 4: submission packaging
```

State file at project root: `hackson-state.md`

## Cross-cutting Concerns

- **Bilingual:** DoraHacks has Chinese and English hackathons. Skills should handle both. Submission materials generated in whatever language the competition requires.
- **Platform-agnostic ideas, DoraHacks-optimized packaging:** Ideas can work anywhere, but `/hackson-ship` knows DoraHacks BUIDL format specifically.
- **Rollback is cheap:** Any phase can jump back to ideation. State file tracks history so nothing is lost.
