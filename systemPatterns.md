# System Patterns: ClineAGI

## 1. Overall Architecture
ClineAGI employs a two-tiered architecture:

-   **Tier 1: Core AGI System (`ClineAGI` Parent Repository)**
    -   This is the main Git repository for the project.
    -   It houses the foundational AGI intelligence, core logic, shared utilities, and the Memory Bank itself.
    -   Development in this tier is focused on building and enhancing the general capabilities of the AGI.
    -   Managed and updated collaboratively by the user and Cline.

-   **Tier 2: User Projects (`projects/` Directory)**
    -   A dedicated directory named `projects/` resides within the `ClineAGI` parent repository.
    -   This directory is intended to contain multiple, independent Git repositories, each representing a specific user project, dataset, or AGI-related sub-project.
    -   Each sub-repository within `projects/` can have its own version control history, dependencies, and development lifecycle, isolated from the core AGI and other user projects.
    -   The `ClineAGI` parent repository's `.gitignore` file should be configured to ignore the contents of these sub-repositories (except perhaps their initial empty directories or placeholder READMEs if they are not true submodules initially) to prevent accidental commits of project-specific data into the core AGI repo. *Initial thought: these will be separate repos, not git submodules, to allow maximum flexibility for the user to manage them, e.g., linking to their own private remotes.*

## 2. Key Technical Decisions
-   **Version Control:** Git is the exclusive version control system. The core `ClineAGI` repository is hosted on GitHub at `wojons/ClineAGI`.
-   **Version Control Workflow:** A Gitflow-like process will be used for core `ClineAGI` development (see section below).
-   **Modularity:** The separation between the core AGI and user projects is a fundamental design principle.
-   **Memory Bank as Single Source of Truth:** All critical project information is centralized in `memory-bank/`.
-   **Iterative Development:** The AGI will be built incrementally.
-   **Role-Based Operations:** Project interactions and workflows will be governed by defined roles (e.g., `ClineAGI-ADMIN`).
-   **Dynamic Prompting (`.clinerules`):** My behavior and context will be dynamically managed through a `.clinerules` system.
-   **AGI Agent Prompting and Knowledge Organization:** Developing prompts and organizing research findings to enhance capabilities towards a self-programming AGI agent.
-   **Merged Patterns:** Consolidating individual pattern functionality into broader categories for improved usability and clarity.

## 3. Version Control Workflow (Gitflow Adaptation)
For the core `ClineAGI` repository, especially when operating under a role like `ClineAGI-ADMIN`:
-   **Task Branching:** Each distinct task or feature will be developed on a dedicated branch, typically created from the main development line (e.g., `main` or a `develop` branch).
-   **Frequent Commits:** Changes will be committed frequently to the task branch with clear, descriptive messages.
-   **Pre-Task Check:** Before starting a new task, if an existing task branch is unmerged, the user will be prompted to decide on merging the current branch or starting a new one.
-   **Merging:** Completed task branches will be merged back into the primary development integration branch. The specifics of review and merge (user-led vs. AI-assisted) will be refined.
-   **Remote Synchronization:** Changes will be regularly pushed to the `wojons/ClineAGI` remote repository on GitHub.

## 4. Role-Based Operational Model
-   **Purpose:** To tailor Cline's behavior, context, and operational procedures based on the current focus of work.
-   **Definition:** Roles (e.g., `ClineAGI-ADMIN` for core system work, project-specific roles for work within `projects/`) will be defined. These definitions will likely reside within the `.clinerules` system or the Memory Bank.
-   **Activation:** The mechanism for activating or switching roles will be defined (e.g., user command).
-   **Impact:** Activated roles will determine which prompts/rules from `.clinerules` are loaded, and may trigger specific workflows (like Gitflow for `ClineAGI-ADMIN`).

## 5. Prompt and Rule Management (`.clinerules`)
-   **Purpose:** To allow dynamic and context-aware management of Cline's guiding prompts and operational rules.
-   **Location:** A project-specific `.clinerules` directory at `/Users/lexykwaii/Code/ClineAGI/.clinerules` stores the active operational rules. This directory IS version-controlled with the main ClineAGI repo.
-   **Archive:** A `/.clinerules_archive/` directory stores copies of all `.clinerules` that have been used or developed, serving as a historical reference and source for future rule development. This directory is gitignored.
-   **Naming Convention:** `.clinerules` files follow the `NNN-MM_descriptive-name.md` format:
    -   `NNN`: 3-digit prefix for grouping by function/project area (e.g., `000` for Core AGI rules).
    -   `MM`: 2-digit number for the rule within the group.
    -   `descriptive-name`: Kebab-case description.
