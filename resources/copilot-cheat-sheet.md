# GitHub Copilot Cheat Sheet — VS Code

Quick reference for all GitHub Copilot interactions in VS Code.

---

## Keyboard Shortcuts

### Inline Completions (Ghost Text)

| Action | Shortcut |
|--------|----------|
| Accept suggestion | `Tab` |
| Dismiss suggestion | `Esc` |
| Next suggestion | `Alt+]` |
| Previous suggestion | `Alt+[` |
| Accept next word | `Ctrl+→` |
| Trigger suggestion | `Alt+\` |

### Copilot Chat

| Action | Shortcut |
|--------|----------|
| Open Chat panel | `Ctrl+Alt+I` |
| Open Inline Chat | `Ctrl+I` |
| Open Agent Mode | `Ctrl+Shift+I` |

---

## Chat Participants

Type these at the start of a Chat message to route to specialized handlers:

| Participant | What It Does | Example |
|------------|-------------|---------|
| `@workspace` | Answers questions using your entire project as context | `@workspace What API endpoints does this project expose?` |
| `@terminal` | References terminal output and runs commands | `@terminal Explain the last error` |
| `@vscode` | VS Code editor questions and settings | `@vscode How do I enable word wrap?` |

---

## Slash Commands

Type these in Chat or Inline Chat for specialized actions:

| Command | What It Does | Where |
|---------|-------------|-------|
| `/tests` | Generate unit tests for selected code | Inline Chat / Chat |
| `/fix` | Fix a problem in selected code or based on errors | Inline Chat / Chat |
| `/explain` | Explain how selected code works | Inline Chat / Chat |
| `/doc` | Generate documentation comment for selected code | Inline Chat |
| `/new` | Scaffold a new project or file | Chat |
| `/clear` | Clear the chat session | Chat |

---

## Context References

Reference specific context in Chat messages:

| Reference | What It Does | Example |
|-----------|-------------|---------|
| `#file:path` | Include a file's content as context | `#file:src/utils/auth.ts` |
| `#selection` | Include the currently selected text | `Explain #selection` |
| `#codebase` | Search the codebase for relevant context | `#codebase How is auth handled?` |
| `#terminalLastCommand` | Include the last terminal command and output | `Fix the error from #terminalLastCommand` |

---

## Chat Modes

Switch between modes using the dropdown at the top of the Chat panel:

| Mode | What It Does | Best For |
|------|-------------|----------|
| **Ask** | Answers questions; doesn't modify files | Learning, exploring, understanding code |
| **Edit** | Proposes edits to specific files you indicate | Targeted changes, refactoring |
| **Agent** | Plans and executes multi-step tasks autonomously | Features, bug fixes, complex workflows |

---

## Inline Chat Quick Patterns

Select code (optional), press `Ctrl+I`, then type:

| Type This | What Happens |
|-----------|-------------|
| `/doc` | Adds documentation comment above the function |
| `/tests` | Generates unit tests for the selected code |
| `/fix` | Fixes issues in the selected code |
| `/explain` | Explains what the selected code does |
| `Refactor this to...` | Refactors with your specific instructions |
| `Add error handling` | Wraps code in try/catch with proper error handling |
| `Make this async` | Converts synchronous code to async/await |
| `Add TypeScript types` | Adds type annotations to untyped code |

---

## Enterprise Features

These features are available with GitHub Copilot Enterprise:

| Feature | Description |
|---------|-------------|
| **Bing Web Search** | Copilot can search the web for current information (enabled by default in Chat) |
| **Knowledge Bases** | Organization-curated documentation collections that Copilot can reference |
| **PR Summaries** | Auto-generated pull request descriptions on GitHub.com |
| **Docset Search** | Search internal documentation repositories |

---

## Common Workflows

### "I want to understand this code"
1. Select the code
2. `Ctrl+I` → `/explain`
3. For deeper analysis: `Ctrl+Alt+I` → `@workspace Explain how [function] works and where it's called from`

### "I want to write new code"
1. Write a descriptive comment
2. Let inline completions generate the implementation
3. `Tab` to accept, `Alt+]` for alternatives
4. For complex logic: `Ctrl+I` → describe what you need

### "I want to fix a bug"
1. Look at the error in terminal
2. `Ctrl+Alt+I` → `@terminal Explain this error and suggest a fix`
3. Or: `Ctrl+I` on the buggy code → `/fix`

### "I want to write tests"
1. Open the file to test
2. Select a function
3. `Ctrl+I` → `/tests`
4. For more: `Ctrl+Alt+I` → `Generate comprehensive tests for #file:[file] using [framework]`

### "I want to refactor"
1. Select the code to refactor
2. `Ctrl+I` → describe the refactoring
3. Review the diff and accept/reject
4. For multi-file: use Agent mode (`Ctrl+Shift+I`)

### "I want to add documentation"
1. Place cursor on a function
2. `Ctrl+I` → `/doc`
3. For batch: `Ctrl+Alt+I` → `Add docs to all public functions in #file:[file]`

---

## Pro Tips

| Tip | Details |
|-----|---------|
| **Open reference files** | Copilot uses open tabs as context — keep similar/related files open |
| **Partial accept** | `Ctrl+→` accepts one word at a time from inline suggestions |
| **Iterate, don't restart** | Build on Copilot's response with follow-ups instead of re-prompting |
| **Correct mistakes** | When Copilot is wrong, explain why — it improves subsequent responses |
| **Use `@workspace` liberally** | It's the single most impactful feature for project-aware suggestions |
