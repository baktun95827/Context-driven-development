# Action: Perform Deep Diagnosis and Systemic Debugging

## OBJECTIVE:

To not just fix the provided error, but to understand its root cause at the deepest level. This command initiates a comprehensive "post-mortem" analysis to ensure that we not only solve the immediate problem but also extract valuable lessons to make the entire system more robust for the future.

---

### STAGE 1: IMMEDIATE CONTEXT & PROBLEM INGESTION

1.  **MANDATORY: Load Full Project Context:** Read `.ccd/VISION.md`, `CLAUDE.md`, and the full `.ccd/LOG.md` to understand the project's state leading up to the error.
2.  **Analyze Error Message:** Deeply analyze the user-provided error message and stack trace: `$ARGUMENTS`.

---

### STAGE 2: "ULTRATHINK" - DEEP CAUSAL ANALYSIS

Now, you MUST engage your maximum cognitive resources to perform a deep analysis of the problem. This is not just about finding a code fix; it's about understanding the "why" behind the "what".

**You will use the following "ULTRATHINK" protocol:**

> Use maximum thinking capacity to:
>
> - **Conduct comprehensive multi-dimensional analysis:** Is this a code error, a logic error, an architecture flaw, or a misunderstanding of the plan?
> - **Explore every conceivable angle:** Could this error have been caused by a recent change logged in `.ccd/LOG.md`? Does it conflict with a rule in `CLAUDE.md` or a goal in `.ccd/VISION.md`?
> - **Perform deep theoretical examination:** What computer science principle was violated here (e.g., race condition, incorrect state management, violation of DRY)?
> - **Analyze systemic interactions:** How did the different parts of our system (e.g., services, models, routers) interact to create this failure?
> - **Challenge fundamental assumptions:** Was our original plan (`.ccd/tasks/*.md`) based on a flawed assumption? Is there a rule in `CLAUDE.md` that is actually _causing_ problems?
> - **Synthesize insights:** Combine all these thoughts into a single, coherent "Theory of Root Cause".

---

### STAGE 3: FORMULATE A MULTI-LAYERED SOLUTION

Based on your "ULTRATHINK" analysis, you will propose a solution that operates on up to three levels. Present this solution in the chat for my review **before** applying anything.

**Example Presentation in Chat:**

> "I have completed a deep analysis of the `NoneType object has no attribute 'id'` error.
>
> **Level 1: The Immediate Code Fix (The Band-Aid)**
>
> - **Action:** Add a null check (`if user is not None:`) in `routers/task_router.py` before accessing `user.id`.
> - **I will apply this fix to resolve the immediate crash.**
>
> **Level 2: The Root Cause Fix (The Cure)**
>
> - **Root Cause:** The `get_current_user` dependency can, in some edge cases, return `None`, but our application logic assumes it always returns a valid user. This is a systemic flaw.
> - **Action:** I will modify the `get_current_user` dependency to raise a specific `HTTPException(401, "User not authenticated")` instead of returning `None`. This makes the "user not found" case explicit and handled correctly at the framework level.
>
> **Level 3: The Systemic Lesson (The Vaccine)**
>
> - **Lesson:** Our plans must always explicitly account for functions or dependencies that can return `None`.
> - **Action:** I will now log this as a `LESSON LEARNED` in `.ccd/LOG.md` so that future planning (`/plan`) and evolution (`/evolve`) can incorporate this knowledge.
>
> **If you agree with this multi-layered solution, please reply with "Proceed".**"

---

### STAGE 4: APPLY AND LOG UPON APPROVAL

**Wait for my explicit confirmation ("Proceed").**

Once received, perform the following actions:

1.  **Apply Code Fixes:** Apply the necessary code changes (from both Level 1 and Level 2, if applicable) and submit them for my final diff-review.
2.  **MANDATORY: Log the Lesson:** Append the rich, detailed `LESSON LEARNED` block (from Level 3) to `LOG.md`.
3.  **Confirmation:** Announce that the issue has been resolved at multiple levels and the lesson has been permanently logged.
