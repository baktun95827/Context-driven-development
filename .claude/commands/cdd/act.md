# Action: Execute Implementation Plan Atomically

## OBJECTIVE:

Execute all checklist items in the plan file (`$ARGUMENTS`) as a single atomic operation. Either all steps complete successfully, or no permanent changes are made.

**SUCCESS CRITERIA:** All checklist items marked as `[x]` and comprehensive log entry created.

---

### STEP 1: STARTUP & VALIDATION

**MANDATORY PREPARATION:**
- [ ] Read `.claude/VISION.md` and `CLAUDE.md` for context
- [ ] Read complete plan from `$ARGUMENTS` task file  
- [ ] Verify plan has clear checklist items (`- [ ]` format)
- [ ] Initialize internal progress tracker (no file writes yet)

**BATCH CONTEXT LOADING:**
Before starting execution, proactively read related files based on task patterns:

**Auto-Read Strategy:**
1. **Scan plan for file mentions** - Read any files specifically named in checklist items
2. **Pattern-based loading** - Based on task type, batch-read likely needed files:

**Common File Patterns:**
- **Data structures mentioned** → Also read related business logic and tests
- **API/service endpoints** → Read routing, validation, and related processing logic
- **Database/storage changes** → Read schema definitions, access patterns, migrations
- **UI components** → Read similar components, styling, and interaction patterns
- **Test creation** → Read existing test files in same area for patterns

**Batch Reading Strategy:**
```
Extract keywords from plan → Generate search patterns:

Plan mentions "data processing":
→ Search for: **/*{data,process,parse,transform}* and read related files

Plan mentions "file operations":  
→ Search for: **/*{file,io,read,write,stream}* and read existing patterns

Plan mentions "algorithm implementation":
→ Search for: **/*{algorithm,sort,search,calculate}* and read similar implementations

Plan mentions "configuration setup":
→ Search for: **/*{config,setup,env,init}* and read configuration patterns
```

**EFFICIENCY RULE:** Read all likely-needed files NOW to avoid context switching during execution.

**VALIDATION QUESTIONS:**
1. Are all checklist items specific and actionable?
2. Do I understand what success looks like for each item?
3. Are there any obvious conflicts with VISION.md or CLAUDE.md?

**QUICK CONSISTENCY CHECKS:**
- [ ] **Naming conventions:** Do file/function names match existing patterns?
- [ ] **Import patterns:** Are imports organized consistently with existing files?
- [ ] **Code style:** Does approach match CLAUDE.md rules (TDD, API design, etc.)?
- [ ] **VISION alignment:** Does this work support "Simplicity Above All" principle?
- [ ] **No regressions:** Will this break existing functionality?

**IF VALIDATION FAILS:** Stop immediately and recommend `/cdd:revise-plan`.

---

### STEP 2: EXECUTION LOOP

**FOR EACH INCOMPLETE CHECKLIST ITEM (`- [ ]`):**

#### A. SANITY CHECK (Before Acting)
Ask these specific questions:
- "Does this step logically follow from what I just completed?"
- "Am I about to contradict something I did earlier?"
- "Do I have all the information needed to complete this step?"

**SANITY CHECK EXAMPLES:**
- ✅ PASS: Previous step created a model, current step writes tests for that model
- ❌ FAIL: Previous step deleted a file, current step tries to modify the same file
- ❌ FAIL: Current step requires information not specified in the plan

**IF SANITY CHECK FAILS:** ABORT entire operation, report the conflict, recommend `/cdd:revise-plan`.

#### B. EXECUTE STEP
- Perform the exact action described in checklist item
- Use tools as needed (Read, Write, Edit, Bash, etc.)
- Ensure action aligns with existing codebase patterns

#### C. RECORD PROGRESS (In Memory Only)
Add one line to internal log using this format:
```
✓ [Phase/Item]: [Brief description of what was actually done]
```

**EXAMPLE LOG ENTRIES:**
```
✓ Setup: Created User model in models/user.py with email and password fields
✓ Auth: Implemented JWT token generation in utils/auth.py  
✓ Tests: Added unit tests for User model validation in tests/test_user.py
```

#### D. CONTINUE LOOP
Move immediately to next `- [ ]` item without any chat output.

---

### STEP 3: ATOMIC COMPLETION

**ONLY EXECUTE IF ALL STEPS SUCCEEDED:**

#### A. ANNOUNCE SUCCESS
"✅ All plan steps completed successfully. Performing atomic file updates..."

#### B. UPDATE LOG.MD (Single Write Operation)
Append task completion and check for patterns:

**STANDARD COMPLETION LOG:**
```
---
## COMPLETED TASK: [YYYY-MM-DD HH:MM:SS]
**Task File:** [exact filename from $ARGUMENTS]
**Total Steps:** [number of checklist items completed]
**Summary:**
[paste complete internal log here]
---
```

**PATTERN DETECTION:**
After 3+ similar tasks, also add a PATTERN LEARNED entry:
```
---
## PATTERN LEARNED: [YYYY-MM-DD HH:MM:SS]
**Task Type:** [Auth/API/Frontend/Testing/etc.]
**When Working On:** [type of feature/change]
**Files That Always Need Changes:** [consistent files modified]
**Common Steps:** [recurring implementation steps]
**Example Task:** [this task file as reference]
**Efficiency Gain:** [how following this pattern saves time]
---
```

**Pattern Examples:**
- **Data processing tasks** typically need: input parsing, processing logic, output formatting, validation
- **Algorithm tasks** typically need: core implementation, edge case handling, performance tests
- **Configuration tasks** typically need: setup files, validation logic, documentation
- **File handling tasks** typically need: I/O operations, error handling, format validation

#### C. UPDATE TASK FILE (Single Write Operation)  
Change all `- [ ]` to `- [x]` for completed items in the task file.

#### D. FINAL CONFIRMATION
"🎯 Execution complete. LOG.md and task file atomically updated. System ready for next task."

---

### ERROR HANDLING

**EXECUTION FAILS:** 
- Report specific error with step that failed
- Do NOT write to any files
- Recommend appropriate next action:
  - Code errors → `/cdd:debug [error message]`
  - Plan conflicts → `/cdd:revise-plan [task file]`
  - Missing info → Ask user for clarification

**INTERRUPTION OCCURS:**
- Stop immediately  
- Do NOT write to any files
- Report current progress
- System remains in clean state for resume

**RECOVERY INSTRUCTIONS:**
- Small fixes: Use `/cdd:revise-plan` to adjust problematic steps
- Major issues: Use `/cdd:debug` for root cause analysis
- Resume: Re-run `/cdd:act` after fixes (will skip completed items if task file was updated)