# Challenge: README & API Docs

| | |
|---|---|
| **Track** | Documentation |
| **Difficulty** | ⭐ Beginner |
| **Time** | 30-45 minutes |
| **Copilot Features** | Chat, `@workspace`, Enterprise Bing search |

## Objective

Use GitHub Copilot to create or significantly improve your project's README file and API documentation. You'll learn how `@workspace` enables Copilot to generate accurate, project-specific documentation by understanding your codebase's structure, dependencies, and patterns.

## Prerequisites

- Your codebase open in VS Code
- A README that's missing, outdated, or incomplete (most projects qualify!)

## Your Mission

### Step 1: Generate or Rewrite the README (15 min)

**If you have no README (or a minimal one):**

```
@workspace Generate a comprehensive README.md for this project. Include:

1. **Project Title & Description** — What this project does and why
2. **Tech Stack** — Languages, frameworks, and key libraries used
3. **Getting Started** — Prerequisites, installation, and setup steps
4. **Usage** — How to run the project, key commands, configuration
5. **Project Structure** — Key directories and what they contain
6. **Contributing** — How to contribute, coding standards, PR process
7. **License** — (if applicable)

Base everything on the actual codebase — don't make assumptions.
```

**If you have an existing README to improve:**

```
@workspace Review our current README (#file:README.md):
1. What sections are missing or incomplete?
2. Is the getting started guide accurate based on our actual dependencies and config?
3. Is the project structure section up to date?
4. What would a new developer need that isn't covered?

Generate an improved version.
```

### Step 2: Generate API Documentation (15 min)

**For REST APIs:**

```
@workspace Analyze the API endpoints in this project and generate documentation:

For each endpoint, document:
- **HTTP Method & Path**
- **Description** — What it does
- **Request** — Parameters, query strings, headers, body schema (with examples)
- **Response** — Status codes, response body schema (with examples)
- **Authentication** — Required auth/permissions
- **Error Responses** — Common error codes and meanings

Format as a Markdown API reference.
```

**For libraries/SDKs:**

```
@workspace Generate API documentation for the public interface of this library:

For each public class/function/module:
- **Signature** — Parameters with types and descriptions
- **Returns** — Return type and description  
- **Example** — Usage example
- **Throws/Errors** — What exceptions/errors can occur
```

**For OpenAPI/Swagger:**

```
@workspace Generate an OpenAPI 3.0 specification (YAML) for our REST API. 
Include all endpoints, request/response schemas, and authentication requirements.
Base it on the actual route handlers in the code.
```

### Step 3: Add Configuration & Environment Docs (10 min)

```
@workspace Document all configuration options for this project:

1. **Environment Variables** — List all env vars used, with descriptions, 
   default values, and required/optional status
2. **Config Files** — Document the config file format and all options
3. **Feature Flags** — Any toggleable features and how to enable them

Generate a "Configuration" section for the README or a separate CONFIG.md file.
```

### Step 4: Review and Polish (5 min)

```
Review the documentation you just generated. Check for:
1. Technical accuracy — does the getting started guide actually work?
2. Completeness — are there undocumented features or options?
3. Freshness — does anything reference deprecated files or features?
4. Tone — is it clear and welcoming for new developers?
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Quick README | `@workspace Generate a README.md. Focus on getting a new developer from clone to running in 5 minutes.` |
| Architecture diagram | `@workspace Generate a Mermaid diagram showing the key components and how they interact.` |
| Changelog | `@workspace Generate a CHANGELOG entry for recent changes based on the git history.` |
| Badges | `Generate Markdown badges for: build status, code coverage, license, and latest version.` |
| FAQ | `@workspace What are the most common questions a new developer would have about this project? Generate an FAQ section.` |

## Pro Tips

- **`@workspace` is essential for README generation** — Without it, Copilot can only See the currently open file. With it, the README reflects the real project
- **Generate, then edit** — Use Copilot for the first draft, then manually refine tone, add screenshots, and fix inaccuracies
- **Test the getting started guide** — Actually follow the steps Copilot generated. You'll often find missing steps
- **Add examples** — Ask Copilot to generate code examples for the README: `Generate 3 code examples showing common usage of this library`
- **Keep it DRY** — Don't duplicate information that's in code comments or config files. Link to them instead

## Self-Assessment Checklist

- [ ] I generated or improved a README with at least 5 meaningful sections
- [ ] The getting started guide is accurate (I tested or verified the steps)
- [ ] I documented the project's API or public interface
- [ ] Configuration/environment options are documented
- [ ] I reviewed the generated documentation for accuracy and completeness
- [ ] The documentation would actually help a new developer onboard

## Going Further

- Generate a **CONTRIBUTING.md** with coding standards, PR guidelines, and development workflow
- Create **Architecture documentation** with Mermaid diagrams
- Move to the [Onboarding Guide](challenge-3-onboarding-guide.md) challenge for a more comprehensive developer guide
- Set up **auto-generated API docs** from code comments (Swagger, TypeDoc, Sphinx)
