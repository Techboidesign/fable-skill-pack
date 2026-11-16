---
name: debug-loop
description: "Systematic debugging - reproduce, isolate, one hypothesis at a time, fix the cause, prove it. Use for /debug, 'it's broken', failing builds, or after two failed fix attempts."
---

# Debug loop

No fix without a reproduction. No second guess without new evidence.

## 1. Reproduce
- Get the exact error text, the command/action, and what was expected.
- Make it fail on demand. Can't reproduce -> gather more (logs, console, network, versions), don't patch.

## 2. Shrink
- What changed last? (`git log -5`, `git diff`, recent deploys, dependency bumps.)
- Halve the search space: comment out, bisect commits, minimal test case.

## 3. Hypothesise - one at a time
Write: `Hypothesis: <cause>. If true, <observation> will show <X>.`
Run the **cheapest** observation that can prove it false (a log line, a print, curl, devtools). Read the actual output.

## 4. Fix the cause
- Smallest change at the root, not a guard around the symptom.
- If the fix is a workaround, label it as one and say what the real fix is.

## 5. Prove
- Re-run the reproduction: it passes.
- Run the nearby tests/build: nothing else broke.
- Add a test or check if the project has tests.

## 6. Report
```
Cause: <one line>
Fix: <file:line, what changed>
Proof: <command + result>
Not checked: <...>
```

## Stop rules
- **Two failed fixes -> stop editing.** Go back to step 2 and add logging.
- Never change several things at once.
- Never claim fixed without running step 5.
- Common fast checks first: typo/case in path, stale cache/build, wrong env var, wrong branch, version mismatch, missing await, CSS specificity/overflow.
