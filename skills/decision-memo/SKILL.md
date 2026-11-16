---
name: decision-memo
description: "Structure a choice between options - criteria, weighted table, risks, recommendation, what would change it. Use for /decide, 'should I...', 'A or B', tool/stack/offer choices."
---

# Decision memo

## 1. Pin the decision
- **Decision:** one sentence, phrased as a choice.
- **By when**, and **how reversible** (easy / costly / one-way). Reversible + cheap -> skip the memo, pick and go.

## 2. Options
2-4 real ones. Always consider "do nothing / wait". Drop any that fail a hard constraint and say why.

## 3. Criteria
3-6, taken from what the user said they care about. Weight each 1-3. Ask for weights only if they are truly unknown and change the result.

## 4. Table
| Criterion (weight) | Option A | Option B | Option C |
|---|---|---|---|
Score 1-5 with a **reason in the cell**. Compute totals in code or carefully; show them.

## 5. Beyond the table
- **Worst realistic case** for each option, and whether it is survivable.
- **What you'd have to believe** for each option to be right.
- **Cheap test:** can 1 hour or a small spend reduce the uncertainty before committing?

## 6. Recommendation
```
VERDICT: <option>
Because: <2 lines>
Changes if: <the fact that would flip it>
First step: <concrete>
```

## Rules
- Facts need sources or a "assumed" tag. Look up anything current (prices, terms, rates).
- Give a recommendation; don't hide behind "it depends". State confidence.
- Hold the position if pushed without new information; update if given some.
- Legal/financial/health choices: give the facts and structure, flag that it is not professional advice, leave the call to the user.
