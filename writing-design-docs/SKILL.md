---
name: writing-design-docs
description: "Use before coding a feature or refactor (not small fixes), once the user agreed to the one-pager. Writes one detailed design doc that is also the implementation plan."
---

# Writing design docs

One document contains the design and the plan. An implementer with no context, including a fresh agent, must be able to build each phase from this doc alone.

## Workflow

Track this checklist in your plan or todo tool, not in the reply:

```
- [ ] 1. Inputs ready: investigation findings, agreed one-pager
- [ ] 2. Resolve open questions with the user (few, one at a time)
- [ ] 3. Write the doc from the template
- [ ] 4. Review gate: 2 rounds (reviewing-changes, design-review)
- [ ] 5. Hand to the user; on approval, commit it with the code branch
```

1. Inputs. No doc without a known cause and an agreed direction. If either is missing, go back to `investigating` or to the one-pager.
2. Questions. Ask only what the code, records and research cannot answer: scope, priorities, trade-offs the user owns. One question per message, recommendation first. In a non-interactive run, take the recommended answer, record it under Decisions, and proceed.
3. Write with [references/template.md](references/template.md). Put it where the repo keeps design records (for example `docs/design/YYYY-MM-DD-<slug>.md`).
4. Run the `reviewing-changes` gate before the user sees it. A doc that has not passed 2 rounds is a draft.
5. The user approves or pushes back (non-interactive: proceed and flag the doc as unapproved in the report). Update the doc when the plan changes during the build; it must match what was built.

## Rules

- Few, big phases: about 3. Each phase is a vertical slice that works and is tested on its own: types, storage, logic, wiring and tests together. Never a phase "add tests" or a task per file.
- Simplest design first. List what you cut and why. Reuse existing code.
- One end state. The old path is deleted in a phase of the same doc, not "later".
- Exact names. File paths, type names, routes, config keys, each checked against the code (or marked new).
- Tests as properties. Each phase lists the properties its tests check, with the oracle or invariant. Unit cases only where no property fits.
- No dev history. No "review round 2 said", no meeting dates. State decisions and the reason.
- Rejected options go into the doc with the reason, so the next reader does not propose them again.
