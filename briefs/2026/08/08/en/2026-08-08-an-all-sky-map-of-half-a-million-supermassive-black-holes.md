---
title: "Look Up to Find Black Holes"
date: "2026-08-08"
canonical: "https://raytally.com/en/ideas/2026-08-08-an-all-sky-map-of-half-a-million-supermassive-black-holes/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "An all-sky map of half a million supermassive black holes"
  observed_at: "2026-08-08T00:33:12.884Z"
sources:
  - url: "https://www.sdss.org/black-hole-mapper-release-20/"
    boundary: "Observed at 2026-08-08T00:33:12.884Z."
  - url: "https://news.ycombinator.com/item?id=49211921"
    boundary: "Published at 2026-08-07T00:00:00.000Z. Observed at 2026-08-08T00:33:12.884Z."
  - url: "https://www.stellarium-labs.com/stellarium-mobile-plus/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://skysafariastronomy.com/products/skysafari-8-basic"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-08-an-all-sky-map-of-half-a-million-supermassive-black-holes/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Look Up to Find Black Holes
Point a phone at the night sky to find supermassive black holes above the horizon, then follow guided directions and distance stories to explore them.

## Product concept

While walking at night, camping, or stargazing with children, users open the app and point their phone at the sky. Using their location, date, time, and phone orientation, it selects only supermassive black holes currently above the horizon. Directional arrows guide them toward the next target, with no need to know constellations or decipher a dense all-sky map. Each target appears as a short card: the direction of its host galaxy, its distance, its mass, and how long its light took to reach Earth. Users can tap for a one-minute narration, such as: “In the direction you are facing, this light began its journey before dinosaurs appeared.” Cards clearly state that these black holes usually cannot be seen directly with the naked eye; the screen shows a sky direction derived from astronomical catalogs. As users turn their phone, nearby targets appear in order of bearing. They can choose a route for “closest to me,” “most massive,” or “easiest to explain to children tonight.” After completing several targets, the app creates a black-hole postcard with the location, time, and direction. On cloudy nights or under severe light pollution, it still works as a directional exploration tool without pretending to provide a naked-eye observation. The first version combines public black-hole catalogs, star catalogs, and the phone compass for outdoor look-up exploration. It does not simulate telescope imagery or present disputed candidate objects as confirmed discoveries.

## Why now (backed by facts)

From July 30 to 31, SDSS released the DR20 all-sky distribution map and opened its black-hole mapping data and query tools. In a Hacker News snapshot on August 8, the related page ranked 14th with 134 points and 35 comments, exposing more people to the all-sky map while still leaving a need to turn it into directions usable from where they stand.

## Direction (model inference, not independently verified)

Target user: The core user is a parent taking an evening walk or camping with children. They have just looked up and become curious, but cannot pick out a tellable target from a dense star map. Their companions' attention is brief, and this is not the moment to learn constellation coordinates. A direction to turn and one story can immediately turn idle outdoor time into shared exploration.

Minimal entry point: Start with DR20 and its value-added catalogs to select a verifiable set of objects. Keep only targets with clearly documented coordinates, redshifts, and mass sources. The backend converts right ascension and declination into altitude and azimuth for a given location and time. The client reads location, clock, and orientation sensors, then calculates the arrow offset. Launch on one mobile platform only, with a curated selection of objects. Use a fixed methodology for distance and light-travel time, and cite the data source on every card. Do not render an all-sky map or simulate telescope imagery at first.

The strongest case against: Compasses can be disrupted by vehicles, metal gear, and phone cases, causing arrows to drift noticeably. If users repeatedly fail to find a target direction, they will quickly doubt the entire positioning system. The cataloged visible signal often comes from an active galactic nucleus or quasar, not the black hole itself. Redshift, distance, and mass may also use different estimation methods, and short cards can easily erase that uncertainty. Family-oriented narration requires item-by-item verification, so editorial costs grow with the catalog. An inaccurate arrow or an overstated story in a postcard would directly damage scientific credibility.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Build a no-install web demo around DR20, where visitors enter a city to see a few directions for tonight. Turn each target into a short video showing only a turn arrow and one distance story. Include the object ID and an openable route link on each postcard so recipients can reproduce the experience. Planetariums, camping communities, and family science creators already have fitting contexts; customized routes can secure the first real demonstrations.

## Competitors & gaps (model inference)

- Stellarium Mobile: Stellarium Mobile already simulates the sky by location and time. It supports sensor-based pointing and includes quasars and black holes. Its strengths are a broad catalog and a complete sky view, well suited to open-ended searching. Its public positioning still centers on a general sky map and object identification. The opportunity is not to add more objects, but to narrow the exploration task: list only supermassive black holes above the horizon, then connect them into a turn-by-turn route. Each target explains distance and light-travel time through a short family-friendly story. A persistent note that these objects cannot usually be seen with the naked eye must remain on the main screen, so users do not think the phone is seeing a black hole. Postcards can also bind the location, time, bearing, and object ID into a shareable record people can revisit.
- SkySafari: SkySafari 8 already offers point-and-identify, recommendations for what is visible tonight, and object descriptions. It also provides guided audio and covers large numbers of stars and deep-sky objects. These capabilities suit comprehensive stargazing and long-term learning, while giving people familiar with sky maps substantial freedom. Its public feature pages do not emphasize dedicated outdoor routes for invisible black holes. A new product can reduce choice to just a few targets near the user’s current direction. Routes are ordered by distance, mass, or ease of explaining them to children, rather than by general observing value. The narration must repeatedly distinguish the black hole itself from its host galaxy and active galactic nucleus. The real distinction comes from that editorial standard and the rhythm of continuous turning and exploring, not from a larger catalog.

## How it makes money (model inference)

The free tier shows a small set of selected targets. A one-time purchase unlocks full routes, offline data, and a family audio pack. Themed routes edited by astronomy writers can be sold separately later.

## Source context

Theme: All-sky map of 500,000 supermassive black holes
Trigger Hacker News post (original English): An all-sky map of half a million supermassive black holes
Heat at capture: ~134 points, 35 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Mapping Monsters: SDSS-V Data Release 20 Unveils All-Sky Views of Supermassive Black Holes (https://www.sdss.org/black-hole-mapper-release-20/)
- An all-sky map of half a million supermassive black holes (https://news.ycombinator.com/item?id=49211921)
- Stellarium Mobile and Stellarium Plus (https://www.stellarium-labs.com/stellarium-mobile-plus/)
- SkySafari 8 Basic (https://skysafariastronomy.com/products/skysafari-8-basic)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
