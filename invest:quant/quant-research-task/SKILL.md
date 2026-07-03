---
name: quant-research-task
description: Retired question-oriented quantitative research workflow kept for compatibility with old quant-researcher or quant-research-task references. Do not use as the primary workflow for new work; use File Organization for project/folder routing and Exploration Task Workflow for question discovery, research direction finding, and evidence-backed next steps.
metadata:
  author: wjs
  last_update_time: "2026-07-03 21:00:13 HKT"
  status: retired
---

# Quant Research Task

Status: retired.

This is the historical `quant-researcher` workflow. It is retained only as a compatibility reference for old quant research projects and references.

For new work, use:

- `../../fundamental/file-organization/SKILL.md` for project-level folder organization, research documents, project nodes, data, notebooks, outputs, and skills.
- `../../fundamental/exploration-task-workflow/SKILL.md` for question discovery, uncertain research direction, assumption discovery, option comparison, and evidence-backed next steps.

## Core Principle

Start quant research from a clear research question. The first artifact should
be a question-oriented roadmap: what is being asked, why it matters, what
intuition guides the work, and which tasks must be completed before the
question can be answered.

The first artifact should clarify:

| Layer | Purpose |
| --- | --- |
| Goal | Explain what capability, decision, or understanding this question should enable. |
| Research question | State the central thing the researcher is trying to answer. |
| Intuition | Explain the mental model, expected mechanism, or core idea behind the work. |
| Data format / inputs | Name required data, code paths, examples, schemas, or source systems. |
| Tasks | Break the question into concrete checklists that can be completed and reviewed. |
| Evidence links | Point to code, docs, data, papers, experiments, or notes that should be read. |
| Open issues | Record uncertainties and follow-up questions only when the user explicitly asks for open issues, open questions, or follow-up uncertainties. |

Use reproducible pipeline structure when the question turns into a concrete
operation such as data reconstruction, alignment, signal construction, detection,
or backtest.

## Top-Level Structure

Use this structure for a research area:

```text
projects/<research_area>/
  README.md
  SKILL.md                 # optional; use only when the project pattern itself should be reusable
  questions/
  research/
  reports/
  <project_id>_<project_name>/
```

Use the folders this way:

- `questions/`: Research question carriers. Define goal, research question,
  intuition, inputs, tasks, checklists, and linked docs.
- `research/`: Source research notes, literature reviews, API probes, data
  source notes, and empirical reconnaissance.
- `reports/`: Final or semi-final report documents after evidence is strong
  enough to support claims.
- `<project_id>_<project_name>/`: Work folder for one concrete research project.

The project id is a stable numeric prefix. It does not need to imply that all
previous numbers exist.

Examples:

```text
001_factor_momentum/
002_three_token_taker/
003_cross_market_residuals/
```

## Question Files

Create or update a question file as the primary roadmap. The question file is a
thinking guide for research direction and task decomposition. Match the style of
the `stat_arbitrage/questions` files: direct title, inline status, clear goal,
research question, intuition, and task checklists.

Default document rule: do not proactively add sections titled `Open Questions`,
`Open Issues`, `Follow-ups`, or similar uncertainty / future-work sections.
Include those sections only when the user explicitly asks for them. If the user
asks for a concise document or provides a specific structure, follow that
structure exactly.

Use question files to formulate the research problem, guide investigation, and
record what a useful answer should contain. Do not put generated artifacts,
implementation scripts, or detailed run logs inside `questions/`.

Use English titles and filenames unless the user explicitly asks otherwise.

For a broad research area, use a compact question scaffold:

```markdown
# Short English Title

Status: scaffolded research question

## Research Question

State the central research question.

## Null Hypothesis

State the skeptical baseline that would make the opportunity or idea disappear.

## First Slice

Start with the smallest read-only or low-risk investigation:

1. First concrete step.
2. Second concrete step.
3. Third concrete step.

## Linked Docs

- Link to scope, plan, project folder, source note, code path, or report.
```

For a concrete requirement or implementation-oriented research question, use a
task roadmap:

```markdown
# Short English Title

Status: draft requirement

Project: Project name

Primary example: Optional market, module, dataset, or code path.

## Goal

Explain what capability, decision, or understanding this work should enable.

## Research Question

State the question this document is trying to answer.

## Intuition

Explain the core mental model, mechanism, or expected structure.

## Data Format

Describe required data, code paths, schemas, runtime inputs, example markets, or
other source material. Rename this section to `Inputs` or `Code Paths` when that
is more precise.

## Task 1: First Task Name

State the first research or implementation task.

### 1. Concrete Subtask

- [ ] Checklist item.
- [ ] Checklist item.

### 2. Concrete Subtask

- [ ] Checklist item.
- [ ] Checklist item.

## Task 2: Second Task Name

State the second research or implementation task.

### 1. Concrete Subtask

- [ ] Checklist item.
- [ ] Checklist item.

## Linked Docs

- Link to project folder, source note, code path, or report.
```

## Project Folders

A project folder represents one coherent research project or concrete work area.

Use phase folders when the project becomes large:

```text
<project_id>_<project_name>/
  <phase_name>/
    <subtask_id>_<subtask_name>/
```

