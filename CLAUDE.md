# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Purpose

This repo is both a skill suite AND a workspace for all hackathon competitions. Skills define the workflow; `competitions/` holds all actual hackathon projects.

## Architecture

```
hackson/
├── skills/                          ← Skill definitions (the methodology)
│   ├── hackson.md                   ← Hub controller
│   ├── hackson-scout.md             ← Phase 1: research & select
│   ├── hackson-ideate.md            ← Phase 2: idea generation
│   ├── hackson-build.md             ← Phase 3: MVP implementation
│   └── hackson-ship.md              ← Phase 4: submission packaging
├── competitions/                    ← All hackathon projects (the work)
│   ├── dorahacks-ai-2026/
│   │   ├── hackson-state.md         ← State for this competition
│   │   ├── src/                     ← MVP source code
│   │   ├── submission/              ← Pitch, screenshots, descriptions
│   │   └── README.md
│   └── eth-global-may/
│       └── ...
└── docs/superpowers/                ← Design specs & plans
```

## Workflow

1. `/hackson` — entry point, shows all competitions, resume or start new
2. `/hackson-scout` — research DoraHacks listings, score ROI, pick a competition
3. `/hackson-ideate` — generate 8-10 ideas, filter to 1, output idea spec
4. `/hackson-build` — scaffold + implement + deploy MVP (zero scheduling)
5. `/hackson-ship` — package submission materials, pre-submit checklist

## Key Principles

- **Zero scheduling** — all code is AI-implemented immediately, no time estimates
- **Demo-driven** — only build what judges can see
- **Per-competition isolation** — each hackathon gets its own folder, no cross-contamination
- **Bilingual** — skills handle Chinese and English hackathons
- **Rollback is cheap** — any phase can jump back to ideation
