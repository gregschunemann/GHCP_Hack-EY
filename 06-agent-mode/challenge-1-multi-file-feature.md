# Challenge: Multi-File Feature

| | |
|---|---|
| **Track** | Agent Mode |
| **Difficulty** | ⭐⭐ Intermediate |
| **Time** | 60-90 minutes |
| **Copilot Features** | Agent Mode, `@workspace`, `#file`, terminal commands |

## Objective

Use Copilot Agent mode to implement a feature that spans multiple files — the kind of task where you'd normally be switching between files, keeping a mental model of changes, and wiring things together. Agent mode handles the coordination while you guide the direction and review the work.

## Prerequisites

- Agent mode enabled (mode picker in Chat panel set to "Agent")
- A feature that requires changes in 3+ files
- Completed the [Feature Implementation](../02-code-generation/challenge-1-feature-implementation.md) challenge (recommended)

> **Good multi-file tasks:**
> - Add a new CRUD feature (model + service + controller + tests + route registration)
> - Implement a cross-cutting concern (logging, caching, or rate limiting across multiple endpoints)
> - Add a new notification/event system (event definition + publisher + subscriber + handler)

## Your Mission

### Step 1: Write a Detailed Task Brief (10 min)

Quality in = quality out. Spend time on this prompt:

```
Implement the following feature in this codebase:

**Feature:** [concise description]

**Detailed Requirements:**
1. [Specific requirement with expected behavior]
2. [Another requirement]
3. [Edge cases to handle]

**Technical Constraints:**
- Follow the existing code patterns in this project
- Reference #file:[example-model] for data model patterns
- Reference #file:[example-controller] for API endpoint patterns
- Reference #file:[example-test] for test patterns
- Use existing shared utilities from #file:[utils-file]
- Don't add new dependencies unless absolutely necessary

**Expected Files:**
- New: [list files you expect to be created]
- Modified: [list files you expect to be changed]

**Definition of Done:**
- All new files follow existing naming and organization conventions
- Basic error handling is included
- Unit tests are written and pass
- The project builds without errors

Analyze the codebase first and propose your plan before making changes.
```

### Step 2: Review and Refine the Plan (5-10 min)

Agent mode will typically respond with a plan. **Read it carefully:**

- Are the right files being created/modified?
- Does the approach match your project's patterns?
- Is anything being over-engineered or unnecessarily complex?

Common redirections:
```
Good plan, but:
- Put the new model in src/models/, not src/entities/ — that's our convention
- We don't need a separate DTO; our models include serialization
- Add the route registration to #file:src/routes/index.ts, not a new route file
```

### Step 3: Supervise Execution (30-40 min)

As Agent mode works, for each proposed change:

**File creations:** Check:
- File name and location follow conventions
- The generated code matches project patterns
- Imports reference the correct paths

**File modifications:** Check:
- The diff makes sense — is it changing the right section?
- It's not accidentally removing or breaking existing code
- New additions are in the right place (e.g., route registration order)

**Terminal commands:** Check:
- The command is correct and safe
- It's using the project's actual build/test commands

**When something is wrong:**
```
Don't modify that file — [reason]. Instead, [correct approach].
```

```
The import path is wrong. In this project, we use @/[module] aliases. 
Check #file:tsconfig.json for path mappings.
```

### Step 4: Validate the Result (10 min)

After Agent completes, do a holistic review:

```
You're done with the implementation. Now:
1. Run the full build to check for errors
2. Run the test suite to check for regressions
3. List all files you created and modified
4. Are there any TODOs or incomplete items?
```

Then review the changes yourself:
- Do the new files fit naturally into the project?
- Would a teammate looking at the PR understand the changes?
- Is there anything Agent added that shouldn't be there?

### Step 5: Document the Experience (5 min)

For the showcase, note:
- How many files did Agent touch?
- How many times did you need to redirect?
- What did Agent do surprisingly well?
- What did it struggle with?

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| CRUD feature | `Implement a complete CRUD feature for [entity] including model, service, controller, routes, and tests. Follow patterns in #file:[ref].` |
| Cross-cutting concern | `Add [logging/caching/validation] to all [controllers/services] in src/[dir]/. Follow the approach in #file:[ref].` |
| Integration | `Connect [module A] to [module B]: when [event] happens in A, [action] should occur in B. Handle errors and add tests.` |
| Phased implementation | `Phase 1: Create the data model and database migration for [entity]. Don't implement the API yet.` |

## Pro Tips

- **Refer to existing files constantly** — `#file:` references are Agent mode's most powerful context signal
- **Phase large tasks** — "Do the data layer first, stop, then I'll tell you to do the API layer" gives you checkpoints
- **Let it build and test** — Agent mode's ability to run terminal commands and self-correct on failures is one of its strongest features
- **Watch for drift** — If Agent starts going in a wrong direction, redirect immediately. The longer it runs off-course, the harder it is to fix
- **Don't accept large diffs blindly** — If a diff is > 50 lines, read it carefully. Consider asking Agent to explain the non-obvious parts

## Self-Assessment Checklist

- [ ] I wrote a detailed task brief with requirements, constraints, and file references
- [ ] I reviewed and refined Agent's plan before execution
- [ ] Agent created/modified 3+ files in a coordinated way
- [ ] I redirected Agent at least once (nobody gets it perfect first try)
- [ ] The project builds and tests pass after Agent's changes
- [ ] I could articulate what Agent did well and where it needed help

## Going Further

- Try a **larger feature** that spans 7+ files — how does Agent handle the complexity?
- Compare Agent mode with manual [Feature Implementation](../02-code-generation/challenge-1-feature-implementation.md) — when is each approach better?
- Move to the [End-to-End Workflow](challenge-3-end-to-end-workflow.md) challenge for implementation + tests + docs in one session
