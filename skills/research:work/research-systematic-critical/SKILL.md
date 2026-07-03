---
name: research-systematic-critical
description: 快速生成研究型 Markdown 初稿。Use when the user asks to quickly research a question, replace a long evidence-gathering prompt, create a dated research note, compare viewpoints, collect authoritative sources, produce a Markdown report/table with citations, or save research into the My Research date-based folders.
metadata:
  author: wjs
  last_update_time: "2026-07-03 21:11:43 HKT"
  status: active
---

# Research Systematic Critical

## Purpose

Use this skill to turn a research question into a concise, evidence-backed Markdown report. It is optimized for exploratory product, market, social science, policy, healthcare, technology, macro, and business questions where the user wants a first-pass answer with sources, reflection, and a saved research note.

## Trigger Shape

Typical requests:

- `用 quickresearch 研究：养老到底是什么，怎么定义的`
- `quickresearch：慢病管理目前大家怎么解决？保存到 May 16`
- `帮我快速研究这个问题，输出 table，放到今天文件夹`
- `替代我之前那段资料查找 prompt，做一个初步回答`

## Workflow

1. Resolve the research question.
   - Extract the core question from the user request.
   - If the user provides existing notes, hypotheses, selected text, or prior findings, treat them as inputs to verify rather than as facts.
   - If the question is broad, state the most relevant domain role at the top, such as `养老与医疗服务交叉领域研究者` or `科技与宏观经济交叉领域研究者`.

2. Resolve language and scope.
   - Default to Chinese when the user writes in Chinese.
   - Keep the user's language unless they explicitly request another language.
   - If the user specifies geography, industry, user segment, or date, preserve it.
   - If the user says `今天`, use the current environment date.

3. Gather evidence.
   - Browse when facts may be current, when precise citations are needed, or when the user asks for sources.
   - Prioritize authoritative Chinese and English sources:
     - government agencies
     - universities
     - international research institutions
     - peer-reviewed papers
     - official company/product pages
     - reputable financial/business media
     - industry research reports
   - Avoid Zhihu, Xiaohongshu, Toutiao, random blogs, and social platforms unless the user explicitly asks for them.
   - For OpenAI/API topics, follow the `openai-docs` skill instead of this general source rule.

4. Analyze with the HEPE-lite structure.
   - Explore the problem: define what is being asked and why it matters.
   - Collect evidence: summarize data, viewpoints, and product/company examples.
   - Verify assumptions: compare sources and check whether claims conflict.
   - Reflect: identify blind spots, missing data, weak evidence, and likely explanations.
   - Conclude: answer the user directly and explain whether the result matches common intuition.

5. Save when requested.
   - If the user asks to save, create, put into a doc, add to a doc, or place in a folder, use `report-organization` routing rules.
   - Default path pattern:
     `/Users/wjs/Library/CloudStorage/OneDrive-Personal/My Research/2026/<MonthAbbr>/<YYYY-MM-DD>/`
   - Create the date folder if needed.
   - Use a clear Chinese filename based on the research question, ending in `.md`.
   - If the user asks to add to an existing document, inspect the target document first and append or insert in the most relevant section.

## Required Markdown Report Structure

Use this structure unless the user asks for a different shape:

```markdown
# {研究问题标题}

> 角色设定：你是{自动判断领域}专家，需要进行：探索问题 -> 搜集证据 -> 验证假设 -> 提出反思。

## 问题背景

约 200 字。说明问题为什么值得研究，涉及哪些利益相关方、场景或决策。

## 主要发现

至少 3 个发现。每个发现包含：观点、解释、证据引用。

## 支持证据

用表格整理关键数据、观点、来源、含义、局限。

## 模型反思

交叉比较主要观点。指出冲突、盲点、数据缺口、适用边界和可能解释。

## 分析结论

直接回答用户问题。说明结论与常识预期是否一致或相悖。

## 参考资料

[1] [原文标题](直达链接)
[2] [原文标题](直达链接)
```

## Citation Rules

- Cite sources in the body as `[1]`, `[2]`, etc.
- Number references in first-citation order.
- Keep every reference clickable and one per line.
- Reference format:
  `[编号] [原文标题](直达链接)`
- Prefer official pages, paper landing pages, DOI pages, PubMed pages, arXiv abstract pages, or stable institutional URLs.
- Do not add author/year/conference in the reference list unless needed to disambiguate.
- If a claim has no reliable source, mark it as `模型推测`.
- Do not overquote source text; summarize instead.

## Table Defaults

When the user asks for a table or the topic benefits from comparison, include one or more tables with columns such as:

- `观点/发现`
- `具体证据`
- `来源`
- `对用户问题的含义`
- `证据强度/局限`

For product or company research, prefer:

- `方向`
- `代表产品/公司`
- `解决的问题`
- `优点`
- `不能解决的缺口`
- `适合场景`

For JTBD research, prefer:

- `When`
- `I want to`
- `So that`
- `当前替代方案`
- `未满足需求`
- `可衡量结果`

## Quality Bar

Before finalizing, check:

- The report directly answers the user's research question.
- There are at least 3 substantive findings unless the user asks for a tiny note.
- Important quantitative claims have citations.
- The analysis distinguishes fact, source interpretation, and model inference.
- The conclusion is not just a summary; it states what the user should believe or investigate next.
- If saved, the final response includes the absolute file path.

## Boundaries

- Do not pretend the literature has exact data when it does not. Say `没有找到可靠分层数据` and provide the closest available evidence.
- Do not treat a product page as proof of real-world effectiveness.
- Do not use social media anecdotes as evidence unless the user explicitly asks for sentiment or UGC research.
- Do not make the report longer than necessary for a first-pass answer; prioritize high-signal evidence and clear reasoning.
