# verify-protocol-change

Authoring skill for testing whether a skill's Maintenance section is correctly understood by a naive agent. Use this when you have changed the AGENTS.md protocol and want to verify that an existing skill's maintenance block communicates the right behavior.

## Steps

1. **Read AGENTS.md** to understand the current protocol and template.

2. **Select a skill** to test with. Default to `skills/cv-data-gathering/SKILL.md` unless the user specifies another. Read the skill file.

3. **Update the skill's Maintenance section** to conform to the current AGENTS.md template:
   - Replace any plain-prose maintenance instructions with the SudoLang operation block (`install(...)` / `update(...)`)
   - Ensure `original_location` and `version` fields are present
   - Omit optional fields (`required_skills`, `setup`, `local_adaptations`) if they are blank, per template rules
   - **Vary `setup` and `local_adaptations`** to be non-trivial and realistic for the skill's domain — do not leave them as `none`. Invent plausible values based on what the skill actually does.

4. **Spawn a subagent** with the following constraints:
   - Context: only the updated skill file content (no AGENTS.md, no other files)
   - Task: describe step-by-step what actions it would take to perform one of the operations listed in the Maintenance block
   - The operation to test: choose one of `install` or `update`, or use the one specified by the user
   - Instruction to subagent: do NOT take any real actions, only describe what it would do

5. **Report results** in a table with these columns for each test run:
   - **What changed**: which fields in the maintenance section were modified and how
   - **Operation tested**: which operation (`install` or `update`) was given to the subagent
   - **Agent response**: summary of the steps the subagent described
   - **Pass / Fail**: your judgment of whether the agent correctly derived the intended behavior from the skill file alone, with a brief reason

## Pass criteria

The subagent passes if it:
- Correctly interprets the SudoLang operation signature (conditions, optional params, sequencing)
- Handles `local_adaptations?` correctly — preserving them on update, applying them on install
- Handles `setup?` correctly — verifying preconditions before proceeding
- Does not confuse remote skill content with local adaptations
- Does not require AGENTS.md or external context to derive correct behavior
