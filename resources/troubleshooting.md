# Troubleshooting

Common issues with GitHub Copilot in VS Code and how to fix them.

---

## Copilot Not Activating

### Symptoms
- No Copilot icon in the status bar
- No inline suggestions when typing
- Chat panel shows "Copilot is not available"

### Solutions

1. **Check the extension is installed**
   - Open Extensions (`Ctrl+Shift+X`)
   - Search for "GitHub Copilot" — both the main extension and "GitHub Copilot Chat" should be installed and enabled

2. **Sign in to GitHub**
   - Click the Accounts icon (bottom-left sidebar)
   - Sign in with your GitHub account that has Copilot access
   - If already signed in, sign out and sign back in

3. **Verify your Copilot license**
   - Go to [github.com/settings/copilot](https://github.com/settings/copilot)
   - Confirm your subscription is active
   - For Enterprise: confirm your organization has assigned you a seat

4. **Check extension version**
   - Update both extensions to the latest version
   - Reload VS Code after updating (`Ctrl+Shift+P` → "Developer: Reload Window")

---

## No Inline Suggestions

### Symptoms
- Copilot icon is present but suggestions don't appear when typing
- Ghost text never shows up

### Solutions

1. **Check if suggestions are enabled**
   - Click the Copilot icon in the status bar
   - Make sure "Enable Completions" is checked
   - Check that completions are enabled for your file's language

2. **Check settings**
   - Open Settings (`Ctrl+,`)
   - Search for `editor.inlineSuggest.enabled` — should be `true`
   - Search for `github.copilot.enable` — should have `"*": true`

3. **Check file type**
   - Some file types may be excluded. Check `github.copilot.enable` in settings for language-specific overrides

4. **Trigger manually**
   - Press `Alt+\` to manually trigger a suggestion
   - If this works, the issue is with auto-triggering, not Copilot itself

5. **Wait for it**
   - On large files, suggestions may take a few seconds
   - Network latency can cause delays — check your internet connection

---

## Chat Not Responding

### Symptoms
- Chat panel opens but messages get no response
- "Thinking..." spinner runs indefinitely
- Error messages in Chat

### Solutions

1. **Reload VS Code**
   - `Ctrl+Shift+P` → "Developer: Reload Window"

2. **Clear Chat session**
   - Type `/clear` in the Chat panel to start fresh

3. **Check network**
   - Copilot Chat requires internet access
   - Verify you can reach `api.github.com` — no VPN/proxy issues

4. **Check for rate limiting**
   - Heavy usage may temporarily result in slower responses
   - Wait a minute and try again

5. **Check output logs**
   - Open Output panel (`Ctrl+Shift+U`)
   - Select "GitHub Copilot Chat" from the dropdown
   - Look for error messages

---

## Agent Mode Not Available

### Symptoms
- No "Agent" option in the Chat mode dropdown
- Agent mode starts but can't edit files or run commands

### Solutions

1. **Check VS Code version**
   - Agent mode requires a recent VS Code version
   - Update VS Code: `Help` → `Check for Updates`

2. **Check extension version**
   - Update GitHub Copilot and Copilot Chat extensions to the latest version

3. **Check Copilot tier**
   - Agent mode availability may depend on your Copilot license tier
   - Verify with your organization admin

4. **Workspace trust**
   - Agent mode requires a trusted workspace
   - `Ctrl+Shift+P` → "Workspaces: Manage Workspace Trust" → Trust the workspace

---

## `@workspace` Not Working

### Symptoms
- `@workspace` queries return generic answers instead of project-specific ones
- "I don't have enough context about your workspace" messages

### Solutions

1. **Wait for indexing**
   - After opening a project, Copilot needs time to index the workspace
   - Large projects may take a few minutes — look for indexing indicators in the status bar

2. **Check workspace size**
   - Very large workspaces may not be fully indexed
   - Try narrowing your question: `@workspace` + specific file references `#file:`

3. **Open the root folder**
   - Copilot indexes the folders open in VS Code
   - Make sure you've opened the project root, not a parent or subfolder

---

## Poor Quality Suggestions

### Symptoms
- Suggestions are generic, wrong framework, or don't match project style
- Copilot ignores your project's conventions

### Solutions

1. **Add more context**
   - Use `@workspace` in Chat for project-aware responses
   - Use `#file:` references to point at specific files
   - Open related files in editor tabs (Copilot uses open tabs as context)

2. **Be more specific in prompts**
   - ❌ "Write a function" → ✅ "Write an async function using our ApiService pattern that fetches user data and handles 404 errors"
   - Include framework, library, and convention details

3. **Use existing code as reference**
   - "Follow the pattern in #file:src/controllers/userController.ts"
   - Open reference files in split panes

4. **Iterate, don't re-ask**
   - "Good start, but use async/await instead of promises" builds on context
   - Re-prompting from scratch loses the conversation context

---

## Network / Proxy Issues

### Symptoms
- Copilot works at home but not at the office
- Intermittent connection errors

### Solutions

1. **Check proxy settings**
   - VS Code Settings → search "proxy"
   - Set `http.proxy` if your organization uses a proxy

2. **Allow-list Copilot domains**
   - Copilot needs access to:
     - `api.github.com`
     - `copilot-proxy.githubusercontent.com`
     - `*.githubcopilot.com`
   - Contact your IT team to allow-list these domains

3. **VPN considerations**
   - Some VPNs interfere with Copilot's connections
   - Try disconnecting VPN temporarily to verify

4. **Certificate issues**
   - If your org uses SSL inspection, VS Code may not trust the proxy certificate
   - Set `http.proxyStrictSSL` to `false` (temporary workaround, not recommended for production)

---

## Performance Issues

### Symptoms
- VS Code is slow after installing Copilot
- High CPU or memory usage

### Solutions

1. **Check extension host**
   - `Ctrl+Shift+P` → "Developer: Show Running Extensions"
   - Check if Copilot extensions are using excessive resources

2. **Reduce workspace size**
   - Exclude large folders from workspace (node_modules, build outputs) via `.vscode/settings.json`:
     ```json
     {
       "files.exclude": {
         "**/node_modules": true,
         "**/dist": true,
         "**/.git": true
       }
     }
     ```

3. **Restart extension host**
   - `Ctrl+Shift+P` → "Developer: Restart Extension Host"

---

## Still Stuck?

1. **Check [GitHub Copilot Docs](https://docs.github.com/en/copilot)** — Official documentation with the latest information
2. **Check [GitHub Status](https://www.githubstatus.com/)** — Verify Copilot services are operational
3. **Ask a facilitator** — Event facilitators can help with venue-specific and license-specific issues
4. **Check the Output panel** — `Ctrl+Shift+U` → Select "GitHub Copilot" or "GitHub Copilot Chat" for detailed logs
