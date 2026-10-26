---
name: reviewing-changes
description: "Use to review a diff, MR/PR or design doc before any human sees it, and after each round of fixes. Runs independent review rounds until a round is clean."
---

# Reviewing changes

Nothing goes to a human for review until it has passed the review gate. Agents catch the cheap mistakes first, so human review time goes to decisions.

## The gate

| Artifact | Minimum rounds | Done when |
|---|---|---|
| Small fix | 1 | one round with no confirmed findings above "nit" |
| Feature or refactor | 2 | the last round has no confirmed findings above "nit" |
| Design doc | 2 | same |
| MR description | 1 | same, also checked against [../communicating/references/public-text.md](../communicating/references/public-text.md) |

Other public text (ticket comments, chat drafts) gets a self-check against `public-text.md`, not a review round.

A round that finds and fixes something does not count as clean. Run another round on the new state.

Cap: 4 rounds. If round 4 still has confirmed findings, stop and hand over to the user with the open list.

## One round

Track this checklist in your plan or todo tool, not in the reply:

```
Review round N:
- [ ] Review each dimension independently
- [ ] Verify each finding against the code
- [ ] Fix confirmed findings (code: one commit per round)
- [ ] Write one-line rebuttals for rejected findings
- [ ] Re-run tests (code changes only)
```

1. Review each dimension independently. Pick dimensions from [references/dimensions.md](references/dimensions.md).
   - With subagents: one reviewer per dimension, in parallel, with fresh context. Give them the goal, the diff or document, and where to look; never your conclusion or your opinion of the change. Brief template: [references/reviewer-brief.md](references/reviewer-brief.md).
   - Without subagents: one separate cold pass per dimension. Re-read the full diff from the top with only that dimension's questions in mind.
2. Verify every finding. Reviewers are confident and often wrong. Reproduce it, read the code path, or write the failing test. Classify it as confirmed, rejected (with evidence), or nit.
3. Fix confirmed findings in the same branch. A finding that shows a missing test gets the test.
4. Write a one-line rebuttal with evidence for each rejected finding.
5. For code, re-run the tests. Design docs and MR descriptions get no commit and no test run per round. The next round gets the new diff plus the list of earlier findings and rebuttals, so reviewers do not repeat closed points. Use fresh reviewers again.

## Design docs

Review a design doc against [references/design-review.md](references/design-review.md) before the user reads it.

## Report to the user

When the gate passes, add one block to the hand-over:

```
Review: 2 rounds. Fixed: <n> (<one line each>). Rejected: <n> (<one line each, why>). Open: none.
```
