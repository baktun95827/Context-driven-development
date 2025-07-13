# Action: Generate Intelligent, Grounded, and Battle-Tested Implementation Plan

## OBJECTIVE:

To create a plan that is deeply rooted in the project's actual, existing code. This plan will not be theoretical; it will be a direct, logical extension of the work that has already been done, informed by all available context.

---

### PRE-PLANNING: MANDATORY CONTEXT LOADING

1.  **Load Foundational Context:** Read `VISION.md` and `CLAUDE.md`.
2.  **Perform Tactical Log Review:** Smart-scan `LOG.md` for `## LESSON LEARNED:` sections.
3.  **Read the Task File:** Read the feature description from `$ARGUMENTS`.

---

### STEP 1: GROUNDED CODE RESEARCH (The Most Critical Step)

Before you can plan, you must become an expert on the _relevant sections_ of this codebase. Perform the following research steps:

1.  **Identify Keywords:** From the task description in `$ARGUMENTS`, extract 2-3 key technical terms (e.g., for "implement JWT auth endpoint", the keywords are `jwt`, `auth`, `endpoint`, `router`).

2.  **Request Relevant Files:** Announce that you are entering the code research phase and **ask me (the user) to provide you with the contents of the files most relevant to these keywords**. You can suggest files based on your general knowledge and the file names you may have seen in the `LOG.md`.

    - **Your Prompt to Me Should Look Like This:**
      > "To create the best plan, I need to study our existing code patterns. Based on the task of implementing a 'JWT auth endpoint', please provide me with the content of the following files, if they exist, or any other files you deem relevant:
      >
      > - `src/routers/user_router.py`
      > - `src/services/auth_service.py`
      > - `src/utils/security.py`
      >   Awaiting files..."

3.  **Analyze Provided Code:** Once I provide the relevant files, you must deeply analyze them to understand:
    - **The "Local Dialect":** What is our specific way of structuring FastAPI routers? How do we handle dependency injection? What does our error handling look like in practice?
    - **Reusable Components:** Are there existing functions, classes, or utilities (like a `get_current_user` dependency) that you must reuse in your plan?
    - **Implicit Patterns:** Identify any consistent coding patterns that are not explicitly written down in `CLAUDE.md`.

---

### STEP 2: SYNTHESIZE & STRATEGIZE (ULTRATHINK)

Now, pause. You have the complete picture. Synthesize all of this information:

- The **Soul** (`VISION.md`)
- The **Laws** (`CLAUDE.md`)
- The **Wisdom** (Lessons from `LOG.md`)
- **The Reality of Our Code** (Your analysis from Step 1)
- The **Task at Hand** (`$ARGUMENTS`)

Formulate your strategy based on this comprehensive, grounded understanding.

---

### STEP 3: GENERATE THE GROUNDED PLAN

Generate the checklist-driven plan.

- **CRITICAL:** Your plan must now be **explicitly grounded in the code you just read**. Reference specific functions to reuse and patterns to follow.
  - **Bad:** "- [ ] Create a new function to hash passwords."
  - **Good:** "- [ ] In `src/utils/security.py`, create a new function `verify_password`, following the same style as the existing `create_access_token` function."
- **Destination:** Append the plan to the task file at `$ARGUMENTS`.

---

### STEP 4: CONFIRMATION

Announce that the grounded plan has been appended. Briefly mention which key files you referenced to create it, so I know the plan is well-informed. Provide a confidence score and state you are ready for `/cdd:next`.
