# Action: Initialize a New Task

## OBJECTIVE:
Create a properly structured task file from the user's description: "$ARGUMENTS"

## VALIDATION:
**Check task description quality:**
- [ ] Is the description specific and actionable?
- [ ] Does it describe WHAT to build, not HOW to build it?
- [ ] Is it scoped to a single feature or change?

**GOOD TASK EXAMPLES:**
- ✅ "Implement user authentication with JWT tokens"
- ✅ "Add email validation to user registration"  
- ✅ "Create a dashboard for admin users"
- ✅ "Fix memory leak in background task processor"

**POOR TASK EXAMPLES:**
- ❌ "Make the app better" (too vague)
- ❌ "Use React hooks and implement auth with JWT and add tests" (multiple tasks)
- ❌ "Write UserService.authenticate() method in auth.py" (too prescriptive about HOW)

## TASK CREATION PROCESS:

1. **GENERATE FILENAME**
   - Create descriptive snake_case name (max 50 chars)
   - Check `.claude/cddtasks/` directory for next number (001_, 002_, etc.)
   - Format: `{number}_{descriptive_name}.md`

2. **CREATE TASK FILE** 
   Create file in `.claude/cddtasks/` directory with this template:

   ```markdown
   # TASK: $ARGUMENTS

   **Created:** [YYYY-MM-DD HH:MM:SS]
   **Status:** Planning Required

   ## Description:
   [One paragraph elaborating on the task if needed]

   ## Success Criteria:
   - [ ] [What does "done" look like?]
   - [ ] [How will we know it works?]

   ## Implementation Plan:
   _This plan has not been generated yet. Run `/cdd:plan` on this file to create it._
   ```

3. **CONFIRM CREATION**
   Announce: "✅ Task created: `.claude/cddtasks/{filename}.md`. Next step: run `/cdd:plan {filename}` to generate implementation plan."

## VALIDATION FAILURE:
If task description is too vague or complex, suggest improvements:
"⚠️ Task description needs refinement. Consider: [specific suggestions for improvement]"
