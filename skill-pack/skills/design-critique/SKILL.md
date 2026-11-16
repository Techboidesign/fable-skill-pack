---
name: design-critique
description: "Structured critique of a UI screen, web page or brand piece - hierarchy, layout, type, colour, states, accessibility - with ranked fixes. Use for /crit, 'review this design', screenshots, Figma links."
---

# Design critique

Critique against the **goal**, not against taste. Look before judging: open the file, screenshot the page, or read the Figma node.

## 1. Frame
- What is this, who is it for, what is the one thing the viewer should do or feel?
- Unknown -> state the assumption in one line and continue.

## 2. Pass through the layers (in this order)
| Layer | Ask |
|---|---|
| **Purpose** | Is the primary action/message obvious within 3 seconds? |
| **Hierarchy** | Squint test: what reads 1st, 2nd, 3rd? Is that the intended order? |
| **Layout** | Grid, alignment, spacing rhythm (consistent scale?), density, edge cases: long text, empty, overflow. |
| **Typography** | Number of sizes/weights, line length (45-75 chars body), line-height, contrast between levels. |
| **Colour** | Role per colour, accent used once per view, contrast (WCAG AA: 4.5:1 text, 3:1 large text/UI). |
| **Components** | Consistent radii, borders, shadows, icon style; states: hover, focus, active, disabled, loading, error, empty. |
| **Content** | Labels say what happens; no lorem; tone matches brand. |
| **Responsive** | 360 / 768 / 1280+. Tap targets >= 44px. |
| **Brand** | Would this be recognisable with the logo removed? What makes it generic? |

Measure when possible (computed styles, contrast ratio in code, Figma variables). Don't eyeball what can be measured.

## 3. Output
```
VERDICT: SHIP | SHIP WITH FIXES | REWORK
Working: 2-3 specific things to keep
| # | Issue | Where | Why it hurts the goal | Fix | Impact H/M/L | Effort S/M/L |
Top 3 to do first: ...
```
Order by impact / effort. Max 10 issues.

## Rules
- Every issue names a location and a concrete fix (a value, not "improve spacing").
- Separate **standards** (WCAG, platform guidelines) from **opinion**; label opinion.
- No redesign unless asked. If asked, change the fewest things that fix the top issues.
- Honest over kind: say REWORK when it is.
