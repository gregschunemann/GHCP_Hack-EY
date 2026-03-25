# Challenge: ADR Generation

| | |
|---|---|
| **Track** | Planning & Design |
| **Difficulty** | ⭐⭐ Intermediate |
| **Time** | 30-45 minutes |
| **Copilot Features** | Chat, `@workspace`, Enterprise Bing search |

## Objective

Use GitHub Copilot to draft an Architecture Decision Record (ADR) for a pending technical decision. ADRs document the "why" behind architectural choices — the context, alternatives considered, trade-offs, and final decision. You'll learn how Copilot can research alternatives, analyze trade-offs, and produce well-structured decision documents.

## Prerequisites

- A pending technical decision (e.g., "which database for the new service?", "should we adopt a monorepo?", "which auth library?")
- Your codebase open in VS Code (for context on current state)
- If you don't have a pending decision, pick one retroactively: a past decision that was never documented

## Your Mission

### Step 1: Describe the Decision Context (5 min)

Open Copilot Chat (`Ctrl+Alt+I`) and frame the decision:

```
@workspace I need to create an Architecture Decision Record (ADR) for the following decision:

**Decision:** [e.g., "Choose a state management library for our React frontend"]

**Context:** [e.g., "Our React app currently uses prop drilling and local state. As the app grows, we need a more scalable state management approach. The team has experience with Redux but is open to alternatives."]

First, analyze our current codebase to understand the current state of things related to this decision.
```

### Step 2: Research Alternatives (10 min)

Ask Copilot to research and compare options:

```
For this decision, identify the top 3-4 alternatives and compare them:

For each alternative, provide:
1. **Description** — What it is and how it works
2. **Pros** — Advantages for our specific project
3. **Cons** — Disadvantages and trade-offs
4. **Fit with our codebase** — How well does it integrate with what we already have?
5. **Community & support** — Maturity, popularity, maintenance status

Present this as a comparison table.
```

**Leverage Bing search (Copilot Enterprise):**
```
Search for recent benchmarks and community comparisons of [option A] vs [option B] vs [option C]. What's the current recommendation for projects like ours in 2026?
```

### Step 3: Generate the ADR (10 min)

Now ask Copilot to draft the full ADR:

```
Draft an Architecture Decision Record using this template:

# ADR-[number]: [Decision Title]

## Status
[Proposed / Accepted / Deprecated / Superseded]

## Date
[Today's date]

## Context
What is the issue that we're seeing that is motivating this decision or change?

## Decision
What is the change that we're proposing and/or doing?

## Alternatives Considered
What other options were considered? Why were they rejected?

## Consequences
What becomes easier or harder because of this change?

## References
Links to research, benchmarks, or related ADRs.

Base the content on our discussion above and our codebase context.
```

### Step 4: Refine and Challenge (10 min)

Push Copilot to strengthen the ADR:

```
Play devil's advocate: What are the strongest arguments AGAINST the recommended decision? What could go wrong?
```

```
@workspace What would be the migration effort if we chose [recommended option]? Which files would need to change? Estimate the scope.
```

```
Review this ADR for completeness. Are there any:
- Missing alternatives we should have considered?
- Consequences we haven't thought of?
- Assumptions that should be explicitly stated?
```

### Step 5: Save the ADR (5 min)

Copy the final ADR into your project. Common locations:
- `docs/adr/` folder in your repo
- A wiki or Confluence page
- A GitHub Issue or Discussion

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Research a technology | `What are the pros and cons of [technology] for [use case] in [year]? Compare with alternatives.` |
| Analyze migration effort | `@workspace If we switch from [current] to [proposed], how many files would be affected? What's the migration strategy?` |
| Check compatibility | `@workspace Is [proposed technology] compatible with our current stack? Check our dependencies in #file:package.json` |
| Get team perspective | `What questions should a team consider before adopting [technology]? What are the hidden costs?` |
| Historical context | `@workspace Have we made similar decisions before? Are there patterns in how we've adopted new libraries or frameworks?` |

## Pro Tips

- **Use Bing search for current data** — Copilot Enterprise can search the web for up-to-date benchmarks, community sentiment, and recent releases
- **Be specific about constraints** — Tell Copilot your team size, deployment environment, performance requirements, and budget — these shape the trade-off analysis
- **Document the "No" decisions too** — ADRs for "we considered X and decided not to adopt it" are just as valuable as "we chose Y"
- **Link ADRs to code** — Reference specific files/modules that would be affected by the decision
- **Use the `Architect` agent** — If you've set up the [AI-Assisted Dev Kit](../../resources/AI-assisted_dev_kit/), switch to the `Architect` agent in Agent mode. It specializes in strategic technical planning, trade-off analysis, and architectural documentation — ideal for ADR generation
- **Keep a running folder** — Start a `docs/adr/` directory in your repo today

## Self-Assessment Checklist

- [ ] I framed a real technical decision with appropriate context
- [ ] Copilot researched and compared at least 3 alternatives
- [ ] The generated ADR follows a clear, standard template
- [ ] I challenged the recommendation and considered counter-arguments
- [ ] The ADR references specific aspects of my codebase
- [ ] The final ADR is good enough to share with my team for review

## Going Further

- Create ADRs for **past decisions** that were never documented — use `@workspace` to help reconstruct the context
- Set up an `docs/adr/` folder with a numbering convention and an index file
- Ask Copilot to generate an **ADR template** customized to your team's needs
- Use the ADR as input for the [Feature Implementation](../02-code-generation/challenge-1-feature-implementation.md) challenge
