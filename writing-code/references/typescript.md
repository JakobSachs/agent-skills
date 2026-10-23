# TypeScript and frontend

## TypeScript

- `strict` and `noUncheckedIndexedAccess` on.
- Discriminated unions with a literal `kind` tag and an exhaustive `switch` ending in a `never` check.
- Branded types for IDs: `type UserId = string & { readonly __brand: "UserId" }`.
- Parse external data at the boundary with a schema library (zod or the repo's choice) and infer types from the schema. Prefer generated types from the backend's OpenAPI spec over hand-written ones.
- No `any`. `unknown` at boundaries, narrowed by parsing.
- fast-check for property tests.

## Frontend scope

- When the repo has a design team or design system, build function only: data wiring, state, routes, tests. Visual design is theirs.
- Use the design system's components and tokens. No raw colors, no hand-rolled versions of library components, no own styling choices.
- When porting a design team's mock, copy its look exactly, and style features it does not cover in the same idiom. Do not invent new design.
- Reviewers do not raise design or styling findings as blockers.

## Frontend checks

- After a change: run the app, take screenshots of every changed view (see [../../verifying/references/ui-and-live.md](../../verifying/references/ui-and-live.md)).
- Check the browser console for errors.
- A frontend mirror of backend validation must never reject what the backend accepts (see [../../testing/references/fixtures.md](../../testing/references/fixtures.md)).
