# Skill pack

15 model-agnostic skills. Each is one folder with one `SKILL.md` (plain Markdown + 2-line YAML header).

## Install

| Where | How |
|---|---|
| **Claude Code, all projects** | copy the folders inside `skills/` into `~/.claude/skills/` |
| **Claude Code, one project (shareable via git)** | copy them into `<repo>/.claude/skills/` and commit |
| **Claude app (claude.ai)** | ask Claude "save this as a skill" with the SKILL.md pasted/attached, or zip one skill folder and upload it under Skills in settings |
| **Any other LLM / a Project** | paste the SKILL.md body into project instructions or the chat |

Invoke with `/skill-name`, or just describe the task — the `description` line is what triggers it.

## Index

### Process (use on everything)
| Skill | Use when |
|---|---|
| `orchestrator` | big multi-part task; routes steps to cheapest model, verifies, writes handoff |
| `verify-pass` | double-check any finished deliverable |
| `spec-first` | vague idea -> one-page spec before any building |
| `session-handoff` | end of a session / context getting long / switching model |
| `delegation-brief` | writing a prompt for a subagent or a cheaper model |
| `debug-loop` | something is broken and guessing isn't working |
| `research-brief` | bounded, sourced research with a stop rule |
| `decision-memo` | choosing between options |
| `learn-mode` | learning a new topic fast, with practice |

### Design & front-end
| Skill | Use when |
|---|---|
| `design-critique` | review a screen, page or brand piece |
| `design-system-audit` | check tokens/components for drift and gaps |
| `frontend-ship-check` | before deploying a site (a11y, perf, SEO, meta) |

### Career & portfolio
| Skill | Use when |
|---|---|
| `job-application` | tailor CV + cover letter to a posting (EN/DE) |
| `case-study-writer` | turn a project into a portfolio case study |
| `interview-prep` | prepare for a specific interview |

## How they combine
`spec-first` -> `orchestrator` (uses `delegation-brief` for subagents) -> `verify-pass` -> `session-handoff`.

## Editing
Keep the `description` under ~200 characters and specific: it decides when the skill fires. Keep bodies short; every line is loaded into context when the skill runs.
