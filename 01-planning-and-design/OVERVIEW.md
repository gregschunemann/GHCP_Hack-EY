# Planning & Design Challenges

Use GitHub Copilot to go from idea to design *before* writing code. These challenges show how Copilot can help you think through requirements, analyze architecture, and document decisions — all using your own codebase as context.

## When to Use These Challenges

Pick these if your team wants to:
- Turn a vague backlog item into a concrete technical specification
- Get an AI-assisted review of your project's architecture
- Document a pending technical decision with trade-off analysis

## Challenges

| Challenge | Difficulty | Time | Description |
|-----------|-----------|------|-------------|
| [Spec from Issue](challenge-1-spec-from-issue.md) | Beginner | 30-45 min | Turn a backlog item into a full technical spec |
| [Architecture Review](challenge-2-architecture-review.md) | Intermediate | 45-60 min | Analyze your repo's architecture with Copilot |
| [ADR Generation](challenge-3-adr-generation.md) | Intermediate | 30-45 min | Draft an Architecture Decision Record |

## Key Copilot Features for This Track

- **`@workspace`** — Gives Copilot visibility into your entire project structure, dependencies, and code patterns
- **Copilot Chat** (`Ctrl+Alt+I`) — Best for longer, conversational planning tasks
- **Enterprise Bing search** — Ask Copilot to research technologies, compare frameworks, or find best practices (enabled by default in Copilot Enterprise)

## AI-Assisted Dev Kit Resources

If you've added the [AI-Assisted Dev Kit](../resources/AI-assisted_dev_kit/) to your repository, these resources are especially useful for this track:

| Resource | Type | How to Use |
|----------|------|------------|
| `Architect` agent | Agent | Invoke in Agent mode for architecture analysis, ADRs, and design documentation |
| `/create-spec` | Prompt | Run to generate a structured technical specification from a feature description |
| `/create-architecture-diagram` | Prompt | Generate Mermaid architecture diagrams from your codebase |
| `/plan-product` | Prompt | Plan a new product or feature with structured documentation |
| `/analyze-product` | Prompt | Analyze your codebase and populate `copilot-instructions.md` with your project's context |

> **Tip:** Run `/analyze-product` first on your repo — it populates `copilot-instructions.md` with your tech stack and conventions, which improves all subsequent Copilot responses.

## Tips

- Be specific about your project's constraints (language, framework, team size, deployment target) when prompting
- Use `#file` references to point Copilot at relevant files: `#file:package.json`, `#file:src/config.ts`
- Ask follow-up questions — planning prompts often benefit from iterative refinement
- Copy Copilot's output into a real document (PR description, Confluence page, GitHub Issue) to make it actionable
