---
name: report-organization
description: Use when the user asks to create, place, organize, or route Markdown reports and notes in a research or project workspace. Use this for deciding date-based Markdown destinations, with routing based on the current cwd/project context such as My Research or Entrepreneur/Fortune subfolders.
metadata:
  author: wjs
  last_update_time: "2026-07-03 21:11:43 HKT"
  status: active
---

# Report Organization

## When to use

- User says "write markdown", "create markdown", or "save note" inside the research workspace.
- User asks for "today's research note" or requests a destination for Markdown notes.
- User requests folder-date naming rules for research writing.

## Routing rule (default)

1. Resolve the active research/project root from the current `cwd` and conversation context before writing. Do not mechanically default to `My Research`.
2. Common roots:
   - If the current context is under `/Users/wjs/Library/CloudStorage/OneDrive-Personal/My Research`, route under `/Users/wjs/Library/CloudStorage/OneDrive-Personal/My Research/2026`.
   - If the current context is under `/Users/wjs/Library/CloudStorage/OneDrive-Personal/Entrepreneur/Fortune/<ProjectOrTopic>`, route under that subfolder's own `2026` folder, for example `/Users/wjs/Library/CloudStorage/OneDrive-Personal/Entrepreneur/Fortune/Polymarket/2026`.
   - More generally, when working inside a project/topic subfolder, prefer `<current project/topic folder>/2026` over a global research folder.
3. 每天研究放到当天的 folder: `YYYY-MM-DD`。
4. Use month subfolder in short English form (`Jan`, `Feb`, `Mar`, ..., `Dec`).
5. Use daily folder name in `YYYY-MM-DD` format.
6. Default destination for a specific day is:

   `<resolved-root>/2026/<MonthAbbr>/<YYYY-MM-DD>`

   Examples:

   - `/Users/wjs/Library/CloudStorage/OneDrive-Personal/My Research/2026/May/2026-05-08`
   - `/Users/wjs/Library/CloudStorage/OneDrive-Personal/Entrepreneur/Fortune/Polymarket/2026/Jun/2026-06-15`

## Execution policy

- Prefer this format even if older folders use mixed naming.
- Create the target folder if it does not exist.
- Keep explicit project/event folders only when user asks for them.
- If user provides a date string, use that date; if user says "today", use current date.
- If both date and explicit project folder are provided, follow the explicit project request.
- If the current `cwd` is inside a known project folder, use that folder's `2026` route unless the user explicitly asks for a different destination.
- If the current `cwd` is too broad, such as `/Users/wjs/Library/CloudStorage/OneDrive-Personal/Entrepreneur/Fortune`, infer the project/topic subfolder from the active conversation when obvious, such as `Polymarket`; otherwise ask one short clarification question before writing.
- If the request is ambiguous, ask one short clarification question before writing.

## Workflow

1. Resolve target date.
2. Inspect current `cwd` and conversation context to resolve the active root.
3. Resolve whether a project/event folder is explicitly requested.
4. Map to `<resolved-root>/2026/<Month>/<YYYY-MM-DD>/`.
5. Create directories as needed.
6. Write/read/update Markdown in that folder.
7. Return the absolute path used.

## Maintenance rule

Keep this convention in:

- `/Users/wjs/Library/CloudStorage/OneDrive-Personal/My Research/2026/README.md`
- relevant project `2026/README.md` files when they exist, such as `/Users/wjs/Library/CloudStorage/OneDrive-Personal/Entrepreneur/Fortune/Polymarket/2026/README.md`
- the active conversation state for this session.
