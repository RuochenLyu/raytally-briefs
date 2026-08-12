---
title: "Baldur’s Gate 3 Ending Planner"
date: "2026-08-12"
canonical: "https://raytally.com/en/ideas/2026-08-12-is-there-a-tool-that-maps-consequences-details-in-post/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Is there a tool that maps consequences? (Details in post)"
  observed_at: "2026-08-12T00:35:50.552Z"
sources:
  - url: "https://www.reddit.com/r/BaldursGate3/comments/1vln13t/is_there_a_tool_that_maps_consequences_details_in/"
    boundary: "Published at 2026-08-11T00:00:00.000Z. Observed at 2026-08-12T00:35:50.552Z."
  - url: "https://bg3.wiki/wiki/Endings"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://gamestegy.com/bg3/checklists"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://js.cytoscape.org/index.html"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-12-is-there-a-tool-that-maps-consequences-details-in-post/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Baldur’s Gate 3 Ending Planner
Plan a new Baldur’s Gate 3 run by selecting the characters, endings, and rewards you want to preserve, then get a feasible route and the branches you cannot combine.

## Product concept

Players preparing a second run of Baldur’s Gate 3 often already know which companion they want to save, which reward they want to earn, or which ending they want to reach. What they do not know is whether those wishes fit in the same save. They select their goals and choose how much spoiler exposure they will accept. A goal might be a character’s fate, a romance, or a key piece of equipment. The product places those goals on a collapsible story-node graph and works backward from the ending through prerequisite choices, trigger conditions, and mutually exclusive branches. It produces a chapter-by-chapter route that marks what must be done and what can be skipped. When two goals cannot coexist, it identifies the earliest choice where they conflict and shows what remains possible if either goal is abandoned. Before entering a chapter, players expand only the nodes they need to know about now. Changing one key decision immediately recalculates the rest of the route. Every node includes the game version, trigger conditions, and links to community-maintained evidence, making it easier to spot outdated guidance or rule changes caused by mods. The first release can cover main-story endings, companion endings, and key rewards for one stable version, rather than trying to catalog every chest or provide a complete step-by-step walkthrough. It answers, “Can these wishes all happen together?” so players can start a run with their own plan.

## Why now (backed by facts)

An August 11 r/BaldursGate3 post asked how to plan choices and consequences in advance, but commenters could offer only wiki searches and firsthand play. The poster then specifically asked about the earlier implications of character-survival goals and mutually exclusive routes, exposing a gap: the information exists, but is difficult to combine.

## Direction (model inference, not independently verified)

Target user: The core user has finished the game once and is preparing a second run. They already know some of the story and have clear intentions about companions, romances, or rewards they want to preserve. Their need peaks between character creation and entering a new chapter: one wrong choice may not surface for dozens of hours, while checking guides again can reveal irrelevant spoilers. They do not want a full walkthrough; they want to know whether their few wishes can coexist.

Minimal entry point: Start with a manually curated, versioned directed graph of conditions. Include only main-story endings, companion endings, and key rewards. Classify edges as prerequisites, exclusions, character-preservation conditions, and chapter locks. Convert selected goals into Boolean constraints, then use backtracking and conflict detection to find feasible combinations and return the earliest incompatible node. Cytoscape.js can render the collapsible relationship graph; it supports interactive directed graphs and graph analysis. The first version should not automatically parse every guide or promise mod coverage. Editors enter each rule with its source article and verification status.

The strongest case against: A wrong rule could leave players dozens of hours into a run before they discover their route has failed. Unlike an ordinary guide correction, that kind of error can quickly destroy trust. Branch conditions may also depend on hidden states, dialogue order, and whether a character is present. Recording only obvious choices would create routes that look feasible but are not. Game updates and mods can change conditions, making version maintenance an ongoing editorial cost. Spoiler tiers also require node-by-node review; hiding section headings is not enough. Without reproducible test saves and a community review process, the product should stay focused on a small set of high-frequency endings rather than seek full story coverage.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users are already in second-run planning threads, companion-ending discussions, and build communities. Shareable conflict cards can answer whether two specific goals can coexist while hiding later spoilers. Search acquisition can target long-tail queries such as whether a player can save a specific character and obtain a specific reward. Free links open with goals preselected, turning community replies from text explanations into routes others can keep editing. Contributors can submit evidence links and version revisions, gradually expanding coverage of high-frequency branches.

## Competitors & gaps (model inference)

- bg3.wiki: bg3.wiki documents quests, endings, and outcomes for individual characters. Its ending pages also explain how earlier choices alter final scenes. Players can follow links to trace individual conditions and consequences, and its depth is sufficient for manual planning. But it is organized around articles and quests, not a player’s set of goals. Users must decide for themselves whether multiple conditions can coexist and remember prerequisites across chapters. For mutually exclusive routes, it does not directly identify the earliest point of conflict. It works well as an evidence base, but does not turn that information into a recalculable personal route. The opening is reverse planning from goals, conflict explanations, and spoiler-tiered disclosure.
- Gamestegy BG3 Checklists: Gamestegy offers full walkthroughs and item checklists across all chapters. Entries are organized by area and sequence, and users can save checklist progress in their browser. That is more convenient than searching page by page for players worried about missing quests, gear, and interactions. Its public pages present a relatively complete recommended checklist, centered on collection and completion. It does not first ask which character a player wants to save or which ending they want. When goals conflict, players still need to read the entries and make the trade-off themselves. Nor can a checklist recalculate only the affected later steps after one key choice changes. This product can avoid competing on completionism and focus on the feasibility and cost of a few goals.

## How it makes money (model inference)

Charge once per stable game version to unlock the full goal library, saved routes, and multi-plan comparison. A free tier can trial a limited set of main-story and companion goals, while version updates are sold as separate content packs.

## Source context

Theme: Baldur’s Gate 3 choice-consequence and branch-conflict planning
Trigger Reddit single-post demand observation: r/BaldursGate3 — Is there a tool that maps consequences? (Details in post)

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Is there a tool that maps consequences? (Details in post) (https://www.reddit.com/r/BaldursGate3/comments/1vln13t/is_there_a_tool_that_maps_consequences_details_in/)
- Endings - bg3.wiki (https://bg3.wiki/wiki/Endings)
- Baldur's Gate 3 (BG3) - All Checklists (https://gamestegy.com/bg3/checklists)
- Cytoscape.js (https://js.cytoscape.org/index.html)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
