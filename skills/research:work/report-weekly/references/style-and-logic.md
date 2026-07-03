# Weekly Report Style And Logic

This reference summarizes the format, naming convention, and writing logic extracted from prior reports. The source examples are research reports, but the skill should generalize the same concise weekly-update logic to other projects, including quantitative research and engineering work.

`/Users/wjs/Library/CloudStorage/OneDrive-Personal/My Research/weekly report/`

## Naming

Report files use:

```text
weekly report - YYYYMMDD.md
```

Examples:

- `weekly report - 20260125.md`
- `weekly report - 20260222.md`
- `weekly report - 20260526.md`

Some reports are stored as `.textbundle`; in those cases, the Markdown body is at:

```text
weekly report - YYYYMMDD.textbundle/text.md
```

## Header

Use the generalized header by default:

```markdown
# Weekly Report
Author - Junshi Wang

Date - May 26, 2026
```

The historical examples often use `# Weekly Research Report`; preserve that legacy title only when the user explicitly asks for a research-only report or when editing an existing report that already uses it. Earlier files sometimes omit the blank line before `Date`; prefer the blank line.

## Optional Epigraph

Several reports include a short quote after the date and before the first section:

```markdown
> Quote text - Author
```

This is optional. Do not add a decorative quote unless the user provides one or the draft clearly contains one intended for the report.

## Common Section Patterns

The exact section names vary by week. Choose names that match the actual weekly logic.

Common openings:

- `## Research Progress / Project Progress`
- `## Summary`
- `## Overview`

Common body sections:

- Conceptual framing or rationale, e.g. `## Conceptual Development`, `## Rationale Behind Physiological Design`, `## Strategy Rationale`
- Literature/source synthesis, e.g. `## Literature Review`, `## Survey of General Multimodal Learning Approaches`, `## Market and Data Review`
- Model/design section, e.g. `## New Model Design Architecture`, `## Coupling and Feedback Loop Model`, `## Quant Model Development`
- Experiment/diagnosis section, e.g. `## Existing Model Training and Debugging`, `## New Design Model Diagnosis`, `## Backtest and Error Analysis`
- Application/context section, e.g. `## Application Context`

Common endings:

- `## Next Steps`
- `## References`

Use 3-6 sections for a one-page report. Avoid over-fragmenting.

## Writing Style

The style is formal, concise, and project-oriented. For research weeks, keep the academic tone; for quant or engineering weeks, keep the same rigor but focus on hypotheses, data, implementation, results, risk, and next actions.

Prefer:

- Short paragraphs with clear topic sentences.
- A visible progression from motivation to evidence to conclusion.
- Explicit statements of the main conceptual or experimental conclusion.
- Limited bullet points only when they clarify research questions, model components, diagnoses, or next-step lists.
- Strong verbs such as `motivated`, `suggests`, `indicates`, `clarified`, `supports`, `revealed`, `diagnosed`.

Avoid:

- A chronological diary of tasks.
- Excessive bullet points.
- Overly promotional language.
- Vague claims such as "I read many papers" without explaining the insight gained.
- Unexplained technical lists that do not support the weekly argument.

## Core Logic

The most important feature is a logical weekly chain. The report should not merely summarize what happened; it should show how this week's work advanced the project.

A strong report usually follows this pattern:

1. **Motivation or problem:** What research, modeling, trading, engineering, or design uncertainty framed the week?
2. **Evidence gathering:** What papers, discussions, experiments, or notes were used?
3. **Synthesis:** What conceptual framework, diagnosis, or design principle emerged?
4. **Concrete progress:** What model, experiment, literature map, backtest, dataset, implementation, or project decision changed?
5. **Open issue:** What remains unresolved?
6. **Next action:** What will be done next because of the open issue?

If the user gives a clearly ordered story, preserve that order. If the user provides scattered notes, infer this chain and ask for confirmation before finalizing.

## Citation And References

Use inline citations where a specific claim relies on a paper or website:

```markdown
... homeostasis is an active regulatory process [1].
```

Then list all cited sources under:

```markdown
## References

[1] [Title](URL)
[2] Author, Title. Venue. Year.
```

Both numeric link references and bullet references appear in prior reports. Prefer numeric references when the body uses `[1]`, `[2]`.

If the user provides websites or papers in messy notes, cite only sources that are actually used in the report. Do not include unused references solely because they appeared in the raw notes.

## Markdown Delivery

When the user asks for copyable Markdown, output only one fenced code block containing the complete report:

````markdown
```markdown
# Weekly Report
Author - Junshi Wang

Date - Jun 1, 2026

...
```
````

Do not add explanatory prose outside the code block unless the user asks for it.
