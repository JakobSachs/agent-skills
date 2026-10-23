# Explaining

## Summary before detail

Before building something non-trivial: one sentence or a one-pager of what you will build and why. The user reads it, pushes back, then says "go". Do not start building on an unconfirmed plan.

One-pager format:

```
Problem: <one or two lines, what is wrong or missing>
Idea: <the change, in behavior terms>
Not doing: <scope cut, only if the user has to decide it>
Risk: <what could break, how we check>
```

## Pick the altitude

Ask who reads it and what they decide with it.

- Architecture talk: components and flows, no function names. For "how does X work" or a design choice.
- Implementation talk: files, functions, data types. Only when the user is about to read or change the code.
- Customer or stakeholder text: about 20% of the detail you know. What changes for them, what they do. No internals.

Default to the higher altitude. The user asks when they want more depth.

## After a bug

Explain three things, in this order:

1. Root cause: what was wrong.
2. How it happened: why the existing code and tests did not catch it.
3. Fix: what changed and how it is proven.

## Diagrams

When a picture says more than prose: small (4 to 6 boxes), numbered steps, written for a fresh reader with no context. If it needs a legend, it is too big. Mermaid or Excalidraw.

## Prior art

When asked "how do others solve this", research it and report concrete findings: tool name, mechanism, trade-off. Not generic advice.

## Writing for someone else

When the user wants text to forward (to a colleague, a customer, a channel): plain text, ready to paste, in the user's voice. No markdown unless the target renders it. See [public-text.md](public-text.md).
