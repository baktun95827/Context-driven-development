# Action: Collaboratively Generate an Implementation Plan

## OBJECTIVE:

To act as an expert technical architect, collaborating with the human user through an interactive dialogue to create the best possible implementation plan for the task defined in `$ARGUMENTS`. The final output will be a highly detailed, mutually-agreed-upon checklist appended to the task file.

---

### STAGE 1: ANALYSIS & PREPARATION (Silent, Internal Step)

1.  **MANDATORY: Load Full Context:** Read `.ccd/VISION.md`, `CLAUDE.md`.
2.  **Tactical Log Review:** Smart-scan `.ccd/LOG.md` for `## LESSON LEARNED:` sections.
3.  **Grounded Code Research:** As we previously designed, formulate a request for relevant code files to understand existing patterns. **(Wait for user to provide the code).**
4.  **Initial Brainstorming:** Based on all the above, internally brainstorm several potential approaches to implementing the feature. Identify key decision points (e.g., "Should we use a relational DB or a NoSQL store for this data?", "Should this be a real-time feature with WebSockets or a simple polling mechanism?").

---

### STAGE 2: THE PLANNING DIALOGUE (Interactive Conversation)

You will now initiate a structured conversation with me (the user) to refine the plan.

1.  **Present High-Level Options & Ask Key Questions:**

    - Start by summarizing your understanding of the task.
    - Present the 2-3 main architectural or implementation options you've identified. For each option, briefly list its pros and cons in this specific project's context.
    - End by asking clear, high-level questions to guide the decision.

    **Example of the First Message to Me:**

    > "I have analyzed the request to implement a 'real-time notification system'. Based on our `.ccd/VISION.md` which emphasizes simplicity and our `CLAUDE.md` which uses FastAPI, I see two main approaches:
    >
    > **Option A: WebSockets**
    >
    > - **Pros:** True real-time, highly efficient.
    > - **Cons:** Adds complexity to our stack (requires managing persistent connections).
    >
    > **Option B: Server-Sent Events (SSE)**
    >
    > - **Pros:** Simpler than WebSockets, uses standard HTTP.
    > - **Cons:** One-way communication only (server to client).
    >
    > **To proceed, I need your guidance:**
    >
    > 1.  Which approach do you believe better aligns with our "Simplicity Above All" principle?
    > 2.  Do we anticipate needing client-to-server real-time communication in the future?"

2.  **Iterate and Refine Based on My Feedback:**
    - Wait for my answers.
    - Based on my responses, either make a decision and propose the next level of detailed questions, or refine the options.
    - Continue this dialogue until all major architectural and technical decisions have been made and we have a clear, shared vision for the implementation path.

---

### STAGE 3: GENERATE THE FINAL BLUEPRINT

Once the dialogue is complete and all key decisions have been made, perform the following:

1.  **Announce Finalization:** State clearly that the planning dialogue is complete and you will now generate the final, detailed checklist based on our agreed-upon strategy.

    - **Example:** "Great, thank you for the clarifications. Based on our decision to use Server-Sent Events, I will now generate the detailed step-by-step implementation plan."

2.  **Generate the Checklist:** Create the final, highly detailed, step-by-step Markdown checklist. This checklist should be a direct translation of our decisions into concrete, executable tasks.

3.  **Append to Task File:** Append this final plan to the task file at `$ARGUMENTS`.

4.  **Confirmation:** Announce that the final, mutually-agreed-upon plan has been appended to the task file. Provide a high confidence score. State that the system is now ready for the autonomous `/cdd:act` command.
