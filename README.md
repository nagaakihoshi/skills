# skills

A collection of agent skills managed with Tessl.

## Setup

### Install Tessl CLI

```bash
curl -fsSL https://get.tessl.io | sh
```

### Login

```bash
tessl login
```

## Development Cycle

### 1. Create a new skill

> **Note:** `tessl skill new` has a bug where it generates a nested structure instead of the skill-first structure documented at [docs.tessl.io](https://docs.tessl.io/create/creating-skills#understanding-the-tessl-package-structure). Create skills manually until this is fixed.

```text
skills/<name>/
├── tile.json
└── SKILL.md
```

**tile.json template:**

```json
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

### 2. Write SKILL.md

Add agent instructions to `skills/<name>/SKILL.md`.

### 3. Review and optimize locally

```bash
tessl skill review --optimize skills/<name>
```

> **Note:** CLI authentication is not supported in CI. Review and optimize must be done locally before opening a PR.

### 4. Open a PR

GitHub Actions runs automatically on PR create/update:

- `tessl skill lint` — validates skill structure

### 5. Merge → publish

On merge to `main`, GitHub Actions publishes to the Tessl Registry via `tesslio/publish@main`.

## GitHub Secrets

Add the following secret in GitHub repository Settings > Secrets and variables > Actions:

| Secret | Description |
|--------|-------------|
| `TESSL_API_TOKEN` | Tessl API token (generate at [tessl.io](https://tessl.io) account settings) |
