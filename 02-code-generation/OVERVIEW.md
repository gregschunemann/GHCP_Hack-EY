# Code Generation Challenges

Build features faster with AI-assisted coding. These challenges cover the core Copilot workflow — from inline completions to Chat-driven generation to fully autonomous Agent mode.

## When to Use These Challenges

Pick these if your team wants to:
- Implement a real roadmap feature with Copilot assistance
- Learn how to guide Copilot toward high-quality, project-consistent code
- Experience Agent mode for end-to-end feature implementation

## Challenges

| Challenge | Difficulty | Time | Description |
|-----------|-----------|------|-------------|
| [Feature Implementation](challenge-1-feature-implementation.md) | Beginner | 60-90 min | Implement a roadmap feature with Copilot |
| [Boilerplate & Scaffolding](challenge-2-boilerplate-and-scaffolding.md) | Beginner | 30-45 min | Generate repetitive code and project scaffolding |
| [Agent Mode Feature](challenge-3-agent-mode-feature.md) | Advanced | 60-90 min | Let Agent mode implement a feature autonomously |

## Key Copilot Features for This Track

- **Inline completions** — Let Copilot complete code as you type, guided by comments and function signatures
- **Inline Chat** (`Ctrl+I`) — Generate code blocks, refactor selections, ask questions in context
- **Copilot Chat** (`Ctrl+Alt+I`) — Brainstorm approaches, generate larger code blocks, iterate on design
- **Agent Mode** (`Ctrl+Shift+I`) — Autonomous multi-step coding: Copilot plans, creates files, edits code, runs commands

## AI-Assisted Dev Kit Resources

If you've added the [AI-Assisted Dev Kit](../resources/AI-assisted_dev_kit/) to your repository, these resources are especially useful for this track:

| Resource | Type | How to Use |
|----------|------|------------|
| `Developer` agent | Agent | Invoke in Agent mode for TDD-driven feature implementation with built-in test generation and code quality checks |
| `Beast Mode` agent | Agent | Use for complex, multi-step implementation tasks that require persistent autonomous execution |
| `/dev` | Prompt | Run for a structured task-driven development workflow with context discovery, planning, and validation |
| `/execute-tasks` | Prompt | Execute a pre-planned task list from your project's task tracker |

> **Tip:** The `Developer` agent follows a spec-driven, test-first approach. Give it a clear feature description with acceptance criteria for the best results.

## Tips

- **Write clear comments first** — Copilot's inline suggestions are dramatically better when preceded by a descriptive comment
- **Use existing code as a template** — Open a similar file alongside the one you're working on; Copilot picks up patterns from open tabs
- **Iterate, don't accept blindly** — Review every suggestion. Use `Alt+]` to cycle through alternatives
- **Break big tasks into small prompts** — "Implement the entire feature" produces worse results than step-by-step prompts
- **Leverage `@workspace`** — Give Copilot context about your project's conventions, existing patterns, and related code
