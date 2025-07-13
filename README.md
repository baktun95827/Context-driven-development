Of course. Here is a comprehensive and well-structured README.md file for our First-Principles CDD (Context-Driven Development) Framework.

This document explains the project's philosophy, its structure, and provides a clear, practical guide on how to use it, including different workflows and detailed command examples.

The First-Principles CDD Framework

Welcome to the First-Principles Context-Driven Development (CDD) Framework. This isn't just a collection of prompts; it's a complete, systematic methodology for collaborating with Large Language Models like Claude Code to build software. It's designed from first principles to be simple, powerful, and resilient.

This framework transforms you from a "prompt engineer" into a Project Director, managing a brilliant but amnesiac AI engineer. Your role is to provide strategic direction, and this framework automates the rest, ensuring quality, consistency, and a persistent "memory" for your project.

Core Philosophy: Every file and every command has a unique, non-overlapping purpose. The system is designed to be lean, logical, and self-correcting.

🚀 Quick Start & Core Concept

To start using this framework:

Clone this repository.

Define your Vision: Open VISION.md and write down the mission and guiding principles of your project. This is your project's soul.

Establish Laws: Open .claude/CLAUDE.md and define the technical stack, architecture patterns, and coding standards. This is your project's constitution.

Start your first task with /cdd:start.

Follow the workflows outlined below.

📂 Project Structure

This framework uses a minimal set of files, each with a critical role:

Generated code
your-project/
├── .claude/
│ ├── commands/
│ │ └── cdd/
│ │ ├── start.md # Creates a new task
│ │ ├── plan.md # Generates a detailed plan for a task
│ │ ├── act.md # Securely executes ONE step (with full context)
│ │ ├── do.md # Quickly executes ONE step (with recent context)
│ │ ├── revise-plan.md # Modifies a plan when it's flawed
│ │ ├── debug.md # Debugs an error and logs the lesson
│ │ └── evolve.md # Evolves the project's core rules over time
│ └── CLAUDE.md # STATIC MEMORY: The Project Constitution.
├── tasks/ # Holds all evolving feature/task files.
├── LOG.md # DYNAMIC MEMORY: The immutable Captain's Log.
└── VISION.md # STRATEGIC MEMORY: The Project's North Star.

🛠️ The Commands: Your Toolkit

These commands form a complete lifecycle for software development.

Command Role When to Use
/cdd:start Project Manager To initiate a new feature or task.
/cdd:plan Chief Architect To create a detailed, intelligent, step-by-step plan for an initiated task.
/cdd:act Safety Officer To securely execute the first step of a plan, or to restart after an interruption.
/cdd:do Worker To rapidly execute consecutive steps in a plan during a smooth workflow.
/cdd:revise-plan Strategist When an existing plan is flawed or needs to change course.
/cdd:debug Technical Expert When an error occurs during execution.
/cdd:evolve Constitutional Congress Periodically, to update the project's core rules (CLAUDE.md) based on learnings.
⚙️ Workflows: How to Use the Framework

Follow these workflows for different scenarios.

Workflow 1: The "Happy Path" (Building a New Feature)

This is the standard, most common workflow from idea to completion.

Scenario: You want to add a new user authentication feature.

Start the Task:

Generated bash
/cdd:start Implement user authentication with JWT tokens
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

AI creates tasks/001_implement_user_auth.md.

Generate the Plan:

Generated bash
/cdd:plan tasks/001_implement_user_auth.md
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

AI analyzes VISION.md, CLAUDE.md, and the task description, then appends a detailed checklist to the task file.

Execute the First Step (Safely):

Generated bash
/cdd:act tasks/001_implement_user_auth.md
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

AI reads ALL core context files and executes the first checklist item. This "warms up" its short-term memory.

Execute Subsequent Steps (Quickly):

Generated bash
/cdd:do
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Claude automatically uses the same file argument as the last command. AI executes the next step, skipping the expensive re-reading of VISION.md and CLAUDE.md.

Repeat until Done: Continue using /cdd:do until all checklist items are marked complete.

Workflow 2: The "Reality Path" (Handling Problems)

Things don't always go as planned. This workflow shows how to adapt.

Scenario: While using /cdd:do, you hit a step that fails or realize the plan is wrong.

Execution Fails:

Generated bash
/cdd:do
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

> AI: "HALT. Sanity check failed. My previous action conflicts with this one. I recommend running /cdd:revise-plan."

Revise the Flawed Plan:

Generated bash
/cdd:revise-plan tasks/001_implement_user_auth.md The current library is incompatible, we must use `another-library` instead.
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

AI proposes changes to the checklist, awaits your "Proceed", applies them, and logs the revision.

Restart with a Safe act: After the plan is revised, use /cdd:act to restart the execution flow. This ensures the AI re-reads all context and fully understands the new plan.

Generated bash
/cdd:act tasks/001_implement_user_auth.md
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

Return to the "Happy Path": Once you're back on track, switch back to the fast /cdd:do for subsequent steps.

Workflow 3: The "Learning Path" (Project Evolution)

Over time, your project will teach you things. This workflow formalizes that learning.

Scenario: After completing several features, you notice you keep fixing the same type of bug.

Initiate an Evolution Session:

Generated bash
/cdd:evolve
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
Bash
IGNORE_WHEN_COPYING_END

AI analyzes all new LESSON LEARNED entries in LOG.md since the last evolution point.

Review the Proposal:

> AI: "I propose we add a new rule to CLAUDE.md to always validate user input with Pydantic models to prevent NoneType errors... If you agree, please reply with 'Proceed'."

Approve the Change:

You: "Proceed"

Finalize the Evolution:
AI edits CLAUDE.md for your final diff-review and approval, then adds a new EVOLUTION POINT checkpoint to LOG.md. The project's "constitution" is now smarter for all future tasks.

💡 Command Examples

/cdd:start Create a CI/CD pipeline using GitHub Actions

/cdd:plan tasks/002_create_ci_cd_pipeline.md

/cdd:act tasks/002_create_ci_cd_pipeline.md

/cdd:do (No arguments needed if following another act or do)

/cdd:revise-plan tasks/002\_...md The current plan uses outdated actions. We need to update to the latest v4 actions.

/cdd:debug [Paste a full error message here from your terminal]

/cdd:evolve
