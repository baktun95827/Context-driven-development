# Action: Clarify Requirements and Execute Simple Changes

## OBJECTIVE:

To handle straightforward changes that don't require detailed planning files but still need clarification of unclear requirements through targeted questioning, then execute them directly.

**INPUT:** Task description as `$ARGUMENTS` (e.g., "Update the error message format", "Add validation to the login form")

**SUCCESS CRITERIA:** All ambiguous requirements are clarified through user dialogue, then the change is implemented directly without creating task files.

**USE CASES:**

- Simple bug fixes with unclear requirements
- Minor feature additions that need scope clarification
- Configuration changes that need parameter clarification
- Updates to existing functionality with ambiguous specifications

---

### STAGE 1: INITIAL ASSESSMENT

**TASK SUITABILITY CHECK:**

- [ ] Is this a simple change (< 3 hours estimated work)?
- [ ] Does it affect only 1-5 files?
- [ ] Is the core requirement clear but details need clarification?
- [ ] Would a full task file be overkill for this change?

**If task is too complex or vague, redirect:**

```
This change appears complex enough to benefit from detailed planning.
Recommended: Use `/cdd:plan` instead for proper task file creation and strategic planning.

Reasons: [explain why full planning would be better]
```

---

### STAGE 2: CONTEXT LOADING

**MANDATORY PREPARATION:**

- [ ] Read `CLAUDE.md` for technical rules and patterns
- [ ] Analyze the change description from `$ARGUMENTS`

**QUICK CODEBASE SCAN:**

- Extract keywords from change description
- Search for affected files: `**/*{keyword1,keyword2}*`
- Read 1-5 relevant files to understand current implementation
- Identify existing patterns that should be followed

---

### STAGE 3: REQUIREMENT CLARIFICATION (MANDATORY)

**BEFORE IMPLEMENTATION:** Always identify and resolve all ambiguities in the user's requirements.

**CLARIFICATION QUESTIONS BY CHANGE TYPE:**

**For "Fix bug in [component]":**

- What exactly is the incorrect behavior?
- What should the correct behavior be?
- Are there specific scenarios where this happens?
- Should we add validation to prevent this in the future?
- How can we test that the fix works?

**For "Update [UI element/message]":**

- What exactly should the new text/appearance be?
- Should this change affect similar elements elsewhere?
- Are there specific user scenarios to consider?
- Does this need to work across different screen sizes/browsers?
- Should we maintain backwards compatibility?

**For "Add validation to [form/input]":**

- What specific validation rules should be applied?
- What error messages should be shown?
- Should validation happen on input, blur, or submit?
- How should valid/invalid states be visually indicated?
- Should existing data be validated against new rules?

**For "Configure [system/tool]":**

- What specific settings need to change?
- What are the current values and desired values?
- Are there environment-specific considerations?
- Should changes be applied to all environments?
- How do we verify the configuration is working?

**For "Improve [performance/UX]":**

- What specific aspect needs improvement?
- How do we measure current vs improved state?
- Are there acceptable trade-offs to consider?
- Which users/scenarios should this help most?
- How will we know the improvement was successful?

**SCOPE CLARIFICATION:**

```
**CHANGE SCOPE CLARIFICATION:**
To ensure I implement exactly what you need:

**Affected Components:**
- [Component 1]: [What changes here?]
- [Component 2]: [What changes here?]
- [Component 3]: [Any related changes needed?]

**Specific Questions:**
- [Question 1 about unclear requirement]
- [Question 2 about implementation approach]
- [Question 3 about edge cases/scenarios]

**Assumptions to Verify:**
- Assumption 1: [state assumption for user to confirm/correct]
- Assumption 2: [state assumption for user to confirm/correct]
```

**REQUIREMENT CONFIRMATION:**
Only after all clarifications, confirm understanding:

```
**CLARIFIED REQUIREMENTS:**
- **What will change:** [Specific component/behavior changes]
- **How it will work:** [New behavior description]
- **Files affected:** [List of files that need updates]
- **Testing approach:** [How to verify the change works]

**IMPLEMENTATION APPROACH:**
- **Method:** [Specific technical approach]
- **Duration:** [Estimated time: X minutes/hours]
- **Risk level:** [Low/Medium with reasoning]

Is this understanding complete? Any corrections or additional requirements?
```

---

### STAGE 4: DIRECT IMPLEMENTATION

**ANNOUNCEMENT:** "Requirements clarified. Implementing change directly with real-time progress updates."

**EXECUTION PATTERN:**

1. **Pre-implementation check:**

   - Verify current state matches assumptions
   - Create backup of affected files (if significant)
   - Confirm no conflicts with recent changes

2. **Step-by-step implementation with progress updates:**

   ```
   **IMPLEMENTING:** [Brief description of current step]
   **File:** [current file being modified]
   **Change:** [what specifically is being changed]
   ```

3. **Real-time validation:**

   - Test each change immediately after implementation
   - Verify integration points still work
   - Check that assumptions hold true

4. **Final verification:**
   - Run any relevant tests
   - Verify the change meets clarified requirements
   - Check for unintended side effects

**COMPLETION ANNOUNCEMENT:**

```
✅ **CHANGE COMPLETED**

**What was changed:**
- [File 1]: [specific changes made]
- [File 2]: [specific changes made]

**Verification completed:**
- [Test/check 1]: ✅ Passed
- [Test/check 2]: ✅ Passed

**Ready for use** - change meets all clarified requirements.
```

---

### STAGE 5: COMPLETION

**FINAL STATUS:**

```
✅ **CHANGE COMPLETED SUCCESSFULLY**

**Summary:** [brief description of what was accomplished]
**Files modified:** [list of files changed]
**Requirements met:** All clarified requirements have been implemented
**No logging required** - this was a simple clarification-based change
```

**PATTERN RECOGNITION:**
If this is the 3rd+ similar change, suggest:

```
**PATTERN DETECTED:** This type of change has been made [X] times recently.
**Consider:** Creating a more systematic approach or documenting this pattern for efficiency.
**Recommend:** Use `/cdd:evolve` to capture this pattern in CLAUDE.md if it becomes frequent.
```

---

### WHEN TO USE `/cdd:clarify` vs `/cdd:plan`

**Use `/cdd:clarify` for:**

- ✅ Bug fixes with unclear scope
- ✅ Minor UI/UX tweaks needing specification
- ✅ Configuration changes with unclear parameters
- ✅ Simple feature additions needing requirement clarification
- ✅ Updates to existing functionality
- ✅ Quick improvements that need direction

**Use `/cdd:plan` instead for:**

- ❌ New features requiring architectural decisions
- ❌ Changes affecting multiple major components
- ❌ Work requiring strategic planning or trade-off analysis
- ❌ Tasks that will take more than a few hours
- ❌ Changes that might affect system architecture

**Decision criteria:**

- **Complexity:** Simple = clarify, Complex = plan
- **Scope:** Single focused change = clarify, Multiple integrated changes = plan
- **Duration:** < 3 hours = clarify, > 3 hours = plan
- **Architecture impact:** No structural changes = clarify, Architectural decisions needed = plan
