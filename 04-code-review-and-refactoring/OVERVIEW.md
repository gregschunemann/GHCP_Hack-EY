# Code Review & Refactoring Challenges

Clean up, strengthen, and modernize your codebase with AI-assisted review and refactoring. These challenges use Copilot to find code smells, security issues, and legacy patterns — then fix them.

## When to Use These Challenges

Pick these if your team wants to:
- Refactor messy or duplicated code with Copilot as a pair partner
- Get an AI-assisted security and performance review
- Modernize legacy code patterns to current best practices

## Challenges

| Challenge | Difficulty | Time | Description |
|-----------|-----------|------|-------------|
| [Refactor with Copilot](challenge-1-refactor-with-copilot.md) | Beginner | 30-45 min | Refactor messy code using Copilot's help |
| [Security & Performance Review](challenge-2-security-and-perf-review.md) | Intermediate | 45-60 min | Audit for vulnerabilities and bottlenecks |
| [Legacy Code Modernization](challenge-3-legacy-code-modernization.md) | Advanced | 60-90 min | Update deprecated patterns to modern standards |

## Key Copilot Features for This Track

- **Inline Chat** (`Ctrl+I`) — Select code and ask for refactoring suggestions in-place
- **`/fix`** — Quick fixes for identified issues
- **`@workspace`** — Cross-file analysis for systemic issues
- **Chat** (`Ctrl+Alt+I`) — Detailed code review conversations

## AI-Assisted Dev Kit Resources

If you've added the [AI-Assisted Dev Kit](../resources/AI-assisted_dev_kit/) to your repository, these resources are especially useful for this track:

| Resource | Type | How to Use |
|----------|------|------------|
| `Developer` agent | Agent | Invoke in Agent mode for refactoring tasks with code quality checks, linting, and test validation |
| `Beast Mode` agent | Agent | Use for complex, multi-file modernization tasks requiring persistent autonomous execution |

> **Tip:** Run `/analyze-product` before starting these challenges — it populates `copilot-instructions.md` with your project's coding standards, which helps Copilot suggest refactors that match your team's style.

## Tips

- **Review in stages** — First identify issues, then fix them one at a time. Don't try to refactor everything at once
- **Preserve behavior** — Always run tests before and after refactoring to verify nothing broke
- **Use version control** — Commit before refactoring so you can easily diff and revert
- **Focus on readability** — The best refactoring makes code easier for humans to understand, not just shorter
