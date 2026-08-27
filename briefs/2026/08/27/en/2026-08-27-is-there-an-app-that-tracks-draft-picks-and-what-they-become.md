---
title: "Draft Pick Lineage"
date: "2026-08-27"
canonical: "https://raytally.com/en/ideas/2026-08-27-is-there-an-app-that-tracks-draft-picks-and-what-they-become/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Is there an app that tracks draft picks and what they become?"
  observed_at: "2026-08-27T00:36:01.990Z"
sources:
  - url: "https://www.reddit.com/r/DynastyFF/comments/1vzcdvi/is_there_an_app_that_tracks_draft_picks_and_what/"
    boundary: "Published at 2026-08-26T22:46:57.000Z. Observed at 2026-08-27T00:36:01.990Z."
  - url: "https://docs.sleeper.com/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.fantasyamp.com/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://rosteraudit.com/trades/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-27-is-there-an-app-that-tracks-draft-picks-and-what-they-become/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Draft Pick Lineage
When dynasty-league members revisit old trades, they can follow a draft pick through every transfer to the player it ultimately selected.

## Product concept

In dynasty fantasy football leagues, a future draft pick may be traded three or four times. Once the draft happens years later, people remember that they “gave away a first-rounder” but struggle to find out which player it ultimately became. After a league commissioner connects existing league data, the product assigns every pick a permanent ID that does not change with season naming. Each time the pick is traded, its card extends the transfer trail, showing the sender, recipient, accompanying trade assets, and draft position at the time. As soon as someone uses the pick on draft night, the card changes from an abstract year-and-round label into a player profile. Every earlier trade involving that pick is automatically updated with the player, creating an expandable lineage tree. When reviewing an old trade, users can trace back to its origin or forward to the final outcome from any transaction. They can also share an updated trade card in league chat, giving decisions made years ago new life as conversation material. The first release imports trades and drafts from common dynasty leagues, clarifying pick lineage without telling players which trade was better value.

## Why now (backed by facts)

An August 26 r/DynastyFF post asked how to track which player a draft pick in an old trade ultimately became; commenters suggested Roster Audit, Dynasty Deal Maker, Dynasty Report Card, and Fantasy Amp, but a league view that automatically follows the pick through its full transfer history is still missing. As of August 27, the post had 20 points and 8 comments, suggesting that once draft outcomes are set, reviews of old trades immediately trigger this kind of search.

## Direction (model inference, not independently verified)

Target user: The core users are commissioners and active managers in long-running Sleeper dynasty leagues. They need to trace a pick’s path after the draft, when an old trade resurfaces in group chat, or when someone takes over an orphaned team. By then, trade records span multiple seasons, and year-and-round labels no longer identify the same pick. They want a league history they can verify and share, not another trade-value score.

Minimal entry point: Connect through a Sleeper league ID or username with read-only syncing only. Its API can retrieve historical league relationships, weekly transactions, traded picks, past drafts, and individual draft results. Generate a stable local key for each pick using at least the season, round, and original roster_id. Then build directed transfer edges from transaction_id and trade time, and backfill the draft pick’s player_id to every ancestor node. Limit the first release to Sleeper dynasty leagues; do not support ESPN, Yahoo, or screenshot parsing. Clearly flag historical gaps and unusual draft situations for review rather than guessing at missing links.

The strongest case against: Historical data may not always be sufficient to reconstruct every pick uniquely. Broken league-continuation links, commissioner rebuilds, or supplemental drafts can prevent automatic continuity. Multi-team trades, draft-night pick swaps, and compensatory adjustments further raise the chance of incorrect matches. If a pick is misidentified, every old trade could be backfilled with the wrong player, and share cards would amplify the dispute. The product must retain source records, matching evidence, and a way to correct errors manually. Another practical constraint is that Sleeper’s API is read-only and commercial use requires separate authorization, so data licensing must be resolved before charging users.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users are already in r/DynastyFF, Sleeper league chats, and discussion threads about existing tools. Publish a no-signup league example page where commissioners can enter league details and generate a shareable “Who did this pick become?” card. After the draft, generate a batch of the league’s most convoluted pick lineages, which naturally lends itself to replies and group-chat sharing. Then offer dynasty podcasts and league newsletter writers embeddable public timelines, using real historical trades to create search entry points.

## Competitors & gaps (model inference)

- Fantasy Amp: Fantasy Amp already offers a Sleeper Trade Tracker as a free tool. It is the closest match because users do not need to adopt a new league-management platform. Its current offering also includes rookie rankings, tiers, and mock drafts, with trade tracking as one tool among many. Its public pages do not say whether future picks receive permanent cross-season identities or show a continuous lineage when a pick changes hands several times. Even if it maps rookie picks to the players eventually selected, it does not explicitly support tracing the full chain backward and forward from any past trade. The opening is to make “how this pick became that player” the primary interface rather than a supporting trade table. Share cards can also highlight automatic updates years later and renew debate over old trades in league chats.
- Roster Audit: Roster Audit connects to Sleeper leagues and provides full trade histories, per-trade grades, draft grades, and league analysis. It has already solved the import hurdle and covers a common review workflow for commissioners. Its core framing centers on trade ratings, manager records, and value changes, making it useful for judging who came out ahead. This product should not compete on valuation accuracy or rebuild a full league analytics suite. Its public description does not emphasize a permanent identity for each future pick or explain how that identity persists through multiple trades. The remaining opening is to treat a draft pick as a continuing object, not a line item in a trade. The result page should take users from the pick’s origin through every recipient to the player ultimately selected, while retaining the assets exchanged alongside it. That creates a verifiable league history, not another report card.

## How it makes money (model inference)

Charge a one-time per-league archive unlock fee for complete historical backfilling, ongoing sync, and share-card exports. Keep a small number of trades free to preview so commissioners can confirm that the data links correctly before paying. If Sleeper data is used for a commercial service, the necessary authorization must first be confirmed and obtained.

## Source context

Theme: Fantasy football draft-pick lineage tracking
Trigger Reddit single-post demand observation: r/DynastyFF — Is there an app that tracks draft picks and what they become?

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Is there an app that tracks draft picks and what they become? (https://www.reddit.com/r/DynastyFF/comments/1vzcdvi/is_there_an_app_that_tracks_draft_picks_and_what/)
- Sleeper API Documentation (https://docs.sleeper.com/)
- Fantasy Amp: Dynasty Fantasy Football Amplified (https://www.fantasyamp.com/)
- Trade Grades — Every Dynasty Trade Graded A+ to F (https://rosteraudit.com/trades/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
