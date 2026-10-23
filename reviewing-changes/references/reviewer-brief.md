# Reviewer brief

The brief is the only context the reviewer has. Give facts and scope. Leave out your view of the change.

```
Review this change for <dimension>.

Goal of the change: <one or two lines, from the ticket or the user>
Diff: <how to get it, e.g. `git diff origin/<default-branch>...HEAD`, or the file paths>
Read also: <design doc, CONTEXT.md, the module's tests>

Earlier rounds (do not repeat these):
- <finding>: fixed in <commit>
- <finding>: rejected, <evidence>

Questions for this dimension:
<paste the dimension's questions from dimensions.md; for a design doc, from design-review.md>

Rules:
- Read-only. Do not edit files, commit, or post anything.
- Do not print secrets, env vars or connection strings.

Report: a list of findings. Each: file:line, what is wrong, a concrete failure scenario (input -> wrong result), severity (blocking / should-fix / nit). No praise, no summary of the diff. Empty list if nothing is confirmed.
```

Run reviewers for different dimensions in parallel. They are read-only, so they do not collide.
