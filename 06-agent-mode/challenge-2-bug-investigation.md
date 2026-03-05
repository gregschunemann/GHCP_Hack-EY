# Challenge: Bug Investigation

| | |
|---|---|
| **Track** | Agent Mode |
| **Difficulty** | ⭐⭐ Intermediate |
| **Time** | 45-60 minutes |
| **Copilot Features** | Agent Mode, `@workspace`, `@terminal`, `#file` |

## Objective

Use Copilot Agent mode to investigate and fix a bug in your codebase. Agent mode excels at bug investigation because it can search across files, trace code paths, form hypotheses, write reproduction tests, and implement fixes — all in one workflow. You'll learn how to give Agent the right context to track down root causes efficiently.

## Prerequisites

- Agent mode enabled
- A known bug in your codebase (active bug report, failing test, or misbehaving feature)
- Ability to reproduce the bug (or a clear error message/stack trace)

> **Don't have a bug?** Try one of these:
> - Look at recent bug reports or GitHub Issues
> - Check for TODO/FIXME/HACK comments in your code — these often indicate known issues
> - Ask teammates if there's a bug they've been meaning to fix
> - Introduce a bug intentionally and see if Agent can find it (fun exercise!)

## Your Mission

### Step 1: Describe the Bug (5 min)

Give Agent mode a thorough bug report:

```
I need you to investigate and fix a bug:

**Bug Description:** [What's happening vs. what should happen]

**How to Reproduce:** 
1. [Step 1]
2. [Step 2]
3. [Expected result vs. actual result]

**Error Message / Stack Trace:**
[Paste any error output]

**Where I Think the Problem Is:**
[Your best guess — even if uncertain, this helps narrow the search]

**Relevant Files:**
- #file:[file-you-suspect]
- #file:[related-file]

Start by analyzing the code paths involved and form a hypothesis about the root cause before making any changes.
```

### Step 2: Review the Investigation (10-15 min)

Agent will analyze the codebase and propose a root cause. Evaluate:

- Does the hypothesis make sense? Does it explain all the symptoms?
- Did Agent trace the correct code path?
- Is Agent looking at the right files, or did it go down a wrong path?

If it's on the wrong track:
```
I don't think that's the root cause because [reason]. 
The bug only happens when [condition], which suggests the issue is in 
the [area] logic, not the [area] Agent is looking at.

Also check #file:[other-relevant-file] — the data transformation there 
might be the source.
```

### Step 3: Write a Reproduction Test (10 min)

Before fixing, ask Agent to write a test that fails:

```
Before implementing a fix, write a test that reproduces this bug.
The test should:
1. Set up the conditions that trigger the bug
2. Currently FAIL (proving the bug exists)
3. Be designed to PASS once the bug is fixed

Put the test in #file:[appropriate-test-file] following existing test conventions.
```

Having a failing test confirms Agent found the right issue and proves the fix works.

### Step 4: Implement and Validate the Fix (15 min)

```
Now implement the fix. Requirements:
- Fix the root cause, not just the symptoms
- Don't change any behavior beyond fixing the bug
- Make the minimal change needed
- Run the reproduction test to verify it passes
- Run the full test suite to check for regressions
```

Review the fix:
- Is it the minimal change needed?
- Does it handle all the edge cases that could trigger the same bug?
- Could the fix introduce new issues?

### Step 5: Add Defensive Measures (5 min)

```
Now that the bug is fixed:
1. Are there similar patterns elsewhere in the codebase that could have the same bug?
2. Should we add input validation or assertions to prevent this class of bug?
3. Should the error message be improved if this situation occurs again?
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Stack trace analysis | `Analyze this stack trace and identify the root cause: [paste trace]. Check each file in the trace.` |
| Regression hunt | `This feature was working in [describe old behavior] but now [describe current behavior]. Find what changed.` |
| Intermittent bug | `This bug only happens sometimes. It might be a race condition or timing issue. Check for async/concurrency problems in [area].` |
| Data flow tracing | `Trace the data flow from [input point] to [output point]. Where does the data get corrupted or lost?` |
| Fix with safety | `Fix this bug with the minimal change. Add a comment explaining why this fix is needed to prevent regression.` |

## Pro Tips

- **Give Agent all the context you have** — Error messages, stack traces, reproduction steps, and your intuition about the cause. More context = faster investigation
- **Ask for a test first** — Writing a reproduction test before fixing ensures Agent (and you) understand the real problem
- **Watch for band-aid fixes** — Agent might suggest masking the symptom (e.g., adding a null check) instead of fixing the root cause. Push for deeper fixes
- **Let Agent use the terminal** — Agent can run tests, check logs, and execute the code to gather more information
- **Search for similar bugs** — After fixing, ask Agent to look for the same pattern elsewhere: "Are there other places in the codebase with the same problem?"

## Self-Assessment Checklist

- [ ] I provided Agent with a clear bug description, reproduction steps, and context
- [ ] Agent identified the root cause (or I redirected it to the right area)
- [ ] A reproduction test was written that fails before the fix
- [ ] The fix addresses the root cause, not just the symptom
- [ ] The reproduction test passes after the fix
- [ ] The full test suite passes (no regressions)
- [ ] I checked for similar bugs elsewhere in the codebase

## Going Further

- Try investigating a **hard-to-reproduce bug** (intermittent, timing-dependent, or environment-specific)
- Ask Agent to generate a **post-mortem** document explaining the bug, root cause, fix, and prevention
- Use the findings to improve the [Security & Performance Review](../04-code-review-and-refactoring/challenge-2-security-and-perf-review.md)
- Try the [End-to-End Workflow](challenge-3-end-to-end-workflow.md) combining bug fix + tests + documentation
