# Potential User Workflows

This document outlines potential user workflows for the Conductor-GitHub Copilot integration.

## 1. Workflow: Initiating a Conductor-Powered Copilot Session

1.  **Prerequisites:**
    *   The user has the Conductor CLI installed and a project set up with the `conductor/` directory.
    *   The user has the Conductor Copilot Extension installed in their IDE.
    *   The user has an active track and is ready to work on a task.

2.  **Initiation:**
    *   The user opens their project in the IDE.
    *   The Conductor Copilot Extension automatically detects the `conductor/` directory.
    *   The extension reads the `tracks.md` file to identify the current in-progress track (`[~]`).
    *   The extension then loads the context from the corresponding track's directory (`spec.md`, `plan.md`) and the project-level context files (`product.md`, `tech-stack.md`, `workflow.md`).

3.  **User Notification:**
    *   A notification appears in the IDE, confirming that Conductor context has been loaded for the current track. For example: "Conductor context loaded for track: 'Implement user authentication'."

## 2. Workflow: Context-Aware Code Generation

1.  **User Action:** The user starts writing code related to a task in the `plan.md`. For example, they might start writing a new function or a test.

2.  **Copilot Invocation:** The user invokes GitHub Copilot for a code suggestion (e.g., by typing a comment or a function signature).

3.  **Context-Enhanced Prompt:** The Conductor Copilot Extension intercepts the prompt and enriches it with the relevant context from the loaded Conductor files. For example, it might prepend the prompt with:
    *   "You are working on a project with the following goal: [from product.md]. The tech stack is [from tech-stack.md]. The current task is [from plan.md]."
    *   "The following is the specification for the current track: [from spec.md]."
    *   "The code should adhere to the following workflow: [from workflow.md]."

4.  **Informed Code Generation:** GitHub Copilot receives the context-enhanced prompt and generates code that is more likely to be aligned with the project's requirements, tech stack, and coding standards.

5.  **User Review:** The user reviews the generated code and accepts, rejects, or modifies it.

## 3. Workflow: Switching Tracks or Tasks

1.  **User Action:** The user completes a task and marks it as complete using the Conductor CLI (or potentially a future IDE command).
2.  **Context Reload:** The Conductor Copilot Extension detects the change in the `plan.md` file and reloads the context for the next task.
3.  **User Notification:** A notification confirms that the context has been updated for the new task.
