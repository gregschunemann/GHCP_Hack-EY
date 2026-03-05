# Challenge: Test Coverage Gaps

| | |
|---|---|
| **Track** | Testing & Quality |
| **Difficulty** | ⭐⭐ Intermediate |
| **Time** | 45-60 minutes |
| **Copilot Features** | Chat, `@workspace`, `#file`, `/tests` |

## Objective

Systematically identify areas of your codebase with low or missing test coverage, then use Copilot to generate tests that fill those gaps. This goes beyond testing one function — you'll analyze your project's test health and prioritize where new tests will have the most impact.

## Prerequisites

- Your codebase open in VS Code
- Existing tests (even a few) so Copilot can follow your conventions
- Optionally: a coverage report (from tools like Istanbul/nyc, coverage.py, dotnet-coverage)

## Your Mission

### Step 1: Assess Current Coverage (10 min)

**If you have a coverage tool:**

Run your coverage report and share the results with Copilot:

```
Here's our test coverage summary: [paste coverage output or key numbers]

Identify the modules/files with the lowest coverage that are most critical 
to test. Prioritize by risk — which untested code is most likely to cause bugs?
```

**If you don't have a coverage tool:**

Let Copilot analyze the test-to-code ratio:

```
@workspace Analyze the test coverage of this project:
1. Which source files have corresponding test files? Which don't?
2. For files that have tests, are the main functions/methods covered?
3. What are the highest-risk untested areas (business logic, data access, API handlers)?
4. Prioritize: which 3-5 files would benefit most from new tests?
```

### Step 2: Analyze a Gap in Detail (10 min)

Pick the highest-priority untested file and do a deep analysis:

```
@workspace Analyze #file:[untested-file] in detail:
1. What does this file do?
2. What are all the public functions/methods?
3. What are the different code paths (branches, conditions)?
4. What dependencies would need to be mocked for testing?
5. Generate a test plan listing every test case needed for full coverage.
```

### Step 3: Generate Tests Systematically (20 min)

Use the test plan as your guide. Generate tests in batches:

```
Based on the test plan above, generate tests for #file:[untested-file].

Use the test framework and conventions from #file:[existing-test-file].
Start with the happy path tests for all public methods.
```

Then add the negative and edge case tests:

```
Now add the following test categories:
1. Error/exception handling paths
2. Null/empty/undefined input handling
3. Boundary conditions
4. Concurrent/async scenarios (if applicable)
```

### Step 4: Verify Coverage Improvement (10 min)

Run your tests and (if available) check the coverage report:

```
@terminal Run the test suite and check coverage for [file/module].
```

If tests fail:
```
These tests are failing: [paste failures]
Analyze whether the failures indicate bugs in the test or bugs in the code.
Fix the tests that have incorrect expectations.
```

### Step 5: Repeat for Next Priority (10 min)

Move to the next file on your priority list. Each iteration should be faster as Copilot has learned your test patterns.

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Coverage analysis | `@workspace Which source files have no corresponding test files?` |
| Test plan generation | `Create a comprehensive test plan for #file:[source-file]. List every test case with input/expected output.` |
| Batch generation | `Generate all unit tests for #file:[source-file]. Organize by method. Use conventions from #file:[test-ref].` |
| Missing branch coverage | `#file:[source-file] has these conditional branches: [list]. Generate tests that exercise every branch.` |
| Integration test gaps | `@workspace Our unit tests cover individual functions, but where are we missing integration tests between modules?` |

## Pro Tips

- **Prioritize by risk, not by line count** — 80% coverage on critical payment code matters more than 100% coverage on utility functions
- **Use coverage tools when available** — Copilot can analyze pasted coverage reports to give targeted recommendations
- **Generate tests file-by-file** — Trying to generate tests for the entire project at once produces lower quality output
- **Look for untested error paths** — Most coverage gaps are in error handling. Ask specifically: "What error conditions in this file have no tests?"
- **Commit as you go** — Commit each batch of new tests separately so you can easily revert if needed

## Self-Assessment Checklist

- [ ] I identified the highest-priority untested areas of my codebase
- [ ] I generated a test plan before writing tests (not just ad-hoc generation)
- [ ] I created new test files or added tests to existing ones
- [ ] Tests follow my project's existing conventions and patterns
- [ ] I ran the tests and verified they pass
- [ ] I can quantify the coverage improvement (files covered, test count, or coverage %)

## Going Further

- Set up a coverage gate in your CI pipeline: `@workspace Help me add a test coverage check to our CI configuration`
- Use the [Edge Case Discovery](challenge-3-edge-case-discovery.md) challenge to go deeper on a specific module
- Generate **mutation tests** — ask Copilot to create test scenarios that would catch specific types of bugs
