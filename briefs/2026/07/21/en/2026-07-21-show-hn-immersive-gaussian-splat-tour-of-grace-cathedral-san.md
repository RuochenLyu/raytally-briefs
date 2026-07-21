---
title: "Accessible Venue Walkthrough"
date: "2026-07-21"
canonical: "https://raytally.com/en/ideas/2026-07-21-show-hn-immersive-gaussian-splat-tour-of-grace-cathedral-san/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Show HN: Immersive Gaussian Splat tour of grace cathedral, San Francisco"
  observed_at: "2026-07-21T03:07:54.003Z"
sources:
  - url: "https://news.ycombinator.com/item?id=48984254"
    boundary: "Published at 2026-07-20T00:00:00.000Z. Observed at 2026-07-21T03:07:54.003Z."
  - url: "https://matterport.github.io/developer-docs/api/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://accessnow.com/faq/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Accessible Venue Walkthrough
Before visiting an unfamiliar venue, people with mobility needs can rehearse their route in a real-world 3D space and verify entrances, ramps, passages, and sightlines from their seat.

## Product concept

Before setting out, wheelchair users, people with limited mobility, and visitors who feel anxious in unfamiliar places can open a venue’s real-world 3D replica. They select an entrance, seat, restroom, or exhibit area, then specify whether they use a wheelchair, cane, or stroller, or may need to rest along the way. The system walks them through the actual route, highlighting door widths, ramps, narrow passages, turns, and places to pause. They can switch to wheelchair height or another low viewpoint to see whether crowds or barriers could block the stage, display cases, or signs. Any key point can be captured and sent to the venue for confirmation. If a route includes unmarked steps, temporary closures, or reliance on an elevator, the product lists it as something to confirm before the trip. Venue staff can add entrance hours, available loaner equipment, and alternative routes. Frequently reported obstacles are aggregated for operators, helping them identify omissions in their accessibility maps. The first version covers only areas the venue has photographed and maintains. It does not replace on-site staff or claim that a venue meets accessibility standards. It is a visit rehearsal that lets people identify conflicts between a route and their own needs before leaving home.

## Why now (backed by facts)

An immersive Gaussian Splat tour of Grace Cathedral, published on July 20, had 88 points and 17 comments and ranked 20th when observed on July 21. The demo makes pre-visiting a real venue in 3D more tangible, while exposing the limitation of generic walkthroughs: they cannot validate a route against an individual’s mobility needs.

## Direction (model inference, not independently verified)

Target user: The core users are wheelchair and cane users preparing to enter an unfamiliar venue for the first time. Caregivers traveling with them and parents with strollers face similar decisions. The need is strongest after tickets are purchased but before departure, when the destination is fixed and the cost of a last-minute detour rises. They need to know not whether a venue is generically “accessible,” but whether their own equipment, stamina, and seat can make the full route work.

Minimal entry point: Start with venues that already have Matterport spaces. Its SDK can control the camera, add tags, and read measurement data. In the venue editor, staff first draw a passable route map manually, with nodes for entrances, elevators, ramps, restrooms, and rest stops. User conditions only filter routes and generate confirmation items; they do not automatically determine whether a venue is compliant. The first release should not infer steps or door widths from imagery, avoiding the presentation of model error as a definitive result. Screenshots should include the route node, viewing height, and issue description so staff can respond directly.

The strongest case against: The central risk is that a 3D model can look realistic without offering sufficiently reliable dimensions or update information. One incorrect clearance could leave a visitor stranded by steps, a narrow door, or an out-of-service elevator. Temporary barriers, crowds, and event setups can also invalidate a route quickly. Venues therefore need to maintain route nodes continuously and clearly identify which data has been manually verified. The 3D interface itself must work with keyboards, screen readers, and low-performance devices, or it creates another barrier to access. If venues will not take responsibility for updates, an independent developer is unlikely to sustain trust by scraping public tours; in that case, avoid automated expansion and focus on a small number of deep partnerships.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Partner first with museums, churches, and small performance venues that already offer 3D tours. Use their existing models to create one real visitor route, reducing the friction of initial deployment. Invite local wheelchair communities to conduct paid walkthrough reviews, then turn their findings into an actionable improvement list for each venue. Share direct links to specific route rehearsals so visitors can open them without installing an app.

## Competitors & gaps (model inference)

- Matterport: Matterport can scan venues into embeddable 3D spaces. Its SDK provides camera controls, spatial tags, and measurement capabilities, while its Model API can access meshes, point clouds, panoramas, and positional data. These capabilities can support a real-world walkthrough, but they primarily serve general digital-twin workflows. Its public developer tools do not directly assess wheelchair turning space, reliance on ramps, or the need for rest stops, nor do they create a list of questions for the visitor to confirm with the venue. The opportunity is not to rebuild a 3D viewer, but to layer personal mobility needs, human-verified route maps, and venue responses onto existing models. This uses venues' existing assets while keeping maintenance responsibility with the operator.
- AccessNow: AccessNow provides place search, accessibility ratings, feature tags, photos, and personal reviews. Users can flag ramps, elevators, automatic doors, and accessible restrooms. It is useful for deciding whether a place is broadly worth visiting and for collecting community experience. But its core unit of information is still the venue, its tags, and post-visit reviews—not a continuous walkthrough of a route inside the venue. Users cannot easily verify a path from an entrance to a specific seat or exhibit area. Photos also rarely answer questions about door width, turning space, and obstructions at a lower viewing height. The opening is to use a venue-maintained, real-world 3D replica so visitors can inspect each segment against their own needs and send concerns, with viewpoint screenshots, back to the venue.

## How it makes money (model inference)

Charge venues an annual subscription tiered by the maintained area and number of editor accounts. Bill separately for initial modeling, data import, and route annotation. Keep the visitor experience free so a critical pre-trip check is not behind a paywall.

## Source context

Theme: Grace Cathedral immersive Gaussian Splat tour
Trigger Hacker News post (original English): Show HN: Immersive Gaussian Splat tour of grace cathedral, San Francisco
Heat at capture: ~88 points, 17 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Show HN: Immersive Gaussian Splat tour of grace cathedral, San Francisco (https://news.ycombinator.com/item?id=48984254)
- Matterport APIs Overview and SDK Documentation (https://matterport.github.io/developer-docs/api/)
- AccessNow FAQ (https://accessnow.com/faq/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
