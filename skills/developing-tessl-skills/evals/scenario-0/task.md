# Prepare a New Skill for Pull Request

## Problem Description

A developer on your team has just finished writing the first draft of a new Tessl skill for querying an internal database. The SKILL.md content is rough and the tile is at version 0.1.0. Before opening a pull request, the skill needs to go through the standard local preparation process.

Your job is to prepare the skill at `skills/db-query/` for a pull request. When you are done, write a file called `process.md` at the root of the workspace documenting each command you ran and the result (including any scores reported).

## Output Specification

- `skills/db-query/SKILL.md` — updated in place after optimization
- `skills/db-query/tile.json` — version incremented appropriately
- `process.md` — a log of every command run and its output summary

## Input Files

The following files are provided. Extract them before beginning.

=============== FILE: skills/db-query/tile.json ===============
{
  "name": "nagaakihoshi/db-query",
  "version": "0.1.0",
  "summary": "Query internal database",
  "private": true,
  "skills": {
    "db-query": {
      "path": "SKILL.md"
    }
  }
}

=============== FILE: skills/db-query/SKILL.md ===============
---
name: db-query
description: Query database.
---

Query the database when asked.
