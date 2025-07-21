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
Discover related files by analyzing the task and project patterns:

**DISCOVERY METHOD:**
1. **Extract keywords** from task description (nouns, verbs, domain terms)
2. **Search for related patterns** using those keywords
3. **Look for similar functionality** already implemented
4. **Find configuration and setup** files that might be relevant

**UNIVERSAL SEARCH PATTERNS:**
```
Extract keywords from ANY task type → Generate search patterns:

"user login system" → **/*{user,login,auth,session,credential,security}*
"data processing pipeline" → **/*{data,process,transform,parse,pipeline,etl}*
"machine learning model" → **/*{model,train,predict,feature,dataset,ml}*
"game physics engine" → **/*{physics,collision,vector,engine,simulation}*
"file compression tool" → **/*{compress,zip,archive,encode,decode}*
"trading algorithm" → **/*{trade,market,price,order,strategy,portfolio}*
"image processing" → **/*{image,pixel,filter,transform,vision,graphics}*
"network protocol" → **/*{network,protocol,socket,tcp,udp,connection}*
"database optimization" → **/*{database,query,index,optimize,performance}*
"embedded sensor" → **/*{sensor,gpio,i2c,spi,hardware,embedded}*
"web scraper" → **/*{scrape,parse,extract,html,web,crawler}*
"configuration management" → **/*{config,settings,env,properties,yaml,json}*
"testing framework" → **/*{test,spec,mock,fixture,assert,verify}*
"documentation generator" → **/*{doc,readme,help,guide,manual,generate}*
```

**RELATIONSHIP DISCOVERY:**
```
For each task, systematically discover:

**Similar Functionality:**
- Search for: **/*{synonym1,synonym2,related_concept}*
- Look for existing implementations of similar problems
- Find code that handles related data types or operations

**Dependencies & Integration Points:**
- Search for: **/*{input_format,output_format,interface}*  
- Find what provides input to your task
- Find what consumes output from your task
- Identify shared utilities, libraries, or frameworks

**Configuration & Constants:**
- Search for: **/*{config,const,param,setting,default}*
- Find where similar settings are defined
- Look for environment variables, config files, constants

**Tests & Validation:**
- Search for: **/*{test,spec,example,demo,sample}*
- Find how similar functionality is tested
- Look for validation patterns and edge cases

**Documentation & Context:**
- Search for: **/*{doc,readme,comment,guide,spec}*
- Find design documents or architectural decisions
- Look for usage examples and API documentation
```

