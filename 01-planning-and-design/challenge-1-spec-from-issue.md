# Challenge: Spec from Issue

| | |
|---|---|
| **Track** | Planning & Design |
| **Difficulty** | ⭐ Beginner |
| **Time** | 30-45 minutes |
| **Copilot Features** | Chat, `@workspace`, Enterprise Bing search |

## Objective

Turn a real backlog item — a feature request, user story, or vague ticket — into a detailed technical specification using GitHub Copilot. You'll learn how Copilot can accelerate the planning phase by analyzing your codebase, suggesting implementation approaches, and drafting structured specifications.

## Prerequisites

- A backlog item, feature request, or GitHub Issue to work from (even a one-liner is fine)
- Your codebase open in VS Code
- Familiarity with your project's tech stack and conventions

## Your Mission

### Step 1: Frame the Problem (5 min)

Pick a real item from your team's backlog. Open Copilot Chat (`Ctrl+Alt+I`) and give Copilot the context:

```
@workspace I'm planning to implement the following feature: [paste your issue/story here].

Before writing any code, help me draft a technical specification. Start by analyzing the existing codebase to understand:
1. What existing code/modules are relevant to this feature?
2. What patterns does the codebase already use for similar functionality?
3. What dependencies or services would be involved?
```

### Step 2: Draft the Spec (15 min)

Now ask Copilot to generate a structured spec. Try this prompt:

```
Based on your analysis, draft a technical specification for this feature with the following sections:

1. **Overview** — What this feature does and why
2. **Requirements** — Functional and non-functional requirements
3. **Acceptance Criteria** — Specific, testable criteria for "done"
4. **Technical Approach** — Proposed implementation strategy, referencing existing code patterns
5. **API/Interface Changes** — Any new or modified APIs, endpoints, data models
6. **Dependencies** — External services, libraries, or other team dependencies
7. **Risks & Open Questions** — Things that need further investigation
```

### Step 3: Refine with Follow-ups (10 min)

The first draft won't be perfect. Refine it with targeted follow-ups:

```
For the Technical Approach section, be more specific:
- Which files would need to be changed?
- What new files need to be created?
- Suggest the function/class signatures for the main components
```

```
Can you identify any edge cases or error scenarios we should handle?
Reference how similar error handling is done in #file:src/[relevant-file]
```

```
@workspace Are there any existing utility functions or shared code we should reuse for this feature?
```

### Step 4: Validate and Polish (5 min)

Ask Copilot to review its own spec:

```
Review the specification you've drafted. Are there any:
- Missing requirements?
- Inconsistencies between sections?
- Assumptions that should be called out?
- Areas where the approach doesn't align with existing codebase patterns?
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Analyze related code | `@workspace What existing code is related to [feature area]? Show me the key files and their responsibilities.` |
| Generate acceptance criteria | `Write acceptance criteria in Given/When/Then format for: [feature description]` |
| Estimate complexity | `@workspace Based on the codebase, how complex would it be to implement [feature]? What are the main areas of work?` |
| Research best practices | `What are industry best practices for implementing [feature type, e.g., "rate limiting", "file upload", "real-time notifications"]?` |
| Identify breaking changes | `@workspace Would implementing [feature] cause any breaking changes to existing APIs or interfaces?` |

## Pro Tips

- **Use `#file` liberally** — Point Copilot at specific files that are relevant: `#file:src/api/routes.ts What pattern should I follow for the new endpoint?`
- **Iterate, don't regenerate** — Build the spec incrementally with follow-up questions rather than re-prompting from scratch
- **Combine with Bing search** — Copilot Enterprise can search the web: ask about patterns, competitor approaches, or library comparisons
- **Copy to a real doc** — Once refined, paste the spec into a GitHub Issue, PR description, or design document where your team can review it

## Self-Assessment Checklist

- [ ] I selected a real backlog item and gave Copilot meaningful context
- [ ] Copilot analyzed my codebase and identified relevant existing code
- [ ] I generated a structured spec with at least 5 sections
- [ ] I refined the spec with at least 2-3 follow-up prompts
- [ ] The spec references actual files, patterns, and conventions from my codebase
- [ ] I saved the spec somewhere useful (Issue, doc, PR description)

## Going Further

- Try generating a spec for a **larger, multi-sprint feature** — see how Copilot handles breaking it into milestones
- Ask Copilot to create a **task breakdown** with estimated effort for each task
- Use the spec as input for the [Feature Implementation](../02-code-generation/challenge-1-feature-implementation.md) challenge
