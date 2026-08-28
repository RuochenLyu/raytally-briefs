---
title: "Wrist Task Levels"
date: "2026-08-28"
canonical: "https://raytally.com/en/ideas/2026-08-28-looking-for-an-app-that-gamifies-tasks/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Looking for an app that gamifies tasks"
  observed_at: "2026-08-28T00:36:05.722Z"
sources:
  - url: "https://www.reddit.com/r/adhdwomen/comments/1w0612p/looking_for_an_app_that_gamifies_tasks/"
    boundary: "Published at 2026-08-27T00:00:00.000Z. Observed at 2026-08-28T00:36:05.722Z."
  - url: "https://developer.apple.com/documentation/WatchConnectivity/transferring-data-with-watch-connectivity"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://developer.apple.com/documentation/watchkit/using-extended-runtime-sessions"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://apps.apple.com/us/app/brili-routines-habit-tracker/id1516036620"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-28-looking-for-an-app-that-gamifies-tasks/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Wrist Task Levels
When getting started feels hard, take on a short Apple Watch level, follow haptic pacing through the next step, and pay a clearly stated one-time price.

## Product concept

Some adults with ADHD know what is on their to-do list, but get stuck when opening their phone leads to messages and a long list. They break tasks into optional levels on the phone, such as “open the document and write the title” or “tidy the desk for three minutes,” then sync them to Apple Watch. Each level includes an estimated duration, required items, and a small enough first action. The watch shows only the current level. Once the user starts, haptic beats cue progress, breaks, and wrap-up without requiring frequent screen checks. If they get stuck, a tap on “Shorten” turns a 15-minute task into a three-minute one, or simply shows the next action. Afterward, the user records how long they actually worked and where they got stuck, allowing the system to adjust the difficulty of the next starting step. Rewards can take the form of character items earned that day, which users can give friends to unlock scenes together, without relying on streak-loss penalties for motivation. Before download, the payment screen states the one-time price for core features; theme packs are sold individually, with no auto-renewing trial. The product does not diagnose or treat any condition. It first makes a complete loop from short wrist-based levels to a difficulty-reduction button and clear pricing.

## Why now (backed by facts)

A post in r/adhdwomen on August 27, 2026, asked for an app with Apple Watch support, task gamification, and transparent pricing. Comments suggested Dubbii, Brili, and Goblin Tools, but the gap remained; as recorded on August 28, it had 1 point and 4 comments.

## Direction (model inference, not independently verified)

Target user: The core user is an adult with ADHD who already owns an Apple Watch and is overwhelmed by long to-do lists. They usually know what to do, but open their phone while preparing to start and get pulled into messages. The critical moment is the few minutes before a meeting, household task, or sitting down at a desk. At that point, one tiny action is easier to start than another view of the full plan.

Minimal entry point: Use SwiftUI on the phone to create levels and store estimated duration, required items, and the next action as local structured data. Sync the current level through WatchConnectivity’s updateApplicationContext, and return completion and friction records through transferUserInfo. Keep the watch interface to four actions: Start, Shorten, Complete, and Stuck. Use WatchKit’s built-in haptics for foreground pacing. If pacing must continue after the screen turns off, validate the applicable extended runtime session category and time limits. The first version should not infer tasks automatically; offer template-based breakdowns with manual adjustment. Start rewards as local items, then add friend gifting once sync is reliable.

The strongest case against: Continuous watch haptics are constrained in the background, so pacing may stop when the user lowers their wrist or leaves the app. Using an extended runtime session to sustain reminders requires showing that the use case fits an approved system category, while managing time limits and battery drain. If vibrations are too frequent, users will turn reminders off and the core value disappears. Difficulty adjustment also needs enough repeated records; otherwise, the system is merely shortening time mechanically. Friend gifting introduces accounts, sync, privacy, and harassment concerns. One-time pricing reduces subscription anxiety but limits the budget for long-term maintenance of cloud sync and new themes.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Recruit initial testers from ADHD communities who already own an Apple Watch, using short TestFlight trials. The demo should show only the contrast between a long phone list and a single wrist-based level. Put the one-time core price in the first App Store screenshot and state clearly that there is no auto-renewing trial. After launch, collect examples of where users got stuck around the “Shorten” button; this should yield more actionable feedback than broad feature requests.

## Competitors & gaps (model inference)

- Brili Routines: Brili turns everyday tasks into timed routines completed in sequence. Users can complete, postpone, delete, or reorder items, with stars as game feedback. Its mature templates and reminders suit recurring morning and evening routines. Its current U.S. App Store listing offers a 10-day trial and monthly, six-month, and annual subscriptions; its compatible-device information does not list Apple Watch. It therefore addresses following a set routine, rather than seeing only the immediate next step on the wrist. Its official materials also do not emphasize one-tap task shortening when someone gets stuck, or using friction feedback to lower the starting difficulty next time. The opening is to combine task initiation, immediate difficulty reduction, and wrist haptics in one loop. A one-time base price also directly addresses subscription concerns. The tradeoff is that a lighter interface alone will not be enough; the shortening button must prove useful.

## How it makes money (model inference)

Sell the core app as a one-time purchase, including phone-based level creation, watch execution, and local records. Offer character themes and scene packs as individual in-app purchases, with no auto-renewing trials. If cloud sync or friend gifting is added, sell a separate one-time sync add-on.

## Source context

Theme: Transparent Apple Watch task gamification
Trigger Reddit single-post demand observation: r/adhdwomen — Looking for an app that gamifies tasks

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Looking for an app that gamifies tasks (https://www.reddit.com/r/adhdwomen/comments/1w0612p/looking_for_an_app_that_gamifies_tasks/)
- Transferring data with Watch Connectivity (https://developer.apple.com/documentation/WatchConnectivity/transferring-data-with-watch-connectivity)
- Using extended runtime sessions (https://developer.apple.com/documentation/watchkit/using-extended-runtime-sessions)
- Brili Routines – Habit Tracker (https://apps.apple.com/us/app/brili-routines-habit-tracker/id1516036620)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
