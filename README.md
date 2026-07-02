# AI Product Manager

> A self-hosted platform that gives software teams an AI-powered product manager — turning codebases into living documentation, structured tickets, and automated development workflows, with all data staying on your own infrastructure.

![Status](https://img.shields.io/badge/status-beta-yellow)

## Overview

Development teams lose enormous amounts of time to undocumented codebases, poorly specified tickets, and the mental overhead of context-switching between tools. AI Product Manager addresses this by connecting directly to a source repository, understanding its structure, and acting as an intelligent layer between the codebase and the team.

It runs entirely on-premises — no data leaves your servers, no SaaS subscription, no vendor lock-in. Teams can query their own code in plain language, generate documentation automatically, plan work through AI-assisted tickets, and even delegate routine implementation tasks to an AI agent that operates under human supervision at every step.

## Key Capabilities

- **Ask your codebase anything** — query any part of the project in natural language and receive answers grounded in the actual source code, not generic documentation
- **Automatic documentation** — analyses the repository and generates structured technical docs covering architecture, APIs, data models, and module relationships; keeps them current as the code evolves
- **AI-assisted ticket creation** — describe a feature or bug in plain language and receive a fully structured ticket with acceptance criteria, implementation steps, affected files, and complexity estimate
- **Human-in-the-loop AI pipeline** — a four-stage workflow (Define → Plan → Develop → Review) where AI drafts each step and a human approves before proceeding; the AI can write and commit code to a branch, then hand off to human review
- **Full project management suite** — kanban board, sprint planning, backlog, story points, velocity tracking, comments, and Jira / GitHub Issues export
- **Compliance document generation** — produces certification-ready documentation (ISO, SOC2, and others) derived directly from codebase analysis
- **Team engagement** — built-in XP system, 100 achievements, and a leaderboard that make day-to-day development measurably more motivating

## Tech Highlights

| Layer | Technology |
|-------|------------|
| Backend | Python, FastAPI |
| Frontend | React, Tailwind CSS |
| AI / LLM | Ollama (local), Anthropic Claude, Google Gemini |
| Semantic search | Vector database (on-premises) |
| Code understanding | Static analysis + AST parsing |
| Version control | Git integration |
| Deployment | Self-hosted Linux server, systemd service |

## Screenshots

> *Screenshots available on request or at [project URL if any]*

## Status & Availability

The platform is in active beta, running in production on a private server. Core features — codebase scanning, RAG chat, documentation generation, ticket management, sprint planning, and the AI development pipeline — are fully functional. Ongoing work focuses on expanding framework support, refining the AI pipeline, and adding deeper integrations with external project management tools.

This is a proprietary project. It can be licensed, demonstrated, or adapted for specific client needs. A full code review is available under NDA.

## Interested?

This is a proprietary project by **Munda Plus d.o.o.**  
The full codebase is available for review upon request.

📧 marko@munda.si  
🌐 [munda.si](https://www.munda.si)
