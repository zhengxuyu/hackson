# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Purpose

This repo contains a suite of Claude Code skills ("hackson skills") designed to systematically win hackathons — primarily on [DoraHacks](https://dorahacks.io/). The skills cover the full hackathon lifecycle:

1. **Research/Recon** — scan hackathon listings, extract rules/judging criteria/prizes/tech requirements, analyze past winners
2. **Idea Pumping** — structured ideation against judging criteria, competitive gap analysis, feasibility scoring
3. **MVP Building** — rapid scaffold-to-deploy pipeline, tech stack selection based on hackathon constraints
4. **Iteration & Polish** — demo prep, pitch deck generation, last-mile UX polish, submission packaging

## Architecture

Skills live as markdown files with YAML frontmatter, following the gstack/superpowers skill format:

```
skills/
  hackson-recon.md        # Hackathon research & intelligence gathering
  hackson-ideate.md       # Idea generation & scoring
  hackson-mvp.md          # MVP scaffolding & rapid build
  hackson-iterate.md      # Polish, demo, pitch, submit
  hackson.md              # Main controller / orchestrator
```

Each skill is a standalone `.md` file with this structure:
```markdown
---
name: skill-name
description: one-line description for skill discovery
---

Skill content (instructions Claude follows when the skill is invoked)
```

## Key Design Principles

- Skills should be opinionated and hackathon-specific — optimize for speed-to-demo, not production quality
- DoraHacks-specific: understand BUIDL submissions, BuidlerDAO judging, quadratic voting mechanics
- Each skill should be independently invocable via `/hackson-<phase>` but also chainable through the orchestrator
- Borrow patterns from gstack skills (browse, ship, qa) but adapt for hackathon tempo — 24-48hr sprints, not week-long dev cycles
- Chinese + English bilingual support since DoraHacks has significant Chinese-language hackathons

## Development

This is a skills-only repo — no build step, no tests, no dependencies. Quality is verified by invoking skills in real hackathon scenarios.

To install skills locally, symlink or copy into `~/.claude/skills/` or the project's `.claude/skills/` directory.
