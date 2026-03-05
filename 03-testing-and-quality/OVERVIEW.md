# Testing & Quality Challenges

Improve your test coverage and find bugs before they ship. These challenges show how Copilot accelerates test writing — from generating unit tests from existing code to discovering edge cases you haven't considered.

## When to Use These Challenges

Pick these if your team wants to:
- Add unit tests to untested or under-tested code
- Identify and fill test coverage gaps
- Discover edge cases and boundary conditions with AI assistance

## Challenges

| Challenge | Difficulty | Time | Description |
|-----------|-----------|------|-------------|
| [Unit Test Generation](challenge-1-unit-test-generation.md) | Beginner | 30-45 min | Generate tests for existing untested code |
| [Test Coverage Gaps](challenge-2-test-coverage-gaps.md) | Intermediate | 45-60 min | Identify and fill coverage gaps |
| [Edge Case Discovery](challenge-3-edge-case-discovery.md) | Intermediate | 30-45 min | Find edge cases and write tests for them |

## Key Copilot Features for This Track

- **`/tests` slash command** — Quick test generation from selected code
- **Inline Chat** (`Ctrl+I`) — Generate tests scoped to a selected function
- **`@workspace`** — Discover existing test conventions and untested code
- **`#file` references** — Point Copilot at existing test files to match style

## Tips

- **Always specify your test framework** — "Write tests using pytest" vs. just "write tests"
- **Reference existing tests** — `Follow the pattern in #file:tests/test_user.py` produces much more consistent output
- **Don't just generate — review** — AI-generated tests can have false assertions, missing edge cases, or test the wrong thing
- **Run the tests** — Always run generated tests to verify they pass (and fail when they should)
- **Test behavior, not implementation** — Guide Copilot toward testing *what* the code does, not *how* it does it
