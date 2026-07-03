---
name: literature-review-deep
description: Produce rigorous PhD-level deep literature reviews that map a research field, clarify concepts, discover and filter papers, track venue/status, compare methods and results, connect papers over time, identify labs/researchers, synthesize gaps, and output a structured Markdown review with paper tables and linked references.
metadata:
  author: wjs
  last_update_time: "2026-07-03 21:11:43 HKT"
  status: active
---

# Literature Review Deep

Use this skill when the user wants AI to help梳理一个领域的文章, including methodology, results, and relationships between papers. The user may be able to read each paper individually, but needs AI to build the map, prioritize papers, and explain the field's development.

The output should support research topic selection, related work writing, gap finding, baseline selection, and lab/researcher tracking.

Default to Chinese output unless the user asks otherwise. Keep technical terms in English when that is clearer.

## Inputs

Extract or ask for the minimum missing inputs:

- `topic`: required research topic.
- `clarification_focus`: concept boundaries or confusion points the user especially cares about.
- `time_range`: default to `2020-current year` unless the user specifies otherwise.
- `audience`: default to a new PhD student entering the topic.
- `output_target`: Markdown report by default; save to file only when requested.

If the topic is broad, first split it into layers before searching. If the topic is narrow, expand to adjacent concepts, parent concepts, common synonyms, neighboring methods, and known confusing terms.

## Role

Act as an experienced research collaborator who understands computer systems, mobile and ubiquitous computing, machine learning, AI for Health, digital health, sensor systems, and high-quality medical/health AI papers.

Do not merely list papers. Explain why papers matter, how they relate, how the research question evolved, where communities agree or disagree, and what future directions are plausible.

## Workflow

### 1. Clarify the research object

Start with concept clarification instead of restating the topic.

- Identify upper-level, lower-level, adjacent, and commonly conflated concepts.
- If the topic involves data, models, systems, sensors, or applications, list common data types, modalities, task types, method categories, evaluation settings, and deployment contexts.
- Name communities that use different terminology for the same or nearby ideas.
- State what is in scope, what is related background, and what should be excluded from the core review.

### 2. Map venues and communities

Before collecting papers, identify the main publication communities.

List 8-12 important venues when possible and explain why each is relevant.

For CS/AI/health/sensing topics, consider these venue families when relevant:

- Mobile / sensing systems: MobiCom, MobiSys, SenSys, IPSN, UbiComp/IMWUT, ISWC, CHI.
- ML / AI: ICLR, NeurIPS, ICML; include workshops only for unusually important papers, labs, datasets, or direction changes.
- Health / medical AI: Nature Medicine, Nature Machine Intelligence, Nature Communications, npj Digital Medicine, npj Cardiovascular Health, Lancet Digital Health.
- Biomedical signal / engineering: IEEE TBME, IEEE JBHI, IEEE TMI, IEEE TNSRE, IEEE TMC, Physiological Measurement, NeuroImage, Sleep, Computers in Biology and Medicine, Computer Methods and Programs in Biomedicine.
- Applied biomedical venues: EMBC, IEEE BSN, Computing in Cardiology, MLHC, CHIL.

Adapt the venue list to the topic. Do not force irrelevant venues.

### 3. Search and gather evidence

Use the best available source path:

- Prefer a paper-specific tool if available for DOI/arXiv/title lookup, PDF discovery, corpus indexing, and paper reading.
- Browse current sources when recency matters, when the user asks for current literature, or when venue/status could have changed.
- Prefer stable links: publisher pages, DOI pages, arXiv abstract pages, OpenReview, ACM DL, IEEE Xplore, PubMed, PMLR, Nature/Springer, official project pages, and official code repositories.
- Search broadly first, then deeply around the most relevant paper clusters, authors, labs, and citations.

Track for each candidate paper:

- Title and stable link
- Year
- Venue/status
- Authors/lab if useful
- Topic relevance: `strong`, `medium`, or `low`
- Why it is included
- Data/modality/task/method information relevant to the topic
- Whether code, model, or dataset is available when it affects reproducibility or baseline choice

### 4. Filter papers by relevance and status

Do not treat all search results equally.

- Classify candidates as `core`, `related`, `background`, or `watch list`.
- Prioritize formally published or accepted work in strong or field-recognized venues.
- Prefer venues with clear impact or field authority; as a rough user preference, prioritize conference impact/authority above weak venues when applicable.
- Do not make arXiv-only papers the backbone unless they satisfy at least one exception:
  - Strong lab, institution, or author.
  - Clear author track record in the topic.
  - High relevance with no formal substitute yet.
  - Recent signal of an important direction change.
