---
name: design-system-audit
description: "Audit a design system or codebase for token drift, hard-coded values, duplicate components and missing states; report only. Use for /ds-audit, 'audit the tokens', 'is this consistent'."
---

# Design system audit

Report only. Change nothing unless asked.

## 1. Inventory (cheap, by script/grep - delegate to a small model)
- **Tokens:** where defined (CSS variables, Tailwind config, JSON, Figma variables). Count per category: colour, type, space, radius, shadow, motion, z-index, breakpoints.
- **Raw values in use:** grep for hex/rgb/hsl, px/rem literals, font sizes, radii, shadows, durations outside the token files.
- **Components:** list with variants, sizes, states.

Useful greps:
```
grep -rEno '#[0-9a-fA-F]{3,8}\b' src | grep -v tokens
grep -rEno '\b[0-9]+(\.[0-9]+)?(px|rem)\b' src --include=*.css --include=*.tsx
```

## 2. Analyse
| Check | Finding looks like |
|---|---|
| **Drift** | Raw values that equal or nearly equal a token (e.g. #1a1a1b vs --gray-900) |
| **Scale holes** | Spacing/type values off the scale; too many near-duplicate steps |
| **Naming** | Mixed schemes; values in names (`blue-500` used as a role); no semantic layer (`--color-text-muted`) |
| **Theming** | Components reading primitives instead of semantic tokens; dark mode gaps |
| **Duplicates** | Two components doing one job; variants that are really separate components |
| **States** | Missing focus-visible, disabled, loading, error, empty |
| **A11y** | Token pairs failing contrast (compute it), focus ring missing, motion without reduced-motion |
| **Design-code parity** | Figma variables vs code tokens: names and values that differ |
| **Docs** | Components without usage notes or examples |

## 3. Output `DS-AUDIT.md`
```
## Summary
Counts: tokens, raw values found, components, issues by severity.
## Findings
| # | Area | Issue | Evidence (file:line / node) | Count | Severity | Fix |
## Quick wins (under 1h each)
## Structural (needs a decision)
## Suggested token map
raw value -> token (for the top 20 offenders)
```

## Rules
- Counts come from commands, not estimates. Show the command.
- Severity: HIGH = user-visible inconsistency or a11y failure; MED = maintenance cost; LOW = tidiness.
- Don't propose a new system. Propose the smallest set of merges/renames that removes the drift.
- Large repo: sample by directory, say what was not covered.
