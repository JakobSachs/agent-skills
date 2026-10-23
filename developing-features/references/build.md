# Build

## Workspace

- Create a git worktree (for example `.worktrees/<branch>`) before the first file write, including the design doc. All edits, tests and commits happen there.
- If the harness already isolates the session (cloud container, harness-managed worktree), work in place instead.
- Branch from the remote default branch (`git fetch`, then `git symbolic-ref refs/remotes/origin/HEAD` to find it; if unset, run `git remote set-head origin -a` first).
- If the sandbox blocks `git worktree add` or commits, ask for approval once; do not work in the user's main checkout instead.
- End with `git status --short` clean.

## Order

Phase by phase from the design doc. Each phase: types and data, logic, wiring, tests, all in one go. Commit when a phase works and its tests pass.

## Subagents

If the harness can spawn subagents:

- Implementation and fixing need a strong model. Weak models report work as done that is not.
- One committing agent per worktree at a time. Pre-commit hooks stash unstaged files, which clobbers another agent's edits. Read-only agents may run in parallel.
- Give each implementer the full phase from the design doc: file paths, types, test properties.
- Tell implementers to run commit hooks in the foreground and not to stop until the commit exists.
- Never put secrets, env dumps or connection strings into a brief, and forbid printing them.
- Long searches (many files, cluster probing) go to a background agent. The main thread keeps decisions.
- Verify every "done" a subagent reports: run the tests yourself and read the diff.

## Commits

- Message format: [../../writing-docs/references/commits-and-mrs.md](../../writing-docs/references/commits-and-mrs.md).
- Never mix behavior changes with whitespace or formatting changes in one commit.
- Never skip hooks with `--no-verify`. If hooks run longer than the harness timeout, run the commit in the background and wait for it. Skip a single hook only when the repo documents that skip (for example a `SKIP=<hook>` variable) and CI runs the same check.

## Contracts

API routes, response models, events, config schemas: see the `writing-code` skill, [../../writing-code/references/structure.md](../../writing-code/references/structure.md#contracts).
