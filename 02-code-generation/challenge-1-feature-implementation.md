# Challenge: Feature Implementation

| | |
|---|---|
| **Track** | Code Generation |
| **Difficulty** | ⭐ Beginner |
| **Time** | 60-90 minutes |
| **Copilot Features** | Inline completions, Inline Chat, Chat, `@workspace` |

## Objective

Implement a real feature from your team's backlog using GitHub Copilot. This challenge focuses on the core Copilot coding workflow: using inline completions for flow-state coding, Inline Chat for targeted generation, and Chat for design decisions. By the end, you'll have a working feature (or significant progress toward one) and a clear sense of how Copilot fits into your development process.

## Prerequisites

- A feature or user story from your backlog (small to medium scope — something achievable in 60-90 min)
- Your codebase open in VS Code
- Understanding of where new code should go in your project

> **Don't have a feature?** Pick one of these universal options:
> - Add input validation to an existing form or API endpoint
> - Add a new API endpoint that follows existing patterns
> - Implement a utility function your codebase is missing
> - Add a configuration option that's been requested

## Your Mission

### Step 1: Plan the Approach (10 min)

Before writing code, use Chat to plan:

```
@workspace I need to implement the following feature: [describe your feature]

Help me plan the implementation:
1. Which existing files will need to be modified?
2. What new files should I create?
3. What's the right order to implement things?
4. Are there existing patterns in the codebase I should follow?
```

### Step 2: Scaffold the Structure (10 min)

Create new files or functions with Copilot's help. Use Inline Chat (`Ctrl+I`) in the appropriate file:

```
Create a [class/function/component] called [name] that [description].
Follow the same patterns used in #file:[similar-existing-file].
```

Or use a comment-driven approach — type a descriptive comment and let inline completions do the work:

```python
# Service class for handling user notifications
# Follows the same pattern as UserAuthService
# Methods: send_notification, get_notifications, mark_as_read
```

### Step 3: Implement Core Logic (30-40 min)

This is the main coding phase. Alternate between:

**Inline completions** — Write a comment or function signature, let Copilot complete:
```javascript
// Validate that the email address is in the correct format
// and is not already registered in the database
function validateEmail(email) {
  // Copilot completes from here...
}
```

**Inline Chat** (`Ctrl+I`) for specific blocks:
```
Generate the error handling for this function. 
Use the same error types as #file:src/errors.ts
```

**Chat** (`Ctrl+Alt+I`) for design questions mid-implementation:
```
@workspace I'm implementing [feature] and need to decide how to handle [scenario].
How do similar features in this codebase handle it?
```

### Step 4: Wire It Together (10 min)

Connect your new code to the existing codebase:

```
@workspace I've created [new component/function]. 
Now I need to integrate it. Where should I:
1. Register/import it?
2. Add it to routing/configuration?
3. Connect it to the existing data flow?
Show me the specific changes needed in each file.
```

### Step 5: Quick Validation (10 min)

Use Copilot to help you verify the implementation:

```
@workspace Review the feature I just implemented across these files: 
#file:[file1] #file:[file2] #file:[file3]

Check for:
1. Missing error handling
2. Inconsistencies with existing code patterns
3. Potential bugs or edge cases
4. Missing imports or configuration
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Follow existing patterns | `Create a [thing] that follows the same pattern as #file:[existing-file]` |
| Generate with constraints | `Implement [function] with these constraints: [list constraints like "must be async", "handle null input", "return typed result"]` |
| Fill in implementation | Select a function stub → `Ctrl+I` → `Implement this function based on its signature and the surrounding code` |
| Add error handling | Select code → `Ctrl+I` → `Add comprehensive error handling following the patterns in #file:[error-handling-file]` |
| Generate types/interfaces | `@workspace Based on the data flowing through #file:[file], generate TypeScript interfaces / data classes for [entity]` |

## Pro Tips

- **Comment-driven development** — Write the comment *first*, then let Copilot generate the code. Clear comments = better suggestions
- **Open reference files** — Keep files with similar patterns open in other tabs. Copilot draws context from open editors
- **Use `#selection`** — Select code and reference it in Chat: `Explain #selection and then refactor it to also handle [new case]`
- **Partial accept** — Press `Ctrl+→` (Cmd+→ on Mac) to accept a suggestion word-by-word instead of all-at-once
- **Use the `/dev` prompt or `Developer` agent** — If you've set up the [AI-Assisted Dev Kit](../../resources/AI-assisted_dev_kit/), run `/dev` in Agent mode for a structured development workflow (context discovery → research → plan → implement → test). Or switch to the `Developer` agent for spec-driven, TDD-focused implementation
- **Reject and re-prompt** — If the suggestion is wrong, press `Esc`, refine your comment, and try again. Copilot learns from the context you build

## Self-Assessment Checklist

- [ ] I planned the implementation with Copilot before writing code
- [ ] I used at least 2 different Copilot interaction modes (inline, Inline Chat, Chat)
- [ ] I leveraged `@workspace` or `#file` to give Copilot project-specific context
- [ ] I followed my project's existing patterns (Copilot suggested code consistent with the codebase)
- [ ] The feature compiles/runs without errors (or I'm close)
- [ ] I can articulate when inline completions vs. Chat vs. Inline Chat was most useful

## Going Further

- Add unit tests for your feature using the [Unit Test Generation](../03-testing-and-quality/challenge-1-unit-test-generation.md) challenge
- Have another team member review your Copilot-assisted code — can they tell which parts Copilot wrote?
- Try implementing the **same feature** with [Agent Mode](challenge-3-agent-mode-feature.md) and compare the experience
