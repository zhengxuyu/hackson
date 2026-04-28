---
name: hackson-ship
description: Package hackathon submission — project description, demo script, pitch deck, checklist. Use when MVP is ready to submit.
---

# Hackson Ship — Submission Packaging

You package everything needed for a winning submission. Every deliverable is optimized against the competition's judging criteria.

## Prerequisites

Read the current competition's `hackson-state.md` (under `competitions/<name>/`) for:
- Competition info (judging criteria, submission requirements, deadline, language)
- Idea spec
- Build progress + deploy URL
- If phase isn't `shipping`, tell user to run `/hackson-build` first.

All submission materials go into `competitions/<name>/submission/`.

## Deliverable 1: Project Description

Generate the DoraHacks BUIDL submission text:

### Structure:
1. **Project Name + Tagline** (one-liner from idea spec)
2. **Problem** (2-3 sentences — what pain exists)
3. **Solution** (2-3 sentences — what we built)
4. **How It Works** (3-5 bullet points — user journey)
5. **Technical Architecture** (diagram description + key tech choices)
6. **Innovation** (what's novel — map directly to "innovation" judging criterion)
7. **Future Roadmap** (3 bullet points — show vision beyond MVP)

Rules:
- Write in the competition's language (zh or en, from state file)
- Every section should map to at least one judging criterion
- Be specific and concrete, not vague and aspirational
- Include the live demo URL prominently

Present to user for review. Iterate until approved.

## Deliverable 2: Demo Materials

### Demo Video Script

#### Demo Script (target: 2-3 minutes)

**[0:00-0:15] Hook**
- Show: [opening screen/state]
- Say: "[one sentence problem statement]"

**[0:15-0:45] Problem Context**
- Show: [illustrate the pain point]
- Say: "[why this matters]"

**[0:45-2:00] Solution Walkthrough**
- Show: [step-by-step actions on screen]
- Say: "[explain each action and why it's impressive]"
- Key moments to pause on: [list "wow" moments]

**[2:00-2:30] Technical Depth**
- Show: [architecture diagram or code snippet]
- Say: "[explain what's under the hood]"

**[2:30-3:00] Closing**
- Show: [final state / key metric]
- Say: "[future vision + call to action]"

### Pitch Deck (if needed)

Generate slide-by-slide outline:
- Slide 1: Title + tagline
- Slide 2: Problem
- Slide 3: Solution (with screenshot)
- Slide 4: Demo highlights (3 screenshots)
- Slide 5: Technical architecture
- Slide 6: What's next

### Screenshot Shot List

List specific screenshots to capture:
- [Screen]: [What it shows] — [Why judges care]
- Minimum 3, maximum 6 screenshots

## Deliverable 3: Technical Documentation

### README (Judge-Facing)

# [Project Name]

[One-liner]

## Live Demo
[URL]

## What It Does
[3 bullet points]

## Tech Stack
[List with brief justification for each choice]

## Architecture
[Text description or ASCII diagram]

## How to Run Locally
[If required by competition — keep minimal]

## Built For
[Competition name] — [Track/Theme]

### Repo Cleanup (if open-source required)
- Remove debug code, console.logs, TODO comments
- Add LICENSE (MIT unless competition specifies otherwise)
- Ensure `.env.example` exists if env vars are needed
- Clean commit history (squash WIP commits if messy)

## Deliverable 4: Pre-Submission Checklist

Fetch the competition's submission page and extract ALL requirements. Then:

## Submission Checklist for [Competition Name]

- [ ] Project registered on DoraHacks
- [ ] BUIDL page filled out (description, links, team)
- [ ] Demo URL accessible and working
- [ ] Demo video uploaded/linked
- [ ] Source code linked (if required)
- [ ] Screenshots attached
- [ ] All required fields completed
- [ ] Submitted before deadline: [date + time + timezone]
- [ ] Double-checked: no broken links, no placeholder text

Go through each item. For anything incomplete, offer to fix it or flag what the user needs to do manually (e.g., "you need to record the video following the script above").

## Final Step

Once all items checked:
- Update `hackson-state.md` phase to `submitted`
- Congratulate briefly, remind about any post-submission steps (voting, presentations)