For stat-arbitrage or execution research, phases may look like:

```text
<project_id>_<project_name>/
  arbitrage_confirmation/
  architecture_review/
  strategy_design/
  dry_run/
  backtest/
```

Do not put unrelated scripts, figures, or ad hoc outputs directly in the
project root.

## Subtask Folders

Each concrete operation should have its own folder:

```text
<subtask_id>_<subtask_name>/
  README.md
  execute_<subtask_name>.py
  analyze_<subtask_name>.py
  output.md
  output/
```

The exact filenames can vary, but the role split should stay stable.

Examples:

```text
01_order_book_reconstruction/
  README.md
  execute_order_book_reconstruction.py
  analyze_order_book_reconstruction.py
  output.md
  output/
```

```text
02_order_book_time_alignment/
  README.md
  execute_order_book_alignment.py
  analyze_order_book_alignment.py
  output.md
  output/
```

## README Usage

Each subtask `README.md` should describe the reusable module, not just one
example run.

Include:

| Section | Content |
| --- | --- |
| Purpose | What this subtask does and does not do. |
| Scripts | Script names and roles. |
| Input | Required files, columns, identifiers, and assumptions. |
| Output | Generated data files and meanings. |
| Method | Algorithm or transformation used. |
| Usage Example | Copy-paste command for the current example. |
| Current Example Output | Link to `output.md`. |

Write README files as project documentation, not scratch commentary.

Avoid informal notes like "we first try this" or "not sure yet". If uncertainty
matters, state it formally:

```text
This assumption is unverified and should be checked before execution-sensitive analysis.
```

## Output Folder And Output Note

Generated artifacts belong under `output/`:

```text
output/
  example_price_path.png
  example_summary.csv
  example_aligned_data.parquet
```

Use `output.md` for the current concrete run, not the reusable method.

Include:

| Section | Content |
| --- | --- |
| Example | Which match, market, universe, factor, or dataset was used. |
| Inputs | Exact source files or processed folders. |
| Command | Command used to generate outputs. |
| Generated Outputs | Table of generated files and meanings. |
| Findings | Short interpretation of the current run. |
| Caveats | Known issues, mapping problems, stale data, survivorship bias, execution assumptions, or unresolved risks. |

When images are important, embed them:

```markdown
![Diagnostic plot](output/example_price_path.png)
```

## Scripts

Prefer scripts for reproducible pipelines. Use notebooks only when interactive
exploration is genuinely useful.

Scripts should be reusable modules with a thin CLI wrapper:

```python
def load_inputs(...):
    ...

def transform_or_analyze(...):
    ...

def write_outputs(...):
    ...

def main() -> int:
    ...
    return 0

if __name__ == "__main__":
    raise SystemExit(main())
```

Rules:

- Put dataset-specific values in CLI arguments.
- Keep core logic in functions.
- Keep `main()` thin.
- Use explicit input and output paths.
- Validate required columns.
- Print generated output paths.

Separate reusable data generation from diagnostics:

| Script Type | Role |
| --- | --- |
| `execute_*.py` | Create or transform reusable data artifacts. |
| `analyze_*.py` | Read generated artifacts and produce diagnostics, plots, or summaries. |

Do not mix raw data transformation, visualization, and strategy interpretation
in one large script unless the task is tiny.

## Data And Notebook Conventions

Raw data should live under:

```text
data/raw/
  <source_or_api>/
```

Processed data should live under:

```text
data/processed/
  <source_or_project_area>/
```

Project-specific generated outputs should live under:

```text
projects/<research_area>/<project_id>_<project_name>/<phase>/<subtask>/output/
```

Do not store large raw datasets inside `projects/`.

If a notebook produces reusable logic, move that logic into a script module and
keep the notebook as a demo or visual inspection layer.

## Workflow

When organizing a quant research task:

1. Identify or create the research area under `projects/`.
2. Write or update the question-oriented roadmap in `questions/`.
3. Keep the first pass focused on clarifying the question, subquestions, scope,
   expected answer, and evidence to inspect.
4. Create a project folder only when the work becomes concrete enough to need a
   dedicated analysis space.
5. Use a root-level numbered project folder for the concrete work that answers a
   question; keep the question file itself as the roadmap.
6. Create phase and subtask folders only when there is a reproducible operation
   to run.
7. Add `execute_*.py`, `analyze_*.py`, `output.md`, and `output/` only for
   concrete data/experiment/backtest tasks.
8. Record unresolved assumptions and caveats in existing appropriate sections,
   but do not add open-issue sections by default unless the user requests them.

If the user corrects the intended structure, follow the correction exactly and
avoid adding extra files or folders beyond what the user requested.

## Naming

Use precise names:

| Prefer | Avoid |
| --- | --- |
| `execute_order_book_reconstruction.py` | `run.py` |
| `analyze_order_book_alignment.py` | `plot.py` |
| `output.md` | loose comments in README |
| `output/` | figures scattered in task folder |
| CLI parameters | hardcoded match ids |

Use English file titles and folder names by default. Preserve the user's
preferred language inside question text and notes when useful.
