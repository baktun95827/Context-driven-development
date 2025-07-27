# Action: Create Task and Generate Detailed Implementation Plan

## OBJECTIVE:

To create a new task file and generate the most detailed and specific implementation plan possible by clarifying all ambiguous requirements through targeted questioning.

**INPUT:** Task description as `$ARGUMENTS` (e.g., "Add user authentication with JWT tokens")

**SUCCESS CRITERIA:** Plan is complete when task file is created, all requirements are clarified, and checklist items are so specific that any competent developer could execute them without further questions.

**CORE PRINCIPLE:** When something is uncertain or vague, always ask the user relevant questions to make sure things are clear before proceeding.

---

### STAGE 1: TASK FILE CREATION

**AUTOMATIC TASK CREATION:**
1. **Generate filename:**
   - Create descriptive snake_case name from `$ARGUMENTS` (max 50 chars)
   - Check `.claude/cddtasks/` directory for next number (001_, 002_, etc.)
   - Format: `{number}_{descriptive_name}.md`

2. **Create task file template:**
   ```markdown
   # TASK: $ARGUMENTS

   **Created:** [YYYY-MM-DD HH:MM:SS]
   **Status:** Planning Complete

   ## Description:
   [One paragraph elaborating on the task based on clarified requirements]

   ## Success Criteria:
   - [ ] [What does "done" look like based on clarified requirements]
   - [ ] [How will we know it works]

   ## Implementation Plan:
   [Ultra-detailed plan will be generated and inserted here]
   ```

**INITIAL VALIDATION:**
- [ ] Is the task description specific enough for initial understanding?
- [ ] Does it describe WHAT to build, not HOW to build it?
- [ ] Is it scoped to a single feature or change?

If task is too vague (like "make the app better"), immediately ask clarifying questions before creating the file.

---

### STAGE 2: CONTEXT LOADING

**MANDATORY PREPARATION:**
- [ ] Read `.claude/VISION.md` for project goals and principles
- [ ] Read `CLAUDE.md` for technical rules and patterns  
- [ ] Scan `.claude/LOG.md` for recent lessons learned
- [ ] Analyze the task description from `$ARGUMENTS`

**CODEBASE DISCOVERY:**
- Extract keywords from task description
- Search for related files: `**/*{keyword1,keyword2,keyword3}*`
- Read existing similar functionality to understand patterns
- Batch read 3-5 related files for context

---

### STAGE 3: REQUIREMENT CLARIFICATION (MANDATORY)

**BEFORE TECHNICAL PLANNING:** Always identify and resolve all ambiguities in the user's requirements.

**AMBIGUITY CHECKLIST:**
- [ ] **Scope:** What exactly is included/excluded?
- [ ] **Behavior:** How should it work in different scenarios?
- [ ] **Data:** What inputs/outputs are expected?
- [ ] **Integration:** How does this connect to existing systems?
- [ ] **Performance:** Any speed/memory/capacity requirements?
- [ ] **Error handling:** How should failures be handled?
- [ ] **UI/UX:** What does the user interaction look like?
- [ ] **Configuration:** What should be configurable vs hard-coded?
- [ ] **Technologies:** Are unfamiliar libraries/frameworks mentioned?
- [ ] **Documentation:** Do we need examples or docs for mentioned tools?

**CLARIFICATION QUESTIONS BY TASK TYPE:**

**For "Add authentication":**
- Which method? (username/password, OAuth, JWT, sessions?)
- What user data to store? (email, username, profile?)
- How to handle failed attempts? (lockout, rate limiting?)
- Password requirements? (length, complexity, reset?)
- Post-login behavior? (redirect, token storage?)

**For "Optimize performance":**
- Which specific operations are slow?
- Current vs target performance metrics?
- Optimize for what? (speed, memory, throughput?)
- Acceptable trade-offs? (speed vs storage?)
- Tools for measurement? (profiling, benchmarks?)

**For "Build dashboard":**
- What specific data to display?
- Who are the users and their roles?
- Real-time updates or on-refresh?
- What actions can users take?
- How should data be filtered/organized?

**For "Add API endpoint":**
- Exact request/response format?
- Authentication/authorization required?
- Rate limiting needed?
- Error response codes to handle?
- Documentation format required?

**For unfamiliar libraries/frameworks:**
```
**KNOWLEDGE REQUEST NEEDED:**
The task mentions [library/framework name] which I need more information about.

**Please provide:**
- Documentation link: [URL to official docs or tutorial]
- Usage examples: [How you want this used in your project]  
- Integration approach: [How it connects to existing code]
- Specific features: [Which features/methods to use]
- Alternative options: [Other libraries you'd consider]

**OR**
- Should I research this library and propose implementation options?
- Would you like me to suggest alternatives I'm familiar with?
```

**For vague technology requirements:**
```
**TECHNICAL CLARIFICATION NEEDED:**
Your request mentions [vague technology reference].

**Please choose your preferred approach:**

**Option A:** [Specific tech stack interpretation]
- Technologies: [Exact libraries/frameworks]
- Implementation: [How they work together]
- Complexity: [Low/Medium/High]
- Time: [Estimate]

**Option B:** [Alternative tech stack interpretation]
- Technologies: [Different libraries/frameworks]
- Implementation: [How they work together]
- Complexity: [Low/Medium/High]  
- Time: [Estimate]

**OR provide missing details:**
- Preferred tech stack or frameworks?
- Performance/scalability requirements?
- Integration constraints?
```

