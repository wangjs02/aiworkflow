# AI Workflow

This repository is a collection of Junshi Wang's AI workflows, including
personal skills, external skills, MCPs, reusable resources, and related
workflow documentation.

The current focus is a reusable Codex skill library under `skills/`. Over time,
this repository can also hold curated external skills, MCP configuration notes,
workflow resources, templates, and supporting documentation. The goal is to keep
AI workflows explicit, versioned, easy to review, and ready to sync into active
agent environments when they become stable.

## Repository Structure

```text
aiworkflow/
├── README.md                     # Human-facing repository guide
├── AGENT.md                      # Agent/collaborator operating guide
└── skills/                       # Personal and curated Codex skills
    ├── README.md                 # Skill category index and maintenance rules
    ├── composite/                # High-level orchestration skills
    ├── fundamental/              # Core planning, organization, and execution skills
    ├── research:work/            # Research, literature, report, and note workflows
    ├── invest:quant/             # Quantitative research workflows
    └── daily:info/               # Placeholder for daily information workflows
```

## Current Scope

The repository currently contains the personal skill collection. Future
workflow resources can be added as top-level folders when they become concrete,
for example:

```text
external-skills/                  # Curated third-party or copied external skills
mcps/                             # MCP setup notes, manifests, and operational docs
resources/                        # Shared workflow templates, references, and assets
```

Do not create these folders as placeholders unless there is actual content to
store.

The skill library is organized by operating domain:

| Category | Purpose |
| --- | --- |
| `composite` | Top-level orchestration skills that route complex work across lower-level skills. |
| `fundamental` | Core reusable primitives for requirement writing, project structure, code organization, exploration, exploitation, and long-task discipline. |
| `research:work` | Research execution, literature review, paper download, Markdown routing, and report writing workflows. |
| `invest:quant` | Quantitative research task workflows. |
| `daily:info` | Reserved for recurring daily information and briefing workflows. |

For the full skill index, see [skills/README.md](skills/README.md).

## Skill Format

Each skill lives in its own directory and must include a `SKILL.md` file:

```text
skills/<category>/<skill-name>/SKILL.md
```

Every skill frontmatter should include:

```yaml
---
name: skill-name
description: Clear trigger description for when Codex should use this skill.
metadata:
  author: wjs
  last_update_time: "YYYY-MM-DD HH:MM:SS HKT"
  status: active
---
```

`metadata.status` must be either:

- `active`: use for new work when the skill matches the task.
- `retired`: preserve for compatibility or migration guidance, but do not use as the primary workflow for new work.

## Maintenance Workflow

Use this repository as the source of truth before syncing workflows into Codex
or other agent environments.

1. Add or update skills under the most specific category.
2. Keep `SKILL.md` concise; move detailed templates, examples, or style guides into `references/`.
3. Update [skills/README.md](skills/README.md) whenever a skill is added, renamed, retired, moved, or materially changed.
4. Add external skills, MCP notes, or resources only when they have a clear reuse target.
5. Validate names, frontmatter, metadata, and folder alignment before committing.
6. Commit changes by category or resource type when possible, so history remains easy to review.

## GitHub

The intended remote is:

```text
https://github.com/wangjs02/aiworkflow.git
```

or, if SSH is configured for the local machine:

```text
git@github.com:wangjs02/aiworkflow.git
```

The repository root is `/Users/wjs/Code/aiworkflow`; do not run git commands
from `skills/` as if it were a separate repository.
