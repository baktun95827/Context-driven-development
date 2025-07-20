# Action: Collaboratively Generate an Implementation Plan

## OBJECTIVE:

To act as an expert technical architect, creating a clear, actionable implementation plan through structured dialogue. The final output will be a detailed checklist with time estimates and clear success criteria.

**SUCCESS CRITERIA:** Plan is complete when all major decisions are made and checklist items are specific enough that any competent developer could execute them.

---

### STAGE 1: CONTEXT LOADING & ANALYSIS

**VALIDATION CHECKLIST:**
- [ ] Read `.claude/VISION.md` for project goals and principles
- [ ] Read `CLAUDE.md` for technical rules and patterns  
- [ ] Scan `.claude/LOG.md` for recent lessons learned
- [ ] Analyze existing codebase patterns for consistency

**SMART FILE DISCOVERY:**
Based on the task type, also consider reading related files using these **generic patterns**:

**For Authentication/User Features:**
- User-related data structures (models, entities, classes)
- Authentication logic (login, verification, permissions)
- Security middleware or guards
- Existing auth-related tests

**For API/Service Features:**
- Endpoint definitions (routes, controllers, handlers)
- Business logic (services, use cases, domain logic)
- Data access patterns (repositories, DAOs, queries)
- Request/response handling

**For UI/Frontend Features:**
- Similar UI components or views
- State management patterns
- Styling or theming files
- User interaction handlers

**For Testing Features:**
- Existing test files in the same area
- Test configuration and setup files
- Test utilities and helpers
- Mock or fixture data

**For Data/Storage Features:**
- Schema definitions
- Migration files
- Data access layers
- Configuration files

**DISCOVERY STRATEGY:**
1. Identify task category (auth, api, ui, data, testing, etc.)
2. Use keywords to search: `**/*{auth|user|login}*` or `**/*{test|spec}*`
3. Look for naming patterns in the existing codebase
4. **BATCH READ** related files in single operation for efficiency:
   - Group similar functionality together
   - Read in logical dependency order 
   - Use multiple Read tool calls in one message for parallel processing
5. Note any patterns or conventions to follow in the plan

**BATCH READING EFFICIENCY TIPS:**
- ✅ Read 3-5 related files in one message using multiple tool calls
- ✅ Prioritize files that establish patterns (existing similar features)
- ✅ Include test files to understand expected behavior patterns
- ✅ Adapt search terms to project's actual naming conventions
- ❌ Don't assume specific folder structures or file extensions
- ❌ Don't read files one-by-one - batch them for better context understanding

**BRAINSTORMING FRAMEWORK:**
Ask yourself these specific questions:
1. What are the 2-3 main technical approaches for this feature?
2. What are the key architectural decisions that must be made?
3. What existing patterns in the codebase should be followed?
4. What could go wrong with each approach?

**OUTPUT:** Prepare 2-3 concrete options with clear pros/cons.

---

### STAGE 2: STRUCTURED PLANNING DIALOGUE

**DIALOGUE TEMPLATE:**

```
**TASK ANALYSIS:** [One sentence summary of what we're building]

**TECHNICAL OPTIONS:**

**Option A: [Name]**
- **Pros:** [2-3 specific advantages]
- **Cons:** [2-3 specific drawbacks]  
- **Effort:** [Rough time estimate]

**Option B: [Name]**
- **Pros:** [2-3 specific advantages]
- **Cons:** [2-3 specific drawbacks]
- **Effort:** [Rough time estimate]

**KEY DECISIONS NEEDED:**
1. [Specific decision question]
2. [Specific decision question]
3. [Maximum 3 questions total]
```

**ITERATION RULES:**
- Limit discussion to maximum 3 decision rounds
- Each round should resolve 1-2 major architectural choices
- Always provide specific, actionable options
- Stop when technical approach is clearly defined

---

### STAGE 3: GENERATE FINAL CHECKLIST

**ANNOUNCEMENT:** "Planning complete. Generating detailed implementation checklist based on our decisions."

**CHECKLIST FORMAT:**
```markdown
## IMPLEMENTATION PLAN

**SUMMARY:** [One sentence describing the agreed approach]
**ESTIMATED TOTAL TIME:** [Total hours/days]

### Phase 1: [Phase Name] (Est: X hours)
- [ ] [Specific action with clear success criteria] 
- [ ] [Include file names and function signatures where possible]
- [ ] [Each item should take 15-60 minutes maximum]

### Phase 2: [Phase Name] (Est: X hours)
- [ ] [Continue pattern...]

**VALIDATION STEPS:**
- [ ] [How to verify each phase works]
- [ ] [Integration tests or manual verification steps]

**ROLLBACK PLAN:** [What to do if something goes wrong]
```

**QUALITY CHECKS:**
- Each checklist item starts with a verb
- No item takes longer than 60 minutes  
- Success criteria are testable
- File paths and function names are specified when possible
- Dependencies between items are clear

**FINAL ACTIONS:**
1. **VALIDATION CHECKS:** Before appending plan, verify:
   - [ ] Plan aligns with VISION.md principles (especially "Simplicity Above All")
   - [ ] All steps follow CLAUDE.md technical rules (TDD, API design, etc.)
   - [ ] File paths and naming follow existing project conventions
   - [ ] No conflicts with recently completed tasks (check LOG.md)
   - [ ] Estimated times are realistic (15-60 min per step)

2. Append formatted plan to task file `$ARGUMENTS`
3. Confirm plan is ready for `/cdd:act` execution
4. Provide confidence score (High/Medium/Low) based on plan clarity and validation
