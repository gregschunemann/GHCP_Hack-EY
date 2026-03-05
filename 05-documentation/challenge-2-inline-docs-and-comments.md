# Challenge: Inline Docs & Comments

| | |
|---|---|
| **Track** | Documentation |
| **Difficulty** | ⭐ Beginner |
| **Time** | 30-45 minutes |
| **Copilot Features** | `/doc` command, Inline Chat, inline completions, `#file` |

## Objective

Add inline documentation (JSDoc, Python docstrings, C# XML comments, JavaDoc, etc.) to undocumented functions, classes, and modules in your codebase. You'll learn to use the `/doc` slash command for rapid documentation generation and how to guide Copilot toward your project's documentation style.

## Prerequisites

- Your codebase open in VS Code
- Functions, classes, or modules that lack documentation comments

## Your Mission

### Step 1: Find Undocumented Code (5 min)

```
@workspace Which public functions, classes, or methods in this project are 
missing documentation comments (JSDoc, docstrings, XML comments, etc.)?
List the top 10, prioritized by how often they're used or how complex they are.
```

### Step 2: Document with `/doc` (10 min)

The `/doc` command is the fastest way to add inline documentation:

1. Place your cursor on a function or class definition
2. Press `Ctrl+I` (Inline Chat)
3. Type: `/doc`
4. Review and accept the generated documentation

Try it on 3-5 functions. Notice:
- Does Copilot correctly describe the function's purpose?
- Are parameter descriptions accurate?
- Are return values documented?
- Are edge cases or exceptions mentioned?

### Step 3: Improve Quality with Specific Guidance (15 min)

`/doc` gives you a quick baseline. Now improve it:

**Match your project's style:**
```
Generate documentation for this function matching the style used in 
#file:[well-documented-file]. Include the same sections and formatting.
```

**Add specific sections:**
```
Add documentation to this function including:
- Description of what it does and why
- @param for each parameter with type and valid ranges
- @returns with type and description
- @throws / @raises for all possible exceptions
- @example with a realistic usage example
```

**Document complex logic:**
```
Add inline comments explaining the key steps in this algorithm.
Focus on the "why", not the "what" — explain design decisions and non-obvious behavior.
```

### Step 4: Batch Document a File (10 min)

For files with many undocumented functions, use Chat for bulk generation:

```
Generate documentation comments for ALL public functions and classes in 
#file:[target-file]. Use [JSDoc/docstring/XML comments] format.

For each function/class:
- Purpose description
- Parameter documentation with types
- Return value documentation
- Exception documentation
- One usage example for complex functions

Match the style used in #file:[well-documented-reference].
```

### Step 5: Review and Polish (5 min)

```
@workspace Review the documentation I just added to #file:[target-file]:
1. Is any documentation inaccurate or misleading?
2. Are there functions I missed?
3. Is the documentation style consistent across all functions?
4. Is anything over-documented (obvious things that don't need comments)?
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Quick doc | Place cursor on function → `Ctrl+I` → `/doc` |
| Styled doc | `/doc following the conventions in #file:[reference]` |
| With examples | `Add JSDoc with a @example section showing typical usage` |
| Module-level docs | `Generate a module-level documentation comment for #file:[file] explaining what this module does and how it fits into the project` |
| Type documentation | `Document this type/interface/struct — explain each field, valid values, and when to use this type vs. alternatives` |
| Inline logic comments | Select complex code → `Ctrl+I` → `Add comments explaining the key steps and why this approach was chosen` |

## Pro Tips

- **`/doc` for speed, follow-up for quality** — Use `/doc` to get the structure, then refine with specific prompts
- **Document the "why", not the "what"** — `// increment counter` is useless; `// Track retry attempts so we can back off exponentially` is valuable
- **Don't over-document** — Simple getter functions don't need 5-line doc comments. Reserve detail for complex or non-obvious code
- **Use existing docs as examples** — `#file` references to well-documented files are the single most effective way to get consistent output
- **Let completions help** — After documenting one function, Copilot's inline completions will auto-suggest similar docs for the next function

## Self-Assessment Checklist

- [ ] I identified undocumented code in my project
- [ ] I used `/doc` to quickly document at least 5 functions
- [ ] I improved the generated docs with follow-up prompts
- [ ] I batch-documented an entire file
- [ ] Documentation style is consistent with the rest of the project
- [ ] I focused on "why" comments for complex logic, not just "what" comments

## Going Further

- Set up a **linting rule** to require documentation comments on public APIs (ESLint/JSDoc, Python docstring linting, etc.)
- Generate **API reference documentation** from your inline docs (TypeDoc, Sphinx, Sandcastle)
- Move to the [Onboarding Guide](challenge-3-onboarding-guide.md) challenge for higher-level documentation
- Use Copilot to **translate documentation** to another language if your team is multilingual
