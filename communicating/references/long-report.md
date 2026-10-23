# Long report

For investigations, incident analyses, research answers, audits: anything over about 15 lines. The reader must be able to stop after the first block and still act correctly, and must be able to check every claim without re-doing the work.

## Template

```
<Answer or verdict, one line.>
Next: <one action, and who does it>

## Findings
| # | Claim | Evidence | Basis |
|---|---|---|---|
| 1 | <one fact> | <verbatim output, path:line, or URL + date> | measured |
| 2 | <one fact> | <path:line> | read |
| 3 | <one fact> | <which findings it follows from> | inferred |

## Cause            (bugs only)
Root cause: <one line>
How it got past: <why code review and tests missed it>

## Options          (decisions only; 2 to 4, recommendation first)
1. <option> (recommended): <trade-off, one line>
2. <option>: <trade-off, one line>

## Not checked
- <what is still open, and what it would take to check it>
```

Drop any section that does not apply. Keep the order.

## Basis labels

Mark every claim with where it comes from. The reader decides how much to trust each row.

- `measured`: tool output you ran in this session (command, query, log). Quote the output verbatim.
- `read`: stated in code, docs or a record. Cite `path:line` or a URL with its date.
- `inferred`: your reasoning from other findings. List the rows it follows from.
- `assumed`: not checked. Prefer checking it instead. If you can't, it goes under "Not checked" too.

Never present an inferred or assumed claim as if it were measured.

## Evidence rules

- Verbatim quotes and tool output are the main content. Your summary is one line next to them, not a paragraph over them.
- Numbers: show where they came from (query, file, calculation) so the reader can re-run them.
- Link to exact places: `file.py:88`, a pipeline job URL, a log line with timestamp.

## Tone

State findings without first person narration ("I looked at..."), apologies or enthusiasm. A correction is a finding too: "Row 2 of the earlier report was wrong: the cap is 2 GiB, not 1 GiB (`values.yaml:41`)."

## Length

The first block (verdict + next) fits on one line each. The findings table: 3 to 8 rows. More rows: keep the 8 that change the decision, move the rest to a file and link it.