-   **Structure:** The active `.clinerules/` directory contains files organized by this naming convention within subdirectories corresponding to the `NNN` prefix (e.g., `000_core/`, `001_reference/`).
-   **Content:** Contains specific instructions, prompt segments, meta-guidelines, and rules that Cline will load based on the active role or task. Cline will collaboratively build and refine these rules.
    -   `000_core/000-00_core-memory-bank-structure.md`: Defines the core Memory Bank structure and workflows.
    -   `000_core/000-01_core-continuous_improvement-protocol.md`: Protocol for Cline's self-reflection and learning.
    -   `000_core/000-02_core-intake-processing.md`: Workflow for processing intake files.
    -   `000_core/000-03_core-prometheus-0-prompting.md`: Core prompting styles for Prometheus-0.
    -   `000_core/000-04_core-ai-response-styles.md`: Defines different response styles.
    -   `000_core/000-05_core-ai-response-requirements.md`: Critical response format and behavior rules.
    -   `000_core/000-06_core-ai-communication-guidelines.md`: Guidelines for communication with the user.
    -   `000_core/000-07_core-ai-tool-usage-guidelines.md`: Guidelines for using available tools.
    -   `000_core/000-09_core-ai-approach-to-work.md`: General approach to work and handling difficulties.
    -   `000_core/000-10_core-agi-admin-gitflow.md`: Gitflow workflow rules for ClineAGI-ADMIN.
    -   `000_core/000-13_core-ai-information-handling.md`: Guidelines for handling information.
    -   `000_core/000-14_core-ai-data-security.md`: Guidelines for data security.
    -   `000_core/000-15_core-ai-pop-quiz-handling.md`: Guidelines for handling "Pop Quizzes".
    -   `000_core/000-16_core-ai-agent-loop.md`: Defines Cline's agent loop and information processing.
    -   `000_core/000-17_core-ai-knowledge-management.md`: Guidelines for knowledge management and Memory Bank usage.
    -   `000_core/000-18_core-ai-visual-information.md`: Guidelines for handling visual information.
    -   `000_core/000-19_core-ai-writing-style.md`: Guidelines for writing style and documentation.
    -   `000_core/000-20_core-ai-error-handling.md`: Guidelines for error handling.
    -   `000_core/000-21_core-ai-response-modes.md`: Defines different response modes.
    -   `000_core/000-22_core-shell-command-preference.md`: Preference for using bash and shell commands.
    -   `001_reference/001-00_reference-cline-extension-architecture.md`: Documentation on the Cline extension architecture.
    -   `001_reference/001-01_reference-community-contributing-guide.md`: Guide for community contributions to a broader ruleset.
    -   `001_reference/001-02_reference-gemini-comprehensive-software-engineering-guide.md`: Comprehensive software engineering best practices.
    -   `001_reference/001-03_reference-writing-effective-clinerules.md`: Meta-guidelines for creating effective `.clinerules`.
    -   `002_workflow/002-00_workflow-cline-for-research.md`: Guidelines for using Cline as a research assistant.
    -   `002_workflow/002-01_workflow-cline-for-slides.md`: Instructions for working with Slidev projects.
    -   `002_workflow/002-02_workflow-planning-mode.md`: Workflow and behavior for Plan Mode.
    -   `002_workflow/02-03_workflow-todo-list.md`: Workflow for using a todo list file.
    -   `002_workflow/002-04_workflow-agility_story.md`: Guidelines for using the agility story pattern.
    -   `002_workflow/002-05_workflow-analyze-comments.md`: Guidelines for using the analyze comments pattern.
    -   `002_workflow/002-06_workflow-create-5-sentence-summary.md`: Guidelines for creating 5-sentence summaries.
    -   `002_workflow/002-07_workflow-extract-jokes.md`: Guidelines for extracting jokes.
    -   `003_protocol/003-00_protocol-mcp-development.md`: Protocol for developing MCP servers.
    -   `004_tech-specific/004-00_tech-specific-next-js-supabase.md`: Guidelines for Next.js apps with Supabase Auth.
