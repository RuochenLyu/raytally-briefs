---
title: "Screen-Free Eclipse Guide"
date: "2026-08-10"
canonical: "https://raytally.com/en/ideas/2026-08-10-solar-eclipses/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "solar eclipses"
  observed_at: "2026-08-10T00:33:15.439Z"
  active: true
  window_hours: 168
sources:
  - url: "https://science.nasa.gov/eclipses/safety/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://github.com/cosinekitty/astronomy"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://developer.apple.com/documentation/watchkit/wkinterfacedevice/play%28_%3A%29"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://apps.apple.com/us/app/solar-eclipse-timer/id1203105865"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-10-solar-eclipses/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Screen-Free Eclipse Guide
During an eclipse, keep the phone in your pocket while watch haptics and headphone prompts guide safe viewing phases and trigger key photos.

## Product concept

After arriving at an eclipse viewing site on August 12, first-time viewers open the app to confirm their position and select a connected watch, headphones, and Bluetooth camera shutter. The app downloads contact times and eclipse-path boundaries for those coordinates, then asks them to put their phone away. Users still assess cloud cover and traffic themselves; the point is to keep a countdown screen from taking over the few minutes in front of them. Before the partial eclipse begins, the headphones give a brief reminder to put on compliant eclipse glasses, while the watch uses low-frequency haptics to signal that the next phase is near. A prompt to briefly remove glasses appears only after the coordinates have been verified inside the path of totality and local totality has begun. If the user leaves the path, location drifts, or the phase ends, the watch pulses continuously and the voice prompt immediately tells them to put their glasses back on. Every prompt includes a specific local time, preventing the pace of a livestream elsewhere from being mistaken for the live event. Before departure, users can set the camera orientation and burst plan. As key moments approach, the app sends commands to the paired shutter to capture a preset sequence of images. The watch shows only instantly legible states: time remaining, started, and ended. After viewing, the phone displays a phase timeline, photos, and capture settings, letting users revisit what they did not miss by looking down. The first release supports location, watch haptics, headphone voice prompts, and common Bluetooth shutters. It does not replace certified eclipse glasses, promise weather forecasts, or provide camera autofocus. It arranges safety reminders, direct viewing, and one saved photograph into an on-site rhythm that does not require watching a screen.

## Why now (backed by facts)

As observed on August 10, search interest remains active. “solar eclipses” has 20,000+ searches, up 400%; with the August 12 total eclipse approaching, first-time viewers are more likely to look for local timing and safety reminders on site.

## Direction (model inference, not independently verified)

Target user: People visiting the path of totality for the first time, especially those also caring for companions or taking photos. Once on site, they need to verify their location but fear missing brief phases. As totality approaches, putting on or removing glasses and taking photos compete for attention. Screen-free prompts reduce looking down and turn critical actions into a pre-rehearsed rhythm.

Minimal entry point: First, use Astronomy Engine to calculate eclipse phases for a specified coordinate locally and cache data for the event. Focus the first release on iPhone and Apple Watch to reduce cross-platform timing differences. On the watch, use WatchKit’s defined haptic types and local notifications for background reminders. Use system text-to-speech for headphones, with local time included in every announcement. Start Bluetooth shutter support with a device whitelist and pairing self-check rather than claiming universal compatibility. Before the event begins, users must test location, volume, haptics, and shutter control.

The strongest case against: Incorrect location data or phase timing could produce a dangerous prompt to remove eclipse glasses. Any safety alert must default to caution and follow the rule that glasses may be removed only during totality. Direct Apple Watch haptics are constrained by background state, and notification delays must be validated device by device. Disconnected or muted headphones, or ambient noise, can render voice prompts ineffective. Bluetooth shutter protocols and camera-control methods vary widely, so a device whitelist creates ongoing testing costs. One incorrect alert could undermine trust in the entire flow and create liability risk.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Acquire the first users through eclipse travel groups, photography forums, and viewing-site discussion communities. Publish a shareable on-site device-check page so users can test their headphones, watch, and shutter before departing. Generate phase cards by viewing location for trip leaders and photographers to share. After the event, use photo timelines to carry users into subscriptions for the next eclipse.

## Competitors & gaps (model inference)

- Solar Eclipse Timer: Solar Eclipse Timer already calculates contact times by location and announces key phases by voice. It works offline, includes sound checks and rehearsals, and prompts photographers about filters and shooting actions. Users can already spend less time looking at the screen, so the core timing need is covered. Its public feature descriptions still focus on phone voice prompts and notifications, with no apparent coded Apple Watch haptics. Nor does it turn inaccurate location data into an urgent wrist alert. Its photography features guide manual actions rather than orchestrating a paired shutter. The opening here is a single flow that combines safety state, wrist haptics, and camera triggering. The trade-off is having to prove that this coordination is more trustworthy than reliable voice timing.

## How it makes money (model inference)

Sell an offline guidance pack for each eclipse. The free tier checks location, audio, and Apple Watch connectivity; the paid tier downloads local phase data and unlocks the full voice flow and automated shooting.

## Trend background

Theme: August 12, 2026 eclipse viewing
Trigger query (original English): solar eclipses
Approx. search volume: 20000+ (approximate)
Approx. increase: +400% (approximate)

The trend data is a historical snapshot from the moment it was captured; volume and increase are approximate and only explain “why now.” Do not write them into product copy as precise market numbers.

## Sources

- Eclipse Viewing Safety (https://science.nasa.gov/eclipses/safety/)
- Astronomy Engine (https://github.com/cosinekitty/astronomy)
- playHaptic: (https://developer.apple.com/documentation/watchkit/wkinterfacedevice/play%28_%3A%29)
- Solar Eclipse Timer (https://apps.apple.com/us/app/solar-eclipse-timer/id1203105865)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
