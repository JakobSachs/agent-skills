# Structure

## Functional core, imperative shell

- Core: pure functions over values. No I/O, no clock, no randomness, no globals. Easy to property-test.
- Shell: reads inputs, calls the core, writes outputs. Thin, few branches, tested by a small number of integration tests.
- Pass time, IDs and randomness into the core as arguments.

## Interfaces

- Declare an interface (Protocol, trait, abstract class) in the package that implements it.
- Only a core package may declare an interface for plugins it consumes.
- Between plugins or sibling modules, import only their public module (`<module>.public` or the package root), never internals. Use the repo's import linter if it has one.

## Errors

- Fail at the boundary with a clear message. Do not swallow errors to keep going.
- Catch the specific exception you can handle. Let the rest propagate.
- Every retry has a bound and a backoff. Every network call has a timeout.
- Expected failures are values; exceptions are for bugs and the unexpected.

## Configuration

- Every constant with a non-obvious value says why it has that value (one line).
- Config keys are typed and validated at startup, not read ad hoc deep in the code.

## Contracts

When you change an API route, response model, event or config schema: update or regenerate every consumer (OpenAPI spec, client types, docs) in the same change. Frameworks can silently drop undeclared response fields.

## Multi-tenant data

In a multi-tenant repo, every query and every table respects tenant isolation (row-level security or the repo's equivalent). A new table without it is a bug.
