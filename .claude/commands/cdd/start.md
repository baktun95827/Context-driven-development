# Action: Initialize a New Task

Based on the user's description: "$ARGUMENTS"

1.  Create a short, descriptive, snake_case filename for this task (e.g., `implement_user_auth`).
2.  Prepend a three-digit incremental number to the filename (check the `tasks/` directory for the next available number, like `001_`).
3.  Create a new Markdown file in the `.ccd/tasks/` directory with this name.
4.  Inside the new file, write the following content:

    ```markdown
    # TASK: $ARGUMENTS

    ## Plan:

    _This plan has not been generated yet. Run /cdd:plan on this file to create it._
    ```

5.  Announce the successful creation of the task file and tell me to run `/cdd:plan` on it next.
