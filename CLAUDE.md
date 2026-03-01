# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains agent skills — custom tools and capabilities for AI agents, managed with [Tessl](https://tessl.io).

## Repository Structure

```text
skills/<name>/
├── tile.json   # Skill metadata and version
└── SKILL.md    # Agent instructions
```

## Development Workflow

### Creating a skill

> **Note:** `tessl skill new` has a bug where it generates a nested structure. Create skills manually.

```json
// skills/<name>/tile.json
{
  "name": "nagaakihoshi/<name>",
  "version": "0.1.0",
  "summary": "<description>",
  "private": true,
  "skills": {
    "<name>": {
      "path": "SKILL.md"
    }
  }
}
```

### Naming convention

Use gerund form for skill names (e.g., `developing-tessl-skills`, not `tessl-skill-dev`).

### Preparing a skill for PR

1. Optimize: `tessl skill review --optimize skills/<name>`
   - Aim for a score of 70% or higher
2. Bump version in `tile.json` following semver
3. Lint: `tessl skill lint skills/<name>`
4. Stage both `SKILL.md` and `tile.json`

> **Note:** `tessl skill review` requires local login (`tessl login`). It cannot authenticate in CI.

### CI behavior

- **PR:** `tessl skill lint` runs on changed skills only
- **Merge to main:** `tesslio/publish@main` publishes to the Tessl Registry

## Skill Authoring Guidelines

Follow the [Claude skill best practices](https://platform.claude.com/docs/ja/agents-and-tools/agent-skills/best-practices).

### Frontmatter

- **`name`**: lowercase, hyphens only, max 64 chars, gerund form (e.g., `processing-pdfs`)
- **`description`**: third person, max 1024 chars, must describe **what** the skill does AND **when** to use it

```yaml
# Good
description: Runs the complete local development lifecycle for a Tessl skill. Use when preparing a skill for pull request or publication.

# Bad — first person, no trigger condition
description: Helps you prepare Tessl skills for publishing.
```

### Conciseness

Only add context Claude doesn't already know. Each line in SKILL.md competes with the conversation history and other skills in the context window. Keep SKILL.md body under 500 lines.

### Freedom level

Match the level of specificity to the risk of the task:

| Task risk | Style | Example |
|---|---|---|
| High (destructive, exact sequence required) | Exact commands, no deviation | Database migrations |
| Medium (recommended pattern exists) | Template with parameters | Report generation |
| Low (many valid approaches) | High-level steps only | Code review |

### Progressive disclosure

Reference additional detail in separate files rather than packing everything into SKILL.md. Keep references **1 level deep** — all linked files should be referenced directly from SKILL.md.

```text
skills/<name>/
├── SKILL.md          # Overview + links (loaded on trigger)
├── reference.md      # Detail (loaded on demand)
└── scripts/
    └── helper.py     # Scripts (executed, not loaded)
```

For reference files over 100 lines, add a table of contents at the top.

### Workflows

For multi-step tasks, use numbered steps with a copyable checklist:

```markdown
Copy this checklist to track progress:
- [ ] Step 1: ...
- [ ] Step 2: ...

**Step 1: ...**
...
```

Build in feedback loops where quality matters: run validator → fix errors → repeat until passing.

### Content guidelines

- Use consistent terminology throughout (pick one term and stick to it)
- Avoid time-sensitive phrasing; use `<details>` blocks for legacy patterns instead
- Use forward slashes for all file paths (never backslashes)
