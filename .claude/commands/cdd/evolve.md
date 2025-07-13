# Action: Propose and Apply Incremental Constitutional Amendments

## OBJECTIVE:

To perform a stateful, incremental analysis of the project since the LAST evolution point, proposing and applying clean amendments to our core constitution (`CLAUDE.md`). This process is designed to be highly efficient by only considering new information.

---

### STEP 1: INCREMENTAL ANALYSIS & SYNTHESIS

1.  **Read Foundational Docs:** Read `VISION.md` and `CLAUDE.md`.

2.  **Perform Checkpointed Log Reading (CRITICAL CHANGE):**

    - Scan `LOG.md` from the **bottom to the top**.
    - Find the **most recent `## EVOLUTION POINT:` marker**.
    - Your analysis of the log MUST focus **ONLY on the log entries that have been created _after_ this marker**.
    - **If no `EVOLUTION POINT:` marker is found** (meaning this is the first time `/evolve` is ever run), then analyze the entire `LOG.md` file.

3.  **Analyze Real-World Code:** Perform a broad analysis of the existing codebase to identify emergent patterns or rules in `CLAUDE.md` that are being outdated by practice.

---

### STEP 2: PRESENT A CLEAR CASE FOR CHANGE (THE "HEARING")

Based on your analysis of the **new information only**, present your proposed amendments and their rationale in our chat conversation for my review. You must wait for my explicit confirmation (e.g., "Proceed") before taking any action.

**Structure your message clearly.** For each proposed change, you MUST provide:

- **The Proposed Change:** The exact text to be added, removed, or modified.
- **The Rationale:** A clear, concise explanation of _why_ this change is necessary, citing evidence from your analysis of the new logs or the codebase.

**Example Presentation in Chat:**
I have analyzed all project activity since our last evolution point on [date]. Based on this, I am ready to propose one new amendment to CLAUDE.md.
PROPOSAL: Standardize Error Handling
Proposed Change: Add the following line under the "System Patterns" section:
"- All database-related errors MUST be wrapped in a custom RepositoryError exception."
Rationale: The new log entries show we have handled 3 different raw database exceptions in our last task. Centralizing this will simplify our service-layer logic, as per the lesson learned on [date].
If you agree with this proposal, please reply with "Proceed".

---

### STEP 3: APPLY CHANGES AND CREATE NEW CHECKPOINT (THE "AMENDMENT & SAVE STATE" STEP)

**Wait for my explicit confirmation ("Proceed").**

Once you receive it, perform the following actions sequentially:

1.  **Apply Clean Amendments:** Edit `CLAUDE.md` to apply the changes exactly as you proposed. Do not add any comments or extra text. Submit the changes for my final diff-review in the UI.

2.  **MANDATORY - Log the Evolution Event:** After applying the changes to `CLAUDE.md`, you MUST append a **new `EVOLUTION POINT` block** to the bottom of `LOG.md`. This block serves as the new checkpoint for the future.

    **The block must have this exact format:**

    ```
    ---
    ## EVOLUTION POINT: [YYYY-MM-DD HH:MM:SS]
    **Summary:** The project's constitution (`CLAUDE.md`) was successfully evolved.
    **Changes Applied:**
    *   [A brief summary of the first change you made, e.g., "Standardized error handling to use `RepositoryError`."]
    *   [A brief summary of the second change, if any.]
    **Reasoning:** Based on analysis of all new logs created since the previous evolution point.
    ---
    ```

3.  **Final Confirmation:** Conclude with a clear message: "The approved amendments have been applied to `CLAUDE.md`. A new `EVOLUTION POINT` has been recorded in `LOG.md`, checkpointing our progress. The system is now fully evolved and ready for the next phase."
