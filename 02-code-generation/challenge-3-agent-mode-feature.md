# Challenge: Agent Mode Feature

| | |
|---|---|
| **Track** | Code Generation |
| **Difficulty** | ⭐⭐⭐ Advanced |
| **Time** | 60-90 minutes |
| **Copilot Features** | Agent Mode, `@workspace`, terminal integration |

## Objective

Use Copilot Agent Mode to implement a feature end-to-end with minimal manual intervention. Agent mode can plan an approach, create and edit multiple files, run terminal commands (build, test, lint), and iterate on errors — all from a single prompt. You'll learn when to let the agent run and when to intervene, redirect, or correct.

## Prerequisites

- Agent mode enabled in VS Code (check the mode picker dropdown in the Chat panel)
- A well-scoped feature or task (clear enough to describe in 2-3 sentences)
- Your codebase open in VS Code
- Completed the [Feature Implementation](challenge-1-feature-implementation.md) challenge or equivalent experience with Copilot Chat

> **Choosing the right task for Agent mode:**
> - ✅ **Good:** "Add a health check endpoint that returns service status and dependency health"
> - ✅ **Good:** "Create a new settings page with form validation following our existing UI patterns"
> - ❌ **Too vague:** "Improve the app" — Agent needs specific goals
> - ❌ **Too large:** "Rewrite the authentication system" — Break it down first

## Your Mission

### Step 1: Craft a Clear Task Description (10 min)

The quality of Agent mode's output depends heavily on the quality of your prompt. Write a thorough task description:

```
Implement the following feature in this codebase:

**Feature:** [Clear, specific description]

**Requirements:**
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

**Constraints:**
- Follow the existing code patterns and conventions in this project
- Use the same libraries/frameworks already in use (don't introduce new dependencies unless necessary)
- Include error handling consistent with the rest of the codebase
- [Any project-specific constraints]

**Files to reference for patterns:**
- #file:[reference-file-1] — Example of similar existing feature
- #file:[reference-file-2] — Shared utilities to reuse

Start by analyzing the codebase and explaining your plan before making changes.
```

### Step 2: Review the Plan (5 min)

Agent mode will typically present a plan before coding. **Read it carefully:**

- Does the plan make sense?
- Is it modifying the right files?
- Is it following your project's patterns?
- Is it introducing unnecessary dependencies?

If the plan needs adjustment:
```
Good plan, but make these changes:
- Don't create a new utility file — use the existing one in #file:[path]
- Follow the naming convention used in [module]: camelCase for functions, PascalCase for classes
- Include input validation at the API layer, not the service layer
```

### Step 3: Let the Agent Work (30-40 min)

Click through the agent's proposed changes. For each step, you'll see:
- **File edits** — Review diffs before accepting
- **File creations** — Check naming and location
- **Terminal commands** — Review before allowing execution (builds, installs, tests)

**Key decisions to make at each step:**
- ✅ **Accept** — The change looks correct and follows your patterns
- ✏️ **Modify then accept** — The change is close but needs a tweak; tell the agent what to fix
- ❌ **Reject** — The change is wrong; explain why and redirect

**Example interventions:**
```
That file should go in src/services/, not src/utils/. Move it and update the imports.
```

```
Don't use that library — we already have a similar function in #file:src/helpers/validation.ts. Use that instead.
```

```
The error handling here doesn't match our pattern. Look at #file:src/api/userController.ts for the correct approach.
```

### Step 4: Validate the Result (10 min)

After the agent finishes, validate the implementation:

```
Run the project's build command to check for compilation errors.
```

```
Run the existing tests to make sure nothing is broken.
```

```
Review all changes you made and summarize:
1. Files created
2. Files modified
3. Any remaining TODOs or incomplete items
```

### Step 5: Reflect on Agent Mode Effectiveness (5 min)

Document your experience for the showcase:
- What did Agent mode do well?
- Where did you need to intervene?
- How did the quality compare to manual Copilot-assisted coding?
- What makes a good vs. bad Agent mode prompt?

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Feature with constraints | `Implement [feature]. Use only existing dependencies. Follow patterns in #file:[ref]. Include tests.` |
| Fix and iterate | `The build is failing because [error]. Fix it without changing the public API.` |
| Add to existing feature | `Extend #file:[existing-feature] to also support [new capability]. Don't break existing behavior.` |
| Multi-file refactor | `Rename [concept] to [new-name] across the entire codebase. Update all references, imports, and tests.` |
| Generate with tests | `Implement [feature] and also write unit tests. Run the tests and fix any failures.` |

## Pro Tips

- **Front-load context in your prompt** — Agent mode works best when the initial prompt is detailed. Include requirements, constraints, and file references
- **Don't accept everything** — Agent mode is powerful but imperfect. Review every diff, especially in critical code paths
- **Use the plan phase** — The agent's initial plan is your best opportunity to redirect. It's cheaper to fix a plan than to fix code
- **Terminal commands are powerful** — Agent mode can run builds, tests, and linters. Let it iterate on failures — it often self-corrects
- **Break large tasks into sessions** — If the feature is too large for one session, do it in phases: "First, create the data model and service layer. Stop there."

## Self-Assessment Checklist

- [ ] I crafted a clear, specific task description with requirements and constraints
- [ ] I reviewed Agent mode's plan before letting it code
- [ ] I intervened at least once to redirect or correct the agent
- [ ] The agent created/modified multiple files in a coordinated way
- [ ] I let the agent run terminal commands (build, test) and iterate on errors
- [ ] The final result compiles and is close to production-ready
- [ ] I can articulate when Agent mode is better vs. when manual Chat is better

## Going Further

- Try giving Agent mode a **bug to fix** using the [Bug Investigation](../06-agent-mode/challenge-2-bug-investigation.md) challenge
- Compare Agent mode's output with what you built manually in [Feature Implementation](challenge-1-feature-implementation.md)
- Try an **end-to-end workflow**: Agent mode implements → generates tests → generates docs (see [End-to-End Workflow](../06-agent-mode/challenge-3-end-to-end-workflow.md))
