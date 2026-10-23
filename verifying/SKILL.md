---
name: verifying
description: Use before claiming work is done, fixed, passing or live, and before committing or marking an MR ready. Requires fresh evidence for every claim.
---

# Verifying

## The rule

Before any "done", "fixed", "passes", "works" or "live":

1. State the command or check that proves it.
2. Run it now, in full. An earlier run, or a subagent's word, does not count.
3. Read the output: exit code, failure count, the response.
4. Claim exactly what the output shows, and quote it.

## What counts as evidence

| Claim | Evidence |
|---|---|
| Tests pass | the test command and its summary line, run after the last edit |
| Bug fixed | the test that failed before now passes; the original symptom is gone when reproduced the same way |
| Lint and types clean | the linter and type checker output |
| UI works | a screenshot of every changed view in the running app, checked by you. No browser or screenshot tool: report "UI not verified" |
| API works | the response body, not the status code alone |
| Deployed | the running version contains the commit (`git merge-base --is-ancestor <commit> <live-sha>`) |
| Live | the live result itself: endpoint response, rendered page, log line. Not the pipeline color |
| Subagent finished | its diff read and its tests re-run by you |
| Coverage OK | the coverage report on changed lines |

See [references/ui-and-live.md](references/ui-and-live.md) for screenshots and live checks.

## Verify the outcome, not a proxy

A green pipeline, a 200 status, a "success" log line or a closed ticket are proxies. Check the thing the user cares about: the rendered result, the response body, the data in the table.

## Partial results

If some checks pass and others fail or were skipped, say so per check. Never round up. "Unit tests pass (412). E2E not run: no browser in this environment."

## Red flags

- "Should work now."
- "Tests passed" with no output, or from before the last edit.
- "Fixed" without reproducing the original symptom.
- A subagent report pasted as fact.
