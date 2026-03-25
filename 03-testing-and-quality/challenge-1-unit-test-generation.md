# Challenge: Unit Test Generation

| | |
|---|---|
| **Track** | Testing & Quality |
| **Difficulty** | ⭐ Beginner |
| **Time** | 30-45 minutes |
| **Copilot Features** | `/tests` command, Inline Chat, Chat, `#file` references |

## Objective

Use GitHub Copilot to generate unit tests for existing untested code in your project. You'll learn how to use the `/tests` slash command, guide test generation toward your project's conventions, and critically evaluate AI-generated tests for correctness.

## Prerequisites

- Your codebase open in VS Code
- Knowledge of your project's test framework (Jest, pytest, xUnit, JUnit, etc.)
- At least one function or class that lacks unit tests

## Your Mission

### Step 1: Find Untested Code (5 min)

Ask Copilot to help you find code that needs tests:

```
@workspace Which functions or classes in this project have no corresponding 
unit tests? Show me the top 5 candidates that would benefit most from tests.
```

Alternatively, pick a function you know is untested — perhaps one you or your team wrote recently.

### Step 2: Generate Tests with `/tests` (10 min)

1. Open the file with the untested function
2. Select the function body
3. Press `Ctrl+I` and type: `/tests`
4. Review the generated tests

If the test framework is wrong, be specific:

```
/tests using [Jest/pytest/xUnit/JUnit] with [any specific libraries, e.g., "React Testing Library", "Moq", "pytest-mock"]
```

### Step 3: Improve Test Quality (15 min)

The first `/tests` result is a starting point. Now refine:

**Match your project's test style:**
```
Rewrite these tests to match the style and conventions in #file:[existing-test-file]. 
Use the same setup/teardown patterns, naming conventions, and assertion style.
```

**Add more cases:**
```
These tests only cover the happy path. Add test cases for:
1. Invalid input (null, empty, wrong type)
2. Boundary values (min, max, zero, negative)
3. Error scenarios (what should throw/return error?)
```

**Test with mocks/stubs:**
```
This function has external dependencies [database, API, file system]. 
Generate tests with appropriate mocks. Follow the mocking pattern in #file:[test-with-mocks].
```

### Step 4: Run and Fix (10 min)

Run the generated tests:

```
@terminal Run the unit tests for [test file].
```

If tests fail, use Copilot to debug:

```
The test [test name] is failing with this error: [paste error]
Fix the test — the function behavior is correct, the test expectation is wrong.
```

Or, if the test found a real bug:
```
This test failure looks like a real bug in the implementation. 
Explain what the bug is and suggest a fix.
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Basic test generation | Select function → `Ctrl+I` → `/tests` |
| Framework-specific | `/tests using pytest with fixtures and parametrize` |
| Match existing style | `Generate tests for #file:src/service.ts following the patterns in #file:tests/auth.test.ts` |
| Parameterized tests | `Generate parameterized/data-driven tests for this function covering these input ranges: [list]` |
| Test a class | Select entire class → `Ctrl+I` → `/tests for all public methods, including setup and teardown` |
| Mock dependencies | `Write tests for this function, mocking [dependency]. Use [mock library] following the pattern in #file:[ref]` |

## Pro Tips

- **Start with `/tests`, then iterate** — The slash command gives you a fast baseline; follow up with specific improvements
- **Name tests descriptively** — If Copilot generates `test1`, `test2`, ask it to rename: `Rename tests using the pattern: test_[method]_[scenario]_[expected result]`
- **Verify assertions are correct** — AI-generated tests sometimes assert wrong values. Read each assertion carefully
- **Test the test** — Temporarily break the function under test and re-run; if the test still passes, the assertion is wrong
- **Use the `Tester` agent** — If you've set up the [AI-Assisted Dev Kit](../../resources/AI-assisted_dev_kit/), switch to the `Tester` agent in Agent mode for systematic test creation, Playwright automation, and structured test result documentation
- **Use existing tests as few-shot examples** — The more test files you reference, the more consistent the output

## Self-Assessment Checklist

- [ ] I selected untested code from my real project
- [ ] I generated tests using `/tests` or Inline Chat
- [ ] I customized the tests to match my project's test conventions
- [ ] I added tests beyond the happy path (error cases, edge cases, boundaries)
- [ ] I ran the tests and they pass
- [ ] I reviewed every assertion for correctness (not just "it passes")

## Going Further

- Move to the [Test Coverage Gaps](challenge-2-test-coverage-gaps.md) challenge for systematic coverage improvement
- Use the [Edge Case Discovery](challenge-3-edge-case-discovery.md) challenge to find scenarios you missed
- Try generating **integration tests** or **end-to-end tests** with Copilot
- Ask Copilot to generate a **test data factory/builder** for your project's domain objects
