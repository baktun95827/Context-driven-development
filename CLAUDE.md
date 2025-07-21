# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Core System Architecture

This is the Context-Driven Development (CDD) Framework - a sophisticated system for managing AI-assisted development workflows. The framework treats AI as an "amnesiac genius" that needs comprehensive context before every operation.

**Universal Applicability:** This framework works with any programming language, project type, domain, or complexity level:

- **Languages**: Python, JavaScript, Go, Rust, C++, Java, C#, PHP, Ruby, Swift, Kotlin, etc.
- **Project Types**: CLI tools, desktop apps, mobile apps, games, scientific computing, data analysis, machine learning, system administration, DevOps, embedded systems
- **Domains**: Finance, healthcare, education, research, entertainment, security, infrastructure, automation
- **Scales**: Single-file scripts, multi-module projects, distributed systems, monorepos, microservices

### Memory System

The framework implements a three-layer memory architecture:

1. **STATIC MEMORY (`.claude/CLAUDE.md`)**: Project constitution with technical rules and patterns
2. **STRATEGIC MEMORY (`.claude/VISION.md`)**: High-level project mission and guiding principles  
3. **DYNAMIC MEMORY (`.claude/LOG.md`)**: Chronological log of completed tasks and lessons learned

### Workflow Components

- **Tasks (`tasks/*.md`)**: Individual work units that evolve from simple requests to detailed implementation plans
- **Commands (`.claude/commands/cdd/*.md`)**: Specialized workflow orchestrators for different development phases
- **Atomic Operations**: All file modifications are batched and executed atomically to maintain system consistency

## Essential Commands

### Core Development Workflow
- `ruff check .` - Run linting checks (must pass before any commit)
- `ruff format .` - Format Python code according to project standards

### CDD Framework Commands
The framework provides these specialized commands for managing development workflows:

- `/cdd:start <task_description>` - Initialize new tasks with auto-numbered files
- `/cdd:plan <task_file>` - Generate collaborative implementation plans through strategic dialogue
- `/cdd:act <task_file>` - Execute complete plans atomically with full context loading
- `/cdd:revise <task_file> <changes>` - Modify plans with systemic impact analysis
- `/cdd:debug <error_message>` - Perform root cause analysis and log lessons learned
- `/cdd:evolve` - Update core project rules based on accumulated experience

## Command Execution Patterns

### Context Loading Protocol
Before any significant operation, commands must:
1. Load `.claude/VISION.md` for strategic context
2. Load `.claude/CLAUDE.md` for technical rules
3. Scan `.claude/LOG.md` for relevant lessons learned
4. Analyze existing codebase patterns when making implementation decisions

### Atomic Execution Principle
The `/cdd:act` command follows strict atomic execution:
- All file modifications are performed in-memory first
- Sanity checks prevent inconsistent state changes
- Batch writes occur only after complete successful execution
- Failed operations leave the system in clean state for debugging

### Strategic Planning Process
The `/cdd:plan` command implements collaborative architecture:
- Present multiple implementation approaches with trade-offs
- Engage in structured dialogue to resolve strategic decisions
- Generate detailed, executable checklists based on agreed strategy
- Ensure plans align with both VISION.md principles and CLAUDE.md technical rules

## File Structure Conventions

```
project/
├── .claude/
│   ├── commands/cdd/        # Framework command definitions
│   ├── cddtasks/           # Numbered task files (001_*, 002_*, etc.)
│   ├── VISION.md           # Strategic north star
│   └── LOG.md              # Dynamic project memory
├── CLAUDE.md               # Technical constitution (this file)
└── README.md               # Framework documentation
```

## Development Principles

### Test-Driven Development
All new logic must be introduced via failing tests first. This is enforced by the project constitution.

### Error Handling Strategy
- Use centralized exception handlers for consistent JSON error responses
- Log all errors and their resolutions to LOG.md for future reference
- Perform systemic analysis to prevent recurring issues

### Code Quality Gates
- All Python code must pass `ruff check .` before commits
- Format all code with `ruff format .` 
- Maintain atomic operation integrity across all workflow commands

## Workflow Utilization Guide

### Command Selection by Task Type

**For New Feature Development:**
```
/cdd:start → /cdd:plan → /cdd:act → [/cdd:revise if needed] → completion
```

**For Bug Fixes:**
```
/cdd:debug → [/cdd:revise existing task] → /cdd:act → completion
```

**For Project Understanding:**
```
/cdd:context → analyze output → proceed with appropriate workflow
```

### Detailed Command Usage Scenarios

