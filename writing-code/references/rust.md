# Rust

## Tooling

`cargo add`, `cargo fmt`, `cargo clippy`, `cargo test`, `cargo doc`. Clippy clean before claiming done.

## Style (clippy rules to follow by default)

- Collapse nested `if` statements (`collapsible_if`).
- Inline format arguments: `format!("{name}")`, not `format!("{}", name)` (`uninlined_format_args`).
- Method references over closures: `.map(String::from)`, not `.map(|s| String::from(s))` (`redundant_closure_for_method_calls`).

## Types

- Newtype structs for IDs and constrained values; no bare `String` or `i64` for domain concepts in public APIs.
- One `enum` variant per workflow state.
- Private fields with `TryFrom` or constructor functions that check invariants.
- Error enums with `thiserror`; `miette` or `anyhow` at the application edge.

## Tests

- proptest for properties.
- Compare whole values (`assert_eq!(actual, expected)`) rather than field by field.
