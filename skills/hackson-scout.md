---
name: hackson-scout
description: Scan DoraHacks hackathons, score ROI, recommend top competitions to enter. Use when looking for hackathons to compete in.
---

# Hackson Scout — Competition Research & Selection

You help the user find the highest-ROI hackathon to compete in. You do the research, score options, and present recommendations. The user picks.

## Process

### Step 1: Gather Listings

Use WebSearch and WebFetch to find active hackathons on DoraHacks:
- Search: `site:dorahacks.io hackathon` + current month/year
- Fetch the DoraHacks hackathon listing page
- Also check: `dorahacks.io/hackathon` for active/upcoming

For each competition found, extract:
- Name & URL
- Theme/track (Web3, AI, DeFi, infra, social, etc.)
- Prize pool (total + per-track breakdown if available)
- Deadline (submission due date)
- Judging criteria (listed or inferred)
- Technical requirements/constraints (specific chain, language, platform)
- Registration count or team count (if visible)
- Language: zh or en

### Step 2: Score & Rank

Present a **ROI Assessment Table** with columns:

| Competition | Prize | Deadline | Crowdedness | Tech Match | Feasibility | Score |
|---|---|---|---|---|---|---|

Scoring dimensions (1-5 each):
- **Prize/effort ratio**: High prize + low time investment = 5
- **Crowdedness**: Fewer participants = higher chance = 5. >100 teams = 1.
- **Tech match**: User is solo full-stack. Score how well the requirements match one person's ability.
- **Feasibility**: Can a competitive MVP be built before deadline? Factor in remaining days.
- **Score**: Weighted average. Prize×2 + Crowdedness×2 + Tech×1.5 + Feasibility×1.5

### Step 3: Recommend

Present Top 3 with:
- Why this one is good for you
- What type of project would likely win here
- Key risk or downside

### Step 4: User Decides

- User picks one → create competition folder under `competitions/`, write profile to `competitions/<name>/hackson-state.md`, set phase to `ideating`
- User says "none of these" → search with different criteria or broader scope
- User provides a specific competition URL → fetch that directly, assess it, ask if they want to lock it in

## Notes

- Always check deadlines against today's date. Skip anything with <3 days remaining.
- If a competition requires team formation or KYC that blocks solo entry, flag it and lower score.
- Prefer competitions where prize is distributed to more winners (e.g., top 10 each get $X) over winner-take-all.
