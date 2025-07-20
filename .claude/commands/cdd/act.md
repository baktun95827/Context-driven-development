# Action: Autonomously and Atomically Execute an Entire Plan

## OBJECTIVE:

To act as a self-sufficient agent, executing all steps in the provided plan (`$ARGUMENTS`) in a single, uninterrupted "focus session". All file modifications (logging and checklist updates) will be batched and performed ONLY ONCE at the very end of a successful execution run.

---

### PRE-FLIGHT CHECK: LOAD CONTEXT & PREPARE IN-MEMORY LOG

_This happens only once at the beginning._

1.  **Load Core Context:** Read `.ccd/VISION.md` and `CLAUDE.md`.
2.  **Load Plan:** Read the entire plan from the task file at `$ARGUMENTS`.
3.  **Initialize In-Memory Log:** Create a temporary, internal list in your memory to track the results of each step. Do not write to any files yet.

---

### AUTONOMOUS EXECUTION LOOP (IN-MEMORY):

You will now enter a loop. For each incomplete checklist item (`- [ ]`) in the plan, from top to bottom, you will perform the following sub-routine:

#### 1. Pre-Action Sanity Check:

- Glance at your **internal, in-memory log** of the last completed action.
- Ask yourself: "Given what I just did, does this next step still make sense?"
- If the check fails, ABORT the entire operation. Discard your in-memory log and report the coherency failure, recommending `/cdd:revise-plan`.

#### 2. Execute Action:

- Perform the action described in the checklist item.

#### 3. Record In-Memory Progress:

- Upon successful completion of the step, add a summary of what you did to your **internal, in-memory list**. **Example:** `* Created user model in `models.py`.`

#### 4. Loop to Next Step:

- **Immediately continue to the next incomplete checklist item without providing any output in the chat.**

---

### POST-EXECUTION: ATOMIC UPDATE & REPORTING

This stage is reached ONLY if the entire loop completes without any errors.

1.  **Announce Completion:** Start by announcing that the entire plan has been successfully executed.

2.  **Batch-Update LOG.md:**

    - Now, and only now, open `.ccd/LOG.md`.
    - Append a single, comprehensive `COMPLETED` event block to the file. This block will contain the **full in-memory log** you've been keeping.

    **The log entry MUST follow this exact format:**

    ```
    ---
    ## COMPLETED TASK: [YYYY-MM-DD HH:MM:SS]
    **Task File:** tasks/002_implement_user_auth.md
    **Summary of Actions:**
    *   Created Pydantic model for user login request.
    *   Implemented password hashing utility in `utils/security.py`.
    *   Wrote unit test for password hashing.
    *   ... (and so on for all completed steps)
    ---
    ```

3.  **Batch-Update Task File:**

    - Open the task file (`$ARGUMENTS`).
    - Iterate through your completed steps and mark all corresponding checkboxes from `[ ]` to `[x]` in a single file-write operation.

4.  **Final Confirmation:** Conclude with a message: "Execution complete. `LOG.md` and the task file have been atomically updated. Ready for the next assignment."

---

### EXIT CONDITIONS:

The loop will terminate and no files will be written if:

- Any step execution fails.
- Any Pre-Action Sanity Check fails.
- A human user provides a new prompt, interrupting the process.

In case of failure, you will report the error clearly, but you will **NOT** modify `.ccd/LOG.md` or the task file, leaving the system in a clean state, ready for debugging.
