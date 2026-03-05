# Challenge: Boilerplate & Scaffolding

| | |
|---|---|
| **Track** | Code Generation |
| **Difficulty** | ⭐ Beginner |
| **Time** | 30-45 minutes |
| **Copilot Features** | Inline completions, Inline Chat, Chat, `@workspace` |

## Objective

Use GitHub Copilot to rapidly generate repetitive, pattern-based code: API endpoints, data models, configuration files, CRUD operations, and other boilerplate. You'll learn how to guide Copilot toward consistent, project-aligned output by leveraging existing code as templates.

## Prerequisites

- Your codebase open in VS Code
- An area of your project that needs new boilerplate (new endpoint, data model, config, etc.)

> **Don't have boilerplate to write?** Try one of these:
> - Add a new CRUD entity (model + routes + controller) following existing patterns
> - Create a new configuration file following the format of existing configs
> - Add new data transfer objects (DTOs) or API response types

## Your Mission

### Step 1: Identify the Pattern (5 min)

Find an existing piece of code that follows the pattern you want to replicate:

```
@workspace Show me examples of [API endpoints / data models / config files] 
in this project. I want to create a new one following the same pattern.
```

Open the reference file(s) — keeping them in open tabs gives Copilot better context.

### Step 2: Generate from a Template (15 min)

**Option A: Inline Chat in a new file**

Create a new file, then press `Ctrl+I`:

```
Generate a [controller/model/route file] for [entity name] following the exact same 
pattern as #file:[reference-file]. 

The entity should have these fields: [list fields]
Include: [list what to include, e.g., "validation", "error handling", "logging"]
```

**Option B: Comment-driven generation**

Create a new file and write a detailed top-of-file comment:

```python
# User Notification Model
# Follows the same pattern as models/user.py
# Fields:
#   - id: UUID (primary key)
#   - user_id: FK to users table
#   - message: string (max 500 chars)
#   - read: boolean (default false)
#   - created_at: datetime (auto-set)
# Include: validation, serialization, __repr__
```

Then press Enter and let Copilot generate the implementation line by line.

**Option C: Batch generation via Chat**

```
@workspace I need to create a complete CRUD setup for a new [entity] resource. 
Based on how [existing entity] is implemented, generate:

1. The data model / schema
2. The API routes / controller
3. The service / business logic layer
4. The request/response DTOs or types

Use the exact same patterns, naming conventions, and file organization as the existing code.
```

### Step 3: Repeat and Refine (10 min)

Generate additional related files. Each generation should be faster as Copilot picks up on the pattern:

```
Now create the [test file / migration file / serializer] for the same entity, 
following the pattern in #file:[reference-test/migration/serializer]
```

### Step 4: Customize and Validate (5 min)

The generated code will be close but may need adjustment:

```
@workspace Review the files I just created for [entity]:
#file:[new-file-1] #file:[new-file-2] #file:[new-file-3]

Check that they:
1. Follow the same conventions as existing code
2. Have consistent naming
3. Include all necessary imports
4. Don't have copy-paste errors from the template
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| Clone a pattern | `Generate a [thing] for [entity] using the exact same structure as #file:[reference]` |
| Batch field generation | `Generate [TypeScript interfaces / Python dataclasses / C# records] for these entities: [list entities with their fields]` |
| Config generation | `Create a [config type] file following the format of #file:[existing-config]. Settings needed: [list]` |
| Enum/constant generation | `Generate an enum for [domain] with values: [list]. Include descriptions and follow the pattern in #file:[reference]` |
| Repetitive methods | Select a class → `Ctrl+I` → `Add [CRUD/getter/setter/builder] methods for all fields, following the pattern of the existing methods` |

## Pro Tips

- **Open the reference file in a split pane** — Copilot heavily weights open tabs, so having the template visible produces much more consistent output
- **Be explicit about what to include** — "Include validation, error handling, and logging" gets better results than just "generate a model"
- **Generate the boring parts, customize the interesting parts** — Let Copilot handle the structural boilerplate, then manually adjust business logic
- **Use multiple reference files** — Reference 2-3 existing examples: "Follow the pattern used in both #file:userController.ts and #file:orderController.ts"

## Self-Assessment Checklist

- [ ] I identified an existing pattern in my codebase to replicate
- [ ] I generated at least one new file that follows the existing pattern
- [ ] The generated code uses consistent naming and conventions
- [ ] I used reference files (`#file:` or open tabs) to guide Copilot
- [ ] I reviewed and customized the generated output (didn't just accept blindly)
- [ ] The generated code compiles/runs without significant changes

## Going Further

- Generate an **entire new module** (5+ files) following your project's conventions
- Use Chat to generate **database migrations** for your new models
- Create a **code generator prompt** you could reuse for future entities on your project
