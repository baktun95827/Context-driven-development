# Action: Propose and Apply Incremental Constitutional Amendments

## OBJECTIVE:

To perform a comprehensive, incremental analysis of the project since the LAST evolution point, leveraging both LOG.md and git history to propose and apply clean amendments to our core constitution (`CLAUDE.md`). This process combines explicit lessons learned with implicit patterns from actual code changes.

---

### STEP 1: INCREMENTAL ANALYSIS & SYNTHESIS

1.  **Read Foundational Docs:** Read `.claude/VISION.md` and `CLAUDE.md`.

2.  **Perform Checkpointed Log Reading:**

    - Scan `.claude/LOG.md` from the **bottom to the top**.
    - Find the **most recent `## EVOLUTION POINT:` marker**.
    - Your analysis of the log MUST focus **ONLY on the log entries that have been created _after_ this marker**.
    - **If no `EVOLUTION POINT:` marker is found** (meaning this is the first time `/evolve` is ever run), then analyze the entire `LOG.md` file.

3.  **Analyze Git History for Hidden Patterns:**

    **Find Evolution Time Boundary:**
    ```bash
    # If evolution point exists in LOG.md, extract its timestamp
    # Otherwise, use reasonable default (e.g., last 50 commits or 30 days)
    git log --since="[last_evolution_date]" --oneline
    ```

    **Extract Commit Patterns:**
    ```bash
    # Analyze commit messages for recurring themes
    git log --since="[date]" --pretty=format:"%s" | sort | uniq -c | sort -rn
    
    # Find frequently modified files (indicates hot spots)
    git log --since="[date]" --name-only --pretty=format: | sort | uniq -c | sort -rn | head -20
    
    # Identify file modification patterns (what files change together)
    git log --since="[date]" --name-only --pretty=format:"---" | awk '/^---/{if(files)print files; files=""} !/^---/{files=files" "$0}' | sort | uniq -c | sort -rn
    ```

    **Analyze Code Changes:**
    ```bash
    # Review actual diffs for patterns not captured in LOG.md
    git diff [last_evolution_commit]..HEAD --stat
    
    # Look for recurring code patterns in changes
    git log --since="[date]" -p | grep -E "^\+" | sort | uniq -c | sort -rn | head -50
    ```

    **Cross-Reference Findings:**
    - Compare git history patterns with LOG.md entries
    - Identify gaps: changes made but not logged as lessons
    - Find implicit patterns: recurring changes that suggest unwritten rules
    - Detect workflow patterns: common sequences of file modifications

4.  **Analyze Real-World Code:** Perform targeted analysis based on git history findings to identify emergent patterns or rules in `CLAUDE.md` that are being outdated by practice.

---

### STEP 2: PRESENT A CLEAR CASE FOR CHANGE (THE "HEARING")

Based on your analysis of **both LOG.md and git history**, present your proposed amendments and their rationale in our chat conversation for my review. You must wait for my explicit confirmation (e.g., "Proceed") before taking any action.

**Structure your message clearly with THREE CATEGORIES of findings:**

1. **EXPLICIT PATTERNS (from LOG.md):**
   - Lessons learned and patterns documented in LOG.md
   - Clear rules that emerged from completed tasks

2. **IMPLICIT PATTERNS (from git history):**
   - Recurring file modification patterns
   - Common commit message themes
   - Files that frequently change together
   - Workflow patterns not captured in LOG.md

3. **PRACTICE VS DOCTRINE GAPS:**
   - Places where actual practice differs from CLAUDE.md rules
   - Emerging conventions not yet documented
   - Outdated rules that are no longer followed

**For each proposed change, you MUST provide:**

- **The Proposed Change:** The exact text to be added, removed, or modified.
- **The Evidence Source:** Whether from LOG.md, git history, or both.
- **The Rationale:** A clear explanation citing specific evidence.

**Example Presentation in Chat:**
```
I have analyzed all project activity since our last evolution point on [date], including:
- X new LOG.md entries
- Y git commits across Z files
- Identified N recurring patterns

## ANALYSIS SUMMARY:

### From LOG.md:
- 3 lessons about error handling
- 2 patterns for API integration

### From Git History:
- Files X, Y, Z modified together in 80% of commits (suggests coupling)
- 15 commits with "fix validation" (suggests validation pattern needed)
- src/utils/* modified 25 times (hot spot needing attention)

### Practice vs Doctrine Gaps:
- CLAUDE.md says "use async/await" but 60% of new code uses promises
- No rule exists for configuration management, but clear pattern emerges

## PROPOSED AMENDMENTS:

### PROPOSAL 1: Standardize Error Handling
**Change:** Add under "System Patterns" section:
"- All database-related errors MUST be wrapped in a custom RepositoryError exception."
**Evidence:** LOG.md (3 lessons) + Git history (8 commits fixing database errors)
**Rationale:** Both explicit lessons and commit patterns show repeated database error issues.

### PROPOSAL 2: Document File Coupling Pattern
**Change:** Add under "Architecture Rules" section:
"- When modifying authentication, always update: auth.service, auth.guard, and user.model together."
**Evidence:** Git history only - these files changed together in 12/15 auth-related commits
**Rationale:** Strong implicit pattern not previously documented, would prevent incomplete changes.

If you agree with these proposals, please reply with "Proceed".
```

