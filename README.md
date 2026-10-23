# agent-skills

Skills for coding agents: how to communicate, investigate, design, build, test, review and ship. Open Agent Skills format (`SKILL.md` with `name` and `description`, plus `references/`). The skills refer to capabilities ("if the harness can spawn subagents"), never harness-specific tools.

## Skills

| Skill | Fires when |
|---|---|
| `communicating` | every reply (always on) |
| `investigating` | a bug, an unknown, a research question |
| `developing-features` | a code change starts; runs it to live |
| `writing-design-docs` | a feature or refactor needs a design; the doc is also the plan |
| `reviewing-changes` | before any human sees a change; the review gate |
| `testing` | writing or fixing tests |
| `verifying` | before any "done", "fixed" or "live" claim |
| `writing-code` | writing or changing code |
| `writing-comments` | comments, and the comment pass before review |
| `writing-docs` | docs, agent context files, MR text |

Flow: `investigating`, one-pager, `writing-design-docs`, build (`writing-code`, `testing`, `verifying`), `writing-comments`, `reviewing-changes`, MR, live. `developing-features` has the checklist.

Skills link to each other with relative paths (`../communicating/...`), so install all of them side by side in one directory. Where a harness installs skills one by one (ChatGPT), cross-skill links do not resolve; each linking line also states the rule in short.

## Install

| Harness | User scope | Repo scope | Global instructions file |
|---|---|---|---|
| Claude Code | `~/.claude/skills/` | `.claude/skills/` | `~/.claude/CLAUDE.md` |
| Codex | `~/.agents/skills/` | `.agents/skills/` | `~/.codex/AGENTS.md` |
| Others | see the harness docs | | |

Remove any existing skill with the same name first (for example an older `writing-comments`). Then, in sh or bash, from this directory:

```sh
mkdir -p ~/.claude/skills ~/.agents/skills
for d in */; do ln -s "$PWD/${d%/}" ~/.claude/skills/; done   # Claude Code
for d in */; do ln -s "$PWD/${d%/}" ~/.agents/skills/; done   # Codex
```

If one of the two directories is a symlink to the other, run only one loop.

### Always-on `communicating`

Skills load when their description matches. `communicating` must apply to every reply, so add this line to the global instructions file from the table, with the path for your harness:

```
Before every reply, follow ~/.claude/skills/communicating/SKILL.md (Codex: ~/.agents/skills/communicating/SKILL.md).
```

Claude Code, stronger: a `SessionStart` hook that prints `communicating/SKILL.md` into the context.

### Project facts

These skills describe ways of working. Environments, CI quirks, deploy order and repo traps belong in the repo's `AGENTS.md` / `CLAUDE.md` and its docs.

## Testing a change to a skill

1. Pick 3 tasks from your work that the skill should change (one per main rule).
2. Run each on a fresh agent without the skill; note what goes wrong.
3. Run again with the skill; compare.
4. Fix the wording where the agent missed or broke a rule. Test with every model you use.
