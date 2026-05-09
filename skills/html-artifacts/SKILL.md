---
name: html-artifacts
description: Create self-contained HTML artifacts when agent output is easier to understand visually or interactively than Markdown. Use for implementation plans, specs, architecture explainers, PR reviews, design explorations, comparison grids, reports, and one-off editors/playgrounds with diagrams, tables, annotated code or diffs, mockups, controls, and export buttons. Avoid for short answers, changelogs, simple docs, or version-controlled text where Markdown diffs matter.
license: MIT
compatibility: No runtime dependencies; intended for Agent Skills-compatible coding agents.
---

# HTML Artifacts

## Purpose

Use HTML as a working canvas when the user needs to understand, compare, tune, review, or share non-trivial agent output. The goal is not decoration; it is higher-bandwidth human review.

## When To Use

Prefer an HTML artifact for:

- Implementation plans, feature specs, architecture maps, and long technical explainers.
- PR or code-review explainers with annotated diffs, severity labels, and data-flow or control-flow diagrams.
- Design exploration grids, mockups, component inventories, and design-system summaries.
- Research, status, incident, or leadership reports that benefit from scannable sections and visuals.
- One-off editors or playgrounds for hard-to-describe choices: priorities, config, prompts, colors, easing curves, crop regions, schedules, regexes, labels, dataset curation, or annotations.

Use Markdown or chat instead for:

- Short answers, quick summaries, small code snippets, commit messages, changelogs, and ordinary README-style docs.
- Files where clean git diffs are more important than readability.
- Tasks where the user explicitly asks for Markdown, plain text, JSON, or another format.

If the benefit is unclear, ask one concise question before creating the artifact.

## Artifact Rules

- Create a standalone `.html` file in the current workspace unless the user asks for another location.
- Keep it self-contained: inline CSS, inline JavaScript, inline SVG, and local or data-URI assets when practical.
- Do not depend on CDNs, remote fonts, analytics, build tooling, or network access unless the user explicitly wants that.
- Use semantic structure: title, concise intro, sections, tables, figures, captions, and a table of contents or tabs for long artifacts.
- Make it responsive. It should be readable on both laptop and mobile widths without overlapping text or controls.
- Favor diagrams, charts, tables, annotated snippets, mockups, and comparison layouts over long prose.
- Include source and context notes when summarizing multiple files, commits, tools, or external sources.
- Avoid embedding secrets or unnecessary sensitive data. If the file is likely to be shared, call out any privacy-sensitive content.

## Interaction Pattern

For interactive artifacts, close the loop back to the agent:

- Add a clear export action such as `Copy as prompt`, `Copy as JSON`, `Copy diff`, `Copy markdown`, or `Download config`.
- Export only the user's meaningful choices or changed values, not the entire page state.
- Add lightweight validation or guardrails when editing structured data, such as dependency warnings, required fields, or invalid-value states.
- Use simple native controls first: buttons, inputs, sliders, checkboxes, selects, details/summary, and drag-and-drop only when useful.

## Recommended Layouts

- **Comparison**: grid of options with tradeoffs, risks, and a recommended path.
- **Plan**: timeline or phase lanes, acceptance checks, mockups, data flow, key snippets, and open questions.
- **PR review**: changed-files map, annotated diff snippets, severity legend, behavior risks, and test gaps.
- **Explainer**: top-level flow diagram, key concepts, annotated code, gotchas, and what to inspect next.
- **Editor**: form or cards on the left, live preview or diff on the right, export action at the bottom.

## Verification

Before calling the artifact done:

- Open or inspect the file locally when practical.
- Check that layout is nonblank, readable, responsive, and free of obvious overlap.
- Check that any copy/export buttons work or degrade with a visible fallback.
- If the artifact includes generated code snippets or factual claims from files, verify the referenced files or commands enough to avoid misleading the user.

## Delivery

In the final response, link the generated HTML file and summarize what it contains. Keep the chat summary short; the artifact is the detailed output.
