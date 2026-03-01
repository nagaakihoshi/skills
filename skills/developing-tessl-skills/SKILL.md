---
name: developing-tessl-skills
description: Runs the complete local development lifecycle for a Tessl skill by optimizing SKILL.md content using `tessl skill review --optimize`, incrementing the version in tile.json following semantic versioning, linting with `tessl skill lint`, and staging changes for a pull request. Use when preparing a Tessl skill for pull request or publication, when a SKILL.md or tile.json needs to be reviewed, versioned, and validated before committing, or when running the full Tessl skill development workflow locally.
---

## Overview

This skill covers the complete local development lifecycle for a Tessl skill before opening a pull request. It ensures the skill is optimized, properly versioned, and validated.

## Prerequisites

- Tessl CLI installed: `curl -fsSL https://get.tessl.io | sh`
- Logged in: `tessl login`

## Steps

### 1. Identify the skill path

Confirm the skill directory (e.g., `skills/<name>/`) contains both `tile.json` and `SKILL.md`.

### 2. Optimize the skill

```bash
tessl skill review --optimize skills/<name>
```

- Iterates up to 3 times, applying best-practice improvements automatically.
- Accept the proposed changes when prompted, or use `--yes` to auto-accept.
- Aim for a score of 70% or higher. If the score is still below threshold, re-run with `--max-iterations 10`.

### 3. Increment the version in tile.json

Open `skills/<name>/tile.json` and increment `version` following semantic versioning:

| Change type | Example |
|---|---|
| Bug fix or minor wording improvement | `0.1.0` → `0.1.1` |
| New capability, backward-compatible | `0.1.0` → `0.2.0` |
| Breaking change to skill behavior | `0.1.0` → `1.0.0` |

### 4. Validate

```bash
tessl skill lint skills/<name>
```

Confirm the output shows the tile as valid before committing.

If lint fails: review the reported errors, fix the issues in `SKILL.md` or `tile.json`, then re-run `tessl skill lint` until it passes before proceeding.

### 5. Commit and open a PR

Stage all changes to `SKILL.md` and `tile.json`, commit, and open a pull request against `main`. CI will run `tessl skill lint` automatically on the PR.
