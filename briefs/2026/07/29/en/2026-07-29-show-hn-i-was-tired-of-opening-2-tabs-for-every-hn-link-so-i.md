---
title: "In-Context Community Comments"
date: "2026-07-29"
canonical: "https://raytally.com/en/ideas/2026-07-29-show-hn-i-was-tired-of-opening-2-tabs-for-every-hn-link-so-i/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Show HN: I was tired of opening 2 tabs for every HN link, so I made a userscript"
  observed_at: "2026-07-29T00:33:14.625Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49090607"
    boundary: "Published at 2026-07-28T22:09:06.000Z. Observed at 2026-07-29T00:33:14.625Z."
  - url: "https://github.com/twalichiewicz/HNewhere"
    boundary: "Observed at 2026-07-29T00:33:14.625Z."
  - url: "https://web.hypothes.is/help/overview-of-the-hypothesis-system/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://read.glasp.co/p/glasp-extension-v2-suggested-highlights-engine"
    boundary: "Published at 2026-07-22T00:00:00.000Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-07-29-show-hn-i-was-tired-of-opening-2-tabs-for-every-hn-link-so-i/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

In-Context Community Comments
A browser extension that lets readers view a shared long-form article, its community comments, and the exact passages those comments address on one page.

## Product concept

When readers open a long article from Hacker News, Reddit, or Lobsters, the browser extension automatically retrieves the article and its associated discussion. It identifies sentences, links, or figures directly cited in comments, then pins those discussions to the relevant passages instead of making users hunt across two pages. The reading page preserves the article’s normal layout. Small markers at the edge of each paragraph reveal factual corrections, author additions, counterexamples, or questions about that passage; every comment can still expand into its full thread and original link. Discussion that cannot be reliably located in the article remains at the bottom of the page rather than being forced onto an arbitrary paragraph. Readers can change the reading order to prioritize corrections, author responses, or the most disputed points. At any claim, they can save the source excerpt, the key rebuttal, and their own notes as a reading card, so returning later does not leave them with only a dead link. The first release supports clearly structured news, blog, and technical articles, along with several communities that have public comments. It will not pretend to match precisely on paywalled content, dynamically loaded full text, or comments without clear quotations; the extension will clearly say that it found only a related topic.

## Why now (backed by facts)

As observed on July 29, a HNewhere post that combines articles with Hacker News comments ranked 18th, with 83 points and 29 comments. Specific feedback in the discussion extends beyond switching between two tabs to mobile use, duplicate posts, and browser extensions, suggesting that readers are currently encountering more granular comparison-reading problems.

## Direction (model inference, not independently verified)

Target user: The core users are heavy readers who open technical long-form articles from Hacker News, Reddit, or Lobsters. They most urgently need to see community rebuttals when they encounter an unfamiliar conclusion, performance figure, or contested judgment. Switching tabs breaks their context, and long threads are hard to navigate. Showing sourced discussion beside the relevant paragraph lets them decide on the spot whether to trust the article.

Minimal entry point: Start with a verifiable Hacker News integration. Search the article’s normalized URL through HN Algolia, then retrieve the comment tree through the Hacker News API; HNewhere has already validated both dependencies. After parsing the article, store text, links, and positional fingerprints for each paragraph. First apply hard matches based on explicit quotations, shared URLs, and number fragments. Then use semantic similarity only to narrow the candidate paragraphs for remaining comments, rather than allowing a model to choose the anchor outright. Use both text-quote and position selectors for results, following an approach similar to Hypothesis. Put all low-confidence results at the end of the article, and exclude paywalls and frequently changing dynamic pages from the first release.

The strongest case against: A mismatched paragraph can place an irrelevant challenge beside an author’s claim and cause readers to misjudge the article. Quotations are often paraphrased or truncated, so semantic similarity alone can easily create plausible-looking errors. Site redesigns, lazy loading, and duplicate paragraphs can also cause old anchors to drift. Pulling content across communities means handling API limits, deleted material, duplicate posts, and differences in thread ordering. Storing articles and comments also raises privacy and copyright concerns. Unless the tool clearly shows the basis and confidence of each match, it could damage trust more than reading in two tabs.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The most direct early users are already in Hacker News long-form discussion threads. Begin with an inspectable-source userscript and show paragraph mappings on real articles in relevant posts. With each newly supported site, update the project page with before-and-after screenshots and failure cases. Open matching rules and a mis-match feedback channel can draw power readers into submitting unusual pages while letting technical users correct rules themselves.

## Competitors & gaps (model inference)

- HNewhere: HNewhere can already identify the Hacker News discussion associated with an article. It places comments in a resizable sidebar while retaining collapse and reply controls. It also uses the Hacker News API and HN Algolia search to find existing posts. That solves the two-tab switch, but its model remains primarily a side-by-side article and comment view. Its public materials do not indicate that comments are automatically anchored to specific passages in the article. Readers still have to decide which claim a rebuttal addresses. It also does not reorder discussion by corrections, author responses, or level of controversy. When an article has been submitted more than once, it currently uses just one matching record. The opening is to turn existing discussion into verifiable paragraph annotations while remaining conservative about low-confidence matches.
- Hypothesis: Hypothesis already offers a mature web annotation layer, browser extension, and sidebar. When a user selects text, it creates W3C-style selectors that locate the original passage. Annotations can appear as in-page highlights and link directly to sidebar cards. It also supports replies, groups, search, and an open API. These capabilities demonstrate a reliable path for paragraph anchoring and threaded presentation. Its content is primarily annotations users create themselves, rather than imported discussions already taking place in communities. Readers must still wait for others to contribute within the same system. It also does not automatically determine which sentence in an article an external comment quotes. Organizing community threads around corrections, counterexamples, and author responses remains a clear gap.
- Glasp: Glasp covers web highlighting, notes, syncing, and community discovery. Its latest extension includes suggested highlights, article overviews, and a redesigned sidebar. Readers can also see what others highlighted on the same page. It is closer to a personal knowledge base and social highlighting tool than a reconstruction of forum discussions. Community material forms around excerpts users save; it does not automatically retrieve full threads from sites such as Hacker News. Nor does it pin quotations and links in external comments back to the source article. Comment context, author identity, and parent-child reply structure are not its primary presentation. It can help readers find key passages, but not directly show how a particular argument was challenged. The opportunity is to retain forum provenance and thread structure while providing trustworthy paragraph-level correspondence.

## How it makes money (model inference)

The basic extension is free, with local reading and side-by-side comparison for one community. A monthly or annual Pro subscription adds cross-device reading cards, multi-community aggregation, historical discussion merging, and advanced filters.

## Source context

Theme: Hacker News article-and-comment reader
Trigger Hacker News post (original English): Show HN: I was tired of opening 2 tabs for every HN link, so I made a userscript
Heat at capture: ~83 points, 29 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Show HN: I was tired of opening 2 tabs for every HN link, so I made a userscript (https://news.ycombinator.com/item?id=49090607)
- twalichiewicz/HNewhere (https://github.com/twalichiewicz/HNewhere)
- Overview of the Hypothesis System (https://web.hypothes.is/help/overview-of-the-hypothesis-system/)
- Glasp Extension v2: Suggested Highlights, a New Sidebar, and 7 Languages (https://read.glasp.co/p/glasp-extension-v2-suggested-highlights-engine)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
