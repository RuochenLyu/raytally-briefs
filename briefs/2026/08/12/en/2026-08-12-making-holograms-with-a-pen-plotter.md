---
title: "Pen Plotter Holographic Engraving"
date: "2026-08-12"
canonical: "https://raytally.com/en/ideas/2026-08-12-making-holograms-with-a-pen-plotter/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Making holograms with a pen plotter"
  observed_at: "2026-08-12T00:33:19.940Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-12-making-holograms-with-a-pen-plotter/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Pen Plotter Holographic Engraving
For pen-plotter makers creating holographic engravings, it turns a design into calibrated, multi-angle toolpaths and runs them directly on the machine.

## Product concept

A maker with a pen plotter who wants to experiment with holographic engraving first imports an SVG design or simple 3D model, then selects the plastic sheet, metal film, or coated paper they have on hand. Before machining begins, the product asks the machine to draw a small calibration pattern. The user photographs it with their phone, and the system uses the image to measure pen pressure, material reflectivity, and mechanical positioning error. Once calibrated, the design is split into multiple sets of fine engraving paths, each corresponding to a different viewing angle. The screen shows how to rotate the material, which pen to swap in, and what effect will appear when that pass is complete. Users can also drag a virtual light source to preview the design’s highlights, shadows, and parallax at different angles before deciding whether to begin the final run. While the plotter works, the app sends paths one pass at a time rather than generating a long job that is difficult to inspect. If a pen skips or drifts during a pass, the user can upload a photo and recalculate from that pass instead of discarding the entire sheet. Once finished, the project is saved as a reproducible recipe containing the material settings, calibration results, and engraving paths. An initial release need only support common desktop plotters, flat designs, and a small set of material templates. By breaking complex optical design into one calibration step and several visible passes, it lets makers produce their first angle-shifting piece in a single evening.

## Why now (backed by facts)

Discussion of “making holograms with a pen plotter” is currently at No. 15 on the Hacker News front page, with roughly 105 points and 11 comments (August 12 snapshot; figures are approximate at the time observed). That has concentrated attention on this use case right now.

## Source context

Theme: Making holograms with a pen plotter
Trigger Hacker News post (original English): Making holograms with a pen plotter
Heat at capture: ~105 points, 11 comments (point-in-time values)

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
