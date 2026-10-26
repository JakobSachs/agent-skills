---
name: developing-features
description: "Use when asked to build, fix, change or refactor code (not pure research: investigating; not docs-only: writing-docs). Runs the change from request to merged and live, and lists the skill for each step."
---

# Developing features

## Pick the track

| Track | When | Steps |
|---|---|---|
| Small fix | clear cause, local change, the user said "fix" | 1, 4, 5, 6, 7, 8 |
| Feature | new behavior, several files or modules | all |
| Refactor | same behavior, new structure | all; the end state must be clean, see [references/scope.md](references/scope.md) |

If a small fix grows into a refactor, stop and go back to step 2.

## Workflow

Track this checklist in your plan or todo tool, not in the reply:

```
- [ ] 1. Investigate: root cause, prior art, design records
- [ ] 2. Align: one-pager to the user, wait for "go"
- [ ] 3. Create the worktree, write the design doc, review gate (2 rounds), then the user
- [ ] 4. Build in the worktree (create it now if step 3 was skipped)
- [ ] 5. Test and verify
- [ ] 6. Comment pass, then review gate on the diff (fix: 1 round, feature: 2)
- [ ] 7. Open MR, CI green, hand over
- [ ] 8. After merge: deploy, smoke test, roll out
```

1. Investigate with the `investigating` skill. Do not design before the cause is known.
2. Align with a one-pager in the format of [../communicating/references/explaining.md](../communicating/references/explaining.md). Wait for "go", then work on your own to the end of the agreed scope. In a non-interactive run, state the plan and proceed.
3. Create the worktree first (see [references/build.md](references/build.md#workspace)); the design doc is the first file you write. Design with the `writing-design-docs` skill. One detailed doc is also the plan. Run the `reviewing-changes` gate before the user reads it.
4. Build: create the worktree if it does not exist yet, then see [references/build.md](references/build.md).
5. Test with the `testing` skill while building. Use the `verifying` skill before any "done".
6. Do the comment and docs pass over every edited file (`writing-comments`, `writing-docs`), then the `reviewing-changes` gate. No human sees the diff before the gate passes.
7. Ship: see [references/ship.md](references/ship.md).
8. Go live: see [references/ship.md](references/ship.md#after-merge). Merged is not done.

## Rules for every track

- Work in a worktree, never in the user's main checkout. Do not ask first. If the harness already isolates the session (cloud container, harness-managed worktree), work in place. If the sandbox blocks git writes, ask for approval once.
- One feature or one ticket = one MR. Side bugs you find go into the same MR. Exception: a fix for a red default branch gets its own MR (see [references/scope.md](references/scope.md)).
- Fix gaps you find. Do not list them as questions.
- No "follow-up MR later". Reach the clean end state in this MR.
- Never merge or set auto-merge. The user merges, unless they said so for this specific MR.
