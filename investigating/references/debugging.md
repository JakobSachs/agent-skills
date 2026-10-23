# Debugging

## Before forming a hypothesis

- Reproduce reliably. If it is intermittent, find the condition (timing, order, data, load) before going further.
- Check what changed: recent commits, deploys, config, dependency bumps, data. `git log`, the deploy history, the running image version.
- Find a working example of the same thing in the codebase and list every difference.

## Hypothesis loop

1. Write the hypothesis in one sentence: "X fails because Y."
2. State the check that would prove it wrong.
3. Run the check. Change one variable only.
4. Wrong: discard it fully. Do not stack a second fix on a failed first fix.
5. Right: write the failing test that shows it, before the fix.

## Multi-component systems

Before guessing which layer is broken, add evidence at each boundary: log or inspect what enters and leaves each component (client, gateway, service, database). The layer where good input becomes bad output is the one to fix.

## Fix where the fault enters

Trace bad data back to where it enters. A fix where the symptom shows up is often a patch over a cause one or two layers up. Prefer the fix at the source; add a check at the boundary only when the source cannot be trusted.

## Red flags

- "Quick fix for now, investigate later."
- "It's probably X, let me change that."
- A fix that makes the symptom go away but you cannot explain why.
- Retrying a CI job until it is green.
