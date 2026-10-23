# Scope

## One MR per feature or ticket

Related fixes from one investigation ship as one MR, one commit per fix. Side bugs found while working go into the same MR. Parallel worktrees are fine; merge them into one branch before the MR.

Why: N MRs means N CI runs, N review threads, N merges for one context. The reviewer wants to read the change as one unit.

Split only when a part is a separate concern, and say why in the MR. Exception: a fix for a red default branch that blocks everyone gets its own small MR.

## No deferred follow-ups

A refactor reaches its clean end state in the same MR: old path deleted, duplicate framework removed, legacy parameter gone. If it is big, use phases inside the branch, not later MRs.

Why: "after this MR" work usually never happens. A half-migration (two ways of doing one thing) is worse than either end state.

## Fix found gaps

A missing edge case, timeout, small bug or flaky test you hit: fix it, test it, mention it in the report. Ask only when the fix is outward-facing, destructive, or changes the scope a lot.

## Minimal change

The smallest change that fully solves the problem. Reuse before writing new code. A "simple parsing fix" must not come back as a framework rewrite. If the needed fix is bigger than the request, say so in the one-pager and let the user decide.
