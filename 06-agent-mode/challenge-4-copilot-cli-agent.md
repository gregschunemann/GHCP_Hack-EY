# Challenge: Copilot CLI — Terminal-Native Agent

| | |
|---|---|
| **Track** | Agent Mode |
| **Difficulty** | ⭐⭐ Intermediate |
| **Time** | 45-60 minutes |
| **Copilot Features** | Copilot CLI, Plan Mode, `/init`, `/diff`, `/review`, Built-in Agents |

## Objective

Use GitHub Copilot CLI as an agentic coding agent directly from your terminal. Copilot CLI provides the same plan-execute-iterate workflow as VS Code Agent Mode — but entirely in the command line. This challenge walks you through bootstrapping project instructions, planning and implementing a feature, and reviewing your changes — all without leaving the terminal.

## Prerequisites

- Copilot CLI installed (see [Getting Started — Copilot CLI Setup](../00-getting-started/SETUP.md#copilot-cli-setup-optional))
- Your codebase cloned locally
- A small feature, bug fix, or improvement you'd like to implement

> **Don't have Copilot CLI installed?** You can install it quickly:
> - **Windows:** `winget install GitHub.Copilot`
> - **npm:** `npm install -g @github/copilot`
> - **macOS/Linux:** `brew install copilot-cli`

## Your Mission

### Step 1: Bootstrap Custom Instructions with `/init` (15 min)

Good custom instructions make every Copilot interaction better — in VS Code *and* the CLI. The `/init` command analyzes your project and generates a `copilot-instructions.md` file automatically.

1. Open your terminal and navigate to your project root
2. Run `copilot` to start an interactive session
3. Confirm you trust the directory when prompted
4. Type `/init` and press Enter
5. Copilot will analyze your project structure and generate custom instructions

**Review the output:**
- Does it accurately describe your tech stack?
- Did it identify your coding conventions?
- Are the testing and build instructions correct?

**Refine if needed:**
```
The instructions look good, but we use pytest instead of unittest, 
and our naming convention is snake_case for all functions. Please update.
```

> **💡 Compare:** In VS Code, you can achieve similar results by running the `/analyze-product` prompt from the AI-Assisted Dev Kit. Try both and compare the output quality.

### Step 2: Plan and Implement a Feature with Plan Mode (20 min)

Plan mode lets you collaborate with Copilot on an implementation plan *before* any code is written. This is ideal for understanding scope and catching misalignment early.

1. Press `Shift+Tab` to cycle to **plan mode** (you'll see the mode indicator change)
2. Describe your feature or task:

```
I want to [describe your feature]. The relevant files are:
@src/[relevant-file-1]
@src/[relevant-file-2]

Requirements:
1. [Specific requirement]
2. [Another requirement]

Follow the existing patterns in this project.
```

3. Copilot will create a structured plan — **review it carefully:**
   - Are the right files being modified?
   - Does the approach match your project's patterns?
   - Is anything over-engineered?

4. Steer the plan if needed:
```
Good plan, but skip the database migration for now — 
just focus on the API endpoint and the unit tests.
```

5. Once you're satisfied, press `Shift+Tab` to switch back to **standard mode** and tell Copilot to execute the plan
6. Review and approve each file change and terminal command as Copilot works

> **💡 Compare:** How does this plan-first workflow compare to VS Code Agent Mode? Did you get more or less control over the approach?

### Step 3: Review Your Changes (10 min)

Before committing, use Copilot CLI's built-in review tools to check your work.

1. **View all changes** — type `/diff` to see a syntax-highlighted summary of every file changed in this session

2. **Get an AI code review** — type `/review` to run the code review agent:

```
/review Focus on potential bugs, security issues, and whether 
the changes follow the project's existing patterns.
```

3. **Review the feedback:**
   - Are the issues it flagged real problems?
   - Did it catch anything you missed?
   - Are there false positives?

4. If the review surfaces issues, fix them right in the same session:
```
Good catches. Please fix the null check issue in the handler 
and add the missing error handling you mentioned.
```

5. Run `/diff` again to confirm the fixes look right

> **💡 Compare:** How does `/review` compare to having a teammate review your PR? What did it catch that you might have missed?

## Stretch Goals

If you finish early, try these:

- **Switch models:** Type `/model` and try a different model for the same task — compare quality and speed
- **Explore the codebase:** Ask Copilot to use the explore agent: `Use the explore agent to find all the places where authentication is handled in this project`
- **Session management:** Run `/session` to see your session info, then `/share` to export your session as a Markdown file for your team
- **Parallel execution:** Try `/fleet` to split a task across parallel subagents: `/fleet Add unit tests for all the untested utility functions`

## Reflection

After completing this challenge, discuss with your team:
- When would you reach for Copilot CLI vs. VS Code Agent Mode?
- What tasks feel more natural in the terminal?
- How did plan mode help (or hinder) your workflow?
- Would you use `/review` as part of your regular commit workflow?
