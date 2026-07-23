---
title: "Verify Before Cut"
date: "2026-07-23"
canonical: "https://raytally.com/en/ideas/2026-07-23-ghost-cut-or-why-cut-and-paste-is-broken-everywhere/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Ghost Cut – or why Cut and Paste is broken everywhere"
  observed_at: "2026-07-23T00:33:12.762Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-07-23-ghost-cut-or-why-cut-and-paste-is-broken-everywhere/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Verify Before Cut
Keeps cut content at its source until a complete paste into another app is verified, then deletes it—or restores it in place if the transfer fails.

## Product concept

When a writer presses Cut in an editor, the content moves into a visible pending-transfer state instead of disappearing from its original location immediately. The app generates a verification marker for the text or rich content and keeps a temporary move receipt at the edge, making clear that the original has not yet been permanently deleted. After the user pastes into another app, the extension checks whether the destination received an identical copy with formatting intact. Only then is the source deleted. If the target app crashes, the clipboard is overwritten, or table formatting is lost during paste, a one-click restore remains available at the original location. Users can also open a recent moves list to see where content was cut from, where it was pasted, and whether the transfer has been confirmed. For quotes, paragraphs, or tables moved between apps, this short-lived record reduces the panic of wondering where the content they just cut went. The first version starts with text and rich text in browsers and common document editors; it does not promise to handle every system-level file move. It turns Cut from an irreversible deletion into a two-stage handoff, completed only after the destination is verified.

## Why now (backed by facts)

Discussion of “Ghost Cut and broken copy-and-paste mechanics” is currently at #13 on the Hacker News front page, with roughly 118 points and 83 comments (July 23 snapshot; figures are approximate at the time observed). That makes the relevant use cases more concentrated right now.

## Source context

Theme: Ghost Cut and broken copy-and-paste mechanics
Trigger Hacker News post (original English): Ghost Cut – or why Cut and Paste is broken everywhere
Heat at capture: ~118 points, 83 comments (point-in-time values)

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
