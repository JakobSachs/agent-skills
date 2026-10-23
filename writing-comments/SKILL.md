---
name: writing-comments
description: Use when adding code comments or docstrings, and for the comment pass over edited files before review. Keeps intent, invariants and contracts; removes history. READMEs: writing-docs. Design docs: writing-design-docs.
---

# Writing comments

## Principles

1. Explain what the code cannot say: intent, invariants, assumptions, contracts, failure behavior. Never restate syntax.
2. Why over what. Why it exists or is built this way, not what each line does.
3. Scale with importance. Obvious helpers need nothing. Central abstractions, subtle invariants and costly failure points get more, and even then rarely more than a short paragraph.
4. Durable facts, no history. No tickets, phases, review rounds, incident stories, team names or dates. The incident goes into the MR description; the comment states the constraint it revealed.
5. Codebase vocabulary or plain technical words. No figurative terms ("load-bearing", "seam"), no em dashes.
6. Contracts, not signatures. Guarantees, ordering, ownership, lifecycle, side effects. Do not repeat parameter names and types.
7. Next to the subject. A field's meaning goes on the field. A method's contract on the method. An internal detail on the block that does it. The class docstring says only why the type exists and which invariants span members.
8. Each fact once. Explain a mechanism where it is implemented; elsewhere refer to it (`see RetryPolicy`).
9. Section comments only where the code has distinct phases, not as decoration.

Examples: [references/examples.md](references/examples.md).

## Comment pass

Before the review gate, go over every file edited on the branch. If the harness has subagents, split the files by area. For each comment ask:

- What lasting understanding does this give that the code does not?
- Is the length proportional to the concept's importance?
- Is this the place where a reader of that line will find it?
- Would it survive adding one more field or method unchanged?
- Does it mention a ticket, a review, a phase or an incident? Remove that part.

Delete comments that fail. Add a one-line comment where a non-obvious invariant has none.
