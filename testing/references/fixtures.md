# Fixtures, mocks and boundaries

## Ground fixtures in the producer

A consumer test that feeds a state no producer ever emits passes and proves nothing: the branch is unreachable in production, and the states producers emit are untested.

- Record real producer output (API responses, events, stream frames) and replay it, or
- Generate inputs by running the real producer code, not from the published schema. A schema can declare states that nobody emits.

## Symmetric wrongness

A test that only checks two views agree (client vs server, before vs after reload, tab A vs tab B) passes when both are wrong in the same way. It cannot detect an error both sides share. Always assert at least one side against the expected value.

Ask of every cross-boundary test: "What would this test say if both sides had the same bug?"

## Mocks

- Mock only at boundaries you do not own or cannot run: external APIs, clocks, randomness, the network.
- Prefer real dependencies in tests where they are cheap: an in-memory or containerized database, a local server.
- Never assert on mock internals ("was called with") when you can assert on the outcome.
- A mock must behave like the real thing for the cases you test. Base it on recorded real responses.

## Two implementations of one rule

When a frontend mirrors a backend validator (or any two implementations of one rule):

- Run one shared corpus (100+ inputs, including unicode, escapes, edge literals) through both real implementations and count disagreements.
- Classify: a false reject (mirror rejects, source accepts) silently drops valid input and must be zero. A false accept (mirror accepts, source rejects with a visible error) is acceptable and goes into one documented list.
- Prefer deleting a mirror check over adding one. If the gap list keeps growing, the fix is a validate or dry-run route on the source, not more mirror code.
- Watch for language differences: string length (code points vs UTF-16 units), trimming (BOM), YAML 1.1 vs 1.2 booleans.

## Isolation

- Each test sets up its own data. No order dependence.
- Unique names per test (tenant, team, file) so parallel runs do not collide.
- Clean up what you create, or use a fresh schema or temp dir per test.
