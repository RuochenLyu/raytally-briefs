---
title: "CSS Scene Workbench"
date: "2026-09-02"
canonical: "https://raytally.com/en/ideas/2026-09-02-ambient-css-v3-blender-meets-css/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Ambient CSS v3 – Blender meets CSS"
  observed_at: "2026-09-02T00:33:20.953Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-02-ambient-css-v3-blender-meets-css/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

CSS Scene Workbench
A spatial CSS workbench where developers arrange elements, lighting, and depth like a 3D scene, then immediately get commit-ready CSS.

## Product concept

When frontend developers tune a complex card flip, depth-of-field shadow, or 3D layered effect, they often end up guessing values back and forth between the preview window and the CSS file. This workbench reads the current page’s DOM, selectors, and styles, then places editable elements on a rotatable spatial canvas. Developers can directly drag an element’s depth position, rotation axis, light direction, and shadow extent. Alongside the canvas, the affected CSS declarations update in real time, showing the original value, the revised value, and which selectors the change will touch. Hovering over any visual object also traces it back to its source rule. Once the adjustment is right, the user selects “write back to branch,” and the product generates a readable CSS diff and preview link. Teams still review code through Git; reviewers can drag a timeline to compare the visuals before and after a change, ensuring other components using the same selector were not unintentionally altered. The first version focuses on transform, opacity, filter, box-shadow, and stacking order for existing web components. It does not try to generate an entire page design or save the canvas as an unmaintainable proprietary scene file. The final deliverable is always CSS in the project.

## Why now (backed by facts)

Discussion of “Ambient CSS v3 – Blender meets CSS” is currently at No. 9 on the Hacker News front page, with roughly 188 points and 68 comments (September 2 snapshot; figures are approximate at the time observed). That has concentrated attention on related use cases right now.

## Source context

Theme: Ambient CSS v3 — Blender meets CSS
Trigger Hacker News post (original English): Ambient CSS v3 – Blender meets CSS
Heat at capture: ~188 points, 68 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
