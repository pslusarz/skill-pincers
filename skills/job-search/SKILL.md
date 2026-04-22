---
name: job-search
description: Search for and evaluate job opportunities based on the user's profile, preferences, and target criteria.
---

# job-search

## Philosophy

Job searching requires understanding of how recruiting pipelines work. The goal of this stage is to find listings that maximize the candidate's chances of landing an in-person interview. 

This means:
- Ruthlessly qualifying opportunities before investing time in them
- Understanding which hiring pipelines reward the candidate's actual strengths (and avoiding the ones that don't)
- Calibrating effort to expected return — not every application deserves 8 hours
- Treating the search as a portfolio, not a sequence of bets

## Directory Structure

```
job-search/
  inputs/       # reads from cv-data-gathering/outputs/ (catalog.md, sources.md);
                # job criteria and search location config if overriding skill defaults
  scratchpad/   # raw job listings captured during sourcing; per-role qualification notes
  outputs/      # shortlist.md — scored and tiered opportunities with status tracking
                # {company}-brief.md — research briefs for Tier 1 roles (consumed by job-application)
                # weekly-summary.md — roles found, qualified, applied, conversion data
```

## Inputs

candidate profile - This skill requires a candidate job profile (see below) and access to `cv-data-gathering/outputs/` to understand the candidate's background.

job criteria - identified below for this specific search. Criteria include not just characteristics like "remote" or "mid-level AI engineer", but also the type of pipeline (founder-led, ATS, specialized recruiter, etc) and company culture.

search locations - standard list of job boards, but also scour the candidate's favorite leaders feeds, as well as obscure communities.

### This Candidate

**Background:** 20 years of production software engineering at a single company, with the last two years exclusively focused on LLM systems. Has shipped multiple production LLM applications including an MCP server integration serving tens of millions of users, knowledge graph + LLM systems, transformer fine-tuning pipelines, agentic orchestration, and conversational AI. MS in Computer Science with machine learning thesis (hybrid neural/symbolic cognition). Conference speaker. Active in the fast.ai community.

**Core strength:** Operates at the architectural and pattern level of LLM engineering. Understands the mechanisms well enough to build from scratch (implemented programmatic tool calling before mainstream frameworks supported it, built dynamic generative UI from first principles). This translates into good technical judgment about what approaches will work and what won't — the kind of judgment that comes from being critical of hype and thinking from first principles rather than following frameworks.

**What makes this candidate distinctive:**
- Production MCP server development experience (rare and in high demand)
- The combination of deep production engineering experience (20 years of shipping) with current AI/LLM fluency — most candidates have one or the other
- Builds working systems to test ideas, not just theoretical takes
- Genuine learning posture (takes beginner courses with 25 years of experience and finds real value)
- Thinks in XP/pair-programming vocabulary — captain/navigator, clear role separation between human and AI

**What this candidate is NOT:**
- Not a competitive programmer — will underperform on timed algorithmic screens relative to actual ability
- Not a self-promoter — tends to undersell contributions and is uncomfortable with noise-making
- Not a framework follower — evaluates tools critically rather than adopting the popular choice, which means the resume may not keyword-match for the latest trending framework

### Target Criteria

**Must have:**
- Remote-primary (quarterly or even monthly travel to an office is fine; weekly in-office is not)
- AI/ML/LLM/agentic systems space — the role involves building production systems with large language models
- The company understands that AI is changing what skills matter — does not rely on traditional keyword matching for technologies that take days to learn

**Strong signals (look for these):**
- Company is <200 people, or the role is in a small team within a larger org where a human reads applications
- JD describes problems to solve ("build agentic systems that automate X") rather than tech stack checklists ("5+ years of Kubernetes")
- Company is in a transformation moment where the combination of production engineering depth + AI fluency is the exact thing they need
- No automated coding screen, or the technical assessment is conversation-based / take-home
- Agentic systems, MCP, LLM orchestration, or knowledge graphs mentioned in the JD
- Founder, CTO, or engineering lead is publicly visible and has substantive things to say about AI

