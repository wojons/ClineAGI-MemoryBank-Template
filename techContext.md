# Technical Context: ClineAGI

## 1. Core Technologies
-   **Operating System (Development Environment):** [User's OS]
-   **Default Shell (Development Environment):** [User's Shell]
-   **Primary AI Assistant (Cline):** Capabilities include CLI execution, file system operations (read, write, list, search), code definition listing, browser interaction, and access to MCP-provided tools.
-   **Version Control:** Git.
    -   **Remote Repository:** The core `ClineAGI` project is hosted on GitHub at `wojons/ClineAGI.git`.
    -   **Workflow:** A Gitflow-like process is adopted for core development (see `systemPatterns.md`).
-   **Documentation Format:** Markdown for all Memory Bank files.
-   **Prompt & Rule Management:** A `.clinerules` system will be used for dynamic prompt and rule loading based on roles.
-   **`.clinerules` Directory:** Located at the root of the ClineAGI repository (`.clinerules/`). This directory stores the active operational rules and IS version-controlled. Files follow the `NNN-MM_descriptive-name.md` convention within subdirectories.
-   **`.clinerules_archive/` Directory:** Located at the root of the ClineAGI repository (`.clinerules_archive/`). Stores copies of all `.clinerules` that have been used or developed, serving as a historical reference and source for future rule development. This directory is gitignored.
-   **Information Intake Directories:**
    -   `intake/`: Located at the root of the ClineAGI repository (`intake/`). For user-provided files awaiting processing. Gitignored.
    -   `intake-archive/`: Located at the root of the ClineAGI repository (`intake-archive/`). For processed files. Gitignored.
-   **Cline's Toolset:** The tools available to Cline are the primary means of interacting with and modifying the project.
-   **User's IDE/Editor:** VSCode. Auto-formatting and linting are expected.

## 2. AGI Agent Technical Concepts (Prometheus-0)
-   **Planning:** Hierarchical Task Networks (HTN), PDDL Integration, Monte Carlo Tree Search (MCTS).
-   **Reasoning:** Neuro-Symbolic (NeSy) AI, Knowledge Graphs (KGs), Causal Reasoning.
-   **Verification & Reliability:** Formal Methods, Automated Testing, Runtime Monitoring, Sandboxing & Safety Mechanisms.
-   **Self-Awareness & Metacognition:** Uncertainty Quantification, Introspection & Self-Evaluation, Recognizing Knowledge Gaps.
-   **Tool Integration:** Function Calling, Dynamic Tool Generation, Grounding.

## 3. Technical Constraints & Considerations
-   **Cline's Session-Based Memory:** Cline's knowledge is reset between sessions. The Memory Bank is therefore CRITICAL for maintaining project continuity and context. Cline MUST read and rely on the Memory Bank at the start of each task.
-   **Tool Limitations:** Cline operates within the capabilities and limitations of its provided tools.
-   **File System Access:** Cline's file operations are based on paths relative to the current working directory or absolute paths.
-   **Command Execution:** CLI commands are executed in new terminal instances.
-   **Modularity of `projects/` Repositories:** User projects within the `projects/` directory are independent Git repositories.

## 4. Dependencies (Initial)
-   The core `ClineAGI` project itself has no external software dependencies at this initial stage, beyond the user's development environment (Git, shell, etc.) and Cline's operational environment.
-   Individual user projects within `projects/` may introduce their own dependencies as they are developed.

## 5. Tool Usage Patterns
(Summary of key tool usage patterns)

## 6. AGI Agent Prompting and Knowledge Organization
-   **Purpose:** To house the knowledge base and prompt library for the self-programming AGI agent concept ("Prometheus-0").
-   **Location:** Agent-specific knowledge and prompts are stored within the `.clinerules/000_core/000_agent_prompts/` directory. This location is version-controlled with the main ClineAGI repository.
-   **Key Files:** `agent_knowledge_base_summary.md`, `agent_self_programming_main_loop_prompt.md`, `agent_planning_working_backwards_prompt.md`, `agent_reasoning_fake_cot_prompt.md`.

## 7. Project Templating System
-   **Purpose:** Standardized baseline for new user projects.
-   **Template Source:** `wojons/ClineAGI-Project-Template` Git repository.
-   **New Project Workflow:** Clone template, rename remote, initialize project-specific `.clinerules` and `memory-bank`.

## 8. Component Relationships
-   `ClineAGI` parent provides environment/tools.
-   User projects consume/specialize core capabilities.
-   Memory Bank informs all development.

## 9. Critical Implementation Paths (Initial)
(List of initial completed/ongoing paths)

## 10. Future Considerations
(List of future considerations)
