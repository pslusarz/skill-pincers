# skill-pincers

Lightweight and federated agent skill distribution system

## Adding a skill to this repo

It is important to distinguish between agent skills used for authoring and skills meant to be shared in this repo. This instruction file focuses on the latter, which are located in the skills/ folder.

Each new skill needs to have a maintenance section which describes how the skill is to be managed. Follow the template below, include some wording exactly, and fill in the curly brackets with values appropriate to the skill.

Agent should increment skill version between the commits. Check what has been commited, and if versions match, increment the patch number automatically.

When authoring scripts try to make them run independently (specifying dependencies inline where possible, and not installing anything globally), and note in the setup section if certain preconditions have to be met.

Renaming skills should be avoided whenever possible, but if skill author insists, you need to leave a shell skill file in the old directory, pointing to the new skill name.

{template}
## Maintenance
This skill can be updated by checking its original location:

When updating, make sure to include all the associated metadata and also update the required skills. If the skill has been adapted / customized locally by the user, do your best at an intelligent merge, and indicate what you did.

Agent may need to adapt this skill to the user's environment. Local adaptations should be noted briefly in the local_adaptations section below.

When installing or updating this skill, pay attention to the instructions in the setup section.

original_location {required}: https://github.com/pslusarz/skill-pincers/skills/{skill-name}/

 version {required}: {follow major.minor.patch standard, ie 1.0.0}

 required_skills {optional}: {list of skills this skill uses from this repo}

 local_adaptations {optional}: {list of adaptations and customizations that were applied to the original skill}

 setup {optional}: {what is needed in the user's environment to apply this skill? in particular, are there any requirements for the scripts to run?}

 {/template}