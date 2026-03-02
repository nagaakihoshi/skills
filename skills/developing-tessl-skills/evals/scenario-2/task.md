# Validate and Fix a Skill Before Pull Request

## Problem Description

A colleague set up a new Tessl skill for dispatching HTTP webhooks and has asked you to take it through final validation before the pull request is opened. They believe it is complete, but they are new to the Tessl toolchain and may have made configuration mistakes. CI will run the standard validation checks automatically on the PR, so you want to catch any issues locally first.

Run the appropriate local validation tooling against `skills/webhook-sender/`. If any problems are found, investigate the error output, apply the necessary fixes to the skill files, and keep re-validating until the skill passes cleanly. Document every command you run and its result — including any errors encountered and the fixes applied — in a file called `process.md` at the root of the workspace.

## Output Specification

- `skills/webhook-sender/tile.json` — fixed in place (if changes were needed)
- `skills/webhook-sender/SKILL.md` — fixed in place (if changes were needed)
- `process.md` — a log of every validation command run, errors observed, fixes applied, and the final result

## Input Files

The following files are provided. Extract them before beginning.

=============== FILE: skills/webhook-sender/tile.json ===============
{
  "name": "nagaakihoshi/webhook-sender",
  "version": "0.1",
  "summary": "Send HTTP webhooks to external endpoints",
  "private": true,
  "skills": {
    "webhook-sender": {
      "path": "SKILL.md"
    }
  }
}

=============== FILE: skills/webhook-sender/SKILL.md ===============
---
name: webhook-sender
description: Send HTTP POST webhooks to external endpoints with a configurable JSON payload.
---

## Overview

This skill sends an HTTP POST request to a configured webhook URL with a JSON payload.

## Steps

### 1. Configure the endpoint

Set the target URL and any required authentication headers (e.g. `Authorization: Bearer <token>`).

### 2. Define the payload

Specify the JSON body to send in the request. Keys and values are defined by the receiving service.

### 3. Send the webhook

Trigger the POST request. The skill returns the HTTP status code and response body from the server.
