# Action: Find Root Cause and Fix

## OBJECTIVE:

Find the root cause of the error through deep analysis and practical investigation. Focus on understanding why things broke and implementing real fixes.

---

### STEP 1: GATHER FULL CONTEXT

**MANDATORY ACTIONS:**
1. **Load project context:** Read `.claude/VISION.md`, `CLAUDE.md`, and recent entries in `.claude/LOG.md`
2. **Analyze the error:** Examine the error message/stack trace: `$ARGUMENTS`
3. **MANDATORY: Explore related code:**
   - Read ALL files mentioned in the error
   - Search for similar functionality that might be affected
   - Check recent changes to these areas
   - Look for patterns in how this code is used elsewhere

---

### STEP 2: DEEP REFLECTION AND THEORIZATION

**Deeply reflect upon all findings and think about why this isn't working.**

Generate 4-6 different possible sources of the problem:
- Consider immediate causes (what directly failed)
- Consider upstream causes (what led to the failure state)
- Consider design issues (wrong assumptions or patterns)
- Consider integration issues (how components interact)
- Consider data/state issues (unexpected inputs or states)
- Consider timing/order issues (race conditions, initialization)

**Present your analysis:**
```
**INITIAL THEORIES:**
1. [Theory 1]: [Specific explanation with evidence from code]
2. [Theory 2]: [Specific explanation with evidence from code]
3. [Theory 3]: [Specific explanation with evidence from code]
4. [Theory 4]: [Specific explanation with evidence from code]
(continue as needed...)

**DEEP REASONING:**
[Reason through each theory, examining evidence and likelihood]

**MOST PROBABLE CAUSES:**
After deep analysis, the 1-2 most likely root causes are:
1. [Primary root cause with strong evidence]
2. [Secondary possibility if relevant]
```

---

### STEP 3: PROPOSE PRACTICAL FIX

Based on the root cause analysis, present a concrete solution:

```
**PROBLEM:** [What's actually broken - be specific]

**ROOT CAUSE:** [The fundamental reason this happened]

**EVIDENCE FROM CODE:**
- [Specific code snippets or patterns that prove this]
- [Related code that shows why this assumption failed]

**FIX:** 
- [Exact code changes needed]
- [Specific files and line numbers]
- [Any validation or error handling to add]

**PRACTICAL EXAMPLE:**
[Show before/after code snippets demonstrating the fix]

**HOW TO PREVENT THIS:**
[One clear rule based on this specific case]

Reply with "Proceed" to apply the fix.
```

**EXAMPLE ANALYSIS:**

```
**PROBLEM:** API endpoint returns 500 error when user has no profile

**ROOT CAUSE:** Code assumes user.profile always exists, but new users don't have profiles yet

**EVIDENCE FROM CODE:**
- Line 45 in handlers/user.py: `data = user.profile.to_dict()` 
- No null check before accessing profile
- User model shows profile is optional: `profile = relationship("Profile", nullable=True)`

**FIX:**
- Add null check in handlers/user.py line 45:
  ```python
  if user.profile:
      data = user.profile.to_dict()
  else:
      data = {"message": "Profile not created yet"}
  ```

**HOW TO PREVENT THIS:**
Never assume optional relationships exist - always check first
```

---

### STEP 4: APPLY FIX AND LOG LESSON

After user confirms:

1. **Apply the fix** - Make the code changes
2. **Verify it works** - Test that the error is resolved
3. **Check for similar issues** - Search for the same pattern elsewhere
4. **Log the lesson** in `.claude/LOG.md`:

```
---
## LESSON LEARNED: [YYYY-MM-DD HH:MM:SS]
**Problem:** [Specific issue that occurred]
**Root Cause:** [Why it happened]
**Fix Applied:** [What we changed]
**Code Pattern Fixed:** [The problematic pattern we corrected]
**Prevention Rule:** [Simple rule to avoid this]
**Similar Code Checked:** [Other files we verified]
**Files Changed:** [List of modified files]
---
```