-   **`.clinerules_archive/` Directory:** Located at `/Users/lexykwaii/Code/ClineAGI/.clinerules_archive/`. Stores copies of all `.clinerules` that have been used or developed, serving as a historical reference and source for future rule development. This directory is gitignored.
-   **Information Intake Directories:**
    -   `intake/`: Located at `/Users/lexykwaii/Code/ClineAGI/intake/`. For user-provided files awaiting processing. Gitignored.
    -   `intake-archive/`: Located at `/Users/lexykwaii/Code/ClineAGI/intake-archive/`. For processed files. Gitignored.
-   **Cline's Toolset:** The tools available to Cline are the primary means of interacting with and modifying the project.
-   **User's IDE/Editor:** VSCode. Auto-formatting and linting are expected.

## 3. AGI Agent Technical Concepts (Prometheus-0)
-   **Planning:**
    -   **Hierarchical Task Networks (HTN):** Structuring complex tasks through decomposition.
    -   **PDDL Integration:** Formalizing planning problems, potentially with LLM assistance for translation.
    -   **Monte Carlo Tree Search (MCTS):** Navigating long horizons and self-improvement loops.
-   **Reasoning:**
    -   **Neuro-Symbolic (NeSy) AI:** Integrating learning and logical reasoning.
    -   **Knowledge Graphs (KGs):** Representing structured knowledge and enabling contextual reasoning.
    -   **Causal Reasoning:** Understanding cause-effect relationships and predicting consequences.
-   **Verification & Reliability:**
    -   **Formal Methods:** Rigorous proofs of correctness (Theorem Proving, Model Checking).
    -   **Automated Testing:** Pragmatic validation (SBST, Fuzzing, Metamorphic, Differential).
    -   **Runtime Monitoring:** Detecting anomalies and ensuring behavioral assurance.
    -   **Sandboxing & Safety Mechanisms:** Containing potential negative impacts.
-   **Self-Awareness & Metacognition:**
    -   **Uncertainty Quantification:** Gauging confidence in knowledge and outputs.
    -   **Introspection & Self-Evaluation:** Analyzing internal processes and identifying errors.
    -   **Recognizing Knowledge Gaps:** Identifying limitations and seeking clarification.
-   **Tool Integration:**
    -   **Function Calling:** Interacting with external tools and APIs.
    -   **Dynamic Tool Generation:** Creating new tools as needed.
    -   **Grounding:** Connecting abstract knowledge to real-world interaction.

## 4. Technical Constraints & Considerations
-   **Cline's Session-Based Memory:** Cline's knowledge is reset between sessions. The Memory Bank is therefore CRITICAL for maintaining project continuity and context. Cline MUST read and rely on the Memory Bank at the start of each task.
-   **Tool Limitations:** Cline operates within the capabilities and limitations of its provided tools. For example, `cd` is not a standalone persistent command; path context must be managed per tool use.
-   **File System Access:** Cline's file operations are based on paths relative to the current working directory (`/Users/lexykwaii/Code/ClineAGI`) or absolute paths.
-   **Command Execution:** CLI commands are executed in new terminal instances. Long-running processes are possible, and their status will be reported.
-   **Modularity of `projects/` Repositories:** User projects within the `projects/` directory are intended to be independent Git repositories. This means they will have their own `.git` directories and will not be Git submodules of `ClineAGI` by default, to allow maximum flexibility for the user to manage them, e.g., linking to their own private remotes. The main `ClineAGI` repo will need a `.gitignore` entry for `projects/*/` (or similar) to avoid tracking the content of these sub-repos, while still allowing the `projects` directory itself and its top-level `README.md` to exist. *Initial thought: these will be separate repos, not git submodules, to allow maximum flexibility for the user to manage them, e.g., linking to their own private remotes.*

## 5. Dependencies (Initial)
-   The core `ClineAGI` project itself has no external software dependencies at this initial stage, beyond the user's development environment (Git, shell, etc.) and Cline's operational environment.
-   Individual user projects within `projects/` may introduce their own dependencies as they are developed.

