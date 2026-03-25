# Challenge: Refactor with Copilot

| | |
|---|---|
| **Track** | Code Review & Refactoring |
| **Difficulty** | ⭐ Beginner |
| **Time** | 30-45 minutes |
| **Copilot Features** | Inline Chat, Chat, `/fix`, `#file` references |

## Objective

Use GitHub Copilot to identify and refactor code that needs improvement — duplicated logic, long methods, poor naming, complex conditionals, or inconsistent patterns. You'll learn to use Copilot as a refactoring pair partner, iterating on improvements while keeping behavior intact.

## Prerequisites

- Your codebase open in VS Code
- Code that you know needs improvement (every project has some!)
- Existing tests (recommended — gives confidence that refactoring preserves behavior)

## Your Mission

### Step 1: Identify Refactoring Candidates (5 min)

Ask Copilot to find code that needs attention:

```
@workspace Identify the top 5 areas in this codebase that would benefit most 
from refactoring. Look for:
- Long functions (>50 lines)
- Duplicated code across files
- Complex conditional logic (deeply nested if/else)
- Poor or inconsistent naming
- God classes / modules that do too many things
- Magic numbers or hardcoded values

For each, explain what's wrong and suggest what refactoring to apply.
```

### Step 2: Refactor a Long Function (10 min)

Find a long or complex function and break it down:

1. Select the function
2. Press `Ctrl+I` (Inline Chat):

```
Refactor this function by extracting logical sections into smaller, 
well-named helper functions. Keep the same external behavior.
```

Follow up:
```
The extracted functions should have:
- Descriptive names that explain what they do (not how)
- Clear parameter and return types
- No side effects unless necessary
```

### Step 3: Remove Duplication (10 min)

Find duplicated code and consolidate:

```
@workspace Find code that is duplicated or near-duplicated across files. 
Show me the specific locations and suggest how to consolidate them into 
shared utility functions.
```

Then for each instance:
```
Extract the duplicated logic between #file:[file1] and #file:[file2] 
into a shared function. Show me:
1. The new shared function
2. How each call site should be updated
```

### Step 4: Improve Naming and Readability (10 min)

Select a file or module with unclear naming:

```
Review the naming in #file:[target-file]:
- Are variable names descriptive?
- Do function names clearly express what they do?
- Are class/module names consistent with the rest of the project?
- Are there abbreviations or acronyms that should be spelled out?

Suggest specific renames and explain why each is better.
```

Apply the renames:
```
Apply these renames. Also update all references across the codebase.
```

### Step 5: Validate (5 min)

```
@workspace I just refactored #file:[refactored-file]. Review the changes:
1. Is the behavior preserved?
2. Did I miss any references that need updating?
3. Is the refactored code clearer and more maintainable?
```

Run tests to confirm everything still works.

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Extract method | Select code → `Ctrl+I` → `Extract this into a well-named function with proper parameters and return type` |
| Simplify conditionals | Select nested if/else → `Ctrl+I` → `Simplify this conditional logic. Consider early returns, guard clauses, or a lookup table` |
| Remove magic numbers | `Replace all magic numbers in this file with named constants. Group them logically.` |
| Consistent naming | `@workspace What naming conventions does this project use? Rename items in #file:[file] to be consistent.` |
| Reduce complexity | `This function has a cyclomatic complexity that's too high. Refactor to reduce branching.` |

## Pro Tips

- **Commit before refactoring** — Always have a clean commit so you can diff and revert
- **One refactoring at a time** — Don't rename AND restructure AND change logic simultaneously
- **Run tests after each change** — Catch breakage early while, you remember what changed
- **Use Inline Chat for surgical edits** — Select the specific code, `Ctrl+I`, describe the change
- **Let Copilot see the full file** — Open the file fully (don't just paste code into Chat) so Copilot understands the context
- **Use the `Developer` agent for test-safe refactoring** — If you've set up the [AI-Assisted Dev Kit](../../resources/AI-assisted_dev_kit/), the `Developer` agent follows a Red-Green-Refactor TDD cycle, running tests automatically after each change

## Self-Assessment Checklist

- [ ] I identified at least 3 refactoring candidates in my codebase
- [ ] I refactored at least one long/complex function into smaller pieces
- [ ] I removed or consolidated at least one instance of duplicated code
- [ ] I improved naming in at least one file
- [ ] Tests still pass after all refactoring (or I added tests first)
- [ ] The refactored code is measurably more readable

## Going Further

- Apply the [Security & Performance Review](challenge-2-security-and-perf-review.md) to the code you just refactored
- Use the [Architecture Review](../01-planning-and-design/challenge-2-architecture-review.md) findings to guide larger refactoring efforts
- Try using **Agent mode** for a multi-file refactoring: [Multi-File Feature](../06-agent-mode/challenge-1-multi-file-feature.md)
