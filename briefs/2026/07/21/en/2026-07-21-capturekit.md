---
title: "Pre-Share Screenshot Check"
date: "2026-07-21"
canonical: "https://raytally.com/en/ideas/2026-07-21-capturekit/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "CaptureKit"
  observed_at: "2026-07-21T03:07:54.539Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Pre-Share Screenshot Check
Intercepts screenshots just before sharing, flags sensitive information, and creates a redacted copy once the user approves.

## Product concept

Before a screenshot is pasted into a chat or dragged into a sharing window, it detects keys, email addresses, account balances, and internal domains. Once the user confirms, it creates a redacted copy while the original remains only on the device.

## Source context

Theme: CaptureKit: Automatic desktop screenshot organization
Trigger Product Hunt launch: CaptureKit — Keep your desktop clean by auto-organizing screenshots.

This records only that the launch appeared in Product Hunt's public feed and when it was observed. The feed provides no vote count; do not describe feed order as popularity or market demand.

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
