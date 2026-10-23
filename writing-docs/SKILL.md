---
name: writing-docs
description: Use when writing commit messages, MR or PR titles and bodies, or READMEs, AGENTS.md, CLAUDE.md, runbooks and customer docs, and when a change alters documented behavior. Comments: writing-comments.
---

# Writing docs

Docs describe what exists and how it behaves, in plain words, for a reader who has not seen the change.

## Core rules

1. Update docs in the same change that alters behavior. Stale docs mislead agents and humans alike.
2. What exists, not what is absent. Do not write "there is no X" or "X was removed". Keep a negative only when a reader would otherwise get it wrong ("the API does not retry", "never `git add -A`").
3. No history. Change stories go into the MR description and git, not into living docs.
4. Plain UNIX style. Short, factual, like a man page. No marketing, no enthusiasm, no emojis.
5. Audience first. Decide who reads it and what they do with it. Customers get the effect on them, not the internals.
6. Every line costs context. Agent context files are loaded on every request; cut anything a reader can find in the code.

## Which reference to read

| Writing | Read |
|---|---|
| Commit message, MR or PR title and description | [references/commits-and-mrs.md](references/commits-and-mrs.md) |
| README, runbook, standards, CONTEXT.md, customer docs | [references/docs.md](references/docs.md) |
| AGENTS.md, CLAUDE.md, or other agent context files | [references/agent-context.md](references/agent-context.md) |

Public text rules (no group mentions, no names, no secrets) apply to everything here: [../communicating/references/public-text.md](../communicating/references/public-text.md).
