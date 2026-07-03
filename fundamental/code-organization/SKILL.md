---
name: code-organization
description: Design and review code repositories from a system perspective with explicit module boundaries, input/output contracts, module-level README files, same-name code documentation, public APIs, dependency maps, sample cases, failure modes, and neural-network design notes. Use when planning or editing a codebase, creating modules, documenting Python or other code files, controlling entropy during AI coding, or separating dev/prod code responsibilities.
metadata:
  author: wjs
  last_update_time: "2026-07-03 20:45:06 HKT"
  status: active
---

# Code Organization

Use this skill to design a codebase as a system of independent modules with explicit contracts.

The purpose is to minimize entropy during AI-assisted coding. Because much of the project design happens in natural language, the codebase must be organized so agents can reason from documents, module contracts, and examples before touching implementation details.

## Repository-Level Principle

Design the repository as a composite of separate modules. Each module should understand only:

- Its own responsibility
- Its inputs
- Its outputs
- Its public API
- The public contracts of modules it depends on

A module should not need to understand the internal logic of other modules.

For example, if the repo has a `message_gateway` module and a `task_manager` module, define:

- What `message_gateway` receives
- What `message_gateway` emits
- What `task_manager` receives
- What `task_manager` emits
- How the two modules interact

The internal implementation of `message_gateway` should not affect `task_manager` as long as the input contract to `task_manager` remains unchanged.

## Module Boundary Rules

Keep module boundaries explicit:

- Interact through public APIs, schemas, or documented data contracts
- Avoid importing private implementation details from another module
- Avoid circular dependencies between modules
- Keep shared types, schemas, or protocols in a clearly owned shared module when needed
- Treat input/output contract changes as system-level changes
- Update downstream documentation and sample cases when a public contract changes

Before implementing module internals, define the module's inputs, outputs, public API, and dependencies.

## Module-Level Documentation

Each module must have a `README.md` explaining the module's purpose and interface.

The module README must include these sections. Use `N/A` only when a section truly does not apply.

```markdown
# <Module Name>

## Purpose

## Inputs

## Outputs

## Public API

## Dependencies

## Used By

## Responsibilities

## Boundaries

## Architecture

## Tensor Contract

## Debug Checklist

## Sample Case

## Failure Modes
```

Use `Architecture` for complex module structure, multi-component logic, state machines, or important data flow.

Use `Tensor Contract` only for neural-network, tensor-heavy, or array-shape-sensitive modules. Otherwise write `N/A`.

The module README should explain:

- What the module is for
- What inputs it accepts and where those inputs come from
- What outputs it produces and who uses those outputs
- Which objects, functions, classes, schemas, or commands are important
- Which other modules it depends on
- Which modules depend on it
- What belongs inside the module
- What must stay outside the module

## Same-Name Code Documentation

Every important code file must have a same-name Markdown document next to it.

Examples:

```text
feature_builder.py
feature_builder.md

message_gateway.ts
message_gateway.md
```

The same-name Markdown file must explain the code logic and usage in enough detail that an agent could reconstruct the implementation from the document if code comments were missing.

For each code file document, include these sections:

```markdown
# <Code File Name>

## Purpose

## Inputs

## Outputs

## Public API

## Dependencies

## Used By

## Responsibilities

## Boundaries

## Architecture

## Tensor Contract

## Debug Checklist

## Sample Case

## Failure Modes
```

In `Inputs`, state which module, file, user action, external API, dataset, tensor, or command provides each input.

In `Outputs`, state which module, file, notebook, API caller, model, user interface, or downstream process consumes each output.

In `Public API`, list only the objects that other files or modules should call directly.

In `Dependencies`, distinguish internal module dependencies from cross-module dependencies and external libraries.

In `Used By`, list known downstream modules or entrypoints. If unknown, write `Unknown` rather than inventing usage.

In `Boundaries`, state what this file should not do.

## Neural Network And Complex Model Design

For complex model design, write the design clearly before or alongside implementation.

For neural-network, tensor-heavy, CNN, ViT, transformer, embedding, sequence, or other shape-sensitive code, the Markdown design must include:

- Architecture overview
- Tensor Contract
- Shape transformation path
- Sample case
- Failure modes
- Debug checklist

The sample case must be concrete enough to show how an input tensor is processed through the model.

When the `neural-net-design` skill exists, load it for detailed model design. Until that skill is available, use this section as the minimum requirement.

## Design Workflow

When creating or reorganizing code:

1. Identify the modules
2. Define each module's purpose, inputs, outputs, dependencies, and users
3. Write or update each module `README.md`
4. Define public APIs and cross-module contracts before implementing internals
5. Add same-name Markdown documentation for important code files
6. Implement internals without leaking private assumptions across module boundaries
7. Update sample cases and debug checklists
8. Review whether a module can be modified internally without breaking downstream users

If the answer is no, tighten the public contract or split responsibilities.

## Review Checklist

When reviewing a codebase or code change, check:

- The repo is understandable as separate modules
- Each module has a clear responsibility
- Modules interact through documented inputs, outputs, and public APIs
- Module internals are not required knowledge for other modules
- Cross-module dependencies are explicit and justified
- Each module has a useful `README.md`
- Important code files have same-name Markdown documents
- Inputs record where data comes from
- Outputs record who consumes the result
- Public API is separated from private implementation detail
- Complex model or neural-network logic includes architecture, tensor contract, and sample case
- Failure modes and debug checklists are documented
