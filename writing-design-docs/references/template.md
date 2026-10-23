# Design doc template

Drop sections that do not apply. Keep the order.

```markdown
# <Feature> design

## Summary
<3 to 5 lines: the problem, the change, the result for the user.>

## Done when
- <observable behavior 1, checkable by a test or a live check>
- <observable behavior 2>

## Context
<What exists today and why it is not enough. Link the investigation findings,
records and code with path:line.>

## Design
<Components and data flow. A small diagram if it helps (4 to 6 boxes).
Core types first: states, invariants, what is illegal to represent.>

### Contracts
| Surface | Change | Consumers to update |
|---|---|---|
| `POST /api/v1/x` | new field `y` | frontend types, OpenAPI |

### Decisions
- <decision>: <reason>. Rejected: <option> because <reason>.

## Phases

### Phase 1: <name>
Goal: <what works after this phase>
Files: <every path created or changed>
Steps: <short list; enough that an implementer with no context can build it>
Tests:
- property: <invariant or oracle>
- unit (why no property fits): <case>
Done when: <command or check>

### Phase 2: <name>
...

## Rollout
<Migration order, flags, what happens to running work during deploy,
how to roll back, how to smoke test after deploy.>

## Open questions
- <question> (owner: <who decides>)
```

## Level of detail

- Design sections: the what and the why, at architecture level.
- Phase sections: the how, at file and type level. Exact paths and names, short code only where a structure is hard to say in words (a type, a schema, a route signature). Not full implementations.
