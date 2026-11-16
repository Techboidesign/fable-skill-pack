---
name: delegation-brief
description: "Write a tight, self-contained prompt for a subagent or cheaper model so it succeeds first try. Use for /brief, 'write a prompt for...', or before spawning any agent."
---

# Delegation brief

The receiver knows **nothing** about this conversation. A brief that needs context it doesn't carry will fail and cost twice.

## Template
```
ROLE: <one line, only if it changes behaviour>
GOAL: <what done looks like, one sentence>
WHY: <one line of purpose, so it can make sensible trade-offs>
INPUTS: <exact paths / URLs / pasted data>
DO:
1. ...
2. ...
DON'T: <scope fence: files not to touch, things not to decide, "do not spawn agents">
OUTPUT: <file path + format, with a tiny example of the shape>
RETURN: <=150 words: what was done, where it is, anything uncertain
IF STUCK: stop and report what blocked you; do not guess
```

## Checklist before sending
- Could a smart stranger do this with only the brief? If not, add the missing fact.
- Exactly **one** deliverable. Two deliverables = two briefs.
- Output shape shown by example, not described.
- Success is checkable (a test passes, a file exists with N rows, each claim has a URL).
- No "be thorough / be careful" filler. Say what to check instead.

## Sizing the receiver
| Task | Model |
|---|---|
| Mechanical: find, extract, reformat, rename | smallest |
| Read-and-summarise, routine code, lookups | mid |
| Judgment, design, ambiguity | don't delegate; do it yourself |

## For reuse
If the same brief gets written twice, save it as a skill or a file under `prompts/`.