#### `/cdd:context` - Project State Management
**Use when:**
- Starting a new development session after a break
- Feeling lost about current project state
- Need to understand what's been done recently
- Onboarding team members to the project

**Output helps with:**
- Understanding current active tasks
- Seeing recent completed work and lessons learned
- Identifying next logical steps
- Getting quick project overview without reading multiple files

#### `/cdd:start` - Task Initialization
**Use for:**
- ✅ "Implement sorting algorithm for large datasets"
- ✅ "Add input validation to data parser"  
- ✅ "Create configuration management system"
- ✅ "Fix memory leak in processing pipeline"
- ✅ "Setup automated testing framework"
- ✅ "Implement caching layer for expensive operations"

**Avoid for:**
- ❌ "Make the code better" (too vague)
- ❌ "Add logging and fix bugs and write tests" (multiple tasks)
- ❌ "Write sortArray() method in utils.py" (too prescriptive about HOW)

#### `/cdd:plan` - Strategic Planning
**Best for:**
- Complex features requiring architectural decisions
- Features that touch multiple parts of the system
- When multiple technical approaches are possible
- Features that need integration planning

**Planning scenarios - adapt these examples to your domain:**
- **Data structures** - Choose representations, storage formats, access patterns
- **Processing approach** - Sequential vs parallel, batch vs streaming, algorithms
- **Architecture patterns** - Modular vs monolithic, layers, separation of concerns  
- **Integration points** - How components communicate, interfaces, protocols
- **Error handling** - Recovery strategies, validation approaches, failure modes
- **Performance considerations** - Time complexity, memory usage, bottlenecks

#### `/cdd:act` - Execution Engine
**Use when:**
- Plan is complete and well-defined
- Ready for focused, uninterrupted implementation
- All major decisions have been made
- Checklist items are specific and actionable

**Execution patterns:**
- **Happy path**: All steps execute successfully → automatic logging
- **Interruption**: Clean stop, resume with same command later
- **Sanity check failure**: Automatic recommendation for `/cdd:revise`

#### `/cdd:revise` - Plan Adaptation
**Two modes for different needs:**

**Direct Change Mode** (for clear instructions):
- "Change storage format from JSON to binary"
- "Remove the intermediate caching step"
- "Add input validation before data processing"
- "Use quicksort instead of bubble sort"

**Discussion Mode** (for concerns/questions):
- "Is the separate configuration file really necessary?"
- "This approach seems overly complex"
- "Should we consider using a different algorithm?"
- "What about memory usage implications?"

#### `/cdd:debug` - Error Resolution
**Use for any error type:**
- **Runtime errors**: Null pointer exceptions, index out of bounds, memory issues
- **Logic errors**: Wrong calculations, incorrect algorithms, unexpected behavior
- **Integration errors**: File I/O failures, network issues, external dependency problems
- **Build errors**: Compilation errors, missing dependencies, configuration issues

**Three-level solution approach:**
1. **Immediate fix** - Stop the crash/error right now
2. **Root cause fix** - Prevent this category of error systemically  
3. **Prevention lesson** - Update practices to avoid similar issues

#### `/cdd:evolve` - System Learning
**Run periodically to:**
- Update CLAUDE.md based on accumulated lessons
- Incorporate patterns learned from multiple completed tasks
- Refine development practices based on real experience
- Keep the framework's "constitution" current and effective

### Universal Task Workflows

#### Feature Development (any domain)
```
1. /cdd:start "Implement [domain-specific feature]"
2. /cdd:plan → discovers existing patterns, proposes technical approach
3. /cdd:act → implements core logic, supporting code, tests atomically
4. Pattern learned: feature tasks need core implementation + supporting files + validation
```

#### Data Processing Tasks
```
1. /cdd:start "Process [data type] with [transformation]"
2. /cdd:plan → considers input/output formats, processing strategies
3. /cdd:act → implements processing logic, input validation, output generation
4. Pattern learned: data tasks need parsing + processing + validation + output
```

#### Algorithm Implementation
```
1. /cdd:start "Implement [algorithm name] for [problem]"
2. /cdd:plan → considers time/space complexity, edge cases, testing approach
3. /cdd:act → implements algorithm, handles edge cases, adds comprehensive tests
4. Pattern learned: algorithm tasks need core logic + edge case handling + performance tests
```

#### Configuration/Setup Tasks
```
1. /cdd:start "Setup [tool/environment] for [purpose]"
2. /cdd:plan → considers environment requirements, configuration options
3. /cdd:act → creates configuration files, setup scripts, documentation
4. Pattern learned: setup tasks need configuration + automation + documentation
```

