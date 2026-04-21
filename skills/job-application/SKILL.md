---
name: job-application
description: Prepare tailored job application materials including resumes, cover letters, and supporting documents for specific positions.
---

# job-application

## Directory Structure

```
job-application/
  inputs/       # job posting file for the target role (copied from job-search/outputs/{company}-brief.md
                # or pasted by user); references cv-data-gathering/outputs/ and job-search/outputs/
  scratchpad/   # company research notes, leadership profiles, fit assessment per role
  outputs/      # resume-{company}.md — tailored resume
                # cover-letter-{company}.md — tailored cover letter
```

## Inputs

- Single job posting: if job-search was run, ask candidate which Tier 1 posting to focus on and copy the brief from `job-search/outputs/{company}-brief.md` into `job-application/inputs/`. Otherwise paste the raw JD.
- Candidate background: read from `cv-data-gathering/outputs/catalog.md` and `sources.md`.
- Before producing outputs, this skill requires the agent to complete company research (described below) and save it to `job-application/scratchpad/`.

## Outputs

All outputs written to `job-application/outputs/`:
- `resume-{company}.md` — tailored resume
- `cover-letter-{company}.md` — tailored cover letter

## Research on the Company

Save research notes to `job-application/scratchpad/{company}-research.md` before drafting application materials.

- Understand the company's mission, and financial dynamics
- Understand who the decision makers are for this role
- Identify, by name, several key personnel (use LinkedIn, and other social media)
- Identify source statements from the leadership (both corporate and technical) to be able to tie to this candidate's info. Use social media, blogs, youtube (transcripts!), forum and community posts. Do deep dive on specific individuals, but focus on up to one year back
- Prepare profiles, identifying each entity's values, motivations, and passions. Read between the lines - what is not said is often as important as what is emphasized.

## Skill Maintenance

Agent operations: 
install(original_location, after: verify(setup?), this.local_adaptations? = adapt_local())
update(recursive, from: original_location, when(this.version < original_location.version), after(adapt_local(this.local_adaptations?))) 

original_location: https://github.com/pslusarz/skill-pincers/skills/job-application/

version: 0.1.0

required_skills: cv-data-gathering, job-search
