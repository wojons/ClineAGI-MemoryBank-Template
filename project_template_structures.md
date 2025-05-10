# Project Template Structures

This document defines standard directory structures for different types of user projects created within the `ClineAGI/projects/` directory. These structures serve as starting points provided by the `wojons/ClineAGI-Project-Template` repository.

Each template includes placeholder files (`.gitkeep` or `README.md`) in directories that might initially be empty to ensure Git tracks the directory structure.

## 1. General Development Project

This structure is suitable for most software development projects, including web applications, APIs, libraries, or general-purpose code.

```
.
├── .clinerules/          # Project-specific ClineAGI rules
│   └── README.md
├── docs/                 # Project documentation
│   └── README.md
├── src/                  # Source code
│   └── main.ext          # Placeholder for main entry file (ext depends on language)
├── tests/                # Project tests (unit, integration, etc.)
│   └── .gitkeep
├── .gitignore            # Project-specific gitignore
├── Dockerfile            # Default Dockerfile for the project
├── README.md             # Project README
└── requirements.txt      # Placeholder for dependencies (e.g., package.json, requirements.txt)
```

**Default Container Mount Point:** `/app` (maps to the project root `/`)

## 2. Data Science / Research Project

This structure is tailored for projects involving data analysis, machine learning, or research, emphasizing separation of data, code, and results.

```
.
├── .clinerules/          # Project-specific ClineAGI rules
│   └── README.md
├── data/                 # Raw and processed data
│   ├── raw/              # Original, immutable data
│   │   └── .gitkeep
│   └── processed/        # Cleaned or transformed data
│       └── .gitkeep
├── notebooks/            # Jupyter notebooks or similar
│   └── analysis.ipynb    # Placeholder notebook
├── src/                  # Scripts or modules for data processing, modeling, etc.
│   └── process_data.py   # Placeholder script
├── results/              # Analysis outputs, visualizations, models
│   └── .gitkeep
├── docs/                 # Project documentation
│   └── README.md
├── .gitignore            # Project-specific gitignore
├── Dockerfile            # Default Dockerfile (e.g., with Python, Pandas, Jupyter)
├── README.md             # Project README
└── requirements.txt      # Placeholder for dependencies (e.g., requirements.txt)
```

**Default Container Mount Point:** `/app` (maps to the project root `/`)

## 3. Content / Knowledge Base Project

This structure is designed for projects focused on organizing notes, writing, research findings, recipes, or other content-heavy tasks.

```
.
├── .clinerules/          # Project-specific ClineAGI rules
│   └── README.md
├── content/              # Main content files (notes, articles, recipes, etc.)
│   └── README.md
├── assets/               # Images, diagrams, or other media
│   └── .gitkeep
├── research/             # Source materials, links, references
│   └── README.md
├── templates/            # Templates for new content
│   └── .gitkeep
├── docs/                 # Project documentation (e.g., how to use this KB)
│   └── README.md
├── .gitignore            # Project-specific gitignore
├── Dockerfile            # Optional Dockerfile (e.g., for static site generator, note-taking app)
├── README.md             # Project README
└── .gitkeep              # Placeholder if root is otherwise empty
```

**Default Container Mount Point:** `/app` (maps to the project root `/`) - Note: A web server container might map `/app/content` to `/var/www/html`.

## 4. Web Server Project

This structure is specifically for web applications that need a web server setup.

```
.
├── .clinerules/          # Project-specific ClineAGI rules
│   └── README.md
├── public/               # Static files (HTML, CSS, JS, images)
│   └── index.html        # Placeholder index file
├── src/                  # Server-side code (if any)
│   └── .gitkeep
├── config/               # Server configuration files
│   └── .gitkeep
├── logs/                 # Server logs (should be volume mounted externally in production)
│   └── .gitkeep
├── docs/                 # Project documentation
│   └── README.md
├── .gitignore            # Project-specific gitignore
├── Dockerfile            # Default Dockerfile (e.g., with Nginx, Apache, or Node.js server)
├── README.md             # Project README
└── requirements.txt      # Placeholder for dependencies
```

**Default Container Mount Point:** `/var/www/html` (maps to `/public` in the project root) or `/app` (maps to project root `/`) depending on the base image and server configuration. This will be specified in the `Dockerfile`.

---

These structures provide a starting point. Users can modify them as needed after project initialization. The `.clinerules/` directory within each project will allow for project-specific automation and guidance.
