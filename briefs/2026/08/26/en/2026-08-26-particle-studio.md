---
title: "Shared Particle Poster"
date: "2026-08-26"
canonical: "https://raytally.com/en/ideas/2026-08-26-particle-studio/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Particle Studio"
  observed_at: "2026-08-26T00:33:05.313Z"
sources:
  - url: "https://www.producthunt.com/products/particle-studio"
    boundary: "Published at 2026-08-18T15:58:49.000Z. Observed at 2026-08-26T00:33:05.313Z."
  - url: "https://developer.mozilla.org/en-US/docs/Web/API/DeviceOrientationEvent/requestPermission_static"
    boundary: "Published at 2026-08-04T00:00:00.000Z."
  - url: "https://pixijs.com/8.x/guides/components/scene-objects/particle-container"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://screenjam.tv/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-26-particle-studio/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Shared Particle Poster
Turn an event’s static key visual into a shared particle display that audiences can join by QR code and reshape together from their phones.

## Product concept

When an event or exhibition already has a key visual, designers often have little choice but to loop it on the main screen. Creators upload a poster, illustration, or brand image, then mark areas such as people, text, and backgrounds. For each area, they set particle density, color, and how it responds to phone movement. The main screen shows the image in motion. Audience members scan a QR code to join, with no app download or account required. Each person controls only a small assigned patch of particles: tilting a phone pushes them apart, swiping leaves trails, and tapping pulls a local cluster together. The phone interface stays minimal so people can look up and see their actions become part of the shared display. A live console combines everyone’s input into waves, vortices, or a rhythm that gradually restores the original image. The host can switch interaction rules for a talk opening, countdown, or musical peak, and can freeze a frame to export as a commemorative event poster. If the network briefly becomes unstable, phones cache actions and send them into the display once the connection returns. The first version supports one main screen and one QR-code entry point, aimed first at trade shows, launches, and campus events. The point is not to generate a flashy video, but to turn a static key visual into a work the whole room completes together.

## Why now (backed by facts)

Particle Studio turns static images into dynamic particle experiences and ranked No. 2 in Product Hunt’s new-product feed when captured on August 26. That makes it easier for event creators to produce a particle visual first—and more quickly encounter the next problem: it can play, but the audience cannot participate.

## Direction (model inference, not independently verified)

Target user: The core users are event designers and live creative teams that have already finalized a key visual. Once the plan and screen setup are locked, they may realize the image can only loop. It is too late to rebuild a game or commission a custom installation, while a standard poll would break the brand visual. They need to reuse the existing poster and validate an interaction quickly before rehearsal.

Minimal entry point: On the main-screen side, use PixiJS ParticleContainer to render lightweight particles, marking only essential properties such as position as dynamic. After image upload, start with brush masks and color sampling. Map people, text, and backgrounds to a limited set of particle behaviors. On mobile, request device-orientation permission with one tap; this requires HTTPS, and some browsers remain limited. Fall back automatically to touch and swipe controls when permission is unavailable. Send only downsampled motion vectors over the network. The server aggregates input by region, then broadcasts a unified state. Do not build complex timelines or multi-screen synchronization yet.

The strongest case against: Sensor-permission prompts may make the first action after scanning a QR code feel awkward. Unstable venue networks can delay actions, and replaying old inputs may disrupt the current image. As participant count rises, the particle effect can become directionless noise. To keep the key visual recognizable, the system needs rate limits, regional controls, and automatic restoration. Browsers, casting hardware, and screen aspect ratios also expand the testing matrix. If the experience stutters on site, the production team will have little ability to troubleshoot it on the fly. If repeated rehearsals still require a developer present to tune parameters, this is a custom project rather than a repeatable product.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Early users are most likely to come from event visual designers, campus groups, and small exhibition-production teams. Use their existing posters to create QR-playable examples, and record videos that show audience gestures and the main-screen response in the same frame. Build templates for openings, countdowns, and brand reveals. Demo links can also go to stage-design and screen-rental teams for use in proposals and rehearsals.

## Competitors & gaps (model inference)

- ScreenJam: ScreenJam already lets audiences join by QR code without downloading an app or creating an account. Organizers can turn existing screens into interactive touchpoints and switch among games, polls, reactions, and branded content. It suits bars, venues, and routine event operations. Its public materials emphasize prebuilt interaction modules and event flows. They do not show an editor that extracts particles from a key visual and lets multiple people control separate local areas, nor a workflow for choreographing restoration rhythms around people, text, and backgrounds. The opening is to serve design teams that already have visual assets. The product should preserve their original artwork rather than force it into a generic game format. The live result can become part of the event visual identity, not merely a round of entertainment.

## How it makes money (model inference)

Charge per event, including one event room, a key-visual template, and a live control console. Add service fees for brand customization, remote rehearsals, or on-site technical support.

## Source context

Theme: Static-image particle animation tool
Trigger Product Hunt launch: Particle Studio — Transform Static Images Into Dynamic Particle Experiences

This records only that the launch appeared in Product Hunt's public feed and when it was observed. The feed provides no vote count; do not describe feed order as popularity or market demand.

## Sources

- Particle Studio (https://www.producthunt.com/products/particle-studio)
- DeviceOrientationEvent: requestPermission() static method (https://developer.mozilla.org/en-US/docs/Web/API/DeviceOrientationEvent/requestPermission_static)
- Particle Container (https://pixijs.com/8.x/guides/components/scene-objects/particle-container)
- ScreenJam — Engage Your Audience with a Live Multiplayer Experience! (https://screenjam.tv/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
