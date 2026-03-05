# Getting Started — Setup & Warm-up

Complete this guide before diving into the hackathon challenges. Budget **30 minutes** for setup and warm-up.

---

## Prerequisites Checklist

- [ ] **VS Code** installed ([download](https://code.visualstudio.com/))
- [ ] **GitHub account** with Copilot Enterprise license active
- [ ] **GitHub Copilot extension** installed in VS Code ([install](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot))
- [ ] **GitHub Copilot Chat extension** installed in VS Code ([install](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat))
- [ ] **Your codebase** cloned locally and opened in VS Code
- [ ] **Signed in** to GitHub in VS Code (check the Accounts icon in the bottom-left sidebar)

---

## Verify Copilot Is Working

### Step 1: Check the Copilot Status Icon

Look at the bottom-right of the VS Code status bar. You should see the **Copilot icon** (a sparkle/two-wing icon). If it's there, Copilot is active.

- ✅ **Icon is present and not crossed out** — You're good to go
- ❌ **Icon is missing** — Install the Copilot extension and sign in
- ❌ **Icon has a line through it** — Copilot is disabled for this language/file; click the icon to enable
- ❌ **Icon shows an error** — Check [Troubleshooting](../resources/troubleshooting.md)

### Step 2: Test Inline Completions

1. Open any source file in your project
2. Place your cursor at the end of an existing function or on a new line
3. Type a comment describing a small utility function, e.g.:
   ```
   // function that reverses a string
   ```
4. Press `Enter` and wait 1-2 seconds — Copilot should suggest a completion in gray text
5. Press `Tab` to accept, or `Esc` to dismiss

### Step 3: Test Copilot Chat

1. Open Copilot Chat: press `Ctrl+Alt+I` (or click the Chat icon in the sidebar)
2. Type: `@workspace What is this project about?`
3. You should receive a response that describes your project based on its files

If all three checks pass, you're ready to go! 🎉

---

## Recommended VS Code Settings

These settings optimize your Copilot experience for the hackathon. Open VS Code settings (`Ctrl+,`) and search for each setting, or add them to your `settings.json`:

```json
{
  // Show Copilot completions inline as you type
  "editor.inlineSuggest.enabled": true,

  // Enable Copilot for all file types
  "github.copilot.enable": {
    "*": true
  },

  // Show the Copilot status in the editor
  "github.copilot.editor.enableAutoCompletions": true
}
```

---

## Copilot Interaction Modes

Before starting challenges, understand the four ways to interact with Copilot:

### 1. Inline Completions (Ghost Text)
- **What:** Copilot suggests code as you type, shown in gray text
- **How:** Just type — completions appear automatically
- **Accept:** `Tab` | **Dismiss:** `Esc` | **Next suggestion:** `Alt+]` | **Previous:** `Alt+[`
- **Best for:** Writing new code, completing patterns, filling in boilerplate

### 2. Copilot Chat (Side Panel)
- **What:** Conversational AI assistant with full codebase awareness
- **How:** Press `Ctrl+Alt+I` or click the Chat icon in the sidebar
- **Best for:** Asking questions, explaining code, brainstorming, complex generation tasks
- **Key feature:** Use `@workspace` to give Copilot context about your entire project

### 3. Inline Chat (Editor Overlay)
- **What:** Quick Chat overlay right in the editor, scoped to your current selection/file
- **How:** Select code (optional) then press `Ctrl+I`
- **Best for:** Quick edits, refactoring selected code, asking about specific code blocks

### 4. Agent Mode (Agentic Coding)
- **What:** Copilot plans and executes multi-step tasks autonomously — creating files, editing code, running terminal commands
- **How:** Press `Ctrl+Shift+I` to open the Chat panel in Agent mode, or type in Chat and switch to Agent mode using the mode picker
- **Best for:** Implementing features across multiple files, complex refactoring, bug investigation
- **Note:** Review each step the agent takes — you can accept, reject, or redirect

---

## Warm-up Exercises

Complete these three quick exercises to get comfortable with Copilot before starting the challenges. **Time: ~15 minutes total.**

### Warm-up 1: Explain Code (5 min)

1. Open a file in your project that contains a function you (or a teammate) find complex
2. Select the function
3. Press `Ctrl+I` (Inline Chat) and type: `Explain this code`
4. Read the explanation — is it accurate? Does it capture the intent?
5. Now try in the Chat panel (`Ctrl+Alt+I`): `@workspace What does the [function name] function do and where is it called from?`

**What you're learning:** How Copilot explains existing code, and how `@workspace` adds cross-file context.

### Warm-up 2: Generate a Test (5 min)

1. Open a file with a function that has no tests (or limited tests)
2. Select the function
3. Press `Ctrl+I` and type: `/tests`
4. Review the generated test — does it cover the key behaviors?
5. If the test framework isn't right, try: `/tests using [your test framework, e.g., Jest, pytest, xUnit]`

**What you're learning:** How to use slash commands and how to guide Copilot toward your project's conventions.

### Warm-up 3: Ask About Your Project (5 min)

1. Open Copilot Chat (`Ctrl+Alt+I`)
2. Try these prompts:
   - `@workspace What is the overall architecture of this project?`
   - `@workspace What are the main entry points?`
   - `@workspace Where is error handling implemented?`
3. Evaluate the responses — how well does Copilot understand your project's structure?

**What you're learning:** How `@workspace` enables Copilot to reason about your entire codebase, not just the open file.

---

## You're Ready!

Head back to the [main README](../README.md) and pick your first challenge track. Remember:

- **Pick challenges relevant to your codebase and goals**
- **Work as a team** — discuss prompts, compare results, learn together
- **Document your best prompts** — you'll share them in the showcase
- **Have fun** — experiment, be curious, and don't be afraid to try weird prompts

➡️ **[Browse Challenge Tracks](../README.md#2-pick-your-challenges)**
