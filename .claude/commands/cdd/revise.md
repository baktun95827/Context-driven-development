Of course. Here is the complete and final revise-plan.md file, incorporating all the discussed features, including the crucial instruction for systemic, holistic plan analysis to avoid ripple effects. This file is ready to be saved and used in your CDD framework.

Generated markdown

# Action: Revise an Active Implementation Plan

## OBJECTIVE:

To serve as the ultimate partner for critical plan adaptation. My directive is to ensure the plan in `$ARGUMENTS` is always optimal. When revising, I will analyze the **entire plan checklist**—including completed, current, and future steps—to ensure the proposed changes are **systemic, consistent, and account for any potential ripple effects.** I will first perform a comprehensive, self-sufficient analysis of the project's ground truth, then diagnose your intent to determine the correct mode of interaction: either efficient execution for direct commands or a deep, consultative analysis for all other inquiries.

---

### STEP 0: FULL CONTEXT ASSIMILATION & REALITY CHECK (Mandatory)

This is the non-negotiable setup phase I will perform silently before every interaction.

1.  **Load Foundational Context:** I will read `.cdd/VISION.md`, `CLAUDE.md`, and the full `.cdd/LOG.md` to establish a complete understanding of the project's strategic goals, technical laws, and operational history.
2.  **Load Current State:** I will read the target task file at `$ARGUMENTS` and the user's prompt to define the core problem, question, or directive.
3.  **Autonomous Codebase Analysis:** To ensure my analysis is grounded in reality, I will immediately perform a self-sufficient code research process. This involves identifying key files related to your request and reading their contents to understand our project's actual, existing implementation patterns—our "ground truth."

---

### STEP 1: INTENT CLASSIFICATION

Analyze the user prompt and classify it into one of two clear modes:

#### **MODE A: DIRECT CHANGE REQUEST**

**TRIGGER PATTERNS:**
- "Change [X] to [Y]"
- "Replace [X] with [Y]" 
- "Remove [X]"
- "Add [step description]"
- "Use [library/approach] instead"

**EXAMPLES:**
- ✅ "Change the database from Postgres to SQLite"
- ✅ "Remove the authentication steps"  
- ✅ "Add a validation step after user creation"
- ✅ "Use FastAPI instead of Flask"

**ACTION:** Proceed directly to **STEP 2A: EXECUTE CHANGE**.

#### **MODE B: DISCUSSION/QUESTION**

**TRIGGER PATTERNS:**
- Questions: "Should we...", "Is it necessary...", "What about..."
- Concerns: "This seems complex", "I'm worried about..."
- Observations: "This plan feels...", "The approach looks..."

**EXAMPLES:**
- ✅ "Is creating a separate database file really necessary?"
- ✅ "This approach seems overly complex"
- ✅ "Should we consider using a different library?"
- ✅ "What about performance implications?"

**ACTION:** Proceed to **STEP 2B: CONSULTATIVE ANALYSIS**.

---

### STEP 2: EXECUTE BASED ON INTENT

#### **STEP 2A: EXECUTE DIRECT CHANGE**

1. **ACKNOWLEDGE & ANALYZE**
   - Confirm understanding: "Executing change: [restate the requested change]"
   - Analyze impact: Review entire plan to identify which steps are affected
   - Check for conflicts: Ensure change doesn't contradict completed work

2. **QUICK VALIDATION CHECKS:**
   - [ ] Does change align with VISION.md principles?
   - [ ] Does change follow CLAUDE.md technical rules?
   - [ ] Are we maintaining code consistency with existing patterns?
   - [ ] Will this change create more complexity or reduce it?

3. **IMPACT ASSESSMENT**
   Use this structured format:
   ```
   **CHANGE IMPACT ANALYSIS:**
   - Steps to REMOVE: [list specific checklist items]
   - Steps to MODIFY: [list items that need adjustment]  
   - Steps to ADD: [list new items needed]
   - Dependencies affected: [which other steps depend on these changes]
   ```

4. **PRESENT REVISION**
   - Show exact changes in standardized format
   - Proceed to **STEP 3: GET APPROVAL**

#### **STEP 2B: CONSULTATIVE ANALYSIS**

1. **PROBLEM ANALYSIS**
   - Identify the core concern or question
   - Analyze current plan against project VISION.md and CLAUDE.md
   - Research relevant codebase patterns

2. **GENERATE OPTIONS**
   Present exactly 2 options using this template:
   ```
   **ANALYSIS COMPLETE. Two paths forward:**
   
   **Option 1: [Keep Current Approach]**
   - Pros: [2-3 specific advantages]
   - Cons: [2-3 specific drawbacks]
   - Impact: [how many steps affected]
   
   **Option 2: [Alternative Approach]** 
   - Pros: [2-3 specific advantages]
   - Cons: [2-3 specific drawbacks]
   - Impact: [how many steps affected]
   
   **My recommendation:** [Clear preference with reasoning]
   **Your decision:** Which option should I implement?
   ```

3. **AWAIT DECISION**
   - Wait for user choice
   - Once decided, proceed to formulate detailed changes
   - Move to **STEP 3: GET APPROVAL**

---

### STEP 3: GET APPROVAL

Present the proposed changes using this standardized format:

```
**PLAN REVISION PROPOSAL**

**SUMMARY:** [One sentence describing the overall change]

**CHANGES TO MAKE:**

**REMOVE these steps:**
- [ ] [exact checklist item text]
- [ ] [exact checklist item text]

**MODIFY these steps:**  
- [ ] [old text] → [new text]
- [ ] [old text] → [new text]

**ADD these new steps:**
- [ ] [new checklist item with clear success criteria]
- [ ] [new checklist item with clear success criteria]

**IMPACT:** [X steps removed, Y steps modified, Z steps added]

**Reply with "Proceed" to apply these changes.**
```

**WAIT FOR EXPLICIT "Proceed" CONFIRMATION** before making any file changes.

---

### STEP 4: APPLY CHANGES

**ONLY AFTER RECEIVING "Proceed":**

1. **APPLY CHANGES**
   - Edit the task file (`$ARGUMENTS`) with exact changes as proposed
   - Submit file changes for user review
   
2. **LOG THE REVISION**
   - Add brief entry to `.claude/LOG.md`:
   ```
   ## PLAN REVISED: [YYYY-MM-DD HH:MM:SS]
   **Task:** [task file name]
   **Change:** [brief description of what was changed]
   ```

3. **FINAL CONFIRMATION**
   - "✅ Plan revision complete. Use `/cdd:act` to resume execution."
   - Do NOT continue discussion unless user asks follow-up questions
