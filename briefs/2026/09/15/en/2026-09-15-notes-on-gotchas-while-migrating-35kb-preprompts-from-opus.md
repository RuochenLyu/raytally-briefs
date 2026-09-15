---
title: "Long Prompt Migration Testbed"
date: "2026-09-15"
canonical: "https://raytally.com/en/ideas/2026-09-15-notes-on-gotchas-while-migrating-35kb-preprompts-from-opus/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Notes on gotchas while migrating 35kb preprompts from Opus to self-hosted Ollama"
  observed_at: "2026-09-15T00:33:03.877Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-15-notes-on-gotchas-while-migrating-35kb-preprompts-from-opus/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Long Prompt Migration Testbed
A migration testbed that shadow-tests historical tasks to identify the exact prompt sections a target model cannot handle.

## Product concept

When migrating very long system prompts, teams can shadow-run anonymized historical tasks on both the old and new models. The system progressively removes prompt sections to pinpoint the passages that cause missed rules, format drift, or insufficient context.

## Source context

Theme: Long prompt migration
Trigger Hacker News post (original English): Notes on gotchas while migrating 35kb preprompts from Opus to self-hosted Ollama
Heat at capture: ~110 points, 60 comments (point-in-time values)

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
