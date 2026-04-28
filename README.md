# Hackson

A Claude Code skill suite for systematically winning hackathons.

## What is this?

A set of AI-powered skills that guide you through the full hackathon lifecycle — from finding the right competition to submitting a polished entry. Designed for solo developers who want to maximize their win rate on [DoraHacks](https://dorahacks.io/) and similar platforms.

## How to Use

Make sure you have [Claude Code](https://claude.ai/code) installed. Then work from this repo directly.

### Quick Start

```bash
# Start the workflow
/hackson

# Or jump directly to a phase:
/hackson-scout    # Find a competition
/hackson-ideate   # Generate ideas
/hackson-build    # Build the MVP
/hackson-ship     # Package & submit
```

### Workflow

```
/hackson-scout          /hackson-ideate          /hackson-build          /hackson-ship
┌─────────────┐        ┌─────────────┐        ┌─────────────┐        ┌─────────────┐
│ Scan comps  │───────▶│ 8-10 ideas  │───────▶│ Scaffold    │───────▶│ Submission  │
│ Score ROI   │        │ Filter to 1 │        │ Build MVP   │        │ Demo script │
│ Pick one    │        │ Write spec  │        │ Deploy      │        │ Checklist   │
└───���─────────┘        └���────────────┘        └─���───────────┘        └─���───────────┘
                              ▲                       │
                              └───────────────────────┘
                                  (rollback if stuck)
```

### When to Use Each Skill

| Skill | When | What it does |
|-------|------|-------------|
| `/hackson` | Start of any session | Shows all competitions, lets you resume or start new |
| `/hackson-scout` | Looking for a hackathon to enter | Searches DoraHacks, scores competitions by ROI, recommends top 3 |
| `/hackson-ideate` | Competition selected, need ideas | Generates 8-10 ideas, helps you filter down to 1 with a full spec |
| `/hackson-build` | Idea locked, time to code | Scaffolds project, builds modules one by one, deploys MVP |
| `/hackson-ship` | MVP ready, time to submit | Writes submission copy, demo script, README, runs final checklist |

### Per-Competition Isolation

Each hackathon gets its own folder:

```
competitions/
├── dorahacks-ai-agent-2026/
│   ├── hackson-state.md      # Tracks phase, idea, progress
│   ├── src/                  # Your MVP code
│   ├── submission/           # Pitch deck, screenshots, copy
│   └── README.md             # Judge-facing README
└── eth-global-bangkok/
    └── ...
```

## Design Philosophy

- **Zero scheduling** — AI writes all code immediately. No "this will take 3 days."
- **Demo-driven** — only build what judges can see or interact with
- **Rollback is cheap** — stuck on build? Jump back to ideation. Nothing is lost.
- **Bilingual** — handles Chinese and English hackathons natively

## Requirements

- [Claude Code](https://claude.ai/code) CLI
- GitHub account (for repo/deploy)
- That's it. No dependencies to install.
