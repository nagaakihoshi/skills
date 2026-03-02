# Version a Skill After Adding New Capabilities

## Problem Description

A teammate just finished extending the `skills/email-notifier/` skill. Previously it only supported sending a message to a single primary recipient. The updated SKILL.md now covers two additional capabilities: copying additional recipients (CC) and attaching files to the message. Both additions are fully backward-compatible — any existing workflow that uses this skill continues to work without modification.

The skill content itself is already polished and ready to go. The only remaining step before opening a pull request is to update the version in `tile.json` to reflect what changed, and to leave a record of your reasoning.

## Output Specification

- `skills/email-notifier/tile.json` — updated with the correct new version
- `process.md` — a brief log explaining which version bump type was chosen and why, and which files should be staged for the commit

## Input Files

The following files are provided. Extract them before beginning.

=============== FILE: skills/email-notifier/tile.json ===============
{
  "name": "nagaakihoshi/email-notifier",
  "version": "0.1.0",
  "summary": "Send email notifications with optional CC and attachments",
  "private": true,
  "skills": {
    "email-notifier": {
      "path": "SKILL.md"
    }
  }
}

=============== FILE: skills/email-notifier/SKILL.md ===============
---
name: email-notifier
description: Send email notifications to one or more recipients, with optional CC addresses and file attachments.
---

## Overview

This skill sends email notifications. It supports a primary recipient, any number of CC recipients, and optional file attachments up to 10 MB each.

## Steps

### 1. Compose the message

Set the subject, body text, and primary recipient address. Add CC addresses if needed.

### 2. Attach files (optional)

Provide file paths to attach. Each attachment must be under 10 MB.

### 3. Send

Trigger the send action. The skill returns a message ID on success.
