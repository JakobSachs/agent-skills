# Review dimensions

Pick by artifact. Small fix: correctness and tests. Feature or refactor: all five. MR description: one reviewer, see the last section. Design doc: see design-review.md. Neither gets a commit or test run per round.

## Correctness

- Does the change do what the goal says, for all inputs, not only the happy path?
- Error paths, retries, timeouts, concurrency, partial failure, empty and huge inputs.
- Multi-tenant or permission boundaries: can one tenant or user see or change another's data?
- Migrations: order, rollback, old code running against the new schema during a rollout.

## Tests

- Would each new test fail without the change? Check by reverting the fix mentally or for real.
- Do tests check behavior, or do they mirror the implementation?
- Do fixtures match what the real producer sends, or did the test invent a state no producer emits?
- A test that only compares two views (before vs after, client vs server) passes when both are wrong in the same way.
- Coverage of every new branch, including the unhappy ones.

## Contracts and coupling

- Changed public interface: API routes, response formats, events, config keys, CLI flags. Are all consumers updated (generated clients, frontend types, docs)?
- Hidden coupling: does the change rely on an ordering, a naming convention or a side effect that nothing enforces?
- Was an option chosen that design records already rejected?

## Simplicity

- Every line earns its keep. Can a part be deleted?
- Two ways of doing one thing left behind (old path not removed)?
- New code where existing code could be reused?
- Abstraction with one user.

## Docs and comments

- Comments state invariants and intent, not history or mechanics.
- Docs updated where behavior changed. No claims that something is absent.
- MR description matches what the diff does.

## MR description

- Does it follow [../../writing-docs/references/commits-and-mrs.md](../../writing-docs/references/commits-and-mrs.md): goal first, decisions stated, no diff restated?
- Does it pass [../../communicating/references/public-text.md](../../communicating/references/public-text.md): no group mentions, no names, no secrets?
- Does every claim in it match the diff?
