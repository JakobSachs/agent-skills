# Docs

## Structure

- Start with what the thing is and what the reader can do with it, in one or two lines.
- Then how to use it: commands, examples, config. Copy-pastable.
- Then reference detail. Tables for options and flags.
- Headers a reader can skim. Long files (over 100 lines) get a contents list at the top.

## Style

- Plain technical English, short sentences, active voice (see [../../communicating/references/wording.md](../../communicating/references/wording.md)).
- Present tense, describing current behavior.
- Concrete examples over abstract description.
- One term per concept across all docs. Business terms stay in their original language.
- No "simply", "just", "easy". No emojis.

## What to leave out

- Absence claims ("there is no pre-commit", "the old service is removed"). Keep a negative only when a reader would otherwise get it wrong ("no `aud` check").
- Change history and dates of decisions (they go into the MR and ADRs).
- Time estimates, open questions and options the user did not ask to include.
- Anything the code says better (function lists, file trees that drift).

## Customer and stakeholder docs

About a fifth of what you know. What changes for them, what they do, who to ask. No internal names, no architecture. Write natively in the target language.

## Truth check

Every command in a doc must run as written. Every path must exist. Check before committing.
