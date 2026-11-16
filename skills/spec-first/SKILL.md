---
name: spec-first
description: "Turn a vague idea into a one-page spec before building - goal, scope, non-goals, acceptance checks. Use for /spec, 'I want to build...', or any fuzzy request that would be costly to redo."
---

# Spec first

A wrong build costs 10x a short spec. Produce `SPEC.md`, get a yes, then build.

## 1. Extract (don't interrogate)
From the request and any files, fill in what is already known. Ask **one batch of max 4 questions**, only for gaps that change what gets built. Offer a default for each ("A unless you say otherwise").

## 2. Write SPEC.md (max 1 page)
```
# <Name>
## Goal
One sentence. Who it's for, what changes for them.
## Done means
- [ ] 3-7 acceptance checks, each observable (can be run, opened or measured)
## In scope
## Out of scope (non-goals)
Things someone might assume are included but are not.
## Constraints
Stack, budget, deadline, brand, accessibility, devices.
## Smallest useful version
What ships first. Everything else goes under Later.
## Later
## Risks / unknowns
Each with how it will be found out cheaply.
```

## 3. Pressure-test (silently, then fix the spec)
- Can each "Done means" line fail? If not, rewrite it.
- Is anything in scope not needed for the goal? Move to Later.
- What is the riskiest assumption? Make testing it step 1.

## 4. Hand over
Show the spec. Ask: "Build this as written?" On yes, pass SPEC.md to `orchestrator` (or just build if small).

## Rules
- No implementation detail unless it is a constraint.
- No spec for tasks under ~30 minutes of work: just do them.
- If the user says "just build it", write the spec's Goal + Done means in 5 lines at the top of the work and proceed.
