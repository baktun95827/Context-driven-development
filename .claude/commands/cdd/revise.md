# Action: Revise an Existing Implementation Plan

## OBJECTIVE:

To intelligently modify the checklist in a task file (`$ARGUMENTS`) based on new information, a failed execution step, or a change in requirements. This command provides a controlled way to adapt our plan without losing momentum.

---

### PRE-REVISION: CONTEXT & PROBLEM LOADING

1.  **MANDATORY: Load Full Context.** Read `VISION.md`, `CLAUDE.md`, the full `LOG.md` (to understand what has been tried), and the current task file at `$ARGUMENTS`.

2.  **State the Problem:** I, the user, will provide you with the reason for this revision. This could be a new requirement, a failed `next` command's error message, or my observation that the plan is flawed. The problem statement will be part of the prompt after the command.
    - **Example Usage:** `/cdd:revise-plan tasks/002_...md The current plan to use library X is not feasible because it's incompatible with our system. We need to switch to library Y.`

---

### STEP 1: RE-EVALUATE AND PROPOSE A NEW STRATEGY

Based on all the context AND the specific problem I've provided, perform the following:

1.  **Acknowledge the Problem:** Start by confirming you understand the issue. _"Acknowledged. The current plan to use library X is not viable. I will now formulate a revised plan centered on library Y."_

2.  **Formulate the Revised Plan:** Think about what needs to change in the _remaining_ incomplete tasks (`- [ ]`) in the checklist. You don't need to change what's already done (`- [x]`). Your revision might involve:
    - **Modifying** existing steps.
    - **Deleting** now-obsolete steps.
    - **Adding** new steps.
    - **Re-ordering** steps.

---

### STEP 2: PRESENT AND APPLY THE REVISED PLAN

Just like `/cdd:evolve`, this is an interactive process where your role is to clearly communicate the change before applying it.

1.  **Present the Revision Proposal in Chat:** Clearly outline the proposed changes to the plan. Do not touch the file yet.

    - **Example Presentation in Chat:**
      > "I have formulated a revised plan.
      >
      > **I will DELETE the following obsolete steps:**
      >
      > - `- [ ] Install library X`
      > - `- [ ] Configure the client for library X`
      >
      > **I will ADD the following NEW steps:**
      >
      > - `- [ ] Install library Y`
      > - `- [ ] Add configuration for library Y to our settings file`
      > - `- [ ] Refactor the service layer to use the new client from library Y`
      >
      > **If you approve this revision, please reply with "Proceed".**"

2.  **Apply the Revision Upon Approval:** Wait for my explicit confirmation ("Proceed"). Once received:

    - Edit the task file (`$ARGUMENTS`) to apply the changes to the checklist.
    - Submit the file change for my final diff-review in the UI.

3.  **Log the Revision:** After the file is successfully updated, append a record to `LOG.md`:

    - `[YYYY-MM-DD HH:MM:SS] REVISED PLAN: The plan for task [$ARGUMENTS] was revised. Reason: [Briefly state the reason, e.g., "Switched from library X to Y due to incompatibility."]`

4.  **Confirm and Conclude:** Announce that the plan has been successfully revised and logged, and that we are now ready to continue with the `/cdd:next` command on the updated plan.
