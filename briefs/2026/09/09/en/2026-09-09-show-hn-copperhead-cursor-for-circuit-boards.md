---
title: "Guided PCB Probe Navigation"
date: "2026-09-09"
canonical: "https://raytally.com/en/ideas/2026-09-09-show-hn-copperhead-cursor-for-circuit-boards/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Show HN: Copperhead – Cursor for circuit boards"
  observed_at: "2026-09-09T00:33:14.604Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-09-show-hn-copperhead-cursor-for-circuit-boards/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Guided PCB Probe Navigation
When a newly powered circuit board behaves abnormally, it marks the next physical test point in the camera view and uses live readings to guide fault isolation.

## Product concept

When a new circuit board is powered on for the first time and a hardware engineer sees an abnormal reading on a power rail, the slowest part is often identifying the correct pad for the probe. The engineer imports the schematic, PCB layout, and a photo of the board, then calibrates the bench-camera view using two reference points. The product maps schematic nets to the physical pads in the camera image. After the engineer selects a symptom such as “no output after power-on,” the screen circles the first test point on the board image and shows the expected voltage, ground reference, and probe direction. A Bluetooth multimeter returns the measured value, allowing the fault tree to rule out branches already supported by the evidence and bring forward the next test point most likely to narrow the fault. The engineer no longer has to switch repeatedly between a computer screen and dense board silkscreen. Each reading is recorded in a troubleshooting trail with its board location, time, photo, and associated net. A colleague taking over can resume from where the previous probe left off. If a reading differs from the expectation, the product expands the regulators, protection components, and downstream loads connected to that net, helping the engineer decide whether to power down for inspection or continue measuring on a live board. The initial version focuses on low-voltage DC power paths and supports common design files such as KiCad files and Bluetooth multimeters. It provides a measurement sequence and an evidence record; it does not replace an engineer’s judgment about shorts, high-voltage hazards, or component failures.

## Why now (backed by facts)

Discussion of “Show HN: Copperhead – Cursor for circuit boards” is currently ranked ninth on the Hacker News front page, with roughly 202 points and 78 comments (September 9 snapshot; figures are approximate at the time observed). That makes the relevant use cases more concentrated right now.

## Source context

Theme: Show HN: Copperhead – Cursor for circuit boards
Trigger Hacker News post (original English): Show HN: Copperhead – Cursor for circuit boards
Heat at capture: ~202 points, 78 comments (point-in-time values)

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
