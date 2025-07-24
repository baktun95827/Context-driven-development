# Context-Driven Development (CDD) Framework

A sophisticated system for managing AI-assisted development workflows that treats AI as an "amnesiac genius" requiring comprehensive context before every operation.

## Overview

The CDD Framework provides structured workflows for software development with AI assistance, implementing a three-layer memory architecture and atomic operations to ensure consistency and quality across any programming language, project type, or domain.

## Universal Applicability

This framework works with any:
- **Languages**: Python, JavaScript, Go, Rust, C++, Java, C#, PHP, Ruby, Swift, Kotlin, etc.
- **Project Types**: CLI tools, desktop apps, mobile apps, games, scientific computing, data analysis, machine learning, system administration, DevOps, embedded systems
- **Domains**: Finance, healthcare, education, research, entertainment, security, infrastructure, automation
- **Scales**: Single-file scripts, multi-module projects, distributed systems, monorepos, microservices

## Core Architecture

### Memory System

The framework implements a three-layer memory architecture:

1. **STATIC MEMORY (`.claude/CLAUDE.md`)**: Project constitution with technical rules and patterns
2. **STRATEGIC MEMORY (`.claude/VISION.md`)**: High-level project mission and guiding principles  
3. **DYNAMIC MEMORY (`.claude/LOG.md`)**: Chronological log of completed tasks and lessons learned

### File Structure

```
project/
├── .claude/
│   ├── commands/cdd/        # Framework command definitions
│   ├── cddtasks/           # Numbered task files (001_*, 002_*, etc.)
│   ├── VISION.md           # Strategic north star
│   └── LOG.md              # Dynamic project memory
├── CLAUDE.md               # Technical constitution
└── README.md               # Framework documentation
```

## Commands

The framework provides these specialized commands for managing development workflows:

### Core Commands

- **`/cdd:start <task_description>`** - Initialize new tasks with auto-numbered files
- **`/cdd:plan <task_file>`** - Generate collaborative implementation plans through strategic dialogue
- **`/cdd:act <task_file>`** - Execute complete plans atomically with full context loading
- **`/cdd:revise <task_file> <changes>`** - Modify plans with systemic impact analysis
- **`/cdd:debug <error_message>`** - Perform root cause analysis and log lessons learned
- **`/cdd:context`** - Generate comprehensive project state snapshot
- **`/cdd:evolve`** - Update core project rules based on accumulated experience

## Command Workflows

### For New Feature Development
```
/cdd:start → /cdd:plan → /cdd:act → [/cdd:revise if needed] → completion
```

### For Bug Fixes
```
/cdd:debug → [/cdd:revise existing task] → /cdd:act → completion
```

### For Project Understanding
```
/cdd:context → analyze output → proceed with appropriate workflow
```

## Command Usage Examples

### `/cdd:start` - Task Initialization
**Good Examples:**
- ✅ "Implement user authentication with JWT tokens"
- ✅ "Add email validation to user registration"  
- ✅ "Create configuration management system"
- ✅ "Fix memory leak in processing pipeline"

**Avoid:**
- ❌ "Make the code better" (too vague)
- ❌ "Add logging and fix bugs and write tests" (multiple tasks)
- ❌ "Write sortArray() method in utils.py" (too prescriptive about HOW)

### `/cdd:plan` - Strategic Planning
Best for complex features requiring architectural decisions, multiple technical approaches, or integration planning. Engages in structured dialogue to resolve strategic decisions before implementation.

### `/cdd:act` - Execution Engine
Executes plans atomically - either all steps complete successfully or no permanent changes are made. Includes comprehensive context loading and sanity checks.

### `/cdd:revise` - Plan Adaptation
Two modes:
- **Direct Change Mode**: "Change storage format from JSON to binary"
- **Discussion Mode**: "Is the separate configuration file really necessary?"

### `/cdd:debug` - Error Resolution
Three-level solution approach:
1. **Immediate fix** - Stop the crash/error right now
2. **Root cause fix** - Prevent this category of error systemically  
3. **Prevention lesson** - Update practices to avoid similar issues

### `/cdd:context` - Project State Management
Use when starting new sessions, feeling lost about current state, or needing quick project overview.

### `/cdd:evolve` - System Learning
Run periodically to update CLAUDE.md based on accumulated lessons and refine development practices.

## Universal Task Workflows

### Feature Development (any domain)
```
1. /cdd:start "Implement [domain-specific feature]"
2. /cdd:plan → discovers existing patterns, proposes technical approach
3. /cdd:act → implements core logic, supporting code, tests atomically
```

### Algorithm Implementation
```
1. /cdd:start "Implement [algorithm name] for [problem]"
2. /cdd:plan → considers time/space complexity, edge cases, testing approach
3. /cdd:act → implements algorithm, handles edge cases, adds comprehensive tests
```

### Configuration/Setup Tasks
```
1. /cdd:start "Setup [tool/environment] for [purpose]"
2. /cdd:plan → considers environment requirements, configuration options
3. /cdd:act → creates configuration files, setup scripts, documentation
```

## Key Principles

### Atomic Operations
All file modifications are batched and executed atomically to maintain system consistency. Failed operations leave the system in clean state for debugging.

### Context Loading Protocol
Before any significant operation, commands must:
1. Load `.claude/VISION.md` for strategic context
2. Load `.claude/CLAUDE.md` for technical rules
3. Scan `.claude/LOG.md` for relevant lessons learned
4. Analyze existing codebase patterns when making implementation decisions

### Strategic Planning Process
The `/cdd:plan` command implements collaborative architecture through structured dialogue to resolve strategic decisions and generate detailed, executable checklists.

## When to Use CDD vs Direct Development

### **CDD Framework is Better For:**

#### **Complex, Multi-Step Projects**
- Projects with 5+ interconnected tasks where consistency matters
- Features requiring coordination across multiple files/modules
- Work that spans multiple development sessions

#### **Quality-Critical Development**
- Production systems where mistakes are expensive
- Projects requiring architectural decisions and validation
- Code that needs to be maintainable long-term

#### **Team Collaboration Scenarios**
- Multiple developers working on the same codebase
- Projects requiring explicit documentation of decisions
- Systems where knowledge transfer is important

### **Direct Approach is Better For:**

#### **Simple, Immediate Tasks**
- Quick bug fixes that don't affect architecture
- Single-file changes or updates
- Experimental prototyping and exploration

#### **Rapid Development Scenarios**
- Proof-of-concept development
- Throwaway scripts or one-time tools
- Quick experiments to test ideas

## Getting Started

1. **Define your Vision**: Create `.claude/VISION.md` with your project's mission and guiding principles
2. **Establish Technical Rules**: Create `CLAUDE.md` with your technical stack, architecture patterns, and coding standards
3. **Start your first task**: Use `/cdd:start "Your first feature description"`
4. **Follow the workflows**: Use `/cdd:plan` to create implementation plans, then `/cdd:act` to execute them

## Framework Benefits

- **Context continuity** across sessions prevents lost work
- **Pattern recognition** speeds up similar future tasks
- **Atomic operations** prevent half-finished states
- **Strategic planning** catches issues early
- **Systematic learning** improves over time

The CDD Framework transforms AI-assisted development from ad-hoc prompting into systematic, quality-focused engineering practices suitable for any project scale or complexity.