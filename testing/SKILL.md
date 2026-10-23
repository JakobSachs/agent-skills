---
name: testing
description: Use when writing, changing or reviewing tests, or fixing a known test failure (unknown cause: investigating). Property-based first, behavior over implementation, fixtures from the producer, flaky tests fixed on sight.
---

# Testing

## Core rules

1. Behavior, not implementation. Test through the public interface. A refactor that keeps behavior must keep the tests green without edits.
2. Properties first. Hypothesis (Python), proptest (Rust), fast-check (TypeScript). A unit test only where no property fits: a fixed legacy sample, a structural check, one wiring path. Say why in the test name or a one-line comment. See [references/properties.md](references/properties.md).
3. Test first for bugs. Write the test that fails on the bug, watch it fail, then fix. A test you never saw fail proves nothing.
4. Fixtures from the real producer. Feed consumers what the real producer sends, not a state you wrote for the test. See [references/fixtures.md](references/fixtures.md).
5. Every new branch covered, including error paths. Check coverage on the lines you changed.
6. Flaky = bug. Fix it when you see it. See [references/flaky.md](references/flaky.md).

## Which reference to read

| Situation | Read |
|---|---|
| Picking properties, writing strategies | [references/properties.md](references/properties.md) |
| Fixtures, mocks, cross-boundary tests, parity between two implementations | [references/fixtures.md](references/fixtures.md) |
| A test fails sometimes, timing, waits, CI-only failures | [references/flaky.md](references/flaky.md) |

## Red flags

- The test reimplements the function under test to compute the expected value.
- The assertion only checks "no exception".
- A mock asserts that a mock was called.
- Two views are compared with each other (tab A vs tab B, before vs after reload) and nothing checks either against the truth.
- A fixed `sleep()` instead of waiting on a condition.
- A test that passes on the old code too.
