# Action: Intelligently Act on the Next Step in a Plan

## OBJECTIVE:

To act as an intelligent agent by executing ONLY THE NEXT incomplete step in a plan. This command operates in a strict "single-step" mode and will halt after each action to await further instruction.

---

### STEP 1: MANDATORY: Load Core Context

Read `VISION.md` and `CLAUDE.md`.

### STEP 2: Identify Next Action

Read the task file at `$ARGUMENTS`. Scan its checklist and identify the VERY FIRST incomplete item (`- [ ]`). This identified item is the "Target Action".

### STEP 3: Pre-Action Sanity Check

1.  **Review Immediate History:** Briefly glance at the **last 1-2 entries** in `LOG.md`.
2.  **Validate Action Coherency:** Ask yourself: "Given what I just did, does this 'Target Action' still make sense?"
3.  **Make a Decision:**
    - **If YES, the action is valid:** Announce "Sanity check passed. Proceeding with action." and move to Step 4.
    - **If NO, the action is now flawed:** You MUST STOP. Announce the coherency failure and recommend running `/cdd:revise-plan`.

---

### STEP 4: Execute the Target Action

Perform the "Target Action" precisely as described in the checklist.

### STEP 5: MANDATORY: Log Progress (Unified Format)

After successful completion, append a **single-line `COMPLETED` entry** to `LOG.md`, including a timestamp.

**The log entry MUST follow this exact format:**
`[YYYY-MM-DD HH:MM:SS] COMPLETED: [Brief summary of what you did] from task file [$ARGUMENTS].`

### STEP 6: Update Task List

Edit the task file (`$ARGUMENTS`) and mark the "Target Action's" checkbox as done (`- [x]`).

### STEP 7: Confirm and Halt

Announce that the step has been successfully completed. Conclude by stating you are ready for the next command. **DO NOT proceed to the next checklist item automatically.**
