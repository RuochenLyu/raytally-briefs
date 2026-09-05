---
title: "Decision-Point E-Ink Bike Navigation"
date: "2026-09-05"
canonical: "https://raytally.com/en/ideas/2026-09-05-show-hn-open-source-eink-bike-computer/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Show HN: Open-Source eInk Bike Computer"
  observed_at: "2026-09-05T00:33:31.480Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49567437"
    boundary: "Published at 2026-09-04T00:00:00.000Z. Observed at 2026-09-05T00:33:31.480Z."
  - url: "https://opentrailpaper.com/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.garmin.com/en-US/newsroom/press-release/sports-fitness/discover-new-routes-with-the-edge-explore-2-series-from-garmin/"
    boundary: "Published at 2022-07-13T00:00:00.000Z."
  - url: "https://beeline.co/products/beeline-velo-2"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-05-show-hn-open-source-eink-bike-computer/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Decision-Point E-Ink Bike Navigation
Before a long ride, turn a route into low-refresh navigation pages that reveal directions, hazards, or resupply details only when a decision is needed.

## Product concept

Before a long ride, cyclists import a GPX route and the device splits the continuous map into a stack of e-ink event pages. During the ride, the screen persistently shows speed, remaining distance, and the next key point, remaining legible in sunlight without frequent charging over several hours. Only shortly before GPS reaches a complex intersection does the screen refresh to an enlarged turn diagram and a single action prompt. Near a resupply stop, the page shows water availability, opening hours, or a supply checklist. Route authors can also embed alerts for roadworks, hazardous descents, and other conditions at the relevant locations. If a rider leaves the route, the device does not present a dense, hard-to-read map. It shows only the direction and distance needed to return to the route. Once the route is rejoined, navigation automatically returns to the next event page; the full flow still works without network access. The first hardware release can focus on single-day and multi-day riding, with GPX import, offline positioning, and a small number of route annotations. Social rankings, training analytics, and live emergency tracking can wait for later versions, keeping attention on the moments when riders genuinely need to look up and decide.

## Why now (backed by facts)

When observed on September 5, the open-source e-ink bike-computer project ranked sixth on Hacker News, with 221 points and 76 comments. That brought the concrete trade-offs of offline, sunlight-readable, low-power navigation into developer discussion.

## Direction (model inference, not independently verified)

Target user: People riding solo on single-day endurance rides or multi-day bike tours. They typically already have a GPX file from a club, event organizer, or Komoot, and are willing to check resupply and risk points before departure. The real need arises when they are tired, in bright sun, or without signal: reading a complex map is slow, and pulling out a phone breaks riding rhythm.

Minimal entry point: Start with OpenTrailPaper’s open firmware. Its existing hardware already includes an ESP32-S3, GPS, an e-ink display, and an SD card. A phone app first parses the GPX file and creates an ordered event list. The first version recognizes only clear turns, user-set markers, and off-route states. Authors can manually correct complex intersections rather than relying on unreliable automated judgment. The device stores the route polyline, event coordinates, and a simplified basemap. While riding, it matches the current location to the next event and refreshes only the relevant part of the page. Initial offline recovery should use the nearest route segment and direction of travel, not full road-network recalculation.

The strongest case against: A wrong turn directly causes detours and can mean missing resupply in remote areas. GPX files often contain only track points, so automatically inferring an action at an intersection can create false prompts. Roadworks, opening hours, and water availability also go stale, requiring clear maintenance ownership. E-ink refreshes slowly, so continuous speed display and local map updates may compete for power. Outdoor hardware must also handle waterproofing, vibration, low temperatures, and mount reliability. If off-route recovery is not stable enough, riders will quickly return to their phones. Before proceeding, validate turn-prompt accuracy and all-day battery life on real long-distance routes.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Acquire the first users through the DIY bike-computer community. OpenTrailPaper has already attracted people willing to flash firmware and assemble hardware. Publish compatible route packs and an event-page compiler so existing devices can test the experience immediately. Then invite long-distance route authors to create demonstration routes with public resupply and hazard markers. Real route files are more likely than broad promotion to generate downloads, reproducible tests, and improvement feedback.

## Competitors & gaps (model inference)

- OpenTrailPaper: OpenTrailPaper already imports GPX files and displays offline maps on the device. It also provides turn prompts, ride recording, and Bluetooth sensor connectivity. Once routes and maps are loaded, it needs neither a phone nor a network during a ride. It shares this product’s e-ink, offline-navigation, and open-hardware approach. Its interface still centers on a dashboard and follow-along map rather than compiling an entire route into a limited set of event pages. Resupply stops, roadworks, and hazardous descents are not core route objects either. If a rider goes off route and must rely on the map, they still need to interpret the surrounding roads. The opening is stricter information restraint: each refresh answers just one immediate decision question, while route authors decide exactly where an interruption is worthwhile.
- Beeline Velo 2: Beeline Velo 2 already offers simple turn-by-turn navigation. It supports GPX import, off-route rerouting, and ride-data display, including climbs, remaining distance, and estimated arrival time. Its compact display, designed for quick glances, has validated the minimal-navigation form factor. Route planning and the main navigation computations still run in the phone app, and its specifications state that a Bluetooth connection is required. For multi-day riders, phone battery and pairing status remain part of the reliability chain. It is not an e-ink device, and route content is controlled by the navigation system. Users cannot easily embed a water-stop checklist or road-condition warning at a specific location. The opening here is to complete all compilation before departure, then run the device solely on local positioning and event pages during the ride.
- Garmin Edge Explore 2: Garmin Edge Explore 2 already covers mature cycling navigation, with high-contrast maps, turn-by-turn prompts, and off-route handling. Routes can be synced from Garmin Connect, Strava, or Komoot. It also integrates climbs, safety tracking, and an external-device ecosystem. It is more comprehensive for riders who need full maps and training features, but that breadth brings more feature layers and a screen that continuously carries both maps and data. Route authors also cannot easily turn a resupply checklist into the primary page triggered by a location. Multi-day routes still require managing device battery and companion services. A new product should not try to match all of Garmin’s capabilities. It can retain a narrower task boundary focused on infrequent decisions: replacing map reading with a prearranged sequence of events.

## How it makes money (model inference)

Charge once for the hardware and include the route compiler for free. Keep basic offline navigation subscription-free. Later, offer an annual plan for route cloud backup, syncing author annotations, and firmware hosting.

## Source context

Theme: Show HN: Open-Source e-Ink Bike Computer
Trigger Hacker News post (original English): Show HN: Open-Source eInk Bike Computer
Heat at capture: ~221 points, 76 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Show HN: Open-Source eInk Bike Computer (https://news.ycombinator.com/item?id=49567437)
- OpenTrailPaper — DIY e-paper bike computer (https://opentrailpaper.com/)
- Garmin announces Edge Explore 2 series of cycling navigators (https://www.garmin.com/en-US/newsroom/press-release/sports-fitness/discover-new-routes-with-the-edge-explore-2-series-from-garmin/)
- Beeline Velo 2 (https://beeline.co/products/beeline-velo-2)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
