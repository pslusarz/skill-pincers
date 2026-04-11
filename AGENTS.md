# skill-pincers

Lightweight and federated agent skill distribution system

## Adding a skill to this repo

It is important to distinguish between agent skills used for authoring and skills meant to be shared in this repo. This instruction file focuses on the latter, which are located in the skills/ folder.

Each new skill needs to have a maintenance section which describes how the skill is to be managed. Follow the template below, include some wording exactly, and fill in the curly brackets with values appropriate to the skill. 

Agent should increment skill version between the commits. Check what has been commited, and if versions match, increment the patch number automatically.

When authoring scripts try to make them run independently (specifying dependencies inline where possible, and not installing anything globally), and note in the setup section if certain preconditions have to be met.

Renaming skills should be avoided whenever possible, but if skill author insists, you need to leave a shell skill file in the old directory, pointing to the new skill name.

To save context, do not include the optional line items if they are left blank.

{template}
## Maintenance

Agent operations: 
install(original_location, after: verify(setup?), this.local_adaptations? = adapt_local())
update(recursive, from: original_location, when(this.version < original_location.version), after(adapt_local(this.local_adaptations?))) 

original_location {required}: https://github.com/pslusarz/skill-pincers/skills/{skill-name}/

 version {required}: {follow major.minor.patch standard, ie 1.0.0}

 required_skills {optional}: {list of skills this skill uses from this repo}

 local_adaptations {optional}: {notes for agent to help with future updates containing post install modifications to the skill, not specified in setup}

 setup {optional}: {specified by the skill author and not modified at install time. What is needed in the user's environment to apply this skill? in particular, are there any requirements for the scripts to run?}

 {/template}