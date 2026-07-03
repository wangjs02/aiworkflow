# Agent Guide

This document explains how agents and collaborators should work inside the
`aiworkflow` repository.

## Objective

This repository is the source of truth for Junshi Wang's personal AI workflow
system. It is a collection of AI workflows, including personal skills, external
skills, MCPs, reusable resources, and related workflow documentation.

The current primary purpose is to maintain reusable Codex skills that encode
planning, research, writing, coding, reporting, and domain-specific workflows.

Optimize for workflows that remain understandable and reusable after many
iterations. Do not optimize for one-off prompt dumps.

## Project Organization

```text
aiworkflow/
├── README.md                     # Human-facing repository guide
├── AGENT.md                      # Agent/collaborator operating guide
└── skills/
    ├── README.md                 # Skill index and skill maintenance rules
    ├── composite/                # High-level orchestration skills
    ├── fundamental/              # Core workflow primitives
    ├── research:work/            # Research, literature, reports, and notes
    ├── invest:quant/             # Quant research workflows
    └── daily:info/               # Daily information workflows
```

Keep root-level files limited to repository-level guidance and configuration.
Skill content belongs under `skills/`. Add future top-level folders such as
`external-skills/`, `mcps/`, or `resources/` only when they contain real reusable
workflow material.

## Recommended Workflow

### 1. Understand The Requested Change

Before editing, identify whether the request is:

- a new skill
- a skill rename or category move
- a skill content update
- a reference/template migration
- a repository organization change
- an external skill, MCP, or resource addition
- a sync/publish/git operation

Use the existing category structure unless the user explicitly asks for a new
category or the current categories clearly do not fit.

### 2. Read Existing Context

Before changing a skill:

- Read the target `SKILL.md`.
- Read directly referenced files under `references/` when they affect the change.
- Read [skills/README.md](skills/README.md) when category names, status, or skill indexes may change.
- If migrating from a global Codex skill, inspect the source skill structure before copying content.

Prefer `rg` and `rg --files` for search.

### 3. Edit Narrowly

Keep edits scoped to the requested skill or category.

Do not refactor unrelated skills, rename categories, or rewrite old content
unless the user asks for it or the change is required for consistency.

When adding a detailed prompt, style guide, or reusable template, prefer:

```text
skills/<category>/<skill-name>/references/<file>.md
```

and keep `SKILL.md` as the routing and execution guide.

For external skills, MCP notes, and reusable resources, keep provenance clear:
record where the material came from, why it is included, and how it should be
used or synced.

### 4. Maintain Skill Metadata

Every `SKILL.md` must include:

```yaml
metadata:
  author: wjs
  last_update_time: "YYYY-MM-DD HH:MM:SS HKT"
  status: active
```

Rules:

- `name` must match the skill folder name exactly.
- `status` must be `active` or `retired`.
- Update `last_update_time` when materially changing a skill.
- Use HKT timestamps.
- Keep `description` trigger-focused; it should explain when Codex should use the skill.

### 5. Update The Skill Index

Update [skills/README.md](skills/README.md) whenever:

- a skill is added
- a skill is renamed
- a skill is moved between categories
- a skill is retired or reactivated
- the category count changes
- the intended use of a skill materially changes

Do not let the README index drift from the filesystem.

### 6. Validate Before Finishing

At minimum, validate:

```bash
git status --short
rg -n "old-skill-name|old-category-name" skills
```

For metadata consistency, run a local frontmatter check similar to:

```bash
python3 - <<'PY'
from pathlib import Path
import re, sys
root = Path("skills")
errors = []
for path in root.rglob("SKILL.md"):
    text = path.read_text()
    m = re.match(r"^---\n(.*?)\n---\n", text, re.S)
    if not m:
        errors.append(f"{path}: missing frontmatter")
        continue
    fm = m.group(1)
    name = re.search(r"^name:\s*(.+)$", fm, re.M)
    desc = re.search(r"^description:\s*(.+)$", fm, re.M)
    author = re.search(r"^\s+author:\s*(.+)$", fm, re.M)
    last = re.search(r"^\s+last_update_time:\s*\"(.+)\"$", fm, re.M)
    status = re.search(r"^\s+status:\s*(.+)$", fm, re.M)
    if not name or not desc:
        errors.append(f"{path}: missing name or description")
    if not author or not last or not status:
        errors.append(f"{path}: missing metadata author/last_update_time/status")
    elif status.group(1).strip() not in {"active", "retired"}:
        errors.append(f"{path}: invalid status {status.group(1).strip()}")
    if name and path.parent.name != name.group(1).strip():
        errors.append(f"{path}: folder/name mismatch {path.parent.name} != {name.group(1).strip()}")
if errors:
    print("\n".join(errors))
    sys.exit(1)
print("validated", len(list(root.rglob("SKILL.md"))), "skills")
PY
```

## Git Practice

Commit by category or concern when possible.

Examples:

```text
fundamental: update code organization skill
research:work: add weekly report reference
invest:quant: restore quant research task
mcps: add calendar connector notes
resources: add report template references
docs: update category skill index
repo: move skills into repository subdirectory
```

Before committing:

- Confirm `git status --short`.
- Avoid committing `.DS_Store`, temporary files, generated caches, or unrelated user changes.
- Do not rewrite history unless the user explicitly asks.

## Relevant Skills

When working on this repository, the most relevant local skills are:

- `skills/fundamental/file-organization/SKILL.md`
- `skills/fundamental/code-organization/SKILL.md`
- `skills/fundamental/craft-framework/SKILL.md`
- `skills/fundamental/ai-complex-project-guidance/SKILL.md`
- `skills/composite/ai-long-horizon-workflow/SKILL.md`

Use the system `skill-creator` guidance when creating or substantially updating
skills for Codex discovery.

## Good Practices For Agents

- Preserve the user's naming preferences exactly once they are clarified.
- Keep Chinese source content when it is part of the user's workflow.
- Prefer concise skill bodies with detailed reusable material in `references/`.
- Preserve references to user-specific paths only when the workflow genuinely depends on them.
- If a global Codex skill is migrated, rename it deliberately and adjust the trigger description to the local naming convention.
- When a skill references another local skill, use the current local skill name rather than old global names.
- When push fails, distinguish repository state problems from credential problems before changing files.
