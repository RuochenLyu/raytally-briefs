---
title: "Adjacent Schedule Navigator"
date: "2026-08-19"
canonical: "https://raytally.com/en/ideas/2026-08-19-showed-up-for-a-meeting-with-cfo-30-min-early/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Showed up for a meeting with CFO 30 min early"
  observed_at: "2026-08-19T00:38:56.675Z"
sources:
  - url: "https://www.reddit.com/r/ADHD/comments/1vs5voq/showed_up_for_a_meeting_with_cfo_30_min_early/"
    boundary: "Published at 2026-08-18T23:41:23.000Z. Observed at 2026-08-19T00:38:56.675Z."
  - url: "https://developer.apple.com/documentation/eventkit/accessing-the-event-store"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://developer.apple.com/documentation/mapkit/mkdirections"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://support.apple.com/en-euro/guide/iphone/iph3d110f84/ios"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-19-showed-up-for-a-meeting-with-cfo-30-min-early/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Adjacent Schedule Navigator
When back-to-back commitments collide, it combines time, travel, and early-arrival preferences into a clear next action so arriving early for one event does not mean missing the next.

## Product concept

To avoid being late, someone arrives at a meeting with the CFO 30 minutes early—then misses another nearby commitment. For people with ADHD, a row of separate calendar reminders can make “arriving early” look like having the day under control. The real problem is knowing how far to take the task in front of you without crowding out the next two. After connecting work and personal calendars and setting their usual travel modes and early-arrival preference, users see nearby meetings, classes, pickups, and online training linked into a single itinerary. Instead of a pile of lock-screen reminders, they get one current instruction, such as: “Wait in the lobby for 12 minutes; leave at 15:35 to make your next online training.” The next two commitments, their locations, and the latest departure time remain visible below. When a user arrives early, the system recalculates from their current location, the travel time between locations, and the fixed start time of the next commitment. If continuing to wait would create a conflict, it explicitly identifies the affected commitment and offers options to leave, attend online, or tell the other party they will be late. A prewritten message is sent to the relevant contact only after the user selects it. The initial release can support Google Calendar, Apple Calendar, and walking and driving directions. The product stays read-only: it will not cancel meetings or invent free time. Its job is to compress scattered schedules into an actionable next step.

## Why now (backed by facts)

An August 18 post on r/ADHD complained that the author arrived at a meeting 30 minutes early to avoid being late. The post also mentioned training immediately afterward that they had missed the previous week; the comments offered no verifiable solution. The gap is a tool that watches adjacent commitments together.

## Direction (model inference, not independently verified)

Target user: The primary users are adults with ADHD who use both work and personal calendars. They often lose their sense of the whole timeline when meetings, classes, pickups, and travel happen in sequence. The problem usually arises once they have already arrived early or are focused on the current task. Standard reminders merely repeat the start time; they do not answer how long the user can wait or which later commitment will be squeezed out.

Minimal entry point: Start with a native iPhone app that reads the work and personal calendars already connected on the device. EventKit can read calendar events but requires full access; product rules still prohibit write-back or deletion. The first release handles only adjacent events with fixed start times and asks the user to confirm when a location is unclear. MapKit can calculate walking or driving routes and estimated travel time, which can be used to work backward to a latest departure time. The rules engine considers only the current item and the next two, and never changes the original schedule automatically. The lock-screen layer shows one current action alongside its timing basis and the commitments affected. Location is used for recalculation only during an active itinerary, and messages require user confirmation before sending.

The strongest case against: Calendar and location permissions could block first use. On iOS, reading events requires full access, so the permission request will still feel weighty even though the product does not write back. Missing addresses, ambiguous room names, or links buried in notes can all distort travel estimates. If arrival detection or background updates lag by a few minutes, the lock-screen instruction could lead the user toward the wrong choice. Incorrect alerts can heighten anxiety, and an accidental late-arrival message can damage professional relationships. Moving forward requires no automatic messaging by default, visible calculation logic, and a way for users to correct locations and progress at any time.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Recruit the first users from ADHD communities discussing time blindness rather than broadly targeting productivity-tool users. Demos should recreate the full sequence of arriving early for one commitment while crowding out the next. Use TestFlight invites to let users try the product with a real day’s schedule, with particular attention to location corrections and reasons for false alerts. The privacy page should plainly show what is read, when location is enabled, and that the product never changes calendars.

## Competitors & gaps (model inference)

- Apple Calendar: Apple Calendar already supports travel time for events. When an address is added, it uses Apple Maps, traffic, and public-transit information to tell users when to leave. That covers basic reminders for getting to a single event. It also owns the system notification surface, so users do not need another app. Its public documentation still centers on individual events and a single departure reminder, rather than recalculating around the next two commitments as well. Once users arrive early, they must still work out for themselves how long they can wait without affecting what comes next. It also offers no unified latest-departure instruction when an in-person meeting is followed by online training. Nor does it clearly identify the commitment that will be affected, then let the user choose to leave, switch online, or notify someone of a late arrival. The opportunity is a real-time coordination layer on top of the calendar, not a calendar replacement.

## How it makes money (model inference)

Monthly subscription. The free tier provides same-day action guidance and basic conflict alerts; the paid tier unlocks multi-day planning, multiple calendars, location-based recalculation, and message templates.

## Source context

Theme: Adjacent-schedule conflict alerts for people with ADHD
Trigger Reddit single-post demand observation: r/ADHD — Showed up for a meeting with CFO 30 min early

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Showed up for a meeting with CFO 30 min early (https://www.reddit.com/r/ADHD/comments/1vs5voq/showed_up_for_a_meeting_with_cfo_30_min_early/)
- Accessing the event store (https://developer.apple.com/documentation/eventkit/accessing-the-event-store)
- MKDirections (https://developer.apple.com/documentation/mapkit/mkdirections)
- Create and edit events in Calendar on iPhone (https://support.apple.com/en-euro/guide/iphone/iph3d110f84/ios)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
