---
name: writing-zenn-articles
description: Guides the complete Zenn article authoring workflow using zenn-cli — from creating a new article file and configuring front matter, to writing structured content, previewing locally, and publishing via GitHub push. Use this skill whenever the user wants to write, edit, draft, or publish a Zenn article, set up a zenn-cli project, start a local preview, or push an article to make it public on Zenn. Also use it when the user asks about Zenn article structure, front matter fields, or how to organize technical writing on Zenn.
---

## Overview

Zenn articles live in the `articles/` directory of a GitHub-connected repository. Each article is a single Markdown file with YAML front matter. Changes pushed to GitHub are automatically deployed to Zenn.

## Workflow

### 1. Create a new article

```bash
npx zenn new:article
```

This generates `articles/<slug>.md` with a random slug. To specify the slug:

```bash
npx zenn new:article --slug my-article-slug
```

Slug rules: 12–50 characters, lowercase alphanumeric, hyphens, and underscores only.

### 2. Configure front matter

Edit the generated file's front matter:

```yaml
---
title: "記事タイトル"
emoji: "🔖"
type: "tech"      # tech（技術記事）or idea（アイデア・意見）
topics: ["topic1", "topic2"]   # 1–5 topics
published: false  # false until ready to publish
---
```

**type の選び方:**
- `tech` — 技術的な手順・解説・チュートリアル
- `idea` — 考察・意見・体験記

**topics の選び方:** Zenn上の既存トピック名と一致させると検索に載りやすい（例: `"typescript"`, `"react"`, `"nextjs"`）。

### 3. Write the article

For `tech` articles, structure content around: はじめに（背景・動機）→ 環境・前提条件 → 手順（ステップごと）→ まとめ。For `idea` articles, favour a narrative or opinion-led structure.

Zenn-specific Markdown syntax (callouts, collapsible sections, code blocks with filenames, etc.) is documented in [ZENN_MARKDOWN.md](ZENN_MARKDOWN.md).

### 4. Preview locally

```bash
npx zenn preview
```

Opens at http://localhost:8000. The preview hot-reloads on file save. To use a different port:

```bash
npx zenn preview --port 3000
```

Keep the preview running while editing to catch rendering issues early.

### 5. Publish via GitHub

When the article is ready, use a branch + pull request workflow so changes can be reviewed before going live.

1. Set `published: true` in front matter
2. Create a branch, commit, and push:

```bash
git checkout -b article/<slug>
git add articles/<slug>.md
git commit -m "Add article: <title>"
git push -u origin article/<slug>
```

3. Open a pull request and merge into `main`. Zenn deploys automatically within a few seconds of the merge.

**公開予約する場合:** `published_at` を追加（JST、未来の日時）:

```yaml
published_at: "2025-04-01 09:00"
```

Common rendering and deployment issues (image paths, duplicate slugs, topic names) are catalogued in [ZENN_MARKDOWN.md](ZENN_MARKDOWN.md).
