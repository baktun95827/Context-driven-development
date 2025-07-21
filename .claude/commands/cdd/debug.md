# Action: Perform Deep Diagnosis and Systemic Debugging

## OBJECTIVE:

To not just fix the provided error, but to understand its root cause at the deepest level. This command initiates a comprehensive "post-mortem" analysis to ensure that we not only solve the immediate problem but also extract valuable lessons to make the entire system more robust for the future.

---

### STAGE 1: IMMEDIATE CONTEXT & PROBLEM INGESTION

1.  **MANDATORY: Load Full Project Context:** Read `.claude/VISION.md`, `CLAUDE.md`, and the full `.claude/LOG.md` to understand the project's state leading up to the error.
2.  **Analyze Error Message:** Deeply analyze the user-provided error message and stack trace: `$ARGUMENTS`.

---

### STAGE 2: STRUCTURED ROOT CAUSE ANALYSIS

Perform systematic debugging by answering these specific questions:

#### **A. ERROR CLASSIFICATION**
1. **What type of error is this?**
   - [ ] Syntax/compile error (missing imports, typos)
   - [ ] Runtime error (NoneType, KeyError, etc.)  
   - [ ] Logic error (wrong behavior, incorrect calculations)
   - [ ] Integration error (API calls, database connections)
   - [ ] Configuration error (environment, settings)

#### **B. IMMEDIATE CAUSE ANALYSIS**
2. **What exactly failed?**
   - Specific line/function that threw the error
   - Expected vs actual behavior
   - Input values that triggered the failure

3. **Why did this specific line fail?**
   - What assumption was violated?
   - What precondition was missing?
   - What data was unexpected?

#### **C. DEEPER INVESTIGATION**
4. **How did we get to this state?**
   - Trace backwards from error to origin
   - Check recent changes in `.claude/LOG.md`
   - Review implementation against original plan

5. **What systemic patterns emerge?**
   - Is this similar to previous issues?
   - Does this violate CLAUDE.md rules?
   - Does this conflict with VISION.md principles?

#### **D. ROOT CAUSE SYNTHESIS**
Combine findings into a clear theory:
```
**ROOT CAUSE THEORY:**
- **Immediate cause:** [what specific thing failed]
- **Contributing factors:** [what conditions enabled this]  
- **Systemic issue:** [broader pattern or design flaw]
- **Prevention strategy:** [how to prevent this category of error]
```

---

### STAGE 3: MULTI-LAYERED SOLUTION

Present a 3-level solution using this structured format:

```
**DEBUG SOLUTION PROPOSAL**

**ERROR:** [One sentence describing the specific error]

**LEVEL 1: IMMEDIATE FIX** ⚡
- **What:** [Specific code change to stop the crash]
- **Where:** [Exact file and line/function]
- **Action:** [Precise description of the fix]

**LEVEL 2: ROOT CAUSE FIX** 🔧  
- **Root Cause:** [The underlying reason this happened]
- **What:** [Changes to prevent this category of error]
- **Where:** [Files/functions to modify for systemic fix]
- **Action:** [Precise description of the structural changes]

**LEVEL 3: PREVENTION LESSON** 🛡️
- **Pattern:** [What type of error this represents]
- **Lesson:** [Rule to prevent similar issues in future]
- **Action:** [Log specific lesson to help future planning]

**Reply with "Proceed" to apply all three levels.**
```

**SOLUTION EXAMPLES:**

**Runtime Error Example:**
- Level 1: Add null check (`if user is not None:`)
- Level 2: Modify function to raise exception instead of returning None
- Level 3: "Always validate that dependencies cannot return None"

**Logic Error Example:**  
- Level 1: Fix the calculation in the specific function
- Level 2: Add input validation to prevent invalid states
- Level 3: "Add validation steps to all user input processing"

**Integration Error Example:**
- Level 1: Add try/catch around the API call
- Level 2: Implement proper retry and timeout logic
- Level 3: "All external service calls need error handling and fallbacks"

---

### STAGE 4: APPLY FIXES AND LOG LESSON

**ONLY AFTER RECEIVING "Proceed" CONFIRMATION:**

#### **A. APPLY CODE FIXES**
1. **Level 1 Fix:** Apply immediate fix to stop the error
2. **Level 2 Fix:** Apply root cause fix for systemic improvement  
3. **Submit Changes:** Present all file changes for user review

#### **B. LOG THE LESSON** 
Add structured entry to `.claude/LOG.md`:

```
---
## LESSON LEARNED: [YYYY-MM-DD HH:MM:SS]
**Error Type:** [Runtime/Logic/Integration/etc.]
**Problem:** [Brief description of what went wrong]
**Root Cause:** [Underlying reason for the failure]
**Solution:** [What was changed to fix it]
**Prevention Rule:** [Specific rule to prevent similar issues]
**Files Changed:** [List of modified files]
---
```

#### **C. FINAL CONFIRMATION**
"🐛 Debug complete. Error fixed at multiple levels and lesson logged for future prevention."

**VALIDATION:**
- [ ] Immediate error is resolved
- [ ] Root cause is addressed  
- [ ] Lesson is logged in structured format
- [ ] User can continue with development
