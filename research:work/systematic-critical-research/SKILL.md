---
name: quick-research
description: Quickly produce a systematic, evidence-backed research note or first-pass answer. Use when the user needs fast critical research, source collection, viewpoint comparison, concise Markdown synthesis, or a structured answer before deciding whether to continue into exploration or exploitation workflow.
metadata:
  author: wjs
  last_update_time: "2026-07-03 20:50:28 HKT"
  status: active
---

# Quick Research

Use this skill for systematic critical research that should produce a quick, useful first-pass answer.

This skill is for answering a question or producing a concise research note. Use `../exploration-task-workflow/SKILL.md` instead when the main problem is deciding what direction to take next.

## Minimum Output

Produce a Markdown-style result with:

- Research question
- Short answer
- Key evidence
- Source links or local evidence paths
- Competing viewpoints or caveats when relevant
- Practical next steps

## Research Rules

Ground claims in evidence. For current facts, changing information, papers, products, laws, prices, APIs, or recent events, verify with current sources.

Separate what is known from what is inferred.

Prefer a useful first draft over an exhaustive literature review unless the user asks for depth.

If the result becomes a long-horizon project, hand off to `../exploration-task-workflow/SKILL.md` or `../exploitation-task-workflow/SKILL.md`.
