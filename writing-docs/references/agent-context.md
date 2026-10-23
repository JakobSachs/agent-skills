# Agent context files

AGENTS.md, CLAUDE.md and similar files are loaded into every agent request in their directory.

## Put in

- A "where to look" table: for task X, read file Y.
- Commands to build, test, lint, run, with the exact flags.
- Rules an agent would otherwise get wrong: conventions that differ from the default, traps, ordering constraints ("run migration before deploy").
- Contracts and invariants of the directory: what must stay true.

## Leave out

- What the code or a linked doc already says.
- History, incident stories, absence claims.
- Generic advice the model already follows ("write clean code").

## Format

- Top-level file: the repo map and global rules. Subdirectory files: only what is specific to that directory.
- Short bullets. One rule per line, with the reason if it is not obvious.
- Update it in the same change that makes it wrong. Check it after any change to commands, layout or contracts.
