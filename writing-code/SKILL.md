---
name: writing-code
description: Use when writing or changing source code in Python, Rust, TypeScript or frontend apps. Types first, pure core with a thin I/O shell, reuse, one path per job. Comments: writing-comments. Tests: testing.
---

# Writing code

Every line must earn its keep. Prefer readability over cleverness. Well-designed, 10 lines can do the work of 1000.

## Core rules

1. Match the surrounding code: naming, idiom, comment density, error handling. The repo's conventions beat these rules.
2. Types first. Design the core types before the functions. If a function is hard to name or type, the model is wrong. See [references/types.md](references/types.md).
3. Pure core, thin shell. Business logic in pure functions; I/O, time, randomness and global state at the edges. See [references/structure.md](references/structure.md).
4. Reuse before writing. Search for an existing helper, the standard library, then a dependency already in the project. A new dependency needs a reason.
5. One way to do one thing. When you replace a path, delete the old one in the same change.
6. No speculative code. No options, hooks or abstractions without a current user.
7. Never mix behavior changes with formatting changes in one commit.
8. Run the repo's formatter, linter and type checker on what you changed before claiming done.

## Language references

| Language | Read |
|---|---|
| Python | [references/python.md](references/python.md) |
| Rust | [references/rust.md](references/rust.md) |
| TypeScript, frontend | [references/typescript.md](references/typescript.md) |

## Red flags

- A helper used once, with a name longer than its body.
- `status: str`, or a bool plus an optional field that can contradict each other.
- `if x is None` checks deep in the core for values validated at the boundary.
- A comment that explains what the next line does.
- Copy-pasted blocks with small differences.
- Catching all exceptions to "be safe".
