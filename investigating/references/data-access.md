# Data access

## Secrets

- Never print environment variables, connection strings, tokens or keys. Not even names with `env | cut`: multi-line values leak fragments.
- Run queries through the application's own config object or a client that reads credentials itself. Never echo the DSN.
- Do not write credential files to disk (`.pgpass`, token files). If unavoidable, delete them in the same step.
- Put these rules into every subagent brief that touches a cluster or database.

## Customer data

- Some data is restricted to counts and metadata. If the user or the repo says so for a tenant or dataset, read only aggregates (counts, tool names, timestamps), never content.
- Never copy customer content into reports, MRs, tickets or memory.

## Writes

Read-only by default. Database UPDATE or DELETE, cluster apply or patch, secret edits: ask first, and state what changes and how to roll back.

## Replicas and caches

A read replica or cache can be stale. When numbers look wrong, check against the primary before drawing conclusions.
