# Design review

Questions for each design doc round:

1. Problem: is the problem confirmed and stated in terms of behavior? Is the root cause found, or only the symptom?
2. Prior decisions: does the design repeat an option that design records or `CONTEXT.md` already rejected? Search for it.
3. Prior art: did the doc check how existing code or other tools solve this? Is there something to reuse?
4. Simplest version: what is the smallest design that solves the problem? List each part that could be cut.
5. One path: does the end state leave two ways of doing one thing? Is the old path deleted in the same change?
6. Phases: few and big (about 3), each a vertical slice that works and is tested on its own? No phase "add tests later".
7. Contracts: every changed API, schema, event and config listed, with its consumers?
8. Rollout: migration order, rollback, what happens to in-flight work during deploy?
9. Plan quality: could an implementer with no context build from this doc alone? Exact file paths, types, and test properties per phase?
10. Open questions: listed explicitly, not hidden in prose?

A third reviewer option, when the design is contested: ask one reviewer "is there a better third way that neither option considers?"
