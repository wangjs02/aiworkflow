---
name: ai-complex-project-guidance
description: Guide long-running or complicated AI work with strict planning, task decomposition, checklist evidence, single-task execution, draft accumulation, and non-negotiable completion standards. Use when a project is complex, multi-step, long-running, research-heavy, implementation-heavy, or likely to exceed one pass of agent work.
metadata:
  author: wjs
  last_update_time: "2026-07-08 16:51:21 HKT"
  status: active
---

# AI Complex Project Guidance

Use this skill to control long-running AI work. The goal is to make complex work reviewable, resumable, and objectively checkable.

## Hard Constraints

For coding work, do not leave fallback paths, silent degradation, broad exception swallowing, placeholder implementations, or stub behavior. If the requested behavior cannot be implemented, surface the blocker instead of adding fallback logic.

For reports, every substantive argument must be supported by references. Do not present unsupported claims as conclusions.

Do not reduce or reinterpret explicit requirements. If the user asks for a 10-page report, do not deliver fewer than 10 pages. If the user asks for analysis of a specific person, project, paper, dataset, or organization, do not skip it because it is hard to find.

## Preparation Phase

Before execution, create or update the project planning files required by the complex project workflow:

1. `requirement.md`
2. `README.md`
3. Task files for all planned tasks

Write `requirement.md` with the CRAFT Framework. Load `../craft-framework/SKILL.md` before writing or reviewing it.

Use `README.md` to describe the project purpose, current state, task map, important files, and how to resume the work.

Create task files before starting execution. Each task must include:

- Input
- Output
- Constraints
- Actionable steps
- Subtasks, if the task is still broad
- Objective deliverable checklist
- Evidence log
- Draft result section

Split tasks as finely as possible. Prefer many small tasks over one broad task. Each task should be executable and reviewable on its own.

This skill controls project start and execution discipline. For the actual task file format and writing standard, load `../exploitation-task-workflow/SKILL.md` and, for non-trivial tasks, its `references/task-file-writing-guide.md`.

Later tasks may be revised after earlier tasks reveal new problems, evidence, or dependencies. Record the reason for any task revision.

## Checklist Discipline

Each task must have a predefined deliverable standard expressed as checklist items.

Checklist items must be objectively checkable. A valid checklist item should point to a document, code output, test result, source citation, command output, data artifact, screenshot, or other inspectable evidence.

Do not mark a task or subtask complete unless every required checklist item has evidence. If evidence is missing or a checklist item fails, continue iterating.

When checking off an item, record the evidence next to the checklist item. Evidence should be specific enough for another agent or the user to audit.

## Execution Phase

Execute only one task at a time. Within that task, execute only one step or subtask at a time.

Do not advance multiple tasks in parallel. Do not bundle several steps together when they need separate analysis or review.

After completing each task or subtask:

1. Record what was done
2. Record evidence for completed checklist items
3. Write a draft result
4. Note new issues, dependencies, or required task revisions

Use accumulated drafts as the basis for the final report or final deliverable. Do not write the final version from memory when task drafts exist.

## Completion Standard

The task is complete only when the concrete standards in the `Action` section of the requirement are met.

Do not treat partial completion as final completion. If a required detail cannot be satisfied, explicitly report the blocker, the evidence gathered, and what remains unresolved.

The final deliverable must trace back to the completed tasks, their checklist evidence, and their draft results.
