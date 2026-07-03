---
name: literature-review-shallow
description: Quickly build enough background to read an unfamiliar-domain paper or topic. Use when the user wants a shallow literature review, fast paper entry map, prerequisite keyword map, paper-reading checklist, or SpeedyLearn-style output from a paper title, abstract, introduction, PDF text, topic, or keyword set.
metadata:
  author: wjs
  last_update_time: "2026-07-03 21:11:43 HKT"
  status: active
---

# Literature Review Shallow

Use this skill to turn "I cannot yet read this field's paper" into a fast, executable learning workflow. This is the renamed local version of the previous SpeedyLearn workflow.

## Goal

Help the user quickly reach the level needed to read a specific paper or a narrow unfamiliar research topic.

- Use `paper` mode to build problem awareness, a minimal field map, the paper's research story, and a reading checklist.
- Use `keyword` mode to extract and rank prerequisite concepts, paper-native keywords, and learner-bridge keywords.

## Core Workflow

1. Clarify the task input.

```text
- Task mode: paper or keyword
- Paper source: title / link / abstract / introduction / PDF text
- User background: known fields and skills
- Learning goal: e.g. 48 hours / 7 days
- Optional filename preference
- Optional output directory preference
```

2. Resolve and create an independent output folder for this task.

- Each shallow literature review task must use its own folder unless the user explicitly asks to write directly into an existing directory.
- If the user provides an output directory, create the task folder inside it.
- If the user does not provide an output directory, create the folder under the current workspace or active research-note destination:

```text
shallow-lit-review-<YYYY-MM-DD>-<paper-or-topic-slug>/
```

- Derive `<paper-or-topic-slug>` from the paper title, arXiv ID, DOI, topic name, or user-provided filename.
- Use lowercase hyphen-case, remove punctuation, and keep the slug to roughly 6-12 words.
- If the directory already exists and belongs to the same task, continue using it. If writing would overwrite unrelated files, create a `-v2` or `-v3` folder unless the user explicitly asks to overwrite.

3. Select the appropriate reference template.

- `paper` mode: read `references/paper-prompt.md`.
- `keyword` mode: read `references/keyword-prompt.md`.
- When the user's background is not specified, use `references/learner-profile.md` as the default learner profile.

4. Produce mode-specific files in the task folder when saving is requested.

- `paper` mode:
  - `paper-study.md`
  - `paper-reading-checklist.md`
- `keyword` mode:
  - `prerequisite-keywords.md`
  - `keywords-table.md`
  - `keywords-explained.md`

5. Handle missing information explicitly.

- If the paper/topic information is insufficient, state which fields are missing.
- Mark all inference as "这是推测".
- Provide links for factual sources when available.
- Do not turn the task into a broad survey unless the user asks for one.

## Prompt Execution Details

### 1. Collect Minimal Fields

For `paper` mode, collect:

- field or topic name
- paper identifier
- current difficulty
- user background
- learning goal

For `keyword` mode, collect:

- paper identifier
- user background
- known keywords, if any
- learning goal
- whether prerequisite output is needed

### 2. Use Existing Workspace Files

If the paper is already in a study folder, accept file paths or path fragments. Prefer reading:

- `paper.pdf` or title-page metadata
- user-provided abstract or introduction
- local `learner-profile.md`, if present and not superseded by the user

### 3. Output Style

- Write in Chinese by default.
- Follow the selected template structure.
- Avoid generic study advice.
- Tie every explanation back to the current paper, topic, and user goal.
- Make prerequisite order and reading order explicit.

### 4. File Output Convention

When the user asks to save files:

1. Create one independent folder:

```text
shallow-lit-review-<YYYY-MM-DD>-<paper-or-topic-slug>/
```

2. Write fixed filenames inside that folder:

- `paper` mode: `paper-study.md`, `paper-reading-checklist.md`
- `keyword` mode: `prerequisite-keywords.md`, `keywords-table.md`, `keywords-explained.md`

3. Add optional files only when useful:

- If a PDF is downloaded or provided, place it in the same folder as `paper.pdf`.
- If a local learner profile is provided, reference it or copy it only when it is task-specific.

4. At the top of each saved Markdown document, include:

```text
学习目标：<user time/task goal>
来源：<paper or topic identifier>
更新：<current date>
```

## Quality Gates

- The output identifies which knowledge gaps block the next reading step.
- `paper` mode explains problem, motivation, method, evidence, and limitations.
- `keyword` mode distinguishes prerequisites from paper-native keywords.
- The learning order is actionable and scoped to the user's immediate goal.
- Facts and external recommendations include links when available.
