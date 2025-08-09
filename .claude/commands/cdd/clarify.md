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

**CLARIFICATION DIALOGUE EXAMPLES:**

**SCENARIO 1: Vague Input**
```
User: "Fix the login issue"

Claude: **REQUIREMENT ANALYSIS:**
Input: "Fix the login issue"
Detail level: Low
Clear aspects: Something is wrong with login
Unclear aspects: What's broken, where, expected behavior

**CLARIFICATION QUESTIONS:**
1. What exactly happens when you try to login? (error message, redirect, nothing?)
2. Which login method is affected? (email/password, OAuth, all of them?)
3. When did this start happening?
4. What should happen in a successful login?

User: "Users can't login with email/password, they get 'Login failed' but their credentials are correct"

Claude: **FOLLOW-UP:**
5. Where is this error coming from - the frontend validation or backend response?

User: "Backend - it's rejecting valid passwords"

Claude: **READY TO IMPLEMENT:**
Change: Fix backend password validation logic
Files: [backend auth files]
Approach: Debug password comparison, likely hashing issue
Duration: 30-60 minutes
```

**SCENARIO 2: Medium Detail Input**
```
User: "Add email validation to the registration form"

Claude: **REQUIREMENT ANALYSIS:**
Input: "Add email validation to the registration form"  
Detail level: Medium
Clear aspects: Email field needs validation on registration
Unclear aspects: Validation rules, timing, error display

**CLARIFICATION QUESTIONS:**
1. Should validation happen on input blur, form submit, or both?
2. What error message should show for invalid emails?
3. Any specific email format requirements beyond standard email regex?

User: "On blur would be good, message should say 'Please enter a valid email address'"

Claude: **READY TO IMPLEMENT:**
Change: Add email validation to registration form with blur trigger
Files: [registration form component]
Approach: Add blur event handler with email regex validation
Duration: 15-20 minutes
```

**SCENARIO 3: Detailed Input (minimal clarification)**
```
User: "Change the error message in src/components/LoginForm.js line 47 from 'Invalid login' to 'Invalid email or password' and make it red like other error messages"

Claude: **REQUIREMENT ANALYSIS:**
Input: Very detailed with specific file, line, old text, new text, styling
Detail level: High
Clear aspects: Exact location, exact change, styling requirement
Unclear aspects: None significant

**MINIMAL CLARIFICATION:**
Just to confirm - should this change affect only this one location or are there other places showing 'Invalid login'?

User: "Just this one place"

Claude: **READY TO IMPLEMENT:**
Change: Update error message text and ensure red styling
Files: src/components/LoginForm.js
Approach: Direct text replacement, verify CSS class applied
Duration: 5 minutes
```

**SCENARIO 4: Configuration Change**
```
User: "Update the API timeout in the config"

Claude: **REQUIREMENT ANALYSIS:**
Input: "Update the API timeout in the config"
Detail level: Medium-Low  
Clear aspects: API timeout needs changing
Unclear aspects: Which config, current value, new value, scope

**CLARIFICATION QUESTIONS:**
1. Which config file? (main config, environment-specific?)
2. What should the new timeout value be?
3. Should this apply to all API calls or specific ones?

User: "In config/api.js, change from 5000ms to 10000ms for all calls"

Claude: **READY TO IMPLEMENT:**
Change: Update API timeout from 5s to 10s
Files: config/api.js
Approach: Change timeout value in configuration object
Duration: 2 minutes
```

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
