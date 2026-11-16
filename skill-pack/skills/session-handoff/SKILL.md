---
name: session-handoff
description: "Compress the current session into a HANDOFF.md a fresh session or cheaper model can resume from. Use for /handoff, 'wrap up', long sessions, or before switching model."
---

# Session handoff

Long context is the most expensive thing in a session. Write state down, start fresh.

## When
- User says wrap up / handoff / continue later.
- The conversation is long and work remains.
- Before switching to a cheaper model for the remaining steps.

## Write HANDOFF.md
```
# <Project> - handoff <date>
## Status: DONE | PARTIAL | BLOCKED
## Goal
One sentence + link/path to SPEC.md or PLAN.md if present.
## Next action
The single next step, concrete enough to start without thinking.
## Remaining
Ordered list. Mark which steps a cheaper model can do.
## Done
What exists and works, with file paths.
## Decisions + why
Each decision in one line with its reason, so it is not re-argued.
## Dead ends
What was tried and failed, and why. (Stops the next session repeating it.)
## Files
path - what it is
## Unverified / risks
## How to resume
Exact prompt to paste into a new session.
```

## Rules
- Facts only from this session: commands run, files written, things the user said. No guesses presented as state.
- Paths and commands exact, copy-pasteable.
- Under ~60 lines. If it is longer, it is a transcript, not a handoff.
- "How to resume" must work cold: e.g. `Read HANDOFF.md and PLAN.md, then do the Next action. Do not redo anything under Done.`
- Save next to the work (repo root or project folder) and give the user the file.
