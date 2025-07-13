# Action: Execute Next Step in Plan

1.  **MANDATORY: Load Context.** Read `VISION.md` and `CLAUDE.md` fully.
2.  **Read Plan:** Read the task file at `$ARGUMENTS` and identify the FIRST incomplete checklist item (`- [ ]`). If the item has incomplete sub-tasks, select the first incomplete sub-task instead.
3.  **Execute:** Perform the action described in that checklist item precisely.
4.  **MANDATORY: Log Progress.** After successful completion, append a summary of what you just did to the bottom of `LOG.md`, including a timestamp. Format it like this: `[YYYY-MM-DD HH:MM:SS] COMPLETED: [Brief summary of the completed task] from task file [$ARGUMENTS].`
5.  **Update Task List:** Edit the task file (`$ARGUMENTS`) and mark the item you just completed as done (`- [x]`).
6.  **Confirm:** Announce the step is complete and that you are ready for the next `/cdd:next` command.
