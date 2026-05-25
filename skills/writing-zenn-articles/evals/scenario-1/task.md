# Fix Invalid Article Front Matter

## Problem Description

A colleague wrote a draft Zenn article but made several mistakes in the front matter. Your job is to identify and fix each issue, rename the file to match the corrected slug, and document every change in `notes.md` at the root of the workspace.

The following problems exist in `articles/nextjs.md`:

1. The slug `nextjs` is only 6 characters — Zenn requires slugs to be 12–50 characters.
2. There are 7 topics listed — Zenn allows a maximum of 5.
3. The `emoji` field is an empty string, which is invalid.

## Output Specification

- `articles/<correct-slug>.md` — the fixed article file, renamed from `articles/nextjs.md`
- `notes.md` — a log of each issue found and the fix applied

## Input Files

The following files are provided. Extract them before beginning.

=============== FILE: articles/nextjs.md ===============
---
title: "Next.js App Router 入門"
emoji: ""
type: "tech"
topics: ["nextjs", "react", "typescript", "javascript", "vercel", "tailwindcss", "css"]
published: false
---

## はじめに

Next.js の App Router を使い始める際の基本的な手順を解説します。

## セットアップ

```bash
npx create-next-app@latest my-app --typescript
```

## まとめ

App Router を使うことで、より直感的なルーティングが実現できます。
