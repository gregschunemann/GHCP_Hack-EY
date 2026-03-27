# GitHub Copilot CLI Demo Script

**Duration:** ~10 minutes  
**Audience:** Hackathon participants  
**Goal:** Showcase key features of GitHub Copilot CLI as a terminal-native agentic coding assistant

---

## Pre-Demo Setup

Before the demo, ensure:
- [ ] Copilot CLI is installed (`copilot --version`)
- [ ] A sample project is ready (ideally a small web app or API with a few files)
- [ ] Terminal font size is large enough for the audience to read
- [ ] You've practiced the demo flow at least once

---

## Demo Script

### [0:00 - 1:00] Introduction & Launch

**Say:**
> "GitHub Copilot isn't just in VS Code — you can use it directly from your terminal as a full agentic coding assistant. Let me show you Copilot CLI."

**Do:**
```bash
# Navigate to your project
cd my-sample-project

# Launch Copilot CLI
copilot
```

**Point out:**
- The interactive prompt that appears
- The trust dialog (agree to trust the directory)
- The mode indicator in the prompt (shows current mode)

---

### [1:00 - 2:30] Initialize Custom Instructions with `/init`

**Say:**
> "The first thing I do with any new project is run `/init`. This analyzes your codebase and generates custom instructions that make every future Copilot interaction smarter."

**Do:**
```
/init
```

**Point out:**
- Watch as Copilot scans the project structure
- It identifies the tech stack (language, framework, testing tools)
- It creates a `copilot-instructions.md` file with conventions

**Say:**
> "This is the same instructions file that VS Code's Agent Mode uses. Generate it once, benefit everywhere."

**Quick refinement (if time):**
```
Update the instructions to note that we use async/await instead of callbacks
```

---

### [2:30 - 4:30] Plan Mode — Think Before You Code

**Say:**
> "One of my favorite features is Plan Mode. Instead of jumping straight into code, Copilot builds a structured implementation plan first. This catches misunderstandings early."

**Do:**
Press `Shift+Tab` to cycle to **Plan Mode** (watch the mode indicator change)

**Say:**
> "Notice the mode indicator changed. Now when I describe a task, Copilot will create a plan instead of immediately writing code."

**Type a task prompt:**
```
Add a health check endpoint to the API that returns the current server status, 
uptime, and database connection state. Include a unit test.
```

**Point out:**
- The structured plan that appears
- Files it plans to create/modify
- The step-by-step approach

**Steer the plan (demonstrate collaboration):**
```
Good plan, but let's skip the database check for now and keep it simple. 
Just return server status and uptime.
```

**Say:**
> "This back-and-forth on the plan saves time. We align on the approach before any code is written."

---

### [4:30 - 6:30] Execute the Plan in Standard Mode

**Say:**
> "Now let's execute. I'll switch back to Standard Mode where Copilot implements with my approval."

**Do:**
Press `Shift+Tab` to cycle to **Standard Mode**

**Type:**
```
Execute the plan we just created
```

**Point out:**
- Copilot proposes file changes one at a time
- You see a preview before accepting
- Terminal commands (like running tests) also require approval
- This is agent mode in the terminal — same power, different interface

**Accept a few changes, then:**

**Say:**
> "I can accept, reject, or modify each change. Full control, but Copilot does the heavy lifting."

---

### [6:30 - 8:00] Review Your Work with `/diff` and `/review`

**Say:**
> "Before I commit, I want to review everything. Copilot CLI has built-in tools for this."

**Do:**
```
/diff
```

**Point out:**
- Syntax-highlighted summary of all changes
- Easy to scan what was modified

**Then:**
```
/review Focus on potential bugs and whether this follows REST conventions
```

**Point out:**
- The code review agent analyzes the changes
- It flags potential issues, security concerns, style violations
- It's like having a teammate review your PR before you even push

**Say:**
> "If the review catches something, I can fix it right here in the same session — no context switching."

---

### [8:00 - 9:30] Power Features: Agents, Models & More

**Say:**
> "Let me show you a few more powerful features."

**Built-in Agents:**
```
/agent
```

**Point out:**
- `code-review` — dedicated code reviewer (Claude Sonnet)
- `explore` — fast codebase exploration (Claude Haiku)

**Model Selection:**
```
/model
```

**Point out:**
- You can switch between models (Claude, GPT-4, etc.)
- Different models for different tasks

**Session Management:**
```
/session
```

**Point out:**
- See your session history, files touched, and plan state
- `/share` exports to Markdown or GitHub Gist for sharing with teammates

**Parallel Execution (mention):**
> "If you have a large task, `/fleet` can split it across parallel subagents. For example: `/fleet Add unit tests for all untested utility functions` — and Copilot farms it out to multiple workers."

---

### [9:30 - 10:00] Wrap-Up

**Say:**
> "To summarize — Copilot CLI gives you:
> 
> 1. **`/init`** — Smart custom instructions for your project
> 2. **Plan Mode** — Collaborate on the approach before coding
> 3. **Standard Mode** — Approve each change as Copilot executes
> 4. **`/diff` and `/review`** — Built-in code review before you commit
> 5. **Built-in agents** — Specialized tools for exploration and review
> 
> Same AI power as VS Code Agent Mode, but entirely in your terminal. Perfect for SSH sessions, CI pipelines, or if you just prefer the command line.
> 
> The hackathon includes a Copilot CLI challenge — I encourage you to try it with your own codebase."

---

## Command Reference (for Q&A)

| Command | What It Does |
|---------|-------------|
| `/init` | Initialize custom instructions for this repo |
| `/diff` | Review all changes made in the current session |
| `/review [PROMPT]` | Run the code review agent |
| `/plan [PROMPT]` | Create an implementation plan |
| `/compact` | Compress conversation to free up context |
| `/context` | Show token usage |
| `/model` | Switch AI models |
| `/agent` | Browse available agents |
| `/session` | Show session info |
| `/share` | Export session to Markdown or Gist |
| `/fleet [PROMPT]` | Run task in parallel subagents |
| `/delegate [PROMPT]` | Delegate to remote repo via AI-generated PR |
| `/resume` | Resume a previous session |

---

## Common Questions

**Q: How do I install Copilot CLI?**
- Windows: `winget install GitHub.Copilot`
- npm: `npm install -g @github/copilot`
- macOS/Linux: `brew install copilot-cli`

**Q: What's the difference between Copilot CLI and VS Code Agent Mode?**
- Same underlying capabilities — both are agentic coding assistants
- CLI is terminal-native, VS Code Agent Mode is editor-native
- CLI is great for SSH sessions, servers, or terminal-first workflows
- VS Code has deeper editor integration (diagnostics, language servers)

**Q: Do changes sync between CLI and VS Code?**
- Custom instructions (copilot-instructions.md) are shared — edit once, use everywhere
- Session state doesn't sync — they're separate sessions

**Q: Can I use this in CI/CD?**
- Copilot CLI is designed for interactive use with human approval
- For CI/CD automation, consider GitHub Actions with Copilot integration

---

## Demo Tips

1. **Practice the timing** — 10 minutes goes fast
2. **Use a simple, relatable project** — a REST API or small web app works well
3. **Have fallback screenshots** — in case of network issues
4. **Pre-stage the project** — have it cloned and ready, no `npm install` delays
5. **Embrace mistakes** — if something unexpected happens, use `/review` or `/diff` to debug live. It's a great teaching moment!
