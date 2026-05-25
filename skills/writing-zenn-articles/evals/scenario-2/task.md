# Publish a Draft Article via the Branch Workflow

## Problem Description

A finished draft article at `articles/typescript-generics-guide.md` has been reviewed and is ready to go live on Zenn. Your job is to prepare it for publication.

1. Update the article file so it will be published when merged.
2. The article should go live at 9:00 AM JST on 2026-06-01 rather than immediately — add the appropriate scheduling field to the front matter.
3. Document the complete git workflow in `notes.md` at the root: the branch to create, the commit command, and the push command needed to open a pull request.

## Output Specification

- `articles/typescript-generics-guide.md` — updated with `published: true` and `published_at: "2026-06-01 09:00"`
- `notes.md` — documents the git branch name, commit command, and push command for the pull request

## Input Files

The following files are provided. Extract them before beginning.

=============== FILE: articles/typescript-generics-guide.md ===============
---
title: "TypeScript ジェネリクスを React で活用する"
emoji: "🔧"
type: "tech"
topics: ["typescript", "react", "frontend"]
published: false
---

## はじめに

TypeScript のジェネリクスは、型安全なコンポーネントを作るための強力な機能です。

## ジェネリクスとは

型パラメータを使うことで、型を柔軟に扱えます。

## まとめ

ジェネリクスを活用することで、再利用性が高く型安全な React コンポーネントが実現できます。