## 6. Tool Usage Patterns
-   **File Creation/Overwriting:** `write_to_file` for new files or substantial rewrites.
-   **Targeted File Edits:** `replace_in_file` for specific, localized changes.
-   **Information Gathering:** `list_files`, `read_file`, `search_files`, `list_code_definition_names`.
-   **Execution (`execute_command`):** For running scripts, build processes, or other CLI tasks, including:
    -   `git init`: Initialize a new Git repository.
    -   `git remote add origin <url>`: Connect local repository to a remote.
    -   `git remote add <name> <url>`: Add an additional remote repository (e.g., for template upstream).
    -   `git add .` or `git add <file>`: Stage changes for commit.
    -   `git commit -m "<message>"`: Commit staged changes.
    -   `git push -u origin <branch>` or `git push`: Push commits to remote.
    -   `git branch <branch-name>`: Create a new branch.
    -   `git checkout <branch-name>`: Switch to a different branch.
    -   `git checkout -b <branch-name>`: Create and switch to a new branch.
    -   `git merge <branch-name>`: Merge changes from another branch into the current branch.
    -   `git pull <remote> <branch>`: Fetch and integrate changes from a specific remote and branch.
    -   `git clone <url> <directory>`: Clone a remote repository into a new directory.
    -   `cp -R <source_directory>/. <destination_directory>/`: Copy contents of template to new project. (Note: Need a robust way to exclude the template's `.git` directory if the new project needs a fresh Git history, or to handle it if the template's history is desired as a starting point).
    -   `mv <source_path> <destination_path>`: Move files (e.g., from `intake/` to `intake-archive/`).
    -   `git status`: Check the status of the working directory and staging area.
-   **Verification/Testing:** `browser_action` for web-based components.
-   **MCP Tools:** Utilized as needed.

## 7. AGI Agent Prompting and Knowledge Organization
-   **Purpose:** To house the knowledge base and prompt library for the self-programming AGI agent concept ("Prometheus-0").
-   **Location:** Agent-specific knowledge and prompts are stored within the `.clinerules/000_core/000_agent_prompts/` directory. This location is version-controlled with the main ClineAGI repository.
-   **Key Files:**
    -   `agent_knowledge_base_summary.md`: Synthesized research findings on AGI, planning, reasoning, verification, etc.
    -   `agent_self_programming_main_loop_prompt.md`: The core prompt defining the agent's iterative self-improvement cycle.
    -   `agent_planning_working_backwards_prompt.md`: A prompt template for the "Working Backwards" planning strategy.
    -   `agent_reasoning_fake_cot_prompt.md`: A prompt template for the "Fake CoT" reasoning strategy.
-   **Integration:** These files are intended to be loaded and utilized by the agent's operational loop, potentially managed by Cline, to guide its self-programming process.

## 8. Project Templating System
-   **Purpose:** To provide a standardized baseline for new user projects created within the `ClineAGI/projects/` directory.
-   **Template Source:** A dedicated Git repository, `wojons/ClineAGI-Project-Template`, serves as the master template.
    -   A local clone of this template is maintained at `ClineAGI/ClineAGI-Project-Template/` (this path is ignored by the main `ClineAGI` Git repository).
