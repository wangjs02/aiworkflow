---
name: report-weekly
description: Draft, polish, or restructure Junshi Wang's weekly research update reports from draft notes, paper lists, reading summaries, experiment logs, project notes, or rough weekly research progress. Use when the user asks for a one-page weekly research report/update in formal English Markdown, especially when they provide a draft and papers read during the week.
metadata:
  author: wjs
  last_update_time: "2026-07-03 21:11:43 HKT"
  status: active
---

# Report Weekly

Use this skill to turn draft research notes and paper-reading notes into a concise, formal, one-page weekly research update report in English.

The final answer must be a standalone Markdown document inside one fenced code block so the user can copy it directly as Markdown.

Read `references/style-and-logic.md` when generating or polishing a final weekly report, especially when the task needs prior-report style, citation conventions, section patterns, file naming, or the weekly reasoning chain. For this local research-report skill, the required header and fenced-code output contract below override the generalized defaults in the reference.

## Primary Use Case

Use this when the user provides:

- A draft weekly update
- A list of papers read
- Rough research progress notes
- Experiment or analysis notes
- Questions, findings, blockers, or next steps from the week

The output should polish and synthesize the material into a one-page research report rather than merely editing sentences.

## Required Header

Use this exact header format:

```markdown
# Weekly Research Report
Author - Junshi Wang

Date - Month D, YYYY
```

Use today's date unless the user specifies another report date. Example: `Date - Feb 22, 2026`.

## Output Contract

Always output the final report as one independent fenced Markdown code block:

````markdown
```markdown
# Weekly Research Report
Author - Junshi Wang

Date - Month D, YYYY

...
```
````

Do not put the final report outside the fenced code block. A short note before the code block is allowed only if necessary.

## Style

Write in formal English.

Be concise. Aim for one page.

Prefer polished paragraphs over long bullet lists. Use bullets only when they improve readability for next steps, paper lists, or compact summaries.

Avoid casual phrasing, exaggerated claims, and excessive self-evaluation.

Do not invent paper details, citations, results, or claims not supported by the user's draft or supplied papers.

## Recommended Structure

Use this structure unless the user requests another format:

```markdown
# Weekly Research Report
Author - Junshi Wang

Date - Month D, YYYY

## Summary

One concise paragraph stating the week's main research progress, the central question, and why the work matters.

## Research Progress

One to three concise paragraphs explaining what was read, analyzed, designed, tested, or clarified this week. Connect papers and experiments to the research direction instead of listing them mechanically.

## Key Insights

One concise paragraph or a short bullet list describing the main conceptual, empirical, or methodological takeaways.

## Next Steps

A short paragraph or 2-4 bullets with concrete follow-up work.

## References

Include only when the user provided papers or sources that should be cited.
```

## Workflow

1. Identify the main research question or project direction from the draft.
2. Extract what changed this week: papers read, ideas clarified, methods compared, experiments run, blockers found, and decisions made.
3. Compress paper-reading notes into the research logic. Do not write a separate literature review unless the user asks for one.
4. Preserve important technical terms from the user's draft, but rewrite for clarity and formal style.
5. Use the supplied papers as supporting references when relevant.
6. Keep the report to roughly one page.
7. End with concrete next steps.
8. Output the final Markdown in one standalone fenced code block.

## Citation And Paper Handling

Use only papers and sources supplied by the user unless the user asks for additional research.

If paper titles are provided, cite them by title or short title. If authors, year, venue, or links are provided, preserve them in `## References`.

Use inline citations sparingly, such as `[1]` or short linked source mentions, only when they support a specific claim.

If the user gives a paper list without bibliographic details, include the available information without fabricating missing fields.

## When To Ask

Ask one short clarification question before writing only when the draft lacks a clear research direction, main progress, or next step.

If the material is messy but sufficient, infer the report structure and write the report directly.
