---
name: verify-pass
description: "Independent skeptical double-check of a finished deliverable (doc, code, research, numbers). Use for /verify, 'double check this', or before shipping anything high-stakes."
---

# Verify pass

Assume the deliverable is wrong until shown otherwise. Report, don't rewrite.

## 1. Collect the contract
List in 3-8 bullets what the deliverable was supposed to do (from the request, SPEC.md, PLAN.md or the user). If unclear, state the assumed contract in one line.

## 2. Check by type (only the rows that apply)
| Type | Check |
|---|---|
| Facts / research | Re-fetch each cited URL; the claim must appear on the page. Specific uncited claims = flag. |
| Numbers | Recompute in code. Units, totals, percentages, dates. |
| Code | Run it / run tests / lint. Edge cases: empty input, nulls, errors, auth. |
| Docs / copy | Requirements coverage, contradictions, consistent names/dates, working links. |
| Design / UI | Open or render it; spacing, contrast, overflow, breakpoints. |
| Files | Open the actual output; not empty/corrupt, matches the format asked. |

## 3. Output
```
VERDICT: PASS | PASS WITH FIXES | FAIL
| # | Issue | Severity | Evidence | Fix |
```
Severity: BLOCKER (wrong/broken), MAJOR (missing requirement, misleading), MINOR (polish).
End with **Unverified:** what could not be checked, and why.

## Rules
- Evidence for every issue: line, cell, URL or command output. No evidence -> not an issue.
- Cap MINOR at 5. No padding.
- Don't fix unless asked; then BLOCKER -> MAJOR -> MINOR and re-run only the affected checks.
- "I looked and it seems fine" is not a check. Name what was run or opened.
