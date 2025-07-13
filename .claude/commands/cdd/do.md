# Action: Perform FAST Execution of the Next Step

## OBJECTIVE:

To execute the next incomplete step in a plan as quickly and efficiently as possible. This command ASSUMES that the core context (`VISION.md`, `CLAUDE.md`) has been recently loaded by a preceding `/cdd:act` command and is still fresh in the session's short-term memory. IT SKIPS THE EXPENSIVE CONTEXT READS.

---

### STEP 1: Identify Next Action (Lightweight)

Read the task file at `$ARGUMENTS`. Scan its checklist and identify the VERY FIRST incomplete item (`- [ ]`). This is the "Target Action".

### STEP 2: Pre-Action Sanity Check (Still Essential, but Lighter)

1.  **Review Immediate History:** Briefly glance at the last entry in `LOG.md`.
2.  **Validate Action Coherency:** Ask yourself: "Does this 'Target Action' directly and logically follow what I just did?"
3.  **Make a Decision:**
    - **If YES, action is valid:** Proceed to Step 3.
    - **If NO, action is flawed:** You MUST HALT. Announce the coherency failure and state that a "full-context" action like `/cdd:act` or `/cdd:revise-plan` is required to safely proceed.

---

### STEP 3: Execute the Target Action

Perform the "Target Action" precisely.

### STEP 4: Log Progress (Unified Format)

After successful completion, append a single-line `COMPLETED` entry to `LOG.md`.

**The log entry MUST follow this exact format:**
`[YYYY-MM-DD HH:MM:SS] COMPLETED: [Brief summary of what you did] from task file [$ARGUMENTS].`

### STEP 5: Update Task List

Edit the task file (`$ARGUMENTS`) and mark the "Target Action's" checkbox as done (`- [x]`).

### STEP 6: Confirm and Halt

Announce the successful completion of the step and that you are halted, awaiting the next command.