**DISCOVERY STRATEGY:**
1. **Extract domain concepts** from task description (don't assume categories)
2. **Generate search keywords** from those concepts  
3. **Use Glob patterns** to find related files: `**/*{keyword1,keyword2,keyword3}*`
4. **Examine project structure** to understand organization patterns
5. **BATCH READ** related files in single operation for efficiency:
   - Group similar functionality together
   - Read in logical dependency order 
   - Use multiple Read tool calls in one message for parallel processing
6. **Adapt to project conventions** - follow patterns you discover

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

**Option A: [Descriptive Name]**
- **Pros:** [2-3 specific advantages for this project context]
- **Cons:** [2-3 specific drawbacks or trade-offs]  
- **Effort:** [Rough time estimate: hours/days]
- **Complexity:** [Low/Medium/High]

**Option B: [Descriptive Name]**
- **Pros:** [2-3 specific advantages for this project context]
- **Cons:** [2-3 specific drawbacks or trade-offs]
- **Effort:** [Rough time estimate: hours/days] 
- **Complexity:** [Low/Medium/High]

**KEY DECISIONS NEEDED:**
1. [Specific decision question about approach/architecture]
2. [Specific decision question about constraints/requirements]
3. [Optional: Specific decision question about integration/dependencies]

**CONTEXT CONSIDERATIONS:**
- **Performance requirements:** [speed/memory/throughput needs]
- **Maintainability needs:** [how often this will be modified]
- **Integration constraints:** [what this connects to/depends on]
```

**EXAMPLE DIALOGUE:**
```
**TASK ANALYSIS:** Implement efficient sorting for large datasets in memory-constrained environment.

**TECHNICAL OPTIONS:**

**Option A: Quicksort with Custom Pivot**
- **Pros:** Fast average case O(n log n), in-place sorting, well-understood
- **Cons:** Worst case O(n²), not stable, recursive stack usage
- **Effort:** 4-6 hours
- **Complexity:** Medium

**Option B: External Merge Sort**  
- **Pros:** Guaranteed O(n log n), stable, handles datasets larger than RAM
- **Cons:** Requires disk I/O, more complex implementation, temporary files
- **Effort:** 8-12 hours
- **Complexity:** High

**KEY DECISIONS NEEDED:**
1. What's the maximum dataset size we need to handle?
2. Is sorting stability important for this use case?
3. Are there memory constraints that rule out certain approaches?
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

**SUMMARY:** [One sentence describing the agreed approach and why it was chosen]
**ESTIMATED TOTAL TIME:** [Total hours/days with confidence level]
**COMPLEXITY:** [Low/Medium/High]

### Phase 1: [Phase Name] (Est: X hours)
- [ ] [Specific action with measurable success criteria]
- [ ] [Include file names, function signatures, or specific deliverables]
- [ ] [Each item should take 15-60 minutes maximum]
- [ ] [Include any prerequisites or dependencies]

### Phase 2: [Phase Name] (Est: X hours)  
- [ ] [Continue with specific, actionable items]
- [ ] [Ensure each step builds logically on previous ones]

### Phase 3: [Validation & Integration] (Est: X hours)
- [ ] [Testing strategy with specific test cases]
- [ ] [Integration verification steps]
- [ ] [Performance/quality validation]

**VALIDATION STEPS:**
- [ ] [Unit tests: specific test cases to implement]
- [ ] [Integration tests: end-to-end verification]
- [ ] [Manual verification: specific scenarios to check]
- [ ] [Performance benchmarks: specific metrics to measure]

**ROLLBACK PLAN:** 
- **If Phase 1 fails:** [Specific recovery steps]
- **If Phase 2 fails:** [Alternative approach or rollback procedure]
- **Emergency rollback:** [How to quickly revert all changes]

**DEPENDENCIES & ASSUMPTIONS:**
- [External dependencies this plan relies on]
- [Key assumptions that could invalidate the approach]
- [Integration points that must remain stable]
```

**EXAMPLE CHECKLIST:**
```markdown
## IMPLEMENTATION PLAN

**SUMMARY:** Implement quicksort with median-of-three pivot selection for balanced performance
**ESTIMATED TOTAL TIME:** 6 hours (High confidence)
**COMPLEXITY:** Medium

### Phase 1: Core Algorithm (Est: 3 hours)
- [ ] Create `quicksort()` function with signature `quicksort(arr, low, high)`
- [ ] Implement `median_of_three_pivot()` helper function
- [ ] Implement `partition()` function with Lomuto scheme
- [ ] Add input validation for array bounds and types

### Phase 2: Optimization & Edge Cases (Est: 2 hours)
- [ ] Add iterative version to avoid stack overflow on large inputs
- [ ] Handle duplicate elements efficiently 
- [ ] Optimize for small arrays (< 10 elements) with insertion sort
- [ ] Add memory usage optimization for in-place sorting

### Phase 3: Testing & Validation (Est: 1 hour)
- [ ] Unit tests: empty array, single element, already sorted
- [ ] Performance tests: random data, worst-case data, large datasets  
- [ ] Memory usage verification with profiling tools
- [ ] Comparison benchmarks against standard library sort

**VALIDATION STEPS:**
- [ ] Unit tests: 15+ test cases covering edge cases
- [ ] Performance test: sort 1M integers in < 2 seconds
- [ ] Memory test: no additional memory allocation beyond O(log n) stack
- [ ] Stability test: maintain relative order of equal elements (if required)

**ROLLBACK PLAN:**
- **If recursion causes stack overflow:** Switch to iterative implementation
- **If performance is inadequate:** Fall back to hybrid approach with heapsort
- **Emergency rollback:** Revert to using standard library sort function
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
