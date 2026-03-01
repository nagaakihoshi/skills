---
name: dummy
description: Placeholder skill template used for testing and scaffolding new skills. Use when setting up a new skill that has not yet been given real instructions, when validating skill routing infrastructure, when a skill slot needs to be reserved before its capabilities are defined, or when a user lands on an unconfigured or stub skill and needs redirection.
---

## Overview

This is a placeholder skill. It has not yet been given real instructions or capabilities.

## Instructions

When this skill is invoked, inform the user that it has not yet been configured and suggest next steps:

1. Let the user know this skill is a placeholder and does not yet perform any useful work.
2. Invite them to describe what they were trying to accomplish so you can help through other means.
3. If the user is a skill author, guide them to replace this body with step-by-step instructions, concrete examples, commands, or code snippets relevant to the skill's intended task, and update the `description` in the frontmatter to reflect the actual capabilities and trigger conditions.

## Example Structure (to replace)

Replace this section with content tailored to the skill's real purpose. A concrete example for a "run tests" skill might look like:

- **Input:** The user says "run the test suite" or "check if my tests pass."
- **Steps:**
  1. Identify the project's test runner (e.g., `pytest`, `npm test`, `cargo test`).
  2. Execute the appropriate command in the project root.
  3. Parse the output for failures and summarise results.
- **Output:** A short report listing passed/failed tests and any error messages, with suggested fixes for failures.
