---
name: gnotes
description: Cloud memory & note-taking via GitHub MCP (akiitr/gnotes). Covers discovery, search, read, write, update, and delete across the 10-folder layout.
---

# `gnotes` Skill (akiitr/gnotes)

## Directives
- **Pure Cloud / MCP**: No local disk files. Use `gnotes` MCP server exclusively (`owner="akiitr"`, `repo="gnotes"`, `branch="main"`).
- **No README Indexing**: Do NOT edit `README.md`. Discover files dynamically via MCP directory queries.
- **Privacy**: Strict zero-leak. Anonymize employer, internal paths, and project codenames.
- **Quality**: Flat layout, publishable article, `# Title`, tables, Mermaid diagrams. Descriptive PascalCase naming (`Topic-Name.md`).

## 1. 10-Folder Routing
| Folder | Scope |
| :--- | :--- |
| `chips/` | VLSI, STA, PD, EDA commands, silicon architectures |
| `coding/` | Scripts, software engineering, Linux homelab, DevOps |
| `finance/` | Investing, FIRE roadmaps, macro trends, real estate |
| `career/` | Resumes, career strategy, relocation guides |
| `personal/` | Fitness logs, routines, reflections |
| `summaries/` | Distilled articles, books, research frameworks |
| `projects/` | Homelab/OSS project specs and design logs |
| `travel/` | Itineraries, packing checklists, travel safety |
| `inbox/` | Scratch notes, unprocessed ideas |
| `archive/` | Retrospectives, post-mortems, deprecated records |

## 2. MCP Operations Reference
All calls: `ServerName: "gnotes"`, `owner: "akiitr"`, `repo: "gnotes"`, `branch: "main"`.

| Action | Tool | Arguments |
| :--- | :--- | :--- |
| **List Folder** | `get_file_contents` | `path="<folder>"`, `fields=["name", "path", "sha"]`, `owner="akiitr"`, `repo="gnotes"` |
| **Search Code** | `search_code` | `query="repo:akiitr/gnotes path:<folder> <keywords>"` |
| **Read Note** | `get_file_contents` | `path="<folder>/<File>.md"`, `owner="akiitr"`, `repo="gnotes"` |
| **Create Note** | `create_or_update_file` | `path=...`, `content=...`, `message="feat(<folder>): ..."`, `branch="main"` *(no SHA needed)* |
| **Update Note** | `create_or_update_file` | `path=...`, `content=...`, `sha="<blob_sha>"`, `message="docs(<folder>): ..."`, `branch="main"` *(get SHA via `get_file_contents`)* |
| **Batch Write** | `push_files` | `files=[{"path": "...", "content": "..."}]`, `message=...`, `branch="main"` |
| **Delete Note** | `delete_file` | `path="<folder>/<File>.md"`, `message="chore: ..."`, `branch="main"` |

## 3. Query Resolution Protocol
1. **Route**: Match question to domain folder (e.g. regrets $\rightarrow$ `archive/`, timing $\rightarrow$ `chips/`).
2. **Discover**: Call `get_file_contents(path="<folder>", fields=["name", "path"])` OR `search_code`.
3. **Fetch**: Read target note via `get_file_contents(path="<folder>/<File>.md")` and answer concisely.
