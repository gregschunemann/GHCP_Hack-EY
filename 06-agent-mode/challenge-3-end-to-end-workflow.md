# Challenge: End-to-End Workflow

| | |
|---|---|
| **Track** | Agent Mode |
| **Difficulty** | ⭐⭐⭐ Advanced |
| **Time** | 60-90 minutes |
| **Copilot Features** | Agent Mode, `@workspace`, `#file`, terminal, all interaction modes |

## Objective

Execute a complete software development workflow in a single Agent mode session: plan → implement → test → document. This is the ultimate test of Agent mode — can it handle the full lifecycle of a change, from understanding the requirement to delivering production-ready code with tests and documentation? You'll learn how to orchestrate Agent mode for complex, multi-phase tasks.

## Prerequisites

- Agent mode enabled
- Completed at least one other Agent mode challenge
- A well-defined task (feature, bug fix, or improvement) with clear acceptance criteria
- Tests and documentation infrastructure in your project

## Your Mission

### Phase 1: Planning (10 min)

Start Agent mode with a comprehensive brief:

```
I need you to handle the complete lifecycle of this change:

**Task:** [Clear description]

**Acceptance Criteria:**
1. [Criterion 1]
2. [Criterion 2]
3. [Criterion 3]

**Context:**
- This project uses: [key tech stack details]
- Reference patterns: #file:[pattern-ref-1], #file:[pattern-ref-2]
- Test framework: [framework] with examples in #file:[test-ref]
- Documentation style: [JSDoc/docstrings/XML] with examples in #file:[doc-ref]

**I want you to complete ALL of these phases:**

**Phase 1 — Plan:** Analyze the codebase and present a detailed implementation plan.
List every file to create/modify with the purpose of each change.

**Phase 2 — Implement:** Execute the plan. Follow existing code patterns exactly.

**Phase 3 — Test:** Write comprehensive unit tests. Run them and fix any failures.

**Phase 4 — Document:** Add inline documentation and update any relevant docs 
(README, API docs, etc.).

Start with Phase 1 — present the plan and wait for my approval.
```

### Phase 2: Implementation (25 min)

Review the plan, provide feedback, then approve:

```
Plan looks good. Proceed with Phase 2 — implementation. 
Build the project after each major change to catch errors early.
```

During implementation, stay engaged:
- Review each file change for correctness and pattern consistency
- Redirect when Agent deviates from your project's conventions
- Let Agent run builds and fix compilation errors autonomously

### Phase 3: Testing (15 min)

```
Implementation looks good. Proceed with Phase 3 — testing.

Write unit tests that cover:
1. Happy path — all acceptance criteria met
2. Error cases — invalid input, missing data, unauthorized access
3. Edge cases — boundary values, empty collections, concurrent access

Use the test conventions from #file:[test-ref].
Run the tests and fix any failures.
Then run the full test suite to check for regressions.
```

Let Agent iterate on failing tests. Common scenarios:
- Test expectations are wrong → Agent fixes the test
- Test reveals a bug in the implementation → Agent fixes the code
- Test infrastructure is missing → Agent sets up the test utility

### Phase 4: Documentation (10 min)

```
Tests are passing. Proceed with Phase 4 — documentation.

1. Add inline documentation (JSDoc/docstrings/XML comments) to all new 
   public functions and classes
2. Update the README if the feature adds user-facing functionality
3. Add a brief entry to the changelog (if one exists)
4. Ensure all documentation references actual code and is accurate
```

### Phase 5: Final Review (10 min)

```
All phases complete. Now do a final review:

1. List every file you created or modified, grouped by phase
2. Summarize what was implemented and any design decisions you made
3. Confirm all tests pass
4. Flag any remaining concerns, TODOs, or areas that need human review
```

Do your own final review:
- Read through all changes as if reviewing a PR
- Verify the implementation matches the acceptance criteria
- Check that tests actually test meaningful behavior (not just "it runs")
- Ensure documentation is accurate

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Phase gate | `Phase [N] complete. Before moving to Phase [N+1], summarize what you did and confirm everything works.` |
| Course correct | `Stop — the implementation direction is wrong. [Explain issue]. Replan from this point.` |
| Add scope | `The implementation looks good. Also add [additional requirement]. Make sure existing tests still pass.` |
| Reduce scope | `Skip Phase 4 (documentation) for now. Focus on getting Phase 2 and 3 solid.` |
| Quality check | `Before proceeding, review your own work: are there any obvious bugs, missing error handling, or style inconsistencies?` |

## Pro Tips

- **Phase gates are your friend** — Stopping between phases to review gives you natural checkpoints for redirection
- **Let Agent build and test autonomously** — Agent's ability to iterate on build failures and test failures is where it really shines in E2E workflows
- **Accept that it won't be perfect** — Even a great Agent session produces code that needs human polish. The goal is 80-90% done, not 100%
- **Time-box each phase** — If implementation takes too long, simplify scope rather than skipping testing
- **Document your prompts** — The prompts you craft for E2E Agent workflows are reusable. Save the good ones
- **Compare with manual work** — Ask yourself: "How long would this have taken without Agent mode?" The answer is often eye-opening

## Self-Assessment Checklist

- [ ] I provided a comprehensive task brief with all four phases defined
- [ ] Agent created a plan and I reviewed it before implementation began
- [ ] Implementation spans multiple files and follows project conventions
- [ ] Comprehensive tests were written, run, and pass
- [ ] Documentation was added (inline docs + any relevant project docs)
- [ ] I used phase gates to review between stages
- [ ] Final result is close to PR-ready (could submit with minor polish)
- [ ] I can estimate how long this would have taken without Agent mode

## Going Further

- Try the **same workflow with a bug fix** instead of a feature — investigate, fix, test, document
- Attempt a **cross-cutting change** (add logging to all services, add caching to all read endpoints) using the same phased approach
- Create a **reusable prompt template** for your team's most common E2E workflows
- Challenge another team to implement the same feature — one with Agent mode, one without — and compare results
