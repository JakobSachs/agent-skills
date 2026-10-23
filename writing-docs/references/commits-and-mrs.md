# Commits and MRs

## Commit messages

Follow the repo's convention. Default: conventional commits, `<type>(<scope>): <description>` with a lowercase description. Types: `feat` (new behavior), `fix` (bug), `refactor` (no behavior change), `perf`, `test`, `docs`, `chore` (CI, tooling, structure). Large changes get a bullet list of changes in the body. No `@` anywhere.

## MR text

Write for a reviewer who knows the architecture but has not read the diff. Short by default: a one-line fix gets a sentence.

### Title

Same format as a commit message.

### Body order

Most important first, so a reader can stop at any point:

1. Goal and motivation. "In order to X, this MR does Y." X is the situation that made the work necessary, not a rename of Y. Link the ticket here.
2. The change in behavior and structure. Not a file-by-file walk through the diff.
3. Decisions: the approach chosen, what was ruled out and why, anything uncertain. A decision you do not state is one the reviewer cannot check.
4. API changes, if any: added, changed, breaking.
5. Test plan: what proves it. For bug fixes, say whether the new test fails on the default branch.
6. Screenshots for visible changes, before and after.
7. Review: the block from the `reviewing-changes` gate, added after the gate passes.
8. Deploy notes, if any: migration order, flags, manual steps.

### Bug fix format

```
This MR fixes a bug where <symptom a user would hit>.

Before: <what the code did, and the mechanism that caused the symptom>
After: <what it does now>

Test plan: <test> fails on the default branch, passes here.
```

### Do not

- Restate the diff, list every file, or add tables that repeat signatures.
- Invent the why. If the motivation is not in the ticket, the commits or the user's words, ask.
- Add AI attribution lines, unless the repo requires them.
- Rewrite a human-written note at the top of an existing description. Preserve it exactly; edit below it.
- Name people's managers or escalation paths.
