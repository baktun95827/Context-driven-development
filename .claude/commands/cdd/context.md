# Action: Generate Project Context Snapshot

## OBJECTIVE:
Provide a quick, comprehensive overview of current project state to help with context transitions and session resumption.

**SUCCESS CRITERIA:** Clear snapshot that allows instant project understanding without reading multiple files.

---

### STEP 1: GATHER CURRENT STATE

**COLLECT KEY INFORMATION:**
- [ ] Read `.claude/VISION.md` for project goals
- [ ] Read `CLAUDE.md` for technical rules
- [ ] Scan `.claude/LOG.md` for recent activity (last 5 entries)
- [ ] Check `.claude/cddtasks/` directory for active/pending tasks
- [ ] Identify recently modified files (git status if available)

---

### STEP 2: GENERATE CONTEXT SNAPSHOT

**Present information using this standardized format:**

```markdown
# PROJECT CONTEXT SNAPSHOT
**Generated:** [YYYY-MM-DD HH:MM:SS]

## 🎯 PROJECT MISSION
[One sentence from VISION.md describing what we're building]

## 📋 CURRENT TASKS
**Active Task:** [current task file being worked on, if any]
**Pending Tasks:** [list of .claude/cddtasks/ files that haven't been started]
**Completed Recently:** [last 2 completed tasks from LOG.md]

## 📂 KEY FILES TO KNOW
**Core Documents:**
- `.claude/VISION.md` - Project goals and principles
- `CLAUDE.md` - Technical rules and patterns
- `.claude/LOG.md` - Project history and lessons

**Implementation Files:**
[List 5-8 most important/recently changed files with brief descriptions]

## 🔄 RECENT ACTIVITY
[Last 3 entries from LOG.md - completed tasks, lessons learned, etc.]

## ⚠️ CURRENT FOCUS
[One line describing what phase the project is in or what should be worked on next]

## 💡 KEY PATTERNS & RULES
[2-3 most important rules from CLAUDE.md that affect daily development]
```

---

### STEP 3: PROVIDE NEXT-STEP GUIDANCE

**End with actionable guidance:**

```markdown
## 🚀 RECOMMENDED NEXT ACTIONS
[Based on current state, suggest specific next steps like:]
- "Continue with `/cdd:act .claude/cddtasks/003_...md` to finish authentication"
- "Run `/cdd:plan .claude/cddtasks/004_...md` to plan the dashboard feature"  
- "Use `/cdd:debug [error]` to resolve the failing tests"
- "Start new work with `/cdd:start [description]`"
```

**EFFICIENCY NOTES:**
- Keep descriptions brief but informative
- Focus on actionable insights, not exhaustive details
- Highlight blockers or urgent items
- Include confidence level: "High confidence in next steps" vs "Needs strategic decision"

---

### USAGE SCENARIOS

**When to use `/cdd:context`:**
- ✅ Starting a new development session
- ✅ After taking a break from the project
- ✅ When feeling lost about current state
- ✅ Before making major architectural decisions
- ✅ When onboarding new team members

**Output should help answer:**
- "What is this project trying to achieve?"
- "What work is currently in progress?"
- "What should I work on next?"
- "What are the key constraints and patterns?"
- "What has been learned recently?"