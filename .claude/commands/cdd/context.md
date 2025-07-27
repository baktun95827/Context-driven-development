# Action: Generate Project Foundation Context

## OBJECTIVE:
Provide a comprehensive overview of the project's foundational structure, architecture, and patterns to prepare for any kind of future work.

**SUCCESS CRITERIA:** Clear understanding of project foundations that enables informed decision-making for any new development task.

---

### STEP 1: GATHER FOUNDATIONAL INFORMATION

**COLLECT CORE PROJECT KNOWLEDGE:**
- [ ] Read `.claude/VISION.md` for project mission and principles
- [ ] Read `CLAUDE.md` for technical architecture and patterns
- [ ] Analyze `.claude/LOG.md` for established patterns and lessons learned
- [ ] Examine project structure and organization
- [ ] Identify key technologies, frameworks, and dependencies
- [ ] Understand core business domain and concepts
- [ ] Review existing capabilities and modules

---

### STEP 2: GENERATE FOUNDATION CONTEXT

**Present information using this standardized format:**

```markdown
# PROJECT FOUNDATION CONTEXT
**Generated:** [YYYY-MM-DD HH:MM:SS]

## 🎯 PROJECT MISSION & DOMAIN
[Project's core purpose and business domain from VISION.md]

## 🏗️ ARCHITECTURE & STRUCTURE
**Project Type:** [Web app, CLI tool, library, service, etc.]
**Tech Stack:** [Primary languages, frameworks, databases]
**Architecture Pattern:** [MVC, microservices, layered, etc.]
**Key Dependencies:** [Major libraries and frameworks used]

## 📁 PROJECT ORGANIZATION
**Directory Structure:**
```
project/
├── [key directories and their purposes]
├── [core modules and what they handle]
└── [important configuration files]
```

**Core Modules:**
- [Module 1]: [Purpose and responsibilities]
- [Module 2]: [Purpose and responsibilities]
- [Module 3]: [Purpose and responsibilities]

## 🔧 DEVELOPMENT PATTERNS & CONVENTIONS
**From CLAUDE.md and established practices:**
- **Code Style:** [Formatting, naming conventions]
- **Architecture Rules:** [Design patterns followed]
- **Testing Approach:** [Testing strategy and frameworks]
- **Error Handling:** [How errors are managed]
- **Data Management:** [Database patterns, data flow]

## 💡 ESTABLISHED PATTERNS & LESSONS
**From LOG.md analysis - recurring patterns that work:**
- **[Pattern Type 1]:** [What works well in this project]
- **[Pattern Type 2]:** [Established successful approaches]
- **[Pattern Type 3]:** [Key lessons learned and applied]

## 🔍 DOMAIN CONCEPTS & ENTITIES
**Core business concepts this project deals with:**
- [Entity/Concept 1]: [What it represents and key attributes]
- [Entity/Concept 2]: [What it represents and key attributes]
- [Entity/Concept 3]: [What it represents and key attributes]

## ⚙️ AVAILABLE CAPABILITIES
**What the project can currently do:**
- [Capability 1]: [Brief description]
- [Capability 2]: [Brief description]
- [Capability 3]: [Brief description]

## 📋 TECHNICAL CONSTRAINTS & REQUIREMENTS
**Important limitations and requirements to remember:**
- [Constraint 1]: [Why it matters]
- [Constraint 2]: [Why it matters]
- [Performance Requirements]: [If any specific needs]
- [Compatibility Requirements]: [If any specific needs]
```

---

### STEP 3: PROVIDE STRATEGIC GUIDANCE

**End with strategic insights:**

```markdown
## 🧭 STRATEGIC CONTEXT FOR FUTURE WORK

**PROJECT MATURITY:** [Early stage, growing, established, mature]

**CURRENT CAPABILITIES:** 
[What the project can handle well now]

**ARCHITECTURAL READINESS:**
[What kinds of changes the current architecture supports easily]

**COMMON TASK PATTERNS:**
[Based on LOG.md, what types of work are frequently needed]

**INTEGRATION POINTS:**
[Where new features typically need to connect]

**TECHNICAL DEBT AREAS:**
[Known areas that may need attention in future work]
```

**GUIDANCE PRINCIPLES:**
- Focus on foundational understanding over current status
- Emphasize architecture and patterns over specific features
- Highlight constraints and capabilities that affect future decisions
- Provide context for informed architectural choices

---

### USAGE SCENARIOS

**When to use `/cdd:context`:**
- ✅ Starting work on an unfamiliar project
- ✅ Before planning major new features
- ✅ When making architectural decisions
- ✅ Onboarding new team members to the project
- ✅ After breaks to refresh project understanding
- ✅ Before proposing technical changes

**Output should help answer:**
- "What kind of project is this and how is it structured?"
- "What patterns and conventions should I follow?"
- "What capabilities already exist that I can build on?"
- "What are the key constraints I need to work within?"
- "How should new features integrate with existing architecture?"
- "What technical approaches align with this project's patterns?"