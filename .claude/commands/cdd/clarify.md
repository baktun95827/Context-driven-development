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

### STAGE 3: ADAPTIVE CLARIFICATION

**CLARIFICATION STRATEGY:** Ask only what's unclear, adapting to the detail level provided.

**INPUT DETAIL EXAMPLES:**

**VERY DETAILED INPUT (minimal clarification needed):**
```
"Change the login error message in src/auth/login.js line 45 
from 'Login failed' to 'Invalid email or password. Please try again.' 
and make sure it has the same red styling as other error messages."
```
→ **Clarification needed:** None or 1 quick question about edge cases

**MEDIUM DETAILED INPUT (some clarification needed):**
```
"Add email validation to the registration form"
```
→ **Clarification needed:** 2-3 questions about rules, messages, timing

**LOW DETAILED INPUT (lots of clarification needed):**
```
"Fix the login issue"
```
→ **Clarification needed:** 4+ questions about what's broken, expected behavior

**ADAPTIVE QUESTIONING PROCESS:**

**Step 1: Analyze input detail level**
```
**REQUIREMENT ANALYSIS:**
Input: "[user's request]"
Detail level: [High/Medium/Low]
Clear aspects: [list what's specified]
Unclear aspects: [list what needs clarification]
```

**Step 2: Ask targeted questions (max 5)**

**EFFICIENT CLARIFICATION TEMPLATES:**

**For vague requests:**
- "What exactly is the current problematic behavior?"
- "What should happen instead?"
- "Which specific component/file is affected?"
- "How will we know it's working correctly?"

**For medium-detail requests:**
- "Should this follow the existing [pattern] or work differently?"
- "What should happen in [edge case scenario]?"
- "Any specific [format/style/validation] requirements?"

**For detailed requests:**
- "Looks clear - just to confirm: [restate understanding]?"
- Or skip to implementation if truly clear

**SMART DEFAULTS:**
Use project patterns when details aren't specified:
- Error messages → follow existing error message format
- Validation → use current validation approach  
- Styling → match existing component styles
- Behavior → follow established UX patterns

**STREAMLINED CONFIRMATION:**
```
**READY TO IMPLEMENT:**
Change: [one-line summary]
Files: [affected files]
Approach: [brief method]
Duration: [X minutes]

Proceed? (y/n)
```

---

### STAGE 4: STREAMLINED IMPLEMENTATION

**EXECUTION FLOW:**

1. **Quick verification:**
   - Verify current state matches assumptions
   - Confirm no obvious conflicts

2. **Implementation with progress:**
   ```
   🔄 **IMPLEMENTING:** [Brief description]
   📝 **File:** [filename] → [specific change]
   ```

3. **Essential validation:**
   - Test key functionality
   - Verify change works as clarified

**COMPLETION:**
```
✅ **COMPLETED**

**Changed:** [list of files and key changes]
**Duration:** [actual time taken]
**Verified:** [critical functionality tested]

Ready for use.
```

**PATTERN RECOGNITION:**
If similar changes detected:
```
💡 **PATTERN NOTED:** Similar change made recently
Consider using `/cdd:evolve` if this becomes frequent
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