**Red flags (deprioritize):**
- Automated HackerRank/Codility screen with no bypass option
- JD is a wall of "X+ years of Y" requirements with no description of what the team is actually building
- LinkedIn shows 200+ applicants already
- Role has been posted for 4+ weeks (likely already has candidates in pipeline)
- "Remote" but actually requires weekly office presence

**Domain flexibility:** The candidate's experience is in automotive data, but the engineering patterns (LLM pipelines, agentic orchestration, MCP, knowledge graphs) transfer across domains. Healthcare, fintech, govtech, developer tools, agriculture — the domain gap is learnable, the systems design instinct is not. Do not filter out roles in unfamiliar domains if the engineering fit is strong.

### Pipeline Preferences

This candidate converts best in Pipeline 2 (founder/CTO-led companies) and Pipeline 5 (specialized recruiters). Pipeline 1 (corporate ATS with automated screens) is negative expected value without a referral. Pipelines 3 and 4 (community/reputation and referrals) are valuable but slower to activate.

For detailed pipeline analysis, scoring framework, and application workflow tiers, see `resources/pipeline-analysis.md`.

## What This Skill Does

### 1. Source Opportunities
Scan job listings from high-signal sources. Prioritize sources that skew toward Pipeline 2 companies:
- HN "Who is Hiring" (monthly thread, first of each month)
- Wellfound (startup-focused)
- Built In (remote filter + AI filter)
- LinkedIn saved searches (keywords aligned to target criteria, remote, posted in last week)
- Direct career pages of companies identified through community, news, or prior research

### 2. Qualify and Score
For each opportunity, run the 10-minute qualification filter (detailed in `resources/pipeline-analysis.md`). Score 0-2 on five dimensions: Human Reader, Problem-Shaped JD, No Auto Gauntlet, Core Skill Relevance, Remote + Fresh.

Assign a tier:
- **Tier 1 (score 7+):** Full application. Pass to job-application skill with research brief.
- **Tier 2 (score 5-6):** Lightweight application. Tailored resume + short cover note.
- **Tier 3 (score <5):** Skip. Log reason briefly for pattern analysis.

### 3. Build a Research Brief for Tier 1 Roles
For each Tier 1 opportunity, produce a brief that the job-application skill can use:
- Company: name, size, stage, funding, what they build
- Role: title, team, what they need, why the role exists
- Fit assessment: which of the candidate's projects/experiences map to this role's needs, and where the gaps are
- Key references: 2-3 things the candidate can authentically reference in application materials (a founder's public statement, an engineering blog post, a specific product decision)
- Pipeline type: which pipeline is this, and what does that imply about application strategy

### 4. Maintain a Shortlist
Keep a running `job-search/outputs/shortlist.md` with:
- Qualified opportunities, scored and tiered
- Date found, date applied (or skipped + reason)
- Follow-up dates
- Outcomes when known (response, interview, rejection, silence)

Review weekly. Look for patterns: which company types are converting? Which sources yield the best leads? Adjust targeting accordingly.

## Outputs

All outputs written to `job-search/outputs/`:
- `shortlist.md` — running scored list of opportunities with status tracking
- `{company}-brief.md` — research briefs for Tier 1 roles (consumed by job-application skill)
- `weekly-summary.md` — roles found, roles qualified, applications submitted, conversion data

## Skill Maintenance

Agent operations: 
install(original_location, after: verify(setup?), this.local_adaptations? = adapt_local())
update(recursive, from: original_location, when(this.version < original_location.version), after(adapt_local(this.local_adaptations?))) 

original_location: https://github.com/pslusarz/skill-pincers/skills/job-search/

version: 0.2.1

required_skills: cv-data-gathering

setup: Web search capability required. LinkedIn access (via browser or connector) recommended for applicant count checks and hiring manager identification.
