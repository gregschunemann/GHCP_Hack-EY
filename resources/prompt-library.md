# Prompt Library

A curated collection of effective prompt patterns for GitHub Copilot, organized by task type. Use these as starting points and customize for your specific project.

---

## Table of Contents

- [General Principles](#general-principles)
- [Context Management](#context-management)
- [Explaining Code](#explaining-code)
- [Generating Code](#generating-code)
- [Writing Tests](#writing-tests)
- [Refactoring](#refactoring)
- [Code Review](#code-review)
- [Documentation](#documentation)
- [Debugging](#debugging)
- [Architecture & Design](#architecture--design)
- [Agent Mode Prompts](#agent-mode-prompts)

---

## General Principles

### The CRAFT Framework for Effective Prompts

| Letter | Principle | Example |
|--------|-----------|---------|
| **C** | **Context** — Tell Copilot about your project, stack, and constraints | "In our Express.js API using TypeScript and Prisma..." |
| **R** | **References** — Point to specific files and patterns | "Follow the pattern in #file:src/controllers/userController.ts" |
| **A** | **Ask specifically** — Request concrete outputs, not vague help | "Generate a function that validates email format and checks uniqueness" |
| **F** | **Format** — Specify the output format you want | "Return as a table / list / code block / Mermaid diagram" |
| **T** | **Test** — Include validation criteria | "The function should handle null input and throw ValidationError" |

### Golden Rules

1. **Be specific** — "Add error handling for null input" beats "improve this code"
2. **Reference your code** — `@workspace`, `#file:`, and `#selection` dramatically improve output
3. **Iterate** — Build on Copilot's response with follow-ups; don't re-prompt from scratch
4. **Correct mistakes** — When Copilot gets something wrong, say so and explain why
5. **Provide examples** — "Like this: [example]" is the most powerful prompt modifier

---

## Context Management

### How to Give Copilot Context

| Context Type | How | When |
|-------------|-----|------|
| **Entire project** | `@workspace` | Architecture questions, cross-file analysis, finding code |
| **Specific file** | `#file:path/to/file.ts` | Pattern matching, file-specific questions |
| **Selected code** | Select code, then `Ctrl+I` or `#selection` | Refactoring, explaining, or modifying specific code |
| **Terminal output** | `@terminal` | Debugging build errors, test failures |

### Combining Context

```
@workspace Looking at #file:src/models/User.ts and #file:src/models/Order.ts, 
create a new model for Product that follows the same patterns.
```

```
@workspace Based on the error in @terminal, find and fix the bug. 
The error seems related to #file:src/services/authService.ts.
```

---

## Explaining Code

```
# Basic explanation
@workspace What does the function `processPayment` in #file:src/services/paymentService.ts do?

# Deep dive
Explain this code step by step. What is the time/space complexity? 
What edge cases does it handle?

# Architecture explanation
@workspace Explain the data flow from when a user submits a form to when 
the data is saved to the database. Trace through all the files involved.

# "Explain like I'm [role]"
Explain this code to a new team member who knows JavaScript but not this project.

# Explain decisions
Why might the original developer have implemented it this way instead of [alternative]?
```

---

## Generating Code

```
# Feature with constraints
Create a function that [does X]. Requirements:
- Input: [type and description]
- Output: [type and description]
- Handle these errors: [list]
- Follow the pattern in #file:[reference]

# From comment (inline completions)
// Validate that the user has permission to access the resource
// Check both role-based and resource-based permissions
// Return a PermissionResult with grant/deny and reason

# With test-first approach
Here's the test that should pass:
[paste test]
Now implement the function that makes this test pass.

# Generate with specific library
Generate a React component for [description] using:
- React Hook Form for form handling
- Zod for validation  
- TailwindCSS for styling
- Follow the component pattern in #file:src/components/UserForm.tsx

# Convert between languages/frameworks
Convert this Python function to TypeScript, maintaining the same behavior:
[paste code]
Use idiomatic TypeScript patterns (async/await, proper types, const/let).
```

---

## Writing Tests

```
# Basic test generation
/tests using [framework] with [specific libraries, e.g., "React Testing Library"]

# Comprehensive test suite
Generate a complete test suite for #file:[source-file]:
- Test each public method
- Include happy path, error cases, and edge cases
- Use parameterized tests where appropriate
- Mock external dependencies using [mock library]
- Follow conventions from #file:[existing-test]

# Test specific scenarios
Write tests for these scenarios:
1. User submits valid form → data is saved, success message shown
2. User submits invalid email → validation error shown, form not submitted
3. Server returns 500 → error message shown, retry button appears

# Edge case tests
Write tests for boundary conditions of #file:[file]:
- Empty input, null/undefined
- Maximum length strings
- Numbers: 0, -1, MAX_INT, NaN, Infinity
- Collections: empty, one element, very large

# Test with mocks
Write tests for this function that calls [external service].
Mock the service to return: success, failure, timeout, and unexpected response.
Use [mocking library] following the pattern in #file:[test-with-mocks].

# Mutation-style testing
What test cases would catch these potential bugs in #file:[file]:
- Off-by-one errors
- Wrong comparison operators (< vs <=)
- Missing null checks
- Swapped parameters
```

---

## Refactoring

```
# Extract functions
Refactor this function into smaller, well-named functions. Each function 
should have a single responsibility. Keep the same external behavior.

# Simplify conditionals
Simplify this conditional logic. Consider:
- Early returns / guard clauses
- Lookup tables / maps
- Polymorphism
- Null coalescing / optional chaining

# Improve naming
Review the naming in this file. Suggest better names for any variables, 
functions, or classes where the name doesn't clearly communicate the purpose.
Apply all renames.

# Remove duplication
@workspace Find all instances of duplicated logic between #file:[file1] and 
#file:[file2]. Extract into a shared utility with a clear name.

# Pattern migration
Convert this code from [old pattern] to [new pattern]:
- Old: [describe or show example]
- New: [describe or show example]
Keep the same behavior. Show me the before and after.
```

---

## Code Review

```
# General review
Review #file:[file] for:
- Potential bugs or logic errors
- Security vulnerabilities
- Performance issues
- Code style and readability
- Missing error handling

For each finding, explain the issue and suggest a fix.

# Security-focused review
Review #file:[file] for security vulnerabilities:
- Injection attacks (SQL, XSS, command)
- Authentication and authorization gaps
- Sensitive data exposure
- Insecure defaults or configurations
Classify each finding as Critical / High / Medium / Low.

# Performance review
Analyze #file:[file] for performance:
- Time complexity of key operations
- Memory allocation patterns
- I/O efficiency (queries, network calls, file access)
- Caching opportunities

# PR review style
Review these changes as if you were a senior developer reviewing a PR. 
Be constructive but thorough. Categorize feedback as:
🔴 Must fix — Bugs, security issues, breaking changes
🟡 Should fix — Code quality, maintainability, conventions
🟢 Suggestion — Nice to have, alternative approaches
```

---

## Documentation

```
# Inline documentation
/doc

# Detailed documentation
Add documentation to this function including:
- Description (what and why)
- @param for each parameter with type, description, and valid ranges
- @returns description
- @throws for each possible exception
- @example with realistic usage

# Module documentation
Generate a module-level documentation comment for #file:[file]:
- What this module does
- How it fits into the project
- Key classes/functions and when to use them
- Usage example

# README generation  
@workspace Generate a README.md with: description, tech stack, setup guide, 
usage, project structure, and contributing guidelines.

# API documentation
@workspace Generate API documentation for all endpoints. Include method, path, 
description, request schema, response schema, error codes, and examples.
```

---

## Debugging

```
# Error analysis
I'm getting this error: [paste error/stack trace]
Analyze the error, identify the root cause, and suggest a fix.
The error occurs when [describe conditions].

# Logic bug
This function returns [wrong result] when given [input]. 
Expected: [correct result]. Trace through the logic and find the bug.

# Build/compile error
@terminal The build is failing. Analyze the error output and fix the issue.

# Trace execution
Trace the execution path of [function] when called with [specific input]. 
What values do each variable have at each step?

# "What changed?"
Something broke after I made changes to #file:[file]. The error is [error].
What could have caused this? Check if the change affected any callers.
```

---

## Architecture & Design

```
# Architecture analysis
@workspace Describe the architecture of this project:
- Main components and their responsibilities
- How they communicate
- External dependencies
- Key design patterns used

# Design a feature
I need to add [feature]. Analyze the existing architecture and propose 
an implementation approach that fits naturally. What new components are 
needed? What existing ones need changes?

# ADR (Architecture Decision Record)
Draft an ADR for choosing between [option A] and [option B] for [purpose].
Include context, options considered, pros/cons, and recommendation.

# Dependency analysis
@workspace Create a dependency map of the main modules. Which module has 
the most dependents? Which has the most dependencies? Are there cycles?
```

---

## Agent Mode Prompts

```
# End-to-end feature
Implement [feature] in this codebase:
Requirements: [list]
Constraints: Follow patterns in #file:[ref]. No new dependencies.
Phases: 1) Plan 2) Implement 3) Test 4) Document
Start with the plan.

# Bug investigation
Investigate this bug: [description]
Reproduce steps: [list]
Error: [paste]
1. Analyze the code path and identify root cause
2. Write a failing test that reproduces the bug
3. Fix the bug
4. Verify the test passes and no regressions

# Multi-file refactor
Rename [concept] to [new-name] across the entire codebase.
Update: file names, class names, function names, variables, imports, 
comments, tests, and documentation.
Build and test after changes to verify nothing breaks.

# Scaffolding
Create a complete [module type] for [entity] following existing patterns:
- Model: #file:[model-ref]
- Service: #file:[service-ref]
- Controller: #file:[controller-ref]
- Tests: #file:[test-ref]
Register in #file:[registration-file]. Build and run tests.
```

---

## Tips for Discovering What Works

1. **Start broad, narrow down** — If a prompt gives mediocre results, add more context and constraints
2. **Save your best prompts** — When you find a prompt that works great for your project, save it somewhere your team can reuse it
3. **Share with teammates** — The showcase at the end of the hackathon is a great time to share effective prompts
4. **Customize for your stack** — The prompts above are generic; adding your specific framework, library, and convention names makes them much more effective
