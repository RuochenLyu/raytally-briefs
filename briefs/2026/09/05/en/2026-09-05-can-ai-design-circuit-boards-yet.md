---
title: "PCB Machine Jury"
date: "2026-09-05"
canonical: "https://raytally.com/en/ideas/2026-09-05-can-ai-design-circuit-boards-yet/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Can AI design circuit boards yet?"
  observed_at: "2026-09-05T00:33:31.480Z"
sources:
  - url: "https://eebench.org/blog/can-ai-design-circuit-boards-yet/"
    boundary: "Published at 2026-09-04T00:00:00.000Z. Observed at 2026-09-05T00:33:31.480Z."
  - url: "https://docs.kicad.org/10.0/id/pcbnew/pcbnew.html"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.cadence.com/en_US/home/tools/pcb-design-and-analysis/allegro-ai-studio.html"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.altium.com/documentation/altium-designer/tutorial/verifying-board-design"
    boundary: "Published at 2026-07-22T00:00:00.000Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-05-can-ai-design-circuit-boards-yet/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

PCB Machine Jury
Before fabrication, engineers reviewing an AI-modified PCB get manufacturability, signal, and thermal objections they can locate and reproduce in their EDA tool.

## Product concept

After receiving an AI-modified PCB layout, a hardware engineer launches a review from their EDA software before sending the board out for fabrication. The product reads the board file, component libraries, fabricator capability tables, and existing design rules, then pins issues directly to the relevant trace, pad, or component location. Reviews are organized into manufacturability, signal integrity, and thermal categories. Signal-integrity findings explain in plain language whether a high-speed signal may distort along a trace. Every objection includes an executable rule, simulation parameter, or fabrication constraint that the engineer can reproduce in their own software. When an engineer accepts, ignores, or fixes a finding, the system rechecks only the affected areas. The review page preserves before-and-after screenshots, the triggered rule, and the verification result, so the hardware lead can decide whether the change is ready for the next board revision. The first release can start with KiCad projects and common four-layer-board rules, prioritizing frequent issues such as clearance, drill diameter, impedance, and thermal pads. It does not route the board automatically for the engineer or treat an unreproducible model explanation as a review conclusion.

## Why now (backed by facts)

On September 4, EEBench used OpenAI’s demonstration of AI operating KiCad to ask how the reliability of model-generated circuits can be verified. As of September 5, the discussion had 144 points and 84 comments on Hacker News, ranking tenth; a pre-fabrication review of AI-modified boards is therefore more likely to be on engineers' agenda.

## Direction (model inference, not independently verified)

Target user: Hardware engineers and small hardware teams using KiCad. The key moment comes after AI has changed a layout but before the design is submitted to a board fabricator. At that point, the files may look ready to manufacture, while rereading the whole design manually is time-consuming. Engineers need to confirm that the changes have not crossed fabrication limits or hidden high-speed, thermal, or footprint problems in local details.

Minimal entry point: Use KiCad projects as the only input format, parsing board files, rule files, and footprint references. Connect to the running editor through the KiCad IPC API and generate JSON DRC reports with `kicad-cli`. First convert fabricator capability tables into version-controlled rule configurations. Initial checks focus on clearance, drill diameter, differential pairs, and thermal pads. Each conclusion outputs object coordinates, the rule expression, and input parameters. A signal or thermal finding that cannot produce a runnable check is downgraded to manual confirmation and cannot block release.

The strongest case against: False positives would force engineers to review findings one by one and could bury serious issues in alerts. Fabricator capability tables often contain conditions, exceptions, and process options whose context can be lost when converted into rules. Signal-integrity and thermal judgments also depend on stackup, materials, and operating conditions that may not be present in the project files. A partial recheck that misses cross-region coupling could produce a false pass. Teams may also refuse to upload unreleased hardware designs. Without local operation, input-completeness checks, and explicit manual-confirmation states, it will be difficult to earn approvers' trust.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Early users are most likely to come through the KiCad plugin directory, open-source hardware repositories, and PCB-fabrication technical communities. Publish sample boards with deliberate defects so engineers can compare native DRC with incremental review results directly. Maintain public rule packs for common fabricators, using rule updates to drive return visits. Integrating with pull-request checks for open-source hardware projects would also put review reports into teams' existing workflows.

## Competitors & gaps (model inference)

- KiCad’s native DRC and manual review: KiCad already provides rule-driven DRC that can locate violating objects and export text or JSON reports. Engineers can also write custom rules by net, region, and footprint, and set global constraints from board-fabrication parameters. It is well suited to checking rules that have already been expressed, but it does not proactively challenge the assumptions behind an AI-made change. Engineers must still judge the relationships among signal integrity, thermal behavior, and component data themselves. The opening is not to replace DRC, but to turn external constraints into executable rules. The product must also identify each rule’s source, applicable objects, and recheck result. Every finding should locate and run in KiCad, rather than creating another alert list that cannot be verified.
- Cadence Allegro AI Studio: Cadence Allegro AI Studio already covers automated placement, constraint-driven routing, and multiphysics analysis. It brings signal, power, and thermal analysis into the design workflow and supports natural-language initiation of complex tasks. These capabilities serve a full enterprise design and analysis stack with a strong existing automation loop. This product instead has an opening to accept KiCad projects generated or modified by external AI. It does not generate the layout again; it serves as an independent review layer. An initial version could offer a lighter pre-fabrication check centered on common four-layer boards and fabrication constraints. Its viability depends on whether findings are reproducible and whether teams can retain their existing EDA workflow.
- Altium Designer rule checking: Altium Designer is itself a rule-driven environment, with online and batch DRC. Its reports list enabled rules, violation counts, and specific violation details. That already covers many routine checks used by mature teams and reduces the need for a separate review tool. What it does not directly address is how to review the risks introduced by a particular AI change. Teams still need to distinguish pre-existing issues, newly introduced issues, and accepted exceptions. The product could enter through before-and-after comparisons, targeted rechecks, and retained evidence. If it merely repeats clearance and trace-width checks, it will be hard to offer more value than native DRC.

## How it makes money (model inference)

Charge per review project, with a base fee covering one full check and several partial rechecks. A monthly team plan adds shared rule libraries, approval records, and private deployment options.

## Source context

Theme: Can AI design circuit boards yet?
Trigger Hacker News post (original English): Can AI design circuit boards yet?
Heat at capture: ~144 points, 84 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Can AI design circuit boards yet? (https://eebench.org/blog/can-ai-design-circuit-boards-yet/)
- KiCad APIs and Bindings / PCB Editor Documentation (https://docs.kicad.org/10.0/id/pcbnew/pcbnew.html)
- Allegro AI Studio (https://www.cadence.com/en_US/home/tools/pcb-design-and-analysis/allegro-ai-studio.html)
- Verifying Your Board Design (https://www.altium.com/documentation/altium-designer/tutorial/verifying-board-design)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
