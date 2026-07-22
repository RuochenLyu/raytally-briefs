---
title: "Galactic Morning Report"
date: "2026-07-22"
canonical: "https://raytally.com/en/ideas/2026-07-22-show-hn-a-self-running-space-economy-sim-in-rust-and-bevy/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Show HN: A self-running space economy SIM in Rust and Bevy"
  observed_at: "2026-07-22T00:33:19.791Z"
sources:
  - url: "https://news.ycombinator.com/item?id=48996187"
    boundary: "Published at 2026-07-21T18:29:57.000Z. Observed at 2026-07-22T00:33:19.791Z."
  - url: "https://github.com/Kalcode/spaceprojectsim"
    boundary: "Observed at 2026-07-22T00:33:19.791Z."
  - url: "https://www.worldanvil.com/features/chronicles"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.legendkeeper.com/features/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-07-22-show-hn-a-self-running-space-economy-sim-in-rust-and-bevy/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Galactic Morning Report
After defining factions and economic rules, writers can let a world evolve on its own and return to story events with traceable causes.

## Product concept

Science-fiction writers and tabletop game masters often want a world to keep evolving between creative sessions after they have defined its factions, resources, routes, and a few governing rules. They first specify what can happen—such as trade disruptions, alliances, resource shortages, or diplomatic conflicts—then mark the characters and places the system must never alter on its own. The simulator models resource flows and faction decisions in the background. When users return, they do not face a dense data table; they read an "Interstellar Morning Report" first: which planet is short on supplies, who signed a secret agreement, and which route suffered an accident. Every item expands into a causal chain showing the rules, events, and character choices that drove it. Authors can pin events they like as canon, or return to a branch point, change a rule, rerun the simulation, and compare an alternative outcome. Selected events can be exported as plot outlines, quest hooks, or tabletop-session opening briefs. The first version simulates only the resources and relationships users explicitly define. It does not write a complete novel for the author or present random outcomes as the only plausible development.

## Why now (backed by facts)

On July 21, a self-running space-economy simulator reached Show HN, earning 80 points and 25 comments and ranking 19th. It turns autonomous trade, shortages, and migration into a working system, while exposing a gap between simulated change and story material that writers can use directly.

## Direction (model inference, not independently verified)

Target user: The core users are science-fiction writers and tabletop game masters with an existing setting. They use it between chapters, while preparing a session, or after a long hiatus. Their characters and places already exist; what they lack is a believable new development. They do not want to reread an entire setting bible or let a generator rewrite their protagonists. The morning report compresses change into a small set of candidate events, making it easy to resume creative work quickly.

Minimal entry point: Constrain initial input to four entity types: factions, places, resources, and routes. Rules support only conditions, probabilities, resource increases or decreases, and relationship changes. Each simulation step creates structured events and records parent events and triggered rules. Store state in SQLite, and save snapshots and random seeds at branch points. The morning report selects only high-impact changes from the event graph and applies short templates. Its causality page traverses parent events directly rather than asking a model to invent explanations. The Space Project’s pure synchronous simulation core and command-buffer design are useful references. Do not build a 3D star map or allow arbitrary scripting at launch. First validate whether users will review, pin, and rerun events.

The strongest case against: The biggest risk is not an insufficiently complex simulation, but results that seem plausible yet cannot be written into a story. Small rule errors can make shortages and conflicts recur until they overwhelm the feed, leaving users to spend more time clearing noise. If causal chains become too long, the morning report turns back into a data dashboard. Pinning and branching can also create many near-duplicate saves, and users may lose track of which line is current canon. Background simulation adds ongoing compute and version-compatibility costs. If reviewing events takes longer than inventing them, abandon the general-purpose simulation approach. The product needs to narrow itself to a small set of validated world rules.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Create three import-ready sample worlds covering space trade, archipelago politics, and merchant-route warfare. Publish one week of morning reports and their full causal chains for each, so writers can judge whether the output is usable. Write technical breakdowns around open-source space-economy projects to capture related searches from the original HN post. Then invite science-fiction writing communities and tabletop game masters to submit rule sets, crediting strong templates in the product.

## Competitors & gaps (model inference)

- The Space Project: It already simulates autonomous ships, dynamic markets, contracts, and migration. Users can inspect a live event feed and faction relationships, and simulation state can persist in SQLite. It is more an economic system and native client, with authors participating mainly as observers or administrators. Its project description also does not position it as a shippable game. The current interface does not show canon pinning, branch-and-rerun workflows, or writing-oriented plot-outline exports. Galactic Morning Report can reuse its systems-design lessons. The real opening is to edit state changes into reviewable creative material while retaining the rule-and-event causal chain behind every news item.
- World Anvil Chronicles: World Anvil already provides maps, timelines, and custom calendars. Chronicles can connect events to map locations and supports multiple timelines and conflicting histories. It suits users organizing established settings and histories. Its official feature page emphasizes presenting and browsing events. It does not show ongoing simulation of resource economies: authors still need to conceive and enter events themselves. Nor does it show the ability to trace an event back through its governing rules and causes. Galactic Morning Report does not need to replace its world encyclopedia. It can generate candidate events and branch outcomes first, then export confirmed canon into an existing reference library.
- LegendKeeper: LegendKeeper already covers wikis, maps, and multiple timelines. It supports event management, permissions, secrets, collaboration, offline editing, and data export. Authors can link characters, places, and history. Its official page lists procedural generation as a planned feature, while its current strengths remain recording, organizing, and presenting material. It does not show continuous faction-economy simulation or news-style event summaries with causal chains. It works well as a long-term world reference. Galactic Morning Report fits the gap between writing sessions: the system proposes changes, and the author only reviews and pins them. The two products are more likely to connect through export than directly replace one another.

## How it makes money (model inference)

Charge a subscription per world project. The free tier includes one world and limits the length of each simulation run. Paid plans unlock more worlds, branched saves, long-running background simulations, and additional export formats. If compute costs are high, sell simulation-credit packs separately.

## Source context

Theme: Self-running space economy simulation in Rust and Bevy
Trigger Hacker News post (original English): Show HN: A self-running space economy SIM in Rust and Bevy
Heat at capture: ~80 points, 25 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Show HN: A self-running space economy SIM in Rust and Bevy (https://news.ycombinator.com/item?id=48996187)
- Kalcode/spaceprojectsim: The Space Project (https://github.com/Kalcode/spaceprojectsim)
- Visually Interconnect your World throughout Time and Space (https://www.worldanvil.com/features/chronicles)
- Features - Best Worldbuilding App for GMs (https://www.legendkeeper.com/features/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
