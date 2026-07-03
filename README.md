# Skills

This repository stores reusable Codex skills organized by category. Each skill
is a self-contained workflow instruction in a `SKILL.md` file with frontmatter
metadata for name, description, author, update time, and status.

## Directory Convention

Skills are grouped as:

```text
<category>/<skill-slug>/SKILL.md
```

Category names describe the skill's primary operating domain. Some categories
use a namespace-style name such as `research:work` or `invest:quant` when the
top-level domain needs a more specific subdomain.

## Status Convention

Every skill must declare `metadata.status`, and the value must be exactly one
of:

| Status | Meaning |
| --- | --- |
| `active` | Use for new work when the skill matches the task. |
| `retired` | Keep for compatibility and migration guidance; do not use as the primary workflow for new work. |

## Category Index

| Category | Purpose | Skills |
| --- | --- | --- |
| [`composite`](composite/) | High-level orchestration skills that route work across lower-level skills. | 1 active |
| [`daily:info`](daily:info/) | Daily information and briefing workflows. | Empty placeholder |
| [`fundamental`](fundamental/) | Core reusable primitives for planning, organization, code structure, research direction, and execution discipline. | 6 active |
| [`invest:quant`](invest:quant/) | Quantitative investment research workflows and compatibility markers. | 1 retired |
| [`research:work`](research:work/) | Research-note and evidence synthesis workflows. | 1 active |

## `composite`

Use composite skills when the task needs workflow routing before detailed work
begins. Composite skills should point agents to the right fundamental skill
instead of duplicating lower-level procedures.

| Skill | Status | Use When |
| --- | --- | --- |
| [`ai-long-horizon-workflow`](composite/ai-long-horizon-workflow/SKILL.md) | `active` | A task is complex, multi-step, research-heavy, coding-heavy, or needs planning, collaboration structure, memory organization, uncertainty handling, checklist discipline, or coordination across fundamental skills. |

## `daily:info`

This category is reserved for recurring daily information workflows, briefings,
and information-monitoring skills.

Current state: no skills yet. The directory is retained with `.gitkeep` so the
category remains available.

## `fundamental`

Use fundamental skills as the building blocks for most work. They define the
core operating conventions for requirements, files, code, exploration,
execution, and long-running project control.

| Skill | Status | Use When |
| --- | --- | --- |
| [`ai-complex-project-guidance`](fundamental/ai-complex-project-guidance/SKILL.md) | `active` | Work is long-running, complicated, multi-step, research-heavy, implementation-heavy, or likely to exceed one pass of agent work. |
| [`code-organization`](fundamental/code-organization/SKILL.md) | `active` | Planning, editing, or reviewing code repositories; defining module boundaries, public APIs, contracts, dependencies, sample cases, or code documentation. |
| [`craft-framework`](fundamental/craft-framework/SKILL.md) | `active` | Creating, editing, or reviewing `requirement.md` documents using Context, Role, Action, Format, and Tone. |
| [`exploration-task-workflow`](fundamental/exploration-task-workflow/SKILL.md) | `active` | The task direction is uncertain and the agent needs to compare options, surface assumptions, gather evidence, or find a concrete next step. |
| [`exploitation-task-workflow`](fundamental/exploitation-task-workflow/SKILL.md) | `active` | The task direction is clear enough to plan and execute through `requirement.md`, project `README.md`, and numbered task files. |
| [`file-organization`](fundamental/file-organization/SKILL.md) | `active` | Organizing project-level folders, Markdown notes, project docs, data, notebooks, outputs, project skills, `README.md`, or `AGENT.md`. |

## `invest:quant`

Use this category for investment and quantitative research workflows. Retired
skills here are kept to document migration paths from older research structures
to the current fundamental workflow.

| Skill | Status | Use When |
| --- | --- | --- |
| [`quant-research-task`](invest:quant/quant-research-task/SKILL.md) | `retired` | Compatibility only. For new work, use `file-organization` for project routing and `exploration-task-workflow` for research question discovery and evidence-backed next steps. |

## `research:work`

Use this category for research execution skills that produce evidence-backed
notes, source collections, or first-pass synthesis.

| Skill | Status | Use When |
| --- | --- | --- |
| [`quick-research`](research:work/systematic-critical-research/SKILL.md) | `active` | A user needs fast critical research, source collection, viewpoint comparison, concise Markdown synthesis, or a structured answer before deciding whether to continue into exploration or exploitation workflow. |

## Maintenance Rules

- Add new skills under the most specific existing category when possible.
- Create a new category only when the operating domain is meaningfully different
  from the existing categories.
- Keep each skill's frontmatter `name`, `description`, and `metadata.status`
  current. `metadata.status` must be either `active` or `retired`.
- Update this README whenever a skill is added, retired, renamed, moved, or
  materially changes its intended use.
- Prefer active skills for new work. Retired skills should explain what replaced
  them and why they remain in the tree.
