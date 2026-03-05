# Challenge: Edge Case Discovery

| | |
|---|---|
| **Track** | Testing & Quality |
| **Difficulty** | ⭐⭐ Intermediate |
| **Time** | 30-45 minutes |
| **Copilot Features** | Chat, Inline Chat, `@workspace`, `#file` |

## Objective

Use GitHub Copilot as a "what could go wrong?" partner — identifying edge cases, boundary conditions, and error scenarios that your current tests don't cover. This challenge leverages Copilot's ability to reason about code paths and suggest failure modes you might not have considered.

## Prerequisites

- Your codebase open in VS Code
- A module, function, or feature area to analyze
- Ideally: existing tests (so Copilot can identify what's *missing*, not just what to test)

## Your Mission

### Step 1: Pick a Module to Analyze (5 min)

Choose a module that handles complex logic, user input, or external data — these are where edge cases hide:

```
@workspace Which modules in this project handle the most complex business logic, 
user input processing, or external data? These are the areas most likely to have 
unhandled edge cases.
```

### Step 2: Discover Edge Cases (15 min)

Ask Copilot to think adversarially about the code:

```
@workspace Analyze #file:[target-file] for potential edge cases and failure modes:

1. **Input edge cases** — What happens with null, undefined, empty strings, 
   negative numbers, very large values, special characters, Unicode?
2. **Boundary conditions** — What happens at the limits? (max length, 0, -1, 
   Integer.MAX_VALUE, empty collections, single-element collections)
3. **State edge cases** — What if the system is in an unexpected state? 
   (uninitialized, partially initialized, mid-transaction, post-deletion)
4. **Concurrency issues** — What if this runs simultaneously? Race conditions?
5. **External dependency failures** — What if the database/API/file system is 
   unavailable, slow, or returns unexpected data?
6. **Data type edge cases** — Type coercion issues, overflow, precision loss?

For each edge case found, explain what could go wrong and how severe it would be.
```

### Step 3: Prioritize and Plan (5 min)

Not all edge cases are worth testing. Prioritize:

```
From the edge cases you identified, categorize them:

🔴 **Critical** — Could cause data loss, security issues, or crashes
🟡 **Important** — Could cause incorrect behavior visible to users
🟢 **Nice to have** — Unlikely but worth defensive coding

For the Critical and Important ones, suggest how to handle them 
(defensive code, validation, specific error handling).
```

### Step 4: Write Edge Case Tests (15 min)

Generate tests for the highest-priority edge cases:

```
Generate unit tests for the Critical and Important edge cases you identified 
in #file:[target-file].

For each test:
- Name it descriptively: test_[function]_[edge_case]_[expected_behavior]
- Include a comment explaining why this edge case matters
- Use the conventions from #file:[existing-test-file]
```

Follow up for specific scenarios:

```
Generate a test for when [specific edge case] occurs. 
The function should [expected behavior: throw, return default, log warning, etc.]
```

### Step 5: Fix or Protect (5 min)

If Copilot found edge cases that aren't handled in the code:

```
For the unhandled edge cases, add defensive code to #file:[target-file]:
- Input validation at the function entry
- Guard clauses for unexpected states
- Proper error handling for external dependency failures

Show me the changes as diffs.
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Input fuzzing ideas | `What are all the ways a user could provide unexpected input to #file:[file]? Think like a QA tester trying to break it.` |
| Security edge cases | `What are the security-relevant edge cases in #file:[file]? Think about injection, overflow, authentication bypass, unauthorized access.` |
| Race condition analysis | `@workspace Are there any potential race conditions in how [module] handles concurrent requests? What could go wrong?` |
| Error cascade analysis | `@workspace If [external dependency] fails, what happens? Trace the error path through the system.` |
| Data validation gaps | `@workspace Where in the codebase do we accept user input without proper validation? What could be submitted?` |

## Pro Tips

- **Think like an attacker** — Ask Copilot to take an adversarial perspective: "How would a malicious user exploit this function?"
- **Check existing tests first** — Reference your existing tests so Copilot can identify what's already covered: "Given these existing tests in #file:[test-file], what edge cases are missing?"
- **Don't just test — fix** — If Copilot finds an unhandled edge case, the real win is adding protective code, not just a test
- **Use concrete examples** — "What happens if the input is `''`? What about `' '`? What about `null`?" gets better results than "what are the edge cases?"
- **Cross-module edge cases** — The most dangerous edge cases often span multiple modules. Use `@workspace` for cross-cutting analysis

## Self-Assessment Checklist

- [ ] I picked a complex or risky module to analyze
- [ ] Copilot identified at least 5 edge cases I hadn't thought of
- [ ] I prioritized edge cases by severity
- [ ] I wrote tests for the Critical and Important edge cases
- [ ] I added defensive code for at least one unhandled edge case
- [ ] My understanding of the module's failure modes is significantly better than before

## Going Further

- Apply edge case analysis to your **API endpoints** — what unexpected HTTP methods, headers, or payloads could arrive?
- Use the findings to improve input validation across your project
- Create a **"chaos testing" prompt**  — ask Copilot what happens if each external dependency fails one at a time
- Feed critical findings into the [Security & Performance Review](../04-code-review-and-refactoring/challenge-2-security-and-perf-review.md) challenge
