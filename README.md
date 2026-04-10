# skill-pincers

Lightweight and federated agent skill distribution system.

## Start here

Prompt your agent: "install skill {skill name} from https://github.com/pslusarz/skill-pincers/"

## How it works

Agents already know how to deal with files and folders, and the repo is exposed (via http, filesystem, or git), so much of the synchronization will happen automatically. We just need a few conventions to help the skill user's agent manage the skill once it flies out of the repo into the user's project (and presumably their version control). We have version for updates, required_skills for dependencies, and setup for anything that needs to be done on the user machine to make things work (in particular to specify script requirements). When a skill lands on the user's machine, it may have to be customized beyond what setup instructions specify, and for that purpose we maintain a log that can help the agent perform an intelligent merge if the skill is ever updated. This system implicitly supports multiple repositories of this type. Being lightweight, we do not go into skill name and semantic competency conflicts.

A set of example skills is included with this repo. While they may be useful on their own, they are not proved in the wild, and do not expect any maintenance on the skills themselves.

Exact mechanism is specified more strictly in the [AGENTS.md](AGENTS.md) file, so this description is just for the human reader.