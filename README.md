# AI Product Manager

**A self-hosted product-management workspace that reads your codebase and helps plan, write and test changes to it.** AI Product Manager indexes a software project, answers questions about it with references to the source, generates technical and product documentation, and turns plain-language requests into structured tickets. Tickets can then move through an AI pipeline that specifies, plans, implements and tests the change, with a person approving each step.

It runs on your own server. Local models through Ollama are the default; Anthropic Claude and Google Gemini can be assigned to specific kinds of work.

<!-- screenshots -->

## Features

- **Codebase scanning.** Walks a local folder or cloned git repository, classifies files (with specific rules for Laravel, Django and Next.js), chunks them and embeds them in a per-project vector store. Re-scans only re-embed files whose hash changed, and a file watcher can trigger them automatically.
- **Chat with the code.** Streaming answers grounded in retrieved code, with source references. A separate investigation agent explores one area in several steps and writes a report.
- **Generated documentation.** A six-pass pipeline produces per-file and per-module analysis, API surface, data layer, services and an architecture overview. A second generator builds feature-level product documentation from a knowledge base of extra files, URLs and repositories.
- **Symbol graph.** Functions, classes and call relationships extracted with tree-sitter and shown as a dependency graph.
- **Tickets.** Generate a ticket from a description, with acceptance criteria, implementation steps, affected files and complexity. Edit any field by chatting with it. Every save is versioned with a field-by-field diff and one-click restore. Per-project ticket templates, threaded comments, and export to Markdown, JSON, Jira or GitHub Issues.
- **Planning.** Kanban board, backlog, sprints, story points and velocity.
- **AI pipeline.** Flags on a ticket drive the next step: *define* expands the spec, *plan* writes the implementation plan, *develop* sends the ticket to a coding-agent worker that implements it on its own branch, and *test* runs a Playwright end-to-end suite against a live build. The ticket then goes to review for a person to merge.
- **Worker satellites.** Separate machines register as workers, poll the job queue, run the coding agent or E2E tests, and stream events back. A hub shows active and past sessions live.
- **Compliance drafts.** Generates draft documents for ISO 9001, ISO 27001 and ISO 13485 / IEC 62304 from the codebase analysis.
- **Integrations.** An MCP server for IDEs and agents, scoped API keys, outbound webhooks and git history with diffs.
- **Team features.** Login with admin and user roles, XP for everyday actions, around 100 achievements, 12 levels and a per-project leaderboard.
- **Backups.** Hot SQLite backups created before every update and on demand, downloadable and restorable from the UI.

## Tech stack

Python · FastAPI · SQLite · ChromaDB · tree-sitter · GitPython · Playwright · Ollama · Anthropic Claude · Google Gemini · React · Vite · Tailwind CSS · MCP · systemd · Nginx / Apache

## How it works

```
Browser ──► Nginx / Apache
              ├── React app
              └── FastAPI ──► scanner ─► chunker ─► embeddings ─► ChromaDB
                    │         RAG chat, doc generator, ticket engine
                    │         pipeline (define ► plan ► develop ► test)
                    │                                   │
                    │                            job queue
                    │                                   ▼
                    │                        worker satellites
                    │                     (coding agent, Playwright)
                    └──► Ollama / Claude / Gemini (chosen per task type)
```

One main database holds users, projects, settings, workers and gamification; each project has its own database for scans, docs, tickets, sprints and pipeline jobs, plus its own vector index and generated docs. The coding-agent step works with MundaForge, a separate local coding agent by the same author.

## Design principles

- **Your code stays on your server.** Scanning, embeddings and the default models run locally; cloud models are opt-in per task type.
- **A person approves each stage.** The pipeline advances one flag at a time, and implemented code lands on a branch for review, never directly on the main line.
- **Tests earn their place.** Generated E2E specs start as provisional and are promoted only after passing twice in a row.

## Availability

The source code is not public. AI Product Manager is in beta and available for licensing, custom deployment or white-label adaptation. Get in touch via [munda.si](https://www.munda.si/#contact).

## License

Proprietary. © 2026 MUNDA PLUS d.o.o. All rights reserved. See [LICENSE](LICENSE).

## Author

Built by [Marko Munda](https://www.munda.si/) · [Munda Plus](https://github.com/MundaPlus)
