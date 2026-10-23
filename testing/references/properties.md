# Properties

## Catalog

Aim for the strongest property that applies. Weakest to strongest: no exception, type preserved, invariant, idempotence, roundtrip, oracle.

| Property | Form | Use for |
|---|---|---|
| Roundtrip | `decode(encode(x)) == x` | serialization, conversion pairs |
| Idempotence | `f(f(x)) == f(x)` | normalize, format, dedupe, migrations |
| Invariant | a fact holds before and after | any transformation, state machines |
| Oracle / differential | `new(x) == reference(x)` | refactors (old vs new), optimizations |
| Easy to verify | `is_sorted(sort(x))` | results that are hard to compute, easy to check |
| Commutativity | `f(a, b) == f(b, a)` | merges, set operations |
| Model-based | real system and a simple model agree after any sequence of operations | stateful APIs, stores, queues |

For a refactor, the differential test against the old code is the default. Keep the old function in the test until the refactor is merged, or record its outputs.

## Strategies

- Build constraints into the strategy; do not filter with `assume()`. High rejection rates make tests vacuous.
- Bound sizes (`max_size`) so tests stay fast.
- Realistic values: generate what production sends, including unicode, emoji, empty strings, very long values, boundary numbers.
- Define shared strategies once per domain type and reuse them.
- Add explicit `@example` cases for known edge cases and every past bug.

## Settings

Fast locally (few examples), more in CI. Do not raise deadlines to hide slow code.

## Quality check

- Not tautological: the expected value is not computed the same way as the actual value.
- Strong: checks a property, not only "no crash".
- Not vacuous: most generated inputs reach the assertion.
- Multiple properties per function where they exist (length, order, content).

## When a property does not fit

UI layout, a single integration path, a fixed legacy sample, a structural check (two lists of fields stay in sync). Write a unit test and say why.
