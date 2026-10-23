# Ship

## Open the MR

1. Push the branch. Open the MR as a draft.
2. Write title and description with the `writing-docs` skill ([../../writing-docs/references/commits-and-mrs.md](../../writing-docs/references/commits-and-mrs.md)).
3. Frontend change: screenshots of every changed view, taken in the running app, uploaded to the description. Without a browser or screenshot tool, say "UI not verified" in the hand-over.
4. Run the `reviewing-changes` gate on the description (1 round). The diff already passed in step 6 of the workflow; review it again only if it changed since.
5. Wait for CI green (see CI below).
6. Add the review block to the description, mark ready, and hand over.

## CI

- Red CI is your problem. Read the failing job log, fix the cause, push.
- A flaky test is a bug. Fix it now (see the `testing` skill).
- Never retry a job only to get green.
- Never merge or set auto-merge. The user merges, unless they said so for this specific MR.

## Hand-over

```
MR: <url>  (ready, CI green)
What: <one line>
Review: <rounds, fixed, rejected>
Check: <screenshots / how to try it>
Needs from you: merge  [+ anything else, e.g. "run migration first"]
```

## After merge

Watching is read-only and needs no approval. Anything that changes a running system does.

| Step | Approval |
|---|---|
| Watch the pipeline and the automatic deploy | none |
| Check the running version and migrations | none |
| Trigger a deploy, promote to another environment, run a migration by hand | ask first |
| Create smoke-test data in a shared tenant | ask first, unless the user already named the test tenant |
| Roll out to more teams or tenants | ask first |

Steps and checks: [../../verifying/references/ui-and-live.md](../../verifying/references/ui-and-live.md#live-checks-after-deploy). Report where it is live and how it was verified. Clean up worktrees and test data you created.
