---
title: "Reverse Minesweeper Workshop"
date: "2026-07-27"
canonical: "https://raytally.com/en/ideas/2026-07-27-show-hn-reverse-minesweeper/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Show HN: Reverse Minesweeper"
  observed_at: "2026-07-27T00:33:14.904Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-07-27-show-hn-reverse-minesweeper/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Reverse Minesweeper Workshop
Logic-puzzle fans place mines to create a board, instantly verify that it has a unique solution, and share it with friends to solve normally.

## Product concept

Players place mines backward from the clues, while the system instantly shows the affected clue numbers. Once the board is complete, it checks whether the puzzle has exactly one solution and highlights local areas responsible for multiple solutions.

## Source context

Theme: Reverse Minesweeper game
Trigger Hacker News post (original English): Show HN: Reverse Minesweeper
Heat at capture: ~134 points, 48 comments (point-in-time values)

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
