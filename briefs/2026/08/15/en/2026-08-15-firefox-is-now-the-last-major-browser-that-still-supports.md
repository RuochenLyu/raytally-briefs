---
title: "Privacy Browsing Relay"
date: "2026-08-15"
canonical: "https://raytally.com/en/ideas/2026-08-15-firefox-is-now-the-last-major-browser-that-still-supports/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Firefox is now the last major browser that still supports uBlock Origin"
  observed_at: "2026-08-15T00:33:26.882Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-15-firefox-is-now-the-last-major-browser-that-still-supports/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Privacy Browsing Relay
When ad-blocking fails, routes heavily tracked pages to an isolated Firefox session without requiring users to switch their entire browsing setup.

## Product concept

When the current browser detects that essential filtering rules cannot run on a page, it automatically sends the URL to an isolated Firefox container. Once processing is complete, any downloaded files or final links are passed back to the original browser.

## Source context

Theme: Firefox is the last major browser that still supports uBlock Origin
Trigger Hacker News post (original English): Firefox is now the last major browser that still supports uBlock Origin
Heat at capture: ~313 points, 108 comments (point-in-time values)

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
