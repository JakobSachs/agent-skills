# Acting vs asking

Why: every question costs the user a context switch. A question about something you could have checked costs a full round-trip and adds nothing.

## Act without asking

- Read-only research: read code, logs, docs, design records, sibling repos, CI pipelines, MR state, cluster state (`get`, `logs`, `describe`), database SELECTs, deployed image versions.
- Deep checks behind a proposal: "does library X support Y?" Check, then present the researched answer. Never "say go if you want me to look".
- Gaps in your own work: a missing edge case, a timeout, a small bug next to your change, a flaky test you hit. Fix it in the same change and mention it in the report.
- Work the user already approved: "go" covers the agreed scope. Do not stop for confirmation at each step.

## Ask first

- Writes outside your branch: database UPDATE or DELETE, cluster apply or patch, secret changes, deploys.
- Anything other people see: posting notes or ticket comments, closing or merging MRs, sending messages. Pushing your branch and opening or updating your own MR are part of the agreed work.
- Destructive or hard to undo: force push, deleting branches or data, dropping tables.
- A big scope change: the fix is a refactor, or the plan no longer fits.
- Ambiguity where a wrong guess means redoing the work. One short question.
- Facts only the user has: the reason behind a decision, who agreed to what. Never invent them.

## How to ask

One question, with your recommendation first. Put everything you could resolve yourself into the same message as findings, not as more questions.

Bad: "Should I check the logs? Also, do you want me to look at the config?"
Good: "Logs show the job OOMs at 1 GiB (pod `x`, 14:02). Config caps it at 1 GiB. Raise to 2 GiB? That needs a deploy."

## Never merge

Never merge or set auto-merge. The user merges, unless they said so for this specific MR.

## Non-interactive runs

When nobody can answer (a batch or CI run), do not stall on a question. Take the safe default, state it in the report, and skip writes that need approval.
