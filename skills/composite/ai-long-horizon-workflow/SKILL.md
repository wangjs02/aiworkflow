---
name: ai-long-horizon-workflow
description: Highest-level agent workflow skill for complex human-agent interaction and task execution. Use at the start of most complex tasks, long-horizon work, multi-step projects, research or coding projects, and tasks that require planning, collaboration structure, memory organization, uncertainty handling, checklist discipline, or coordination of lower-level skills such as CRAFT Framework, File Organization, Code Organization, Exploitation Task Workflow, Exploration Task Workflow, and AI Complex Project Guidance.
metadata:
  author: wjs
  last_update_time: "2026-07-03 20:45:06 HKT"
  status: active
---

# AI Long Horizon Workflow

This is a composite orchestration skill. Use it to decide which fundamental skill to load and in what order. Do not duplicate the detailed procedures from the fundamental skills here.

## Core Rule

Load only the fundamental skill needed for the current decision point. If multiple layers are needed, load them in this order:

1. Human-agent interaction
2. Agent memory structure
3. Agent task structure
4. Agent work-time structure

If a referenced fundamental skill is still a placeholder or missing detailed instructions, use this skill's routing intent, state the missing dependency briefly, and continue with the best local judgment.

## Skill Map

Paths are relative to this `SKILL.md`.

| Layer | Use For | Fundamental Skill | Path |
| --- | --- | --- | --- |
| Human-agent interaction | Defining how the human and agent should communicate, clarify, constrain, and hand off work | CRAFT Framework | `../../fundamental/craft-framework/SKILL.md` |
| Agent memory structure | Natural language files such as Markdown notes, research docs, plans, reports, and project journals | File Organization | `../../fundamental/file-organization/SKILL.md` |
| Agent memory structure | Code, configuration, generated artifacts, datasets, and other non-natural-language project files | Code Organization | `../../fundamental/code-organization/SKILL.md` |
| Agent task structure | Tasks with high certainty, known goals, clear acceptance criteria, and mostly known execution paths | Exploitation Task Workflow | `../../fundamental/exploitation-task-workflow/SKILL.md` |
| Agent task structure | Tasks with low certainty, unclear assumptions, weak evidence, uncertain feasibility, or no obvious direction yet | Exploration Task Workflow | `../../fundamental/exploration-task-workflow/SKILL.md` |
| Agent work-time structure | Long, complicated, multi-step work that needs checklist discipline and progress state across time | Complicated Task Checklist Guidance | `../../fundamental/ai-complex-project-guidance/SKILL.md` |

## Routing

Start with CRAFT Framework when the task depends on collaboration quality: ambiguous requests, changing preferences, important constraints, expected back-and-forth, or handoff between human and agent.

Use File Organization when the durable output is primarily natural language: Markdown, Notion-derived notes, research writeups, project docs, weekly reports, literature reviews, decision logs, or meeting notes.

Use Code Organization when the durable output is primarily executable or structured project material: source code, configs, test fixtures, generated data, model artifacts, notebooks, package structure, deployment files, or automation scripts.

Use Exploitation Task Workflow when the task has high certainty: the goal is stable, the path is known, dependencies are local, success criteria are clear, and implementation can proceed directly.

Use Exploration Task Workflow when the task has low certainty: the user does not know what to do next, the goal or method is unclear, important assumptions need evidence, the work involves research or diagnosis, or multiple directions must be compared before execution.

Use Complicated Task Checklist Guidance when the task is long enough to require explicit progress control: multiple phases, repeated verification, context transitions, resumable state, or risk of losing track of open loops.

## Composition Patterns

For a long coding project, usually combine:

1. CRAFT Framework
2. Code Organization
3. Exploitation Task Workflow or Exploration Task Workflow
4. Complicated Task Checklist Guidance

For a long research or writing project, usually combine:

1. CRAFT Framework
2. File Organization
3. Exploration Task Workflow
4. Complicated Task Checklist Guidance

For a concrete maintenance task with clear requirements, usually combine:

1. Code Organization or File Organization
2. Exploitation Task Workflow

For an unclear strategic or research task, usually combine:

1. CRAFT Framework
2. File Organization
3. Exploration Task Workflow

## Source Links

- CRAFT Framework: https://app.notion.com/p/CRAFT-Framework-3924448b2bf88062a982cc172c0f3961?pvs=21
- File Organization: https://app.notion.com/p/File-Organization-3924448b2bf8808f9bc2e16cf3a16581?pvs=21
- Code Organization: https://app.notion.com/p/Code-Organization-3924448b2bf8804eb7d9e82fb14a1d89?pvs=21
- Exploitation Task Workflow: https://app.notion.com/p/Project-Task-WorkFlow-3924448b2bf880d98019ec390d8dba8d?pvs=21
- Exploration Task Workflow: https://app.notion.com/p/HEPE-Workflow-3924448b2bf88041a31ff393c135700f?pvs=21
- Complicated Task Checklist Guidance: https://app.notion.com/p/AI-3924448b2bf88000bea6dba965f6a488?pvs=21