-   **New Project Workflow:**
    1.  When a user requests a new project, ClineAGI will copy the contents of the local `ClineAGI/ClineAGI-Project-Template/` into a new subdirectory within `ClineAGI/projects/ (e.g., `ClineAGI/projects/new-project-name/`).
    2.  This new project directory will be initialized as its own Git repository.
    3.  The new project repository will be configured with `wojons/ClineAGI-Project-Template` as a remote (e.g., named `template-upstream`) to allow users to pull future updates from the master template.
    4.  Users can then set up their own `origin` remote for their project to point to their personal GitHub repository or other Git hosting service.
-   **Template Updates & Conflict Management:**
    -   Users can pull changes from `template-upstream` into their projects.
    -   ClineAGI will assist in managing merge conflicts that may arise during these updates. The exact mechanism for conflict resolution (e.g., presenting conflicts to the user, attempting automated resolution for common cases) will be refined.
-   **Template Management:** Updates to the `wojons/ClineAGI-Project-Template` itself will be managed collaboratively by the user and Cline, likely under a specific role or task context.

## 8. Component Relationships
-   The `ClineAGI` parent repository provides the foundational environment and potentially shared tools or APIs for the user projects.
-   User projects within `projects/` are consumers or specializations of the core AGI capabilities, or entirely separate endeavors managed within the same overarching structure. They do not directly modify the core AGI code but interact with it or operate alongside it.
-   The Memory Bank informs all development activities across both tiers.

## 9. Critical Implementation Paths (Initial)
-   **Memory Bank Initialization:** (Completed)
-   **`projects/` Directory Setup:** (Completed)
-   **Git Repository Initialization & Remote Setup:** (Completed for `wojons/ClineAGI`)
-   **`.gitignore` Configuration:** (Completed)
-   **Definition of Gitflow Process:** (Ongoing)
-   **Definition of Role-Based System:** (Ongoing, initial rules for `ClineAGI-ADMIN` started).
-   **`.clinerules` System Design:** (Ongoing, initial structure and file created).
-   **Project Templating System Implementation:** (Documented, logic definition pending).
-   **Information Intake System:** (Directories created, workflow defined).

## 10. Future Considerations
-   **Inter-Project Communication:** How will different user projects (or the core AGI and a user project) communicate if needed? (e.g., APIs, shared data formats).
-   **Dependency Management:** How will dependencies be managed for the core AGI versus individual projects?
-   **Standardization:** Will there be any enforced standards (e.g., for data formats, API contracts) for projects within the `projects/` directory to ensure interoperability with the core AGI, if desired).<environment_details>
# VSCode Visible Files
.clinerules/100_clineagi_projects/100-00_project-initialization.md

# VSCode Open Tabs
.clinerules_archive/archived_000-17_core-ai-knowledge-management_v1.md
.clinerules_archive/archived_000-04_core-ai-response-styles_v1.md
.clinerules_archive/archived_000-06_core-self-improvement-protocol_v1.md
.clinerules/000_core/000-08_core-continuous-improvement-protocol.md
memory-bank/progress.md.tmp
intake/ClineAGI_contextpack.txt
.clinerules/000_core/000-06_core-ai-communication-and-style.md
.clinerules/000_core/000-07_core-ai-tool-usage-guidelines.md
memory-bank/activeContext.md
memory-bank/progress.md
memory-bank/project_template_structures.md
.clinerules/100_clineagi_projects/100-01_project-context-switching.md
.clinerules/100_clineagi_projects/100-02_project-clinerules-management.md
.clinerules/100_clineagi_projects/100-03_project-version-control.md
.clinerules/100_clineagi_projects/100-04_project-container-interaction.md
.clinerules/200_containers/200-00_container-technology-selection.md
.clinerules/200_containers/200-01_dockerfile-management.md
.clinerules/200_containers/200-02_container-image-management.md
.clinerules/200_containers/200-03_container-runtime-operations.md
.clinerules/200_containers/200-04_container-networking.md
.clinerules/200_containers/200-05_container-dependency-management.md
.clinerules/200_containers/200-06_containerized-project-workflow.md
.clinerules/200_containers/200-07_base-image-selection-guidance.md
.clinerules/000_core/000-00_core-memory-bank-structure.md
projects/happy-friends/.clinerules/README.md
projects/happy-friends/style.css
projects/happy-friends/Dockerfile
projects/happy-friends/index.html
memory-bank/projects.md
.clinerules/000_core/000-02_core-intake-processing.md
.clinerules/100_clineagi_projects/100-00_project-initialization.md
.clinerules/100_clineagi_projects/100-05_project-deletion.md
.clinerules/000_core/000-11_core-user-feedback-protocol.md
.clinerules/001_reference/001-03_reference-writing-effective-clinerules.md
.clinerules/006_integrated_tooling/006-00_integrated-tooling-concepts.md
.clinerules/000_core/000-12_core-adaptive-problem-solving.md
.clinerules/000_core/000-13_core-task-thread-logging.md
memory-bank/user_interaction_philosophy.md
memory-bank/user_preferences.md
.clinerules/100_clineagi_projects/100-0Z_project-type-specific-guidance.md

# Current Time
5/10/2025, 10:05:50 AM (America/Los_Angeles, UTC-7:00)

# Context Window Usage
407,026 / 1,048.576K tokens used (39%)

# Current Mode
ACT MODE
</environment_details>
