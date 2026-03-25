# Agent Mode Challenges

Let Copilot drive multi-step workflows autonomously. Agent mode is the most powerful — and most advanced — way to use Copilot. It can plan an approach, create and edit multiple files, run terminal commands, and iterate on errors. These challenges build your skills from guided supervision to confident delegation.

## What Is Agent Mode?

Agent mode turns Copilot from a suggestion engine into an autonomous coding agent. Instead of responding to one question at a time, Agent mode:

1. **Plans** — Analyzes your request and proposes a multi-step approach
2. **Executes** — Creates files, edits code, runs terminal commands
3. **Iterates** — Checks its own work (builds, tests, linting) and fixes issues
4. **Reports** — Summarizes what it did and any remaining issues

You stay in control: every file edit and terminal command requires your approval.

> **Terminal alternative:** GitHub Copilot CLI provides the same agentic workflow directly from your terminal. If you prefer the command line over VS Code, check out the [Copilot CLI Agent challenge](challenge-4-copilot-cli-agent.md).

## How to Use Agent Mode

1. Open the Chat panel (`Ctrl+Alt+I`) or press `Ctrl+Shift+I`
2. Look at the mode picker dropdown at the top of the chat input — select **Agent**
3. Type your task description and press Enter
4. Review each proposed action (file edit, terminal command) and Accept or Reject

## When to Use These Challenges

Pick these if your team:
- Is comfortable with Copilot Chat and wants to try the next level
- Has well-scoped tasks that span multiple files  
- Wants to explore autonomous coding workflows

## Challenges

| Challenge | Difficulty | Time | Description |
|-----------|-----------|------|-------------|
| [Multi-File Feature](challenge-1-multi-file-feature.md) | Intermediate | 60-90 min | Implement a feature across multiple files |
| [Bug Investigation](challenge-2-bug-investigation.md) | Intermediate | 45-60 min | Let the agent find and fix a bug |
| [End-to-End Workflow](challenge-3-end-to-end-workflow.md) | Advanced | 60-90 min | Plan, implement, test, and document in one session |
| [Copilot CLI Agent](challenge-4-copilot-cli-agent.md) | Intermediate | 45-60 min | Use Copilot CLI as a terminal-native coding agent |

## Key Agent Mode Features

- **Multi-file editing** — Agent can create, modify, and delete files in a single workflow
- **Terminal integration** — Agent can run build commands, tests, linters, and shell commands
- **Self-correction** — When builds fail or tests break, Agent automatically attempts fixes
- **Context awareness** — Agent uses `@workspace` context to understand your project before making changes
- **`#file` references** — Point Agent at specific files for context or as pattern examples
- **Terminal-native agent** — Copilot CLI (`copilot`) provides the same agentic workflow from the command line, with plan mode, built-in agents, and `/review` for code review

## Tips

- **Start with a detailed prompt** — Agent mode output quality scales directly with prompt quality
- **Review the plan before executing** — The plan phase is your best chance to redirect
- **Don't accept blindly** — Read every diff before accepting. Reject and redirect when needed
- **Use `#file` references generously** — The more context you give, the better the output
- **Break large tasks into phases** — "Implement the data layer first, then the API layer" works better than "implement everything"