#### Bug Fixes (universal)
```
1. /cdd:debug "[describe the error or unexpected behavior]"
2. /cdd:revise → adjust affected task plan if needed
3. /cdd:act → apply immediate fix + root cause fix + lesson logging
4. Lesson learned: [domain-specific insight to prevent similar issues]
```

### Efficiency Best Practices

#### Context Management
- Use `/cdd:context` at start of each session
- Let commands batch-read related files automatically
- Follow suggested file patterns for your task type

#### Planning Efficiency  
- Trust the structured dialogue in `/cdd:plan`
- Provide clear answers to architectural questions
- Don't overthink - 2-3 options are enough for most decisions

#### Execution Efficiency
- Ensure plans are detailed before running `/cdd:act`
- Let atomic execution complete without interruption when possible
- Use sanity check failures as signals to improve planning

#### Learning Integration
- Pay attention to PATTERN LEARNED entries in LOG.md
- Use patterns from similar completed tasks
- Run `/cdd:evolve` every 5-10 completed tasks

## When to Use CDD vs Direct Development

### **CDD Framework is Better For:**

#### **Complex, Multi-Step Projects**
- Projects with 5+ interconnected tasks where consistency matters
- Features requiring coordination across multiple files/modules
- Work that spans multiple development sessions
- Projects where different people (or AI sessions) need to pick up work

#### **Quality-Critical Development**
- Production systems where mistakes are expensive
- Projects requiring architectural decisions and validation
- Code that needs to be maintainable long-term
- Work requiring systematic error prevention

#### **Team Collaboration Scenarios**
- Multiple developers working on the same codebase
- Projects requiring explicit documentation of decisions
- Systems where knowledge transfer is important
- Work requiring consistent patterns and standards

#### **Learning and Pattern Building**
- Projects where you want to capture and reuse patterns
- Work where systematic improvement is valuable
- Development where lessons learned prevent future issues

### **Direct Claude Code is Better For:**

#### **Simple, Immediate Tasks**
- Quick bug fixes that don't affect architecture
- Single-file changes or updates
- Experimental prototyping and exploration
- Simple documentation updates
- Immediate production fixes

#### **Rapid Development Scenarios**
- Proof-of-concept development
- Throwaway scripts or one-time tools
- Quick experiments to test ideas
- Simple refactoring or cleanup tasks

#### **Low-Stakes Work**
- Personal projects where mistakes are cheap
- Learning exercises and tutorials
- Simple maintenance tasks
- Non-critical feature additions

### **Decision Framework**

**Use CDD when:**
- ✅ Project complexity > individual task complexity
- ✅ Consistency and quality matter more than speed
- ✅ Multiple people will work on or maintain the code
- ✅ You need systematic learning and improvement
- ✅ Mistakes have significant consequences

**Use Direct Approach when:**
- ✅ Task is self-contained and straightforward
- ✅ Speed matters more than systematic approach
- ✅ Work is exploratory or experimental
- ✅ Stakes are low and mistakes are cheap
- ✅ You need maximum flexibility and minimal overhead

### **The Sweet Spot**

**CDD Framework provides maximum value for:**
- **Sustainable development** over **rapid prototyping**
- **Team projects** over **individual experiments**  
- **Long-term systems** over **temporary solutions**
- **Quality-focused work** over **quick-and-dirty tasks**
- **Learning organizations** over **one-off projects**

### **Honest Assessment**

**Framework Overhead Costs:**
- Setup time for task creation and planning
- Mental overhead of choosing the right commands
- File management and organization complexity
- Learning curve for new users

**Framework Value Benefits:**
- Context continuity across sessions prevents lost work
- Pattern recognition speeds up similar future tasks
- Atomic operations prevent half-finished states
- Strategic planning catches issues early
- Systematic learning improves over time

**Bottom Line:** CDD is like proper engineering practices vs quick scripting - both have their place. Choose CDD when the cost of mistakes is high and the project needs to be maintainable. Choose direct interaction when speed and flexibility matter more than systematic approach.

## Working with the Framework

When contributing to this framework:

1. **Understand the Mental Model**: You are working with a system designed to give AI persistent memory and structured workflows
2. **Respect Atomic Operations**: Never partially update files - complete operations or fail cleanly
3. **Maintain Context Integrity**: Always load full context before making decisions
4. **Follow Strategic Dialogue**: Use collaborative planning rather than making unilateral technical decisions
5. **Log Lessons Learned**: Update LOG.md with insights that benefit future development cycles