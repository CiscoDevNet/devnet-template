---
name: skill-name-in-kebab-case
description: >
  Describes the exact Cisco workflow this skill supports and the concrete
  requests that should activate it.
license: Apache-2.0
compatibility: "Claude Code, GitHub Copilot, OpenAI Codex, Cursor, Gemini CLI"
metadata:
  product: replace-with-product-folder
  maturity: draft
---

# Skill Name in Title Case

## Purpose

Explain the operational problem this skill solves and the boundaries of its
guidance.

## When to use

- Concrete trigger scenario one.
- Concrete trigger scenario two.
- Concrete trigger scenario three.

## Prerequisites & environment

- Required product release or supported version range.
- Required read-only or administrative role.
- Required CLI, SDK, MCP server, or API specification.
- Suitable lab or [Cisco DevNet Sandbox](https://developer.cisco.com/sandbox/).

## Step-by-step guidance

1. Confirm the platform, software version, target identifiers, and requested
   outcome.
2. Capture current state with read-only commands or API calls.
3. Validate the candidate operation against current product documentation or a
   live schema.
4. For a change, prepare the smallest candidate diff and a rollback procedure.
5. Apply only with explicit operator approval and appropriate change controls.
6. Verify the result against the baseline before saving or declaring success.

## Best practices

- Treat examples as patterns, not paste-ready production changes.
- Prefer read-only discovery and least-privilege credentials.
- Use placeholders and local secret stores; never place credentials in the
  skill, command line, logs, or chat.
- Bound queries, pagination, retries, payload size, and execution time.
- Link to primary Cisco documentation and state version assumptions.

## Common pitfalls

- **Symptom:** The generated command is rejected or behaves differently.
  **Fix:** Re-check installed CLI help, API schema, and product version instead
  of guessing a replacement.
- **Symptom:** A change risks management lockout.
  **Fix:** Stop, verify out-of-band access and rollback, and review management
  traffic before applying.

## Worked example

Provide one realistic, sanitized example. Show read-only baseline collection,
the candidate action, expected evidence, rollback, and post-change validation.
Use documentation address ranges, synthetic names, and placeholders only.

## Cross-references

- Link directly to related skills or references when they exist.
- Link to the authoritative Cisco product documentation used by this skill.

Reference: https://github.com/CiscoDevNet/skills
