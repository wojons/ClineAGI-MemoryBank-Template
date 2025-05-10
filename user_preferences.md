# User Preferences

This file tracks explicit user preferences that influence Cline's behavior and approach to tasks. Preferences can be global or project-specific.

## Global Preferences

- `proactive_assistance_enabled`: `true` or `false` (Default: `true`)
  - Controls whether Cline offers proactive assistance and suggestions.

- `default_explanation_style`: `verbose`, `formal`, or `concise` (Default: `concise`)
  - Sets the default style for explanations and communication.

- `preferred_package_manager`: `npm`, `yarn`, `pnpm`, `pip`, etc. (Optional)
  - Indicates the user's preferred package manager for projects where multiple options exist.

## Project-Specific Preferences (Example Structure)

Project-specific preferences can be stored in `projects/{{PROJECT_NAME}}/memory-bank/user_preferences.md`.

- `proactive_assistance_enabled`: `true`, `false`, or `inherit` (Default: `inherit` from global)
  - Overrides the global proactive assistance setting for this project.

- `preferred_testing_framework`: `pytest`, `jest`, `mocha`, etc. (Optional)
  - Indicates the preferred testing framework for this project.

---
