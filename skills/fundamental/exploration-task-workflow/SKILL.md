---
name: exploration-task-workflow
description: Explore uncertain tasks when the user does not know what to do next but AI may know enough to help. Use for low-certainty work, early research, diagnosis, unfamiliar domains, direction finding, assumption discovery, option comparison, quick AI-assisted Q&A, and turning unclear questions into evidence-backed next steps before execution.
metadata:
  author: wjs
  last_update_time: "2026-07-03 20:45:06 HKT"
  status: active
---

# Exploration Task Workflow

Use this skill when the problem is: "AI may know, but I do not know what to do next."

The goal is to use AI to quickly answer questions, surface relevant knowledge, compare directions, and produce a concrete next step. This is an exploration workflow, not an execution workflow.

Use `../exploitation-task-workflow/SKILL.md` instead when the goal, path, and acceptance criteria are already clear.

## Core Pattern

Use a lightweight exploration loop:

1. Hypothesis
2. Evidence
3. Plan
4. Execution Decision
5. Reflection

The output of this skill should usually be a direction, decision, research note, task proposal, or handoff into an exploitation workflow.

## Hypothesis

State the current uncertainty explicitly:

- What does the user not know?
- What decision or direction is blocked?
- What assumptions might be true?
- What would change the next step?
- What does the agent need to learn or verify?

Write multiple candidate hypotheses when the situation is broad. Do not collapse uncertainty into one plan too early.

## Evidence

Gather enough evidence to reduce uncertainty:

- Ask AI for explanations, conceptual maps, examples, and likely approaches
- Inspect local files, project docs, code, data, or prior notes when relevant
- Search external sources when current facts, papers, products, laws, prices, APIs, or recent events matter
- Compare precedents, patterns, and alternative approaches
- Record evidence that changes the decision

Evidence must be connected to the next decision. Do not collect background material that does not affect direction.

## Plan

Convert evidence into options:

- Option A, B, C, with tradeoffs
- What each option requires
- What each option would produce
- Risks and unknowns
- What evidence favors or weakens each option
- Recommended next step

If no option is clearly best, choose the cheapest next experiment that can reduce uncertainty.

## Execution Decision

End exploration by deciding what should happen next:

- Move into `exploitation-task-workflow` for clear execution
- Continue exploration with a narrower question
- Create or update a `requirement.md`
- Create a task file under a project node
- Stop and ask the user for a decision if the choice depends on preference, risk tolerance, budget, or project priority

Do not pretend exploration has solved the task when it has only clarified the task.

## Timestamped Notes

For substantial exploration, write timestamped notes using local time:

```text
YYYYMMDD-HHMMSS-topic.md
```

Suggested locations:

- `docs/research/` for research notes
- `docs/design/` for direction or design options
- `docs/reflection/` for failed assumptions or post-decision learning
- `projects/<project-name>/` when the exploration belongs to a concrete project

Each note should include:

```markdown
Timestamp: YYYY-MM-DD HH:MM:SS <timezone>
```

Prefer one focused note per exploration question. Link earlier notes when a later decision depends on them.

## Acceptance For Exploration

Exploration is complete when it produces at least one of:

- A clear recommended direction with evidence
- A short list of viable options and tradeoffs
- A smaller question that should be explored next
- A concrete execution task for exploitation workflow
- A clear blocker that requires user judgment or external input

Do not require implementation-level acceptance criteria unless the work has moved into exploitation.

## Subagents

Use subagents when independent exploration can improve quality:

- Parallel research tracks
- Independent option generation
- Separate source review
- Stress-testing a proposed direction
- Comparing design alternatives

Give subagents only task-local context, raw artifacts, and the question they should answer. Do not give them the expected answer unless the task is explicitly to review it.

Do not use subagents for small local questions where direct inspection is faster.

## Reflection

Write a brief reflection after failed assumptions, surprising evidence, rejected approaches, or direction changes.

Record:

- What was assumed
- What evidence changed the assumption
- What direction was chosen or rejected
- What uncertainty remains
- What the next agent should avoid repeating

Keep reflections operational and concise.

## Review Checklist

Before ending exploration, check:

- The original uncertainty is stated clearly
- Evidence is tied to the decision
- Options are compared rather than listed passively
- The recommended next step is concrete
- Remaining uncertainty is explicit
- The workflow either hands off to exploitation, narrows exploration, or asks the user for a decision