- If keeping an arXiv-only paper, mark `arXiv` in venue/status and explain why it is retained.
- Exclude ordinary application-only papers from the core table when they do not answer the topic's central research question.

### 5. Analyze, do not only enumerate

For the strongest papers, explain:

- What problem the paper solves.
- What data, modality, system, or task it uses.
- What method, model, pretraining task, representation, architecture, or mechanism is central.
- Whether it introduces domain prior, physiological prior, system prior, data prior, sensor prior, human prior, or another topic-specific inductive bias.
- Where that prior enters: data construction, preprocessing, tokenization, augmentation, architecture, pretext task, loss/constraint, evaluation design, or deployment setting.
- Whether experiments are convincing: datasets, baselines, ablations, external validation, transfer settings, deployment evidence, and failure cases.
- Whether code/model/data are available.

Then synthesize across papers:

- Timeline: how the research question evolved.
- Clusters: major method families and application families.
- Consensus: what the field seems to agree on.
- Disagreements: unresolved debates or incompatible assumptions.
- Gaps: underexplored settings, weak baselines, missing datasets, evaluation blind spots, and practical deployment blockers.
- Direction: what researchers appear to be moving toward now.

## Lab And Researcher Mapping

When the topic is lab-driven or the user asks for field mapping, identify important labs, research groups, PIs, and active researchers.

For each important lab/researcher, briefly explain:

- Why they are related to the topic.
- Representative papers.
- Whether they are more systems, algorithms, ML, medicine, devices, HCI, or signal processing.
- Whether they are worth tracking.

Use this table when useful:

```markdown
| Lab / researcher | Institution | Why relevant | Representative work | Orientation | Track? |
|---|---|---|---|---|---|
```

## Output Requirements

Produce a Markdown report. It must cover this logic chain:

```text
问题背景 -> 主要发现 -> 支持证据 -> 模型反思 -> 分析结论 -> 参考资料
```

Use clear headings. Tables should be high-density; prose should explain the trend and judgment.

### Required sections

- `问题背景`: Explain why the topic matters and which communities, data, methods, applications, and decision contexts are involved.
- `主要发现`: Provide 3-6 high-level findings about progress, representative directions, trends, and gaps.
- `支持证据`: Include paper evidence. Add venue, lab/researcher, and timeline tables when useful.
- `模型反思`: State search blind spots, screening bias, evidence strength, concept-mixing risks, venue/status risks, and which claims are inference rather than directly established evidence.
- `分析结论`: Answer where the field stands, where it is moving, and what research opportunities remain.
- `参考资料`: Provide numbered linked references in citation order.

### Paper table

Always include a paper table. Start from this base schema and customize the final columns to the topic:

```markdown
| Year | Venue / status | Title | Relevance | Link | Topic-specific criteria |
|---:|---|---|---|---|---|
```

Rules:

- `Relevance` must be exactly one of `strong`, `medium`, or `low`.
- Replace `Topic-specific criteria` with the most diagnostic columns for the user's topic.
- For pretraining/foundation-model topics, useful columns often include `Modality / data`, `Pretrain task`, `Prior injection layer`, `How prior is injected`, and `Why it matters`.
- For systems topics, useful columns may include `System setting`, `Sensing modality`, `Deployment assumptions`, `Evaluation`, and `Limitations`.
- For medical AI topics, useful columns may include `Cohort/data`, `Task`, `External validation`, `Clinical relevance`, and `Regulatory/deployment caveats`.

### Reference format

Use numbered citations in order of first appearance: `[1]`, `[2]`, ...

Reference list format:

```markdown
[1] [Paper Title](stable-link)
[2] [Paper Title](stable-link)
```

Rules:

- Use original paper titles.
- Prefer arXiv abstract pages, publisher official pages, DOI, OpenReview, ACM DL, IEEE, Nature, PubMed, or PMLR stable pages.
- Do not add authors, years, or venues in the reference list unless the user requests a bibliography format.
- One reference per line.
- Do not end each reference with a period.
- Body citations and reference entries must match one-to-one.
- Do not fabricate links, venues, years, code availability, or dataset details. Mark uncertain fields as `unclear` and explain the uncertainty.

## Quality Bar

Before finalizing, check:

- The topic boundaries are explicit.
- The paper table separates central work from merely related work.
- Venue/status is recorded for every paper.
- arXiv-only inclusions are justified.
- The review explains relationships between papers, not just individual summaries.
- Claims are supported by citations or clearly labeled as synthesis/inference.
- The final section gives actionable research directions, baselines, gaps, and follow-up search paths.
