---
title: "Which EDH Deck Can I Build Tonight?"
date: "2026-08-18"
canonical: "https://raytally.com/en/ideas/2026-08-18-seeing-decks-in-bulk-collection-question/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "\"Seeing\" decks in Bulk - Collection Question"
  observed_at: "2026-08-18T00:36:17.064Z"
sources:
  - url: "https://www.reddit.com/r/EDH/comments/1vr7235/seeing_decks_in_bulk_collection_question/"
    boundary: "Published at 2026-08-17T22:31:12.000Z. Observed at 2026-08-18T00:36:17.064Z."
  - url: "https://github.com/AndreaGiulianini/bulkbrew"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://mtgdeck.build/how-it-works"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://scryfall.com/docs/faqs/i-m-having-trouble-accessing-the-scryfall-api-or-i-m-blocked-17"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-18-seeing-decks-in-bulk-collection-question/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Which EDH Deck Can I Build Tonight?
When an EDH player wants to try a new commander using cards they already own, this tool fills gaps with functional substitutes and produces a complete 100-card deck they can play tonight.

## Product concept

EDH is a Magic: The Gathering format where players build 100-card decks around a single commander. When players want to start a new deck from their own collection, they usually begin with a popular list, then realize they are missing dozens of expensive singles. The real question is not, “How far am I from the original list?” It is whether the cards they already own can form a deck they can play tonight. Players import their collection from a collection-management site and select a commander or theme they want to try. The product breaks cards into functions: early mana acceleration, card draw, answers to opposing threats, and ways to close out a game. It finds cards in the collection that can stand in for popular singles, then explains the trade-off of each replacement, such as being slower or answering only certain target types. Rather than ranking results by the lowest price, the results page groups them into “build now,” “upgrade with a few key cards,” and “the core idea is there, but the build needs a different direction.” Opening any option reveals the complete 100-card list, missing-card priorities, and the role each owned card plays in the deck. Once a player chooses an option, they can export it to a familiar decklist site or create a playtest list with placeholder cards. The first release supports common commander themes and single-collection imports, solving the immediate problem of one player starting one new deck. Price tracking, purchasing assistance, and complex power-level ratings can come later; on day one, it should help a player pull a playable deck from a box of loose cards.

## Why now (backed by facts)

A post on r/EDH dated August 17, 2026 asked whether a personal collection could be compared against EDHRec and Moxfield decklists to find deck shells that could be completed. As of August 18, 2026, the post had a score of 1 and 2 comments; no existing tool was offered in the comments, so the gap remains turning collection overlap into a playable 100-card list.

## Direction (model inference, not independently verified)

Target user: Paper Magic players with a large accumulation of loose cards who do not know what commander deck to build next. The moment may be a game night, a freshly organized collection, or opening a commander they want to try. They do not want to copy a popular list first and then buy dozens of missing cards. They need to see which complete strategies their collection already supports and what a small number of additions would change.

Minimal entry point: Start with ManaBox CSVs, Moxfield exports, and plain-text card lists, normalizing them into card name, printing, and quantity. Use Scryfall bulk data for name resolution, legality, color identity, and rules text rather than making card-by-card requests. Initially cover only common commanders and themes that have been manually reviewed. Tag ramp, card draw, removal, protection, and finishers using rules text, card types, and mana curves. Matching must first satisfy color identity, singleton requirements, and functional quotas, then generate candidates by collection coverage. The first version should not attempt fine-grained power assessments; it should explain replacement trade-offs and output legal 100-card lists.

The strongest case against: If functional-role classification is wrong, the system may produce a decklist with the right card count that cannot actually function. EDH cards often serve multiple purposes, and similar rules text does not necessarily mean the same role in play. Collection records may also omit cards, duplicate them, or include unusable printings, and those errors carry through to recommendations. Explaining the cost of every substitution requires maintaining theme rules and exceptions, while content costs will keep growing with new cards. If an initial list is visibly short on lands, card draw, or finishers, players will have little reason to trust another recommendation. Before proceeding, manually blind-test a small set of commanders and let users quickly correct role tags.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users are already asking collection-matching questions in r/EDH discussions; respond with an anonymized example of a deck they can build. Keep publishing before-and-after comparisons showing what can be built from a box of loose cards, with importable lists attached. Build shareable pages around individual commanders so decklists can naturally enter relevant community discussions. Preserve collection gaps and replacement reasoning on results pages, making them easy to share with friends for review.

## Competitors & gaps (model inference)

- BulkBrew: BulkBrew already imports ManaBox CSVs, Moxfield exports, and plain-text card lists. It can build a complete deck from a collection around a chosen commander, or work in reverse to find the commanders best suited to that collection. Its generation process checks functional roles such as ramp, card draw, removal, and board wipes, and clearly flags missing cards. That makes collection-based auto-building hard to differentiate on its own. The opening is in comparison and explanation: show several realistic options at once, grouped into decks that are ready now, decks that need a few additions, and decks that require a different direction. Each functional substitution should also explain what is lost in speed, target coverage, or consistency. Public documentation does not show this kind of card-by-card trade-off interface.
- MTG Deckbuilder: MTG Deckbuilder already reads ManaBox collection exports and generates legal candidates within collection and format constraints. Users can lock in a commander or let the system find a suitable archetype. Results include a full decklist, structural scores, total cost, and archetype tags, with export to a generic text decklist. It already covers the core job of showing what a player can build from the cards they own, so a new product cannot compete on decklist overlap alone. Its documentation says collection import currently supports only ManaBox; other tracker formats are not yet supported. The opportunity is low-friction import from common sources such as Moxfield, along with EDH-specific explanations of functional substitutions. Players should understand why a card from their collection was selected, not just see an aggregate score.

## How it makes money (model inference)

Freemium subscription. The free tier supports one collection import and a limited number of deck candidates. Subscribers can save multiple collections, generate plans repeatedly, and see full replacement rationales and upgrade paths.

## Source context

Theme: EDH deckbuilding from a personal collection
Trigger Reddit single-post demand observation: r/EDH — "Seeing" decks in Bulk - Collection Question

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- "Seeing" decks in Bulk - Collection Question (https://www.reddit.com/r/EDH/comments/1vr7235/seeing_decks_in_bulk_collection_question/)
- AndreaGiulianini/bulkbrew (https://github.com/AndreaGiulianini/bulkbrew)
- How it works · MTG Deckbuilder (https://mtgdeck.build/how-it-works)
- I'm having trouble accessing the Scryfall API, or I'm blocked (https://scryfall.com/docs/faqs/i-m-having-trouble-accessing-the-scryfall-api-or-i-m-blocked-17)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
