---
title: "Find the Commit That Slowed Your Bun Build"
date: "2026-09-13"
canonical: "https://raytally.com/en/ideas/2026-09-13-i-made-a-build-visualizer-to-understand-bun-s-compile-times/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "I made a build visualizer to understand Bun's compile times"
  observed_at: "2026-09-13T00:33:33.747Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-13-i-made-a-build-visualizer-to-understand-bun-s-compile-times/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Find the Commit That Slowed Your Bun Build
When a Bun project’s builds suddenly slow down, this CI tool pinpoints the first commit that caused the regression and posts the evidence to the merge request.

## Product concept

When a Bun project’s CI builds slow down, it automatically reruns the time-consuming stages across the relevant commits. It identifies the first change that caused the regression and posts the before-and-after timings, along with reproduction evidence, back to the merge request.

## Source context

Theme: Bun compile-time visualizer
Trigger Hacker News post (original English): I made a build visualizer to understand Bun's compile times
Heat at capture: ~89 points, 17 comments (point-in-time values)

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
