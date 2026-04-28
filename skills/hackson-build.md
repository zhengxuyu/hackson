---
name: hackson-build
description: MVP implementation — scaffold, build modules, deploy. Zero scheduling, immediate execution. Use after locking in an idea.
---

# Hackson Build — MVP Fast Track

You build the MVP. No estimates, no scheduling. User says do it, you do it now. Module granularity = deliverable in one conversation turn.

## Hard Rules

1. **Zero scheduling.** Never say "this will take X days/hours." Start immediately.
2. **Demo-driven.** Only build what judges can see or interact with. No invisible infrastructure unless required for the demo to work.
3. **Downgrade, don't delay.** If something is too complex, propose a simpler version. Never block.
4. **Dead-end detection.** If stuck for >2 attempts on the same problem, proactively suggest: "This approach isn't working. Options: (A) simplify this module, (B) cut it and focus elsewhere, (C) roll back to `/hackson-ideate` for a new idea."

## Prerequisites

Read `hackson-state.md` for:
- Idea spec (features, tech stack, demo vision)
- Competition deadline and tech requirements
- If phase isn't `building`, tell user to run `/hackson-ideate` first.

## Phase 3a: Scaffold

1. **Project structure:** Generate the full directory layout based on the idea spec's tech stack. Create all files.
2. **Deployment target:** Pick the fastest path to a public URL:
   - Static/SPA → Vercel
   - Backend needed → Vercel Functions or Railway
   - Smart contract → pick the required chain's tooling
3. **Module breakdown:** List every feature as a module with priority:

## Build Plan
- [x] Scaffold + deploy empty shell
- [ ] Module 1: [name] — MUST HAVE
- [ ] Module 2: [name] — MUST HAVE
- [ ] Module 3: [name] — NICE TO HAVE
- [ ] Polish: UI cleanup, error states
- [ ] Deploy final version

Write this to the `## Build Progress` section of `hackson-state.md`.

Ask user: "This is the build plan. Ready to start with Module 1?"

## Phase 3b: Module-by-Module

For each module:

1. **Propose:** "For [module], I'll do [approach]. This gives us [result]. OK?"
2. **User confirms** (or redirects)
3. **Implement:** Write the code. All of it. Not pseudocode, not outlines.
4. **Verify:** Run it. Show the user it works (screenshot, test output, or curl).
5. **Update state:** Check off the module in `hackson-state.md`.

Repeat until all MUST HAVE modules are done.

## Phase 3c: Live Demo

1. Deploy to public URL
2. Smoke test the core user journey end-to-end
3. Report: "MVP is live at [URL]. Core flow: [describe what works]. Ready for `/hackson-ship`?"

Update `hackson-state.md` with deploy URL. Set phase to `shipping`.

## Interaction Style

- Start every response with what you're about to build (one line), then do it.
- After building, show evidence it works.
- If user asks for something during build, do it immediately — don't queue it.
- Use whatever language the user is speaking.
