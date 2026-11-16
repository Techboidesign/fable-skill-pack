---
name: orchestrator
description: "Plan, route and verify multi-step work on a budget - cheapest model per step, independent double-check, handoff file. Use for /orchestrator or big multi-part tasks."
---

# Orchestrator

Goal: **finished, verified output for the least compute.** Think once, delegate cheap, verify independently, write state to disk.

## 0. Triage (always first, 1 line)
- **S** - single fact / small edit / <3 steps -> do it directly. No plan, no agents, no task list. STOP reading this skill.
- **M** - 3-8 steps, one deliverable -> plan + do inline + self-verify.
- **L** - many parts, research fan-out, or hard to redo -> full pipeline below.

State it: `Triage: M - <why>`.

## 1. Clarify only if expensive + ambiguous
One batch of max 3 questions, only when the task is L **and** a wrong guess costs a redo. Otherwise take the most reasonable reading, state it in one line, go.

## 2. Plan (M and L)
Write `PLAN.md`:
```
# Goal
<one sentence, definition of done>
# Steps
1. <step> | owner: self|haiku|sonnet | input -> output file
# Checks
- <how each output will be verified>
# Assumptions / open questions
```
Mirror steps in the task list. Last task is always **Verify**.

## 3. Route each step to the cheapest capable worker
| Work | Owner |
|---|---|
| File search, grep, listing, extraction, reformatting, bulk renames | **haiku** (or an Explore agent) |
| Web lookups, summarising sources, boilerplate, routine code | **sonnet** |
| Architecture, ambiguous judgment, tricky debugging, final synthesis | **self** |

Rules:
- Delegate only when the step is **self-contained** and its result fits in a short summary or a file. Otherwise do it inline - a spawn re-derives context and can cost more than it saves.
- Run independent subagents **in parallel**, in one message.
- Write every subagent prompt with the `delegation-brief` shape: goal, exact inputs, output path, format, "return <=150 words + file path", "do not spawn further agents".
- Bulk results go to files; only summaries come back into context.
- No subagent tool available? Do every step yourself, same triage and checks.

## 4. Token hygiene
- Grep or read with offset/limit first; never dump whole large files.
- Batch independent tool calls in one turn.
- Don't re-read files you just wrote. Don't re-summarise tool results.
- Compute numbers in code, never in prose.
- Load a format skill (docx/xlsx/pptx) only after the material is gathered.

## 5. Verify (mandatory for M and L)
- **M:** check against `# Checks`: run the code/tests, recompute arithmetic, open the produced file, re-fetch cited URLs.
- **L or high-stakes:** spawn ONE fresh verifier that has not seen the work being made; give it the `verify-pass` skill, the goal, the deliverable path, the requirements list. It reports, it does not fix.
- Fix BLOCKER/MAJOR, re-verify only what changed. **Max 2 fix loops**; then report the gap honestly.

## 6. Handoff (L, or anything spanning sessions)
Write `HANDOFF.md` using the `session-handoff` format. A future session starts by reading it, not by re-deriving.

## 7. Report
- Verdict: **DONE / PARTIAL / BLOCKED**.
- The deliverable (file or link).
- Unverified items, flagged.
- One concrete next step. No recap of steps.

## Anti-patterns
- Agents for S tasks.
- Plans that wait for approval when the task is clear and cheap to redo.
- Agents verifying their own work.
- Pasting full subagent output into context.
- More than 2 verify/fix loops.
