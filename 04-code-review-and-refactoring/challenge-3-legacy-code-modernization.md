# Challenge: Legacy Code Modernization

| | |
|---|---|
| **Track** | Code Review & Refactoring |
| **Difficulty** | ⭐⭐⭐ Advanced |
| **Time** | 60-90 minutes |
| **Copilot Features** | Chat, Agent Mode, `@workspace`, `#file`, Inline Chat |

## Objective

Use GitHub Copilot to identify and modernize legacy patterns, deprecated APIs, and outdated practices in your codebase. This goes beyond simple refactoring — you'll update code to use current language features, modern library APIs, and contemporary best practices while preserving functionality.

## Prerequisites

- A codebase with some age — code written 2+ years ago, or using older patterns/APIs
- Understanding of your language's modern features and idioms
- Tests (strongly recommended — modernization without tests is risky)

> **Examples of legacy patterns to modernize:**
> - Callbacks → Promises → Async/Await (JavaScript/TypeScript)
> - `var` → `let`/`const` (JavaScript)
> - Class components → Functional components with hooks (React)
> - Raw SQL → ORM queries or parameterized queries
> - XML config → code-based configuration (.NET)
> - `Thread` / manual synchronization → `async`/`Task` patterns (C#)
> - Old-style string formatting → f-strings (Python)
> - `unittest` → `pytest` patterns (Python)

## Your Mission

### Step 1: Identify Legacy Patterns (10 min)

```
@workspace Analyze this codebase for legacy or outdated patterns:

1. **Deprecated APIs** — Functions, methods, or libraries that have newer replacements
2. **Old language features** — Patterns that have been superseded by modern language features
3. **Outdated libraries** — Dependencies that have been replaced by better alternatives
4. **Anti-patterns** — Approaches that were once common but are now considered bad practice
5. **Missing modern features** — Places where modern features (async/await, pattern matching, 
   nullability, etc.) could simplify the code

For each finding, show:
- Where it is (file + code)
- What the modern replacement is
- What the migration effort would be (small/medium/large)
```

### Step 2: Prioritize Modernization (5 min)

```
From the legacy patterns you identified, prioritize them into:

**Quick Wins** — Can be modernized file-by-file with no breaking changes
**Medium Effort** — Require coordinated changes across multiple files
**Large Migration** — Requires a migration strategy, possibly phased

For today's hackathon, let's focus on the Quick Wins and one Medium Effort item.
```

### Step 3: Modernize a Quick Win (15 min)

Pick the highest-value quick win and modernize it:

**Using Inline Chat:**
1. Select the legacy code
2. Press `Ctrl+I`
3. `Modernize this code to use [modern pattern]. Keep the same behavior.`

**Using Chat for approach guidance:**
```
I want to modernize #file:[target-file] from [old pattern] to [new pattern].
What's the safest approach? Should I do it incrementally or all at once?
Show me the modernized version of the key functions.
```

**Example prompts by language:**

JavaScript/TypeScript:
```
Convert all callback-based functions in #file:[file] to use async/await. 
Handle errors with try/catch instead of .catch() callbacks.
```

Python:
```
Modernize #file:[file] to use:
- f-strings instead of .format() or % formatting
- Pathlib instead of os.path
- Type hints on all function signatures
- Dataclasses where plain classes are used as data containers
```

C#/.NET:
```
Update #file:[file] to use:
- Nullable reference types
- Pattern matching instead of cascading if/else type checks
- Records where appropriate instead of classes with manual Equals/GetHashCode
- async/await instead of Task.ContinueWith
```

### Step 4: Tackle a Medium Effort Item (20 min)

For larger modernization, use Agent mode (`Ctrl+Shift+I`):

```
Modernize [describe the pattern] across the codebase:

Current state: [old pattern, e.g., "We use callbacks for async operations in the data layer"]
Target state: [new pattern, e.g., "All async operations should use async/await"]

Scope: Focus on [specific module/directory] only.
Constraints:
- Don't change public API signatures (internal changes only)
- Maintain backward compatibility
- Run tests after each file change to verify nothing breaks

Start with the lowest-risk files and work up.
```

### Step 5: Validate the Modernization (10 min)

```
@workspace Review all the modernization changes in [directory/module]:
1. Is the behavior preserved?
2. Are there any remaining instances of the old pattern I missed?
3. Are the modernized versions idiomatic (using best practices, not just "technically modern")?
4. Did any new issues get introduced?
```

Run the full test suite to confirm.

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Find deprecated usage | `@workspace Find all uses of deprecated functions, methods, or APIs in this project.` |
| Language version upgrade | `What modern [language] features (versions [X] through [Y]) could improve this codebase? Show specific examples.` |
| Library migration | `We want to migrate from [old library] to [new library]. What changes are needed in #file:[file]?` |
| API modernization | `Modernize this REST API to follow current best practices: proper status codes, consistent error responses, pagination, etc.` |
| Framework upgrade | `@workspace What changes would we need to make to upgrade from [framework version X] to [version Y]?` |

## Pro Tips

- **Modernize incrementally** — Don't try to rewrite everything at once. Fix one pattern per commit
- **Keep both patterns temporarily** — During migration, it's OK to have both old and new patterns. Add a TODO comment and a tracking issue
- **Run tests obsessively** — Modernization bugs are subtle. Run tests after every logical change
- **Use Agent mode for multi-file changes** — When the same modernization applies across many files, Agent mode can handle the repetition
- **Check your language's release notes** — Ask Copilot: "What features were added in [language] version [X] that are relevant to this codebase?"

## Self-Assessment Checklist

- [ ] I identified at least 5 legacy patterns in my codebase
- [ ] I prioritized them by effort and impact
- [ ] I modernized at least 2 "quick win" patterns
- [ ] I tackled at least one "medium effort" modernization
- [ ] All tests pass after modernization
- [ ] The modernized code is more readable and maintainable
- [ ] I documented remaining modernization work as TODOs or tickets

## Going Further

- Create a **modernization roadmap** — a prioritized list of all legacy patterns and a plan to address them over time
- Use Copilot to help plan a **major framework or language version upgrade**
- Set up **linting rules** that flag old patterns to prevent regression: ask Copilot to suggest ESLint/Pylint/StyleCop rules
- Try Agent mode for a **dependency migration** (e.g., replace one HTTP client library with another across the codebase)
