---
name: craft-framework
description: Create, edit, or review requirement.md documents with the CRAFT Framework: Context, Role, Action, Format, and Tone. Use whenever Codex needs to write task requirements, clarify a user's request into an executable requirement document, prepare human-agent collaboration instructions, or check whether a requirement.md is complete enough for an AI agent to execute.
metadata:
  author: wjs
  last_update_time: "2026-07-03 20:45:06 HKT"
  status: active
---

# CRAFT Framework

Use this skill for every `requirement.md` document. A valid `requirement.md` must be written with the CRAFT Framework and must contain these top-level sections in order:

1. Context
2. Role
3. Action
4. Format
5. Tone

Do not treat CRAFT as decorative formatting. Use it to make the task executable by an AI agent.

## Writing Rules

Write concrete requirements, not generic placeholders. If information is unknown but not blocking, mark it as `TBD` and keep the document usable. If missing information changes the execution plan or risk materially, ask the user before finalizing the requirement.

Preserve the user's original intent and wording where it carries important constraints. Normalize scattered notes into the five CRAFT sections.

Reference relevant skills, documents, tools, and source materials in `Context` so a later agent knows what to load before working.

## Section Requirements

### Context

Describe the background information needed to understand the task:

- What the task is roughly about
- Why the task should be done
- Current project progress or current state
- Difficulties, blockers, or uncertainty already known
- Documents, files, notes, or links the agent should read
- Tools, materials, or skills the agent can use

### Role

Define the role and angle the AI agent should take while executing the task:

- What kind of expert, collaborator, reviewer, implementer, researcher, or planner the agent should act as
- What priorities and judgment style the agent should use
- What perspective the agent should avoid if that matters

### Action

Specify the concrete work to complete:

- What the task output is: report, codebase change, plan, analysis, dataset, document, or other artifact
- What inputs and outputs are expected
- Which sources, files, or materials deserve attention
- Which questions must be answered or problems must be solved
- How the agent should self-check the result
- Whether the agent should ask for feedback midway or work through the task and report after completion

### Format

Define how the AI should perform and package the work:

- Constraints that must be respected
- Preparation steps before execution
- Checklist requirements
- Rules for the work-in-progress phase
- Completion standard and stopping criteria
- Required output structure, if the final response or artifact needs one

### Tone

Define the communication style the AI should use:

- Conversational, direct, professional, academic, concise, detailed, or another tone
- Whether the final output should sound like a working note, formal report, implementation summary, research memo, or user-facing explanation
- Any language preference or terminology style

## Requirement Template

Use this structure when creating a new `requirement.md`:

```markdown
# Requirement

## Context

- Task:
- Purpose:
- Current state:
- Known difficulties:
- Materials to read:
- Available tools or skills:

## Role

- Agent role:
- Execution angle:
- Priorities:

## Action

- Deliverable:
- Inputs:
- Outputs:
- Questions to resolve:
- Self-check:
- User feedback plan:

## Format

- Constraints:
- Preparation:
- Checklist:
- During execution:
- Completion standard:
- Final output format:

## Tone

- Style:
- Level of detail:
- Language:
```

## Review Checklist

When reviewing a `requirement.md`, check:

- It uses all five CRAFT sections in the required order
- `Context` gives enough background and links to relevant materials
- `Role` makes the agent's stance and judgment criteria clear
- `Action` defines concrete deliverables, inputs, outputs, and self-checks
- `Format` defines constraints, checklist behavior, execution process, and completion criteria
- `Tone` states how the agent should communicate
- Any `TBD` item is either safe to leave open or explicitly raised as a question for the user
