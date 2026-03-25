# GitHub Copilot Hackathon

> **Learn GitHub Copilot by shipping real work.**

Welcome to the GitHub Copilot Hackathon! This is a full-day, hands-on event where you and your team will use GitHub Copilot Enterprise to accelerate your real-world development workflows — from planning and design through code generation, testing, refactoring, and documentation.

## Event Format

This is a **Bring Your Own Code (BYOC)** hackathon. You'll apply GitHub Copilot to your own repositories, roadmap features, and bug fixes. The challenges in this repo are workflows and prompt recipes you apply to *your* codebase — not toy exercises. By the end of the day, you'll have shipped real work while building deep fluency with Copilot.

## How to Use This Repo

### 1. Start Here
👉 **[Getting Started — Setup & Warm-up](00-getting-started/SETUP.md)**

Make sure your environment is configured and run through the warm-up exercises before diving into challenges.

### 2. Pick Your Challenges
Challenges are organized by SDLC phase. **You don't need to do them all** — pick the ones most relevant to your team's codebase and goals. Each challenge is self-contained and designed for 30-90 minutes.

| Track | Description | Challenges |
|-------|-------------|------------|
| [**Planning & Design**](01-planning-and-design/OVERVIEW.md) | Go from idea to spec with Copilot | Spec from Issue · Architecture Review · ADR Generation |
| [**Code Generation**](02-code-generation/OVERVIEW.md) | Build features faster with AI-assisted coding | Feature Implementation · Boilerplate & Scaffolding · Agent Mode Feature |
| [**Testing & Quality**](03-testing-and-quality/OVERVIEW.md) | Improve test coverage and find edge cases | Unit Test Generation · Coverage Gaps · Edge Case Discovery |
| [**Code Review & Refactoring**](04-code-review-and-refactoring/OVERVIEW.md) | Clean up and strengthen your codebase | Refactor with Copilot · Security & Perf Review · Legacy Modernization |
| [**Documentation**](05-documentation/OVERVIEW.md) | Generate and improve project docs | README & API Docs · Inline Docs · Onboarding Guide |
| [**Agent Mode**](06-agent-mode/OVERVIEW.md) | Let Copilot drive multi-step workflows | Multi-File Feature · Bug Investigation · End-to-End Workflow |

### 3. Use the Resources
- **[Prompt Library](resources/prompt-library.md)** — Curated prompt patterns for every task type
- **[Copilot Cheat Sheet](resources/copilot-cheat-sheet.md)** — Keyboard shortcuts, slash commands, chat participants
- **[Troubleshooting](resources/troubleshooting.md)** — Common issues and fixes

### 4. Supercharge Your Repo with the AI-Assisted Dev Kit

The [**AI-Assisted Dev Kit**](resources/AI-assisted_dev_kit/) is a collection of VS Code customization files that tailor GitHub Copilot's behavior to your team's workflows. Copy them into your own repository to get more targeted, higher-quality AI assistance.

#### What's Inside

| Folder | File Type | What It Does |
|--------|-----------|--------------|
| **agents/** | `.agent.md` | Custom agent personas (Architect, Developer, Tester, Beast Mode) that give Copilot a specialized role, toolset, and behavior when invoked |
| **prompts/** | `.prompt.md` | Reusable prompt files you can run as slash commands (e.g., `/dev`, `/create-spec`, `/create-commit`) to kick off structured workflows |
| **instructions/** | `.instructions.md` | Contextual rules that Copilot follows automatically when working with matching files — coding standards, commit conventions, task execution guidelines |
| **instructions/languages/** | `.instructions.md` | Language-specific instructions for C#, Python, TypeScript, React, Blazor, Docker, and .NET Aspire |
| **templates/** | `.md` | Reference templates for best practices, code style, and tech stack documentation |
| **ISSUE_TEMPLATE/** | `.yml` | GitHub Issue templates for standardized bug reports and feature requests |
| Root | `copilot-instructions.md` | Global Copilot instructions applied to every chat in the workspace |
| Root | `pull_request_template.md` | Standardized PR template with checklists for type, testing, and review |

#### How to Add These to Your Repository

1. **Copy the folder** into your repo's `.github/` directory:
   ```
   your-repo/
   ├── .github/
   │   ├── copilot-instructions.md
   │   ├── pull_request_template.md
   │   ├── agents/
   │   ├── prompts/
   │   ├── instructions/
   │   ├── ISSUE_TEMPLATE/
   │   └── templates/
   ```
2. **Generate `copilot-instructions.md`** — run the `/analyze-product` prompt (from `prompts/analyze-product.prompt.md`) against your codebase. It analyzes your project and populates `copilot-instructions.md` with your tech stack, coding standards, and architecture conventions automatically.
3. **Customize the language instructions** — keep only the ones relevant to your stack, and tweak rules to match your team's style.
4. **Start using prompts** — in Copilot Chat, type `/` to see available prompt files, or reference them by name.
5. **Invoke agents** — in Agent mode, mention an agent by name (e.g., `@Architect`) to activate its specialized persona.

> **Tip:** These files work with VS Code's built-in Copilot customization support. No extensions or extra tooling required — just drop them in and go.

## Team Guidelines

- **Team size:** 2-4 people recommended
- **Mix roles:** Pair developers with testers, architects, or PMs for richer exploration
- **Choose challenges that matter:** Work on real backlog items — this isn't practice, it's production
- **Document what you learn:** Note effective prompts, surprising results, and limitations
- **Share with everyone:** The showcase at the end is where the whole group levels up

## Prerequisites

- [VS Code](https://code.visualstudio.com/) installed (GitHub Copilot is built in)
- GitHub Copilot Enterprise license active
- Your team's source code repository cloned locally

See the [full setup guide](00-getting-started/SETUP.md) for detailed instructions.

---

*Built for the GitHub Copilot Hackathon. Questions? Reach out to the event facilitators.*