---

### STEP 3: APPLY CHANGES AND CREATE NEW CHECKPOINT (THE "AMENDMENT & SAVE STATE" STEP)

**Wait for my explicit confirmation ("Proceed").**

Once you receive it, perform the following actions sequentially:

1.  **Apply Clean Amendments:** Edit `CLAUDE.md` to apply the changes exactly as you proposed. Do not add any comments or extra text. Submit the changes for my final diff-review in the UI.

2.  **MANDATORY - Log the Evolution Event with Git Reference:** After applying the changes to `CLAUDE.md`, you MUST append a **new `EVOLUTION POINT` block** to the bottom of `LOG.md`. This block serves as the new checkpoint for the future.

    **The enhanced block must have this exact format:**

    ```
    ---
    ## EVOLUTION POINT: [YYYY-MM-DD HH:MM:SS]
    **Summary:** The project's constitution (`CLAUDE.md`) was successfully evolved.
    **Analysis Scope:**
    *   LOG.md entries analyzed: [X entries since last evolution point]
    *   Git commits analyzed: [Y commits since YYYY-MM-DD]
    *   Files with most changes: [top 3 frequently modified files]
    **Changes Applied:**
    *   [A brief summary of the first change you made, e.g., "Standardized error handling to use `RepositoryError`."]
    *   [A brief summary of the second change, if any.]
    **Evidence Sources:**
    *   From LOG.md: [number of supporting patterns/lessons]
    *   From Git History: [number of implicit patterns discovered]
    *   Practice vs Doctrine: [number of gaps addressed]
    **Reasoning:** Based on comprehensive analysis of both explicit lessons in LOG.md and implicit patterns from git history since the previous evolution point.
    ---
    ```

3.  **Final Confirmation:** Conclude with a clear message: "The approved amendments have been applied to `CLAUDE.md`. A new `EVOLUTION POINT` has been recorded in `LOG.md` with full git history reference, checkpointing our progress. The system is now fully evolved and ready for the next phase."

---

### APPENDIX: PATTERN DETECTION GUIDE

**Common Patterns to Extract from Git History:**

1. **File Coupling Patterns:**
   - Files that are frequently modified together indicate architectural coupling
   - Example: If `auth.controller.js` and `auth.service.js` change together 90% of the time

2. **Hotspot Patterns:**
   - Files modified most frequently may need refactoring or special attention
   - Example: If `utils/helpers.js` is modified in 40% of commits, it might be doing too much

3. **Commit Message Patterns:**
   - Recurring themes in commit messages reveal common tasks or issues
   - Example: Many "fix validation" commits suggest need for validation framework

4. **Workflow Patterns:**
   - Common sequences of file modifications reveal development workflows
   - Example: Always modifying test files after implementation files

5. **Technology Patterns:**
   - Introduction or removal of dependencies/frameworks
   - Example: Gradual migration from callbacks to async/await

6. **Bug Fix Patterns:**
   - Files frequently appearing in bug fix commits need attention
   - Example: If `payment.service.js` appears in 70% of "fix" commits

7. **Refactoring Patterns:**
   - Large-scale changes that affect many files at once
   - Example: Renaming patterns, architectural shifts

**Git Commands for Pattern Detection:**

```bash
# Find files that change together (correlation analysis)
git log --name-only --pretty=format: | awk 'NF' | sort | uniq -c | sort -rn

# Analyze commit message patterns
git log --pretty=format:"%s" | awk '{print $1}' | sort | uniq -c | sort -rn

# Find bug-prone files
git log --grep="fix\|bug\|issue" --name-only --pretty=format: | sort | uniq -c | sort -rn

# Identify refactoring commits
git log --grep="refactor\|restructure\|reorganize" --stat

# Track file rename/move patterns
git log --follow --name-status -- [file_path]

# Find commits by specific authors (for team patterns)
git shortlog -sn --since="30 days ago"

# Analyze code churn (additions/deletions)
git log --numstat --pretty=format: | awk 'NF==3 {plus+=$1; minus+=$2; files[$3]++} END {for (f in files) print f, files[f], plus, minus}'
```

**Integration with LOG.md:**
- Cross-reference git patterns with LOG.md lessons
- Validate that logged lessons match actual practice
- Identify gaps where practice diverges from documentation
