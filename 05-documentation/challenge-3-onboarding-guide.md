# Challenge: Onboarding Guide

| | |
|---|---|
| **Track** | Documentation |
| **Difficulty** | ⭐⭐ Intermediate |
| **Time** | 45-60 minutes |
| **Copilot Features** | Chat, `@workspace`, `#file` references |

## Objective

Use GitHub Copilot to generate a comprehensive developer onboarding guide for your repository. This is the document you wish existed when you joined the project — covering setup, architecture, conventions, workflows, and "where is everything?" answers. Copilot's `@workspace` capability makes it uniquely suited for this task because it can analyze the entire codebase.

## Prerequisites

- Your codebase open in VS Code
- Knowledge of your team's workflows (branching strategy, PR process, deployment)
- 10+ minutes of willingness to review and supplement AI-generated content with tribal knowledge

## Your Mission

### Step 1: Generate the Architecture Overview (10 min)

```
@workspace Generate a developer onboarding guide starting with the architecture:

## Project Architecture

1. **High-level overview** — What does this project do? What problem does it solve?
2. **Architecture diagram** — Generate a Mermaid diagram showing main components
3. **Tech stack** — Languages, frameworks, databases, and why they were chosen
4. **Directory structure** — What's in each top-level directory?
5. **Key files** — The 5-10 most important files a new developer should read first
```

### Step 2: Generate the Development Workflow (10 min)

```
@workspace Continue the onboarding guide with the development workflow:

## Development Workflow

1. **Environment Setup** — Step-by-step from fresh machine to running project
   - Required tools and versions
   - How to clone, install dependencies, configure
   - How to run the project locally
   - How to run tests
   - Common setup issues and fixes

2. **Code Organization** — Where does new code go?
   - Folder conventions
   - Naming conventions  
   - Module/package boundaries

3. **Key Patterns** — What patterns should new developers follow?
   - Show real examples from the codebase with #file references
```

### Step 3: Document Conventions and Standards (10 min)

```
@workspace Continue with coding conventions:

## Coding Conventions

1. **Naming** — How things are named in this project (files, variables, functions, classes)
   - Show examples from the codebase
2. **Error Handling** — How errors are handled consistently
3. **Testing** — Test file organization, naming, frameworks, and what to test
4. **API Patterns** — How endpoints / services / components are structured
5. **Configuration** — How config is managed (env vars, config files, feature flags)

Base all examples on ACTUAL code in this repo, not generic advice.
```

### Step 4: Add Operational Knowledge (10 min)

```
@workspace Continue with operational information:

## Operations & Deployment

1. **Environments** — What environments exist (dev, staging, production)?
2. **Branching Strategy** — How branches are used
3. **CI/CD** — What happens when code is pushed? (analyze CI config files if present)
4. **Monitoring & Logging** — How to find logs, check health, debug production issues
5. **Common Tasks** — How to:
   - Add a new API endpoint
   - Add a new database migration
   - Add a new test
   - Deploy a change
```

Supplement with tribal knowledge:
```
I also want to add these points that only team members would know:
- [Add any team conventions not visible in code]
- [Common gotchas or pitfalls]
- [Who to ask about what]
```

### Step 5: Generate a Quick Reference (10 min)

```
Finish the onboarding guide with a quick reference cheat sheet:

## Quick Reference

**Useful Commands:**
| Task | Command |
|------|---------|
| (fill based on project) | |

**Key URLs and Resources:**
| Resource | URL |
|----------|-----|
| (fill based on project) | |

**Glossary:**
Define any project-specific terms, acronyms, or domain concepts that 
a new developer would need to know.
```

### Step 6: Review and Supplement (10 min)

```
@workspace Review the complete onboarding guide. Identify:
1. Sections that are thin or need more detail
2. Anything inaccurate based on the actual code
3. Important topics missing entirely
4. Steps in the setup guide that might fail
```

**Manually add:**
- Team-specific knowledge Copilot can't know (Slack channels, meeting schedules, key contacts)
- Philosophical guidance ("We value X over Y", "When in doubt, Z")
- Historical context ("We chose X because of Y constraint, which is no longer relevant but the code remains")

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Fresh perspective | `@workspace If I just cloned this repo with zero context, what would confuse me? What's non-obvious?` |
| Architecture diagram | `@workspace Generate a Mermaid sequence diagram showing the flow of [key operation, e.g., "user signup"]` |
| "Where is" guide | `@workspace Generate a "Where is everything?" guide: where to find routes, models, services, tests, config, etc.` |
| Troubleshooting | `@workspace What are the most likely things to go wrong when setting up this project? How to fix each?` |
| Domain glossary | `@workspace Generate a glossary of domain-specific terms used in this codebase with definitions.` |

## Pro Tips

- **`@workspace` is the hero feature here** — It enables Copilot to analyze your entire project structure, dependencies, and code patterns to generate accurate documentation
- **Verify setup steps** — The most valuable test is having someone actually follow the guide. Even verifying it yourself after a few weeks reveals missing steps
- **Live document** — Store the guide in the repo and encourage updates during code reviews
- **Add visual aids** — Ask Copilot for Mermaid diagrams, then render them in your markdown viewer
- **Supplement with tribal knowledge** — Copilot generates the structural knowledge; you add the human context

## Self-Assessment Checklist

- [ ] The guide covers architecture, setup, workflow, conventions, and operations
- [ ] It includes real file/code references from the actual codebase (not generic advice)
- [ ] The setup steps are complete and correct
- [ ] I supplemented Copilot's output with team-specific tribal knowledge
- [ ] A new developer could realistically use this guide to get productive
- [ ] The guide is saved in the repository where the team can maintain it

## Going Further

- Have a **teammate who's less familiar** with the codebase review the guide and identify gaps
- Generate **architecture decision records** for key decisions using the [ADR Generation](../01-planning-and-design/challenge-3-adr-generation.md) challenge
- Create a **runbook** for common operational tasks (deploying, rolling back, handling incidents)
- Set up a process to **keep the guide updated** — eg., add a "docs" label to PRs that change architecture
