# Types

## Make illegal states unrepresentable

- Tagged unions over booleans plus optional fields. Never `is_active: bool` with `deleted_at: datetime | None` when the pair can contradict.
- No `status: str`. Use an enum or a union of literal states.
- Two fields that are only valid together become one type.
- Workflow states as separate types (`Draft`, `Paid`, `Shipped`); transitions are functions between them. Fields that exist only in some states are defined only on those types.

## Parse, don't validate

- Validate once at the boundary (API handler, CLI, file load) and return a refined type.
- The core takes the refined type and never re-checks.
- A parse failure is a value (error result), not a docstring note.

## Newtypes, pragmatically

- Identifiers and constrained values get their own type: `UserId`, `TenantId`, `Money`, `Email`.
- Free text (names, comments) stays a plain string.
- Rule: if the value has invariants, a fixed vocabulary, or can be confused with another argument of the same base type, give it a type.

## Signatures state failure

- Expected failure is visible in the return type (`Result`, `X | None`), not a hidden exception.
- Optional input only when absence means something. Say what `None` means in output; if "not found" and "error" differ, they need different representations.

## Separate representations

Domain types, persistence rows and wire DTOs are separate types with explicit mapping at the boundaries. Database nullability and JSON structure do not leak into the domain model.

## Smart constructors

Construction is the only place invariants are checked. If an instance exists, its invariants hold. Expose `parse` / `try_from` returning success or error; make raw construction awkward.
