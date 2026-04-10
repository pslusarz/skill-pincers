---
name: cv-data-gathering
description: Gather and structure raw CV/resume data from the user, including work history, education, skills, projects, and achievements.
---

# cv-data-gathering

Your job is to get a complete picture of the user's professional history. You will use raw/ folder in the project directory to capture all this information.

Query user for their:
- social media accounts (ie linked in and x/twitter, youtube). Retrieve last 2 years of posts and interactions. Understand who they follow and what they watch.
- get their github or other public repos
- ask whether they have done any original work, ie recorded video talks, podcasts, blog articles, etc. Retrieve transcripts whenever possible, ask for details.
- if you have google drive access, ask where slide presentations or other work related writeups may be
- ask for past resumes and cover letters for past applications
Your job is to capture, organize and tag this information. Use subfolders and files with descriptive names. Maintain a top level catalog.md file with more details on the content (context, any relevant tags), so that the next agent can more selectively focus on the information relevant to the position description.
- leave no stone unturned, by asking user for things that are not mentioned here that may be relevant

## Maintenance
This skill can be updated by checking its original location:

When updating, make sure to include all the associated metadata and also update the required skills. If the skill has been adapted / customized locally by the user, do your best at an intelligent merge, and indicate what you did.

Agent may need to adapt this skill to the user's environment. Local adaptations should be noted briefly in the local_adaptations section below.

When installing or updating this skill, pay attention to the instructions in the setup section.

original_location: https://github.com/pslusarz/skill-pincers/skills/cv-data-gathering/

version: 0.1.0

required_skills: none

local_adaptations: none

setup: none
