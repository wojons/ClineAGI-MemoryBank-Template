# Product Context: ClineAGI

## 1. Why ClineAGI Exists
ClineAGI exists to facilitate the collaborative creation of an Artificial General Intelligence (AGI). It serves as a dedicated environment and framework where a user and an AI assistant (Cline) can jointly design, build, and iterate on AGI concepts and functionalities. The project acknowledges the unique challenge and opportunity of using an AI to develop a more advanced AI.

## 2. Problems It Solves
-   **AGI Development Complexity:** Building AGI is an immensely complex undertaking. ClineAGI aims to provide a structured approach to manage this complexity through iterative development and clear documentation (via the Memory Bank).
-   **Separation of Core AGI and User Projects:** It addresses the need to distinguish between the foundational AGI system and user-specific applications or data. This allows the core AGI to evolve independently without breaking user customizations.
-   **Bridging AI Capabilities and User Intent:** ClineAGI acts as the interface and process for translating user ideas and research into tangible AGI components, leveraging Cline's software engineering skills.
-   **Persistent Knowledge for Session-Based AI:** Given Cline's session-based memory, the Memory Bank within ClineAGI is crucial for maintaining continuity, context, and a persistent record of design decisions, progress, and learning.

## 3. How It Should Work (User Experience Goals)
-   **Collaborative Environment:** Users should feel they are in a partnership with Cline, where Cline acts as an expert software engineer, taking direction, offering solutions, and executing development tasks.
-   **Modular Project Management:** Users will interact with Cline to manage their individual projects housed in separate repositories under the `projects/` directory. This interaction includes creating new projects, developing features within them, and versioning them independently.
-   **Non-Disruptive Core Updates:** Users should be able to update the core ClineAGI system (e.g., via `git pull` on the parent repository) to benefit from new functionalities and improvements without negatively impacting their existing projects.
-   **Transparent Development Process:** The Memory Bank should provide a clear and accessible history of the AGI's development, including rationale for decisions, architectural patterns, and current status.
-   **Focus on AGI Capabilities:** The primary interaction should revolve around defining, implementing, and testing AGI-related features and concepts.

## 4. Target Users
-   Initially, the primary user is the individual collaborating with Cline on this specific AGI development effort.
-   Potentially, the framework could be adapted for other researchers or developers looking to build AI systems in a similar collaborative, modular fashion.
