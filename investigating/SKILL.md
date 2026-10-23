---
name: investigating
description: Use before proposing any fix or design, and for research questions: bugs, failing tests, incidents, how X works, whether X exists. Finds and proves root causes. Building the fix: developing-features.
---

# Investigating

No fix and no design before the cause is known and proven.

## Workflow

Track this checklist in your plan or todo tool, not in the reply:

```
- [ ] 1. Reproduce or observe the symptom yourself
- [ ] 2. Read what is already written about it
- [ ] 3. Form one hypothesis, test it, repeat
- [ ] 4. Explain how it got past code review and tests
- [ ] 5. Report with evidence
```

1. Observe. Start from what the user sees: the URL, the error text, the failing job. Then the routes file, then the component or handler. Get the output, not a description of it.
2. Read records first. Design docs, ADRs, `CONTEXT.md` and similar files often state the bug, the layer to fix it in, and options already rejected. Search them for the mechanism before proposing one. See [references/sources.md](references/sources.md).
3. Hypothesis loop. One hypothesis at a time, with a check that can prove it wrong. Change one thing per test. See [references/debugging.md](references/debugging.md).
4. How it got past. Why did the existing tests not catch it? The answer often shows a second fix: a missing test, or a fixture no producer emits.
5. Report in the format of [../communicating/references/long-report.md](../communicating/references/long-report.md): verdict, findings with evidence and basis, cause, options.

## Rules

- Read-only research needs no permission. Do it, then report.
- Check the remote default branch before claiming something does or does not exist. Say which ref you read.
- Check the environment and tenant. If the repo does not say which one is the main target, ask.
- Long searches go to a background subagent if the harness has one. Keep decisions in the main thread.
- Data access rules: [references/data-access.md](references/data-access.md).
- Three failed fixes in a row: stop. Your model of the system is wrong. Go back to step 1 and check the assumption nobody has tested.
