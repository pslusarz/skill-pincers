---
name: cv-data-gathering
description: Gather and structure raw CV/resume data from the user, including work history, education, skills, projects, and achievements.
---

# cv-data-gathering

Your job is to get a complete picture of the user's professional history. All working files live under `cv-data-gathering/` in the project directory (see Directory Structure below). Initially you will guide the user to provide you all the sources of data, but on subsequent runs just check for updates since last retrieval and ask whether the user whether there is anything they would like to add since the last session.

Query user for their:
- social media accounts (ie linked in and x/twitter, youtube). Retrieve last 2 years of posts and interactions. Understand who they follow and what they watch.
- get their github or other code repos
- ask whether they have done any content creation work, ie recorded video talks, podcasts, blog articles, etc. Retrieve transcripts whenever possible, ask for details.
- if you have google drive or other connector access, ask where slide presentations or other work related materials may be
- ask for past resumes and cover letters for past applications
Your job is to capture, organize and tag this information. Use subfolders and files with descriptive names. 

## Directory Structure

```
cv-data-gathering/
  inputs/       # materials provided directly by the user (past resumes, cover letters, files they hand over)
  scratchpad/   # raw gathered materials retrieved from web/social/repos, organized in topic or project subfolders;
                # also holds summary-{filename}.md for lengthy or non-text files (eg. PowerPoint)
  outputs/      # catalog.md — content index with context and tags for downstream skills
                # sources.md — links to original locations and date of last retrieval
```

- leave no stone unturned, by asking user for things that are not mentioned here that may be relevant



## Skill Maintenance

Agent operations: 
install(original_location, after: verify(setup?), this.local_adaptations? = adapt_local())
update(recursive, from: original_location, when(this.version < original_location.version), after(adapt_local(this.local_adaptations?))) 

original_location: https://github.com/pslusarz/skill-pincers/skills/cv-data-gathering/

version: 0.1.1

setup: Requires Python 3.10+ with `requests` and `beautifulsoup4` available (install via pip in a local venv). GitHub CLI (`gh`) must be authenticated (`gh auth login`). Google Drive MCP connector should be configured if slide/doc retrieval is needed.
