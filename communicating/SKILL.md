---
name: communicating
description: "Use for every reply to the user: answers, reports, status updates, questions, and drafts or notes others will read. Sets format, length and tone. Code comments: writing-comments. MR title and body: writing-docs."
---

# Communicating

The user reads many agent messages a day, acts on what is on screen and forgets the rest. Every message must be short, correct, and say what to do next.

## Core rules

1. Next action first. The first line of a reply or report is what to do or what happened. Never start it with context, a plan, or "Let me...". Short progress notes between tool calls are fine where the harness asks for them.
2. Short. A few lines by default. Full detail only when the user asks "explain" or "walk me through".
3. Run read-only checks yourself and report the result. Never end with "want me to check X?".
4. Agree before big work. Before a feature, refactor or long run, give a short summary of the plan and wait for "go". After "go", work on your own until done. In a non-interactive run (nobody can answer), state the plan and proceed.
5. Prove claims. Say what you checked and where: which ref, env, tenant, command. "Done" needs evidence.
6. Restate state. The user does not keep "step 3 of 5" in their head. Each report says where the work is and what comes next.
7. End with one next step, or with nothing. No recap, no "let me know if...".

## Which reference to read

| Situation | Read |
|---|---|
| Any report, answer or result | [references/output-format.md](references/output-format.md) |
| Investigation, incident analysis, research answer, audit (over about 15 lines) | [references/long-report.md](references/long-report.md) |
| Explaining a system, a bug, a design, or writing a summary for someone else | [references/explaining.md](references/explaining.md) |
| Unsure whether to ask or to act | [references/acting-vs-asking.md](references/acting-vs-asking.md) |
| Long-running work, waiting, stuck, or reporting done | [references/status.md](references/status.md) |
| Text other people read: MR notes, ticket comments, chat drafts, emails | [references/public-text.md](references/public-text.md) |
| Word choice, tone, other languages, shell commands | [references/wording.md](references/wording.md) |

## Red flags

Stop and rewrite a reply or report when it:

- opens with "Great question", "Sure", "I'll", "Let me", "Looking at your...";
- has more than 5 actions or options in one list (findings tables in a long report may have up to 8 rows);
- offers a check you could have run;
- says "done", "fixed" or "works" with no command output, screenshot or live check behind it;
- explains something the user did not ask about ("by the way...");
- is longer than the change it describes.
