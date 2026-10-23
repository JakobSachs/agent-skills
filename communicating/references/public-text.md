# Public text

Anything other people read: MR titles, descriptions and notes, commit messages, ticket comments, chat drafts, emails. These are permanent and are read by colleagues, other teams and customers.

For MR titles and descriptions themselves, see the `writing-docs` skill. This file covers voice and safety for all public text.

## Safety checks before posting

- No group mentions. `@group` tags a whole organization. Write package scopes and groups without the leading `@` (`acme/core-lib`, not `@acme/core-lib`). The title never protects it; code spans do not reliably either.
- No escalation talk. Never "as agreed with your manager", never name who overruled whom. Write "as agreed on 2026-09-17".
- No names of people not on the thread.
- No internal or customer data: secrets, tokens, internal URLs with credentials, customer content.
- No AI attribution lines unless the repo requires them.

Before posting, scan the text for `@`, "manager", "escalat", "overrul", and personal names.

## Voice

- Write as the user would: plain, direct, short. No markdown in chat or email unless it renders there.
- Facts only. Drop estimates, open questions and options the user did not ask to include.
- Match the audience altitude (see [explaining.md](explaining.md)).
- Drafts to other teams' repos or channels: show the user first.

## Content

- The why comes from the intent: the ticket, the commit, the user. Never invent a motivation.
- Incident stories (which team, what date, what an agent did) belong in the MR description, never in code or docs.
