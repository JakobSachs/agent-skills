# Sources

In this order. Stop when the answer is proven.

1. Design records: design docs, ADRs, `CONTEXT.md`, `docs/records/` or similar. They list rejected options and the reason. Search for the mechanism you are about to propose.
2. The code on the remote default branch: `git fetch`, then search `origin/<default-branch>`. A local branch can be far behind.
3. Tests: they show the intended behavior and what is not covered.
4. Git history: `git log -S <term>` and `git blame` for why a line exists. The MR that added it often explains it.
5. Running system: logs, metrics, database state, deployed version. Merged is not deployed: compare the running image commit with the commit you are reading.
6. Prior art outside the repo: how other tools or libraries solve the same problem. Clone and read their code for mechanisms; docs alone are often out of date.
7. The internet: current library docs, issue trackers. Note the date of every source.

## Reuse before invention

Before proposing new code, search for an existing function, module or pattern that does most of it. "What can we reuse?" is part of every answer.