**KNOWLEDGE GAP CHECK:**
Before confirming requirements, check if additional information is needed:

**If unfamiliar libraries/frameworks are mentioned in the task:**
```
**ADDITIONAL INFORMATION NEEDED:**
I need more details about [library/framework name] to create an accurate plan.

**Please provide:**
- Documentation link: [URL to official docs or tutorial you want to follow]
- Usage examples: [Show how this library should be used in your project]
- Integration approach: [How it connects to existing code/architecture] 
- Specific features: [Which features/methods you want to use]
- Alternative options: [Are there other libraries you'd consider?]

**OR if you prefer:**
- Should I research this library and propose implementation options?
- Would you like me to suggest alternative approaches I'm familiar with?
```

**If implementation approach needs clarification:**
```
**TECHNICAL APPROACH CLARIFICATION:**
The requirements could be implemented in multiple ways.

**Please choose your preferred approach:**

**Option A:** [Specific implementation approach]
- What this means: [Clear explanation]
- Technologies used: [Specific tools/libraries]
- Architecture: [How components connect]
- Complexity: [Low/Medium/High]
- Time estimate: [Hours/days]

**Option B:** [Alternative implementation approach]
- What this means: [Clear explanation]
- Technologies used: [Different tools/libraries]
- Architecture: [How components connect]
- Complexity: [Low/Medium/High]
- Time estimate: [Hours/days]

**OR provide missing details:**
- [Specific technical question]
- [Architecture decision needed]
- [Integration requirement unclear]
```

**REQUIREMENT CONFIRMATION:**
Only after all clarifications, confirm understanding:
```
**CLARIFIED REQUIREMENTS:**
- [Specific requirement 1 with technical details]
- [Specific requirement 2 with implementation approach]
- [Specific requirement 3 with integration points]

**CONFIRMED TECHNICAL APPROACH:**
- Libraries/frameworks: [Specific tools to use]
- Architecture pattern: [Design approach]
- Integration points: [How it connects to existing system]
- Documentation provided: [Links/examples received]

Is this understanding complete? Any additional requirements or corrections?
```

---

### STAGE 4: GENERATE ULTRA-DETAILED CHECKLIST

**ANNOUNCEMENT:** "Requirements clarified. Generating ultra-detailed implementation checklist with maximum specificity."

**SPECIFICITY REQUIREMENTS:**
- Each step includes exact file names and function signatures
- Success criteria are measurable and testable
- Data structures and variable names specified
- Integration points and error conditions explicit

**CHECKLIST FORMAT:**
```markdown
## IMPLEMENTATION PLAN

**SUMMARY:** [One sentence describing the agreed approach]
**ESTIMATED TIME:** [Total hours with confidence level]
**COMPLEXITY:** [Low/Medium/High]

### Phase 1: [Phase Name] (Est: X hours)
- [ ] [ACTION] [TARGET] with [SPECIFIC CRITERIA]
  - File: `/exact/path/to/file.ext`
  - Function: `function_name(param1: type, param2: type) -> return_type`
  - Success: [Specific, testable outcome]
  - Validation: [How to verify completion]

### Phase 2: [Phase Name] (Est: X hours)  
- [ ] [ACTION] [TARGET] with [SPECIFIC CRITERIA]
  - File: `/exact/path/to/file.ext`
  - Dependencies: [What must be completed first]
  - Data: [Specific formats/structures used]
  - Success: [Specific, testable outcome]

### Phase 3: Testing & Integration (Est: X hours)
- [ ] Create unit tests in `/path/to/test_file.ext`
  - Test cases: [list 5+ specific scenarios]
  - Expected results: [exact values/behaviors]
  - Edge cases: [specific boundary conditions]
- [ ] Verify integration with [specific components]
  - Integration points: [exact APIs/interfaces]
  - Test data: [specific inputs to use]
  - Success criteria: [measurable outcomes]

**VALIDATION STEPS:**
- [ ] Unit tests: [X specific test cases covering Y scenarios]
- [ ] Integration tests: [specific end-to-end workflows]
- [ ] Performance tests: [specific metrics to achieve]
- [ ] Manual verification: [specific user actions to test]

**ROLLBACK PLAN:** 
- **If Phase 1 fails:** [Specific recovery steps]
- **If Phase 2 fails:** [Alternative approach]
- **Emergency rollback:** [Quick revert procedure]
```

**QUALITY STANDARDS:**
- Each item starts with action verb (Create, Implement, Add, Configure)
- No item takes longer than 60 minutes
- File paths and function names specified when possible
- Dependencies between items are clear
- Success criteria are testable

**FINAL VALIDATION:**
Before appending plan to task file:
- [ ] Plan aligns with VISION.md principles
- [ ] All steps follow CLAUDE.md technical rules
- [ ] File paths match existing project conventions
- [ ] No conflicts with recent tasks in LOG.md
- [ ] Time estimates are realistic (15-60 min per step)

**COMPLETION:**
1. Update the created task file with clarified description and success criteria
2. Append the ultra-detailed implementation plan to the task file
3. Announce: "✅ Task created and planned: `.claude/cddtasks/{filename}.md`. Ready for `/cdd:act {filename}` execution."
4. Provide confidence score based on requirement clarity and plan specificity