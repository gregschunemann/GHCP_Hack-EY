# Challenge: Architecture Review

| | |
|---|---|
| **Track** | Planning & Design |
| **Difficulty** | ⭐⭐ Intermediate |
| **Time** | 45-60 minutes |
| **Copilot Features** | Chat, `@workspace`, `#file` references |

## Objective

Use GitHub Copilot to perform an AI-assisted architecture review of your codebase. You'll learn how to use `@workspace` to give Copilot a holistic view of your project, then ask it to identify strengths, weaknesses, coupling issues, and improvement opportunities.

## Prerequisites

- Your codebase open in VS Code
- Basic understanding of your project's intended architecture
- Familiarity with common architectural patterns (MVC, microservices, layered architecture, etc.)

## Your Mission

### Step 1: Get the Big Picture (10 min)

Start by asking Copilot to describe your architecture as it understands it:

```
@workspace Analyze the overall architecture of this project. Describe:
1. The main layers or modules and their responsibilities
2. The key entry points (APIs, CLI, UI)
3. How data flows through the system
4. The major external dependencies and integrations
```

**Evaluate the response:** Does it match your understanding? Correct any misconceptions:

```
Good analysis, but a few corrections:
- [Module X] is actually responsible for [Y]
- We use [pattern] for [purpose], not what you described
With these corrections, continue the review.
```

### Step 2: Analyze Coupling & Cohesion (15 min)

Now dig into the quality of the architecture:

```
@workspace Analyze the coupling and cohesion in this codebase:
1. Which modules are tightly coupled? Show specific import/dependency chains.
2. Are there any circular dependencies?
3. Which modules have low cohesion (doing too many unrelated things)?
4. Which modules are well-designed with high cohesion and loose coupling?
```

Follow up on specific areas:

```
@workspace Focus on #file:src/[module-you're-concerned-about]. 
What does this module depend on, and what depends on it? 
Is it doing too much? How could it be decomposed?
```

### Step 3: Identify Design Patterns and Anti-Patterns (10 min)

```
@workspace Identify the design patterns used in this codebase:
1. Which patterns are used consistently and effectively?
2. Are there any anti-patterns or code smells at the architectural level?
3. Are there places where a pattern is started but not followed through?
4. What patterns are missing that would benefit this project?
```

### Step 4: Evaluate for Scale and Maintainability (10 min)

```
@workspace If this codebase needs to scale to handle 10x the current load/complexity:
1. What are the bottlenecks or weak points?
2. Where would you expect maintenance problems as the team grows?
3. What would you recommend changing to improve scalability?
4. Are there any single points of failure?
```

### Step 5: Generate an Architecture Summary (10 min)

Ask Copilot to synthesize everything into a reviewable document:

```
Based on our architecture review, generate a summary document with:
1. **Architecture Overview** — Brief description with a text-based diagram
2. **Strengths** — What's well-designed
3. **Areas of Concern** — Specific issues with file/module references
4. **Recommendations** — Prioritized list of improvement suggestions
5. **Quick Wins** — Changes that would have high impact with low effort
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Dependency analysis | `@workspace Map the dependency graph of the main modules. Which modules have the most dependents?` |
| SOLID principles check | `@workspace Evaluate this codebase against the SOLID principles. Where are violations?` |
| API surface review | `@workspace Review the public API surface. Are there endpoints/functions that are redundant, inconsistent, or poorly named?` |
| Configuration review | `@workspace How is configuration managed? Are there hardcoded values that should be configurable?` |
| Error handling review | `@workspace How is error handling done across the codebase? Is it consistent? Are there gaps?` |

## Pro Tips

- **Correct Copilot's misunderstandings** — The first analysis may have inaccuracies. Correcting them in follow-ups improves all subsequent responses
- **Use `#file` for deep dives** — When Copilot identifies a problem area, use `#file:path/to/module` to zoom in
- **Compare with documentation** — If you have architecture docs, paste key sections into Chat and ask Copilot to compare the docs with the actual code
- **Use the `Architect` agent** — If you've set up the [AI-Assisted Dev Kit](../../resources/AI-assisted_dev_kit/), switch to the `Architect` agent in Agent mode for deeper architectural analysis and documentation
- **Use the `/create-architecture-diagram` prompt** — Quickly generate a Mermaid architecture diagram from your codebase with a single command
- **Get visual** — Ask Copilot to generate text-based diagrams (Mermaid syntax works well): `Create a Mermaid diagram showing the module dependencies`

## Self-Assessment Checklist

- [ ] Copilot generated an architecture overview that roughly matches my understanding
- [ ] I corrected at least one misconception and saw improved follow-up responses
- [ ] Copilot identified specific coupling or cohesion issues with file references
- [ ] I received actionable improvement recommendations
- [ ] I generated a summary document I could share with my team
- [ ] I learned something new about my codebase from Copilot's analysis

## Going Further

- Ask Copilot to **compare your architecture** with a well-known reference architecture for your tech stack
- Use the findings to create tickets for technical debt reduction
- Feed the recommendations into the [Refactor with Copilot](../04-code-review-and-refactoring/challenge-1-refactor-with-copilot.md) challenge
- Ask Copilot to generate a **Mermaid architecture diagram** and render it
