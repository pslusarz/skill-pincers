---
name: cv-data-gathering
description: Gather and structure raw CV/resume data from the user, including work history, education, skills, projects, and achievements.
---

# cv-data-gathering

Your job is to get a complete picture of the user's professional history. You will use raw/ folder in the project directory to capture all this information. Initially you will guide the user to provide you all the sources of data, but on subsequent runs just check for updates since last retrieval and ask whether the user whether there is anything they would like to add since the last session.

Query user for their:
- social media accounts (ie linked in and x/twitter, youtube). Retrieve last 2 years of posts and interactions. Understand who they follow and what they watch.
- get their github or other code repos
- ask whether they have done any content creation work, ie recorded video talks, podcasts, blog articles, etc. Retrieve transcripts whenever possible, ask for details.
- if you have google drive or other connector access, ask where slide presentations or other work related materials may be
- ask for past resumes and cover letters for past applications
Your job is to capture, organize and tag this information. Use subfolders and files with descriptive names. 

Outputs:
- original materials in the raw/ folder, with recursively project and topic oriented subfolders
- summary-{filename}.md for all lengthy files, or files where content is not easily accessible to the LLM, ie powerpoint.
- top level catalog.md file with more details on the content (context, any relevant tags), so that the next agent can more selectively focus on the information relevant to the position description.
- top level sources.md file with links to the original locations and date of the last retrieval.
- leave no stone unturned, by asking user for things that are not mentioned here that may be relevant



## Maintenance

Agent operations: 
install(original_location, after: verify(setup?), this.local_adaptations? = adapt_local())
update(recursive, from: original_location, when(this.version < original_location.version), after(adapt_local(this.local_adaptations?))) 

original_location: https://github.com/pslusarz/skill-pincers/skills/cv-data-gathering/

version: 0.1.0

setup: Requires Python 3.10+ with `requests` and `beautifulsoup4` available (install via pip in a local venv). GitHub CLI (`gh`) must be authenticated (`gh auth login`). Google Drive MCP connector should be configured if slide/doc retrieval is needed.

local_adaptations: none
