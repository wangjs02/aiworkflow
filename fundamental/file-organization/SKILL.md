---
name: file-organization
description: Organize project-level folders and natural-language workspace files for AI-assisted projects. Use when creating or reviewing a project structure, deciding where documents, requirements, task plans, data, notebooks, outputs, project skills, README.md, or AGENT.md should live, or preparing a workspace so agents and collaborators can work in it consistently.
metadata:
  author: wjs
  last_update_time: "2026-07-03 20:45:06 HKT"
  status: active
---

# File Organization

Use this skill for project-level folder organization, especially for non-coding documents and agent-readable project state.

This skill defines where project materials belong. For detailed module/code layout inside `code/`, load `../code-organization/SKILL.md`.

## Standard Project Layout

Use this structure as the default project root:

```text
<project>/
├── README.md
├── AGENT.md
├── docs/
├── projects/
├── data/
├── code/
│   ├── dev/
│   └── prod/
├── notebooks/
├── outputs/
└── skills/
```

If an existing repository already uses `AGENTS.md`, keep the existing filename instead of creating a duplicate `AGENT.md`. Otherwise prefer `AGENT.md` for this workflow.

## Root Files

### `README.md`

Use `README.md` as the human-facing project guide. It should explain:

- What the project is
- How to use the project
- How to run or inspect the project's code, notebooks, or outputs
- Where important documents, project nodes, data, code, and outputs live
- The current project status, if useful for orientation

Keep `README.md` practical. It should help a human enter the workspace quickly.

### `AGENT.md`

Use `AGENT.md` as the agent and collaborator operating guide. It explains how agents and collaborators should work inside the workspace.

Include these sections when relevant:

- Objective
- Project Organization
- Recommended Workflow
- Development Convention
- Relevant Skills
- Good Practices For Agents

The `AGENT.md` should answer:

- What is this workspace trying to accomplish?
- How should an agent choose the right folder or project node?
- Which workflow should the agent follow before changing files?
- What conventions should the agent preserve?
- Which skills should the agent load for repeated or project-specific work?
- What good practices should agents follow to avoid corrupting project state?

Keep `AGENT.md` current. Update it when project structure, repeated workflows, development conventions, or relevant skills change.

## Directories

### `docs/`

Use `docs/` for general research, design, notes, plans, and reflections that do not yet have a clear long-term project owner.

Good contents:

- General research notes
- Design notes
- Early plans
- Broad analysis
- Runbooks
- Reflections and postmortems

When a document becomes part of a concrete long-term project, move or link it into the appropriate project node under `projects/`.

### `projects/`

Use `projects/` for complex project information and long-horizon task state.

For each substantial project, create a project node such as:

```text
projects/<project-name>/
├── requirement.md
├── README.md
└── tasks/
```

Use `../ai-complex-project-guidance/SKILL.md` when creating or maintaining complex project nodes.

Use `requirement.md` for the CRAFT requirement. Load `../craft-framework/SKILL.md` before creating or reviewing it.

Use the project `README.md` to explain the project objective, current state, important files, task map, outputs, and next steps.

Use `tasks/` for task files. Each task should define input, output, constraints, actionable steps, deliverable checklist, evidence, and draft result.

### `data/`

Use `data/` for source data and local datasets. Keep raw inputs separate from generated outputs.

Default shape:

```text
data/
└── raw/
```

Use `data/raw/` for original source data, downloaded files, API dumps, manually collected source material, fixtures, and other inputs that should remain immutable when possible.

Do not store trained models, final reports, charts, or result packages in `data/`; place those under `outputs/`.

### `code/`

Use `code/` for all module code.

Default shape:

```text
code/
├── dev/
└── prod/
```

Use `code/dev/` for local development, research code, reusable helpers, analysis modules, experiments, and code imported by notebooks.

Use `code/prod/` for production code, deployment code, production repo checkouts, server runners, and code intended for live or operational use.

For detailed code layout, naming, module boundaries, testing, and development conventions, use `../code-organization/SKILL.md`.

### `notebooks/`

Use `notebooks/` for staged result presentation, exploratory analysis, reviewable research outputs, charts, and complex research findings.

Notebooks should import reusable logic from `code/`. Do not leave important reusable code only inside notebooks.

Use notebooks to make results understandable and inspectable, not as the only place where core logic exists.

### `outputs/`

Use `outputs/` for generated artifacts and final outputs.

Good contents:

- Trained models
- Generated reports
- Exported charts
- Result tables
- Evaluation outputs
- Packaged deliverables
- Other output artifacts created by code, notebooks, or project tasks

Keep outputs traceable to the code, notebook, task, data, or project that produced them.

### `skills/`

Use `skills/` for project-related skills.

Store skills here when they capture project-specific workflows, repeated procedures, deterministic script sequences, verification checks, or stable agent instructions.

When a repeated workflow stabilizes, update or create the relevant project skill so future agents do not reconstruct the workflow from scratch.

## Placement Rules

If the file explains the whole workspace, place it at the root as `README.md` or `AGENT.md`.

If the file is general research or design without a concrete project owner, place it in `docs/`.

If the file belongs to a concrete long-term project, place it under `projects/<project-name>/`.

If the file is original input data, place it under `data/raw/`.

If the file is reusable code, place it under `code/dev/` or `code/prod/`.

If the file is a staged analysis or result presentation, place it under `notebooks/`.

If the file is a generated model, report, chart, table, or package, place it under `outputs/`.

If the file is an agent skill for this project, place it under `skills/`.

## Review Checklist

When reviewing a project folder, check:

- The root has a useful `README.md`
- The root has an agent guide as `AGENT.md` or an existing `AGENTS.md`
- General documents are in `docs/`
- Complex project state is in `projects/<project-name>/`
- Each substantial project has `requirement.md`, `README.md`, and `tasks/`
- Raw data is in `data/raw/`
- Reusable code is in `code/dev/` or `code/prod/`
- Notebooks import reusable code instead of hiding important logic
- Generated artifacts are in `outputs/`
- Project-specific repeated workflows are captured in `skills/`
