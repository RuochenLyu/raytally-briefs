---
title: "Offline Archiving for Logged-In Websites"
date: "2026-08-26"
canonical: "https://raytally.com/en/ideas/2026-08-26-help-archiving-starfall-com-games/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Help archiving starfall.com games"
  observed_at: "2026-08-26T00:36:20.994Z"
sources:
  - url: "https://www.reddit.com/r/internetarchive/comments/1vxr01v/help_archiving_starfallcom_games/"
    boundary: "Published at 2026-08-25T00:00:00.000Z. Observed at 2026-08-26T00:36:20.994Z."
  - url: "https://crawler.docs.browsertrix.com/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://webrecorder.net/blog/2021-02-22-archiveweb-page-app-new-tools/"
    boundary: "Published at 2021-02-22T00:00:00.000Z."
  - url: "https://playwright.dev/docs/codegen"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-26-help-archiving-starfall-com-games/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Offline Archiving for Logged-In Websites
After an archivist logs in locally and demonstrates key actions, the tool produces a JavaScript site archive that has been verified through offline interaction.

## Product concept

When web archivists encounter JavaScript games that only launch after login, conventional downloaders often preserve nothing but an empty shell. In an isolated browser on their own computer, users sign in to sites they are authorized to preserve and personally walk through key paths, such as launching a game or switching levels. Login credentials never leave the device. The product uses this real session to explore page states and records scripts, network responses, local storage, and Service Workers. Users do not need to record an entire playthrough; they demonstrate each key point once. The system organizes discovered buttons, page transitions, and resource dependencies into an archive package, then disconnects from the network and replays every recorded path. If a button fails, the result points precisely to the relevant page and action step, so the archivist can re-record only that short segment. Once validation passes, the exported package includes the capture time, path manifest, and resource checksums, making it possible to verify later that it still runs. The first version focuses on interactive webpages and games that users are authorized to access. It does not attempt to bypass logins, paywalls, or access controls. Its purpose is to turn one still-functioning browsing session into a verifiable offline archive.

## Why now (backed by facts)

An August 25 r/internetarchive post asked how to preserve logged-in Starfall JavaScript games. Commenters suggested Browsertrix and ghostarchive.org, but a low-effort, verifiable workflow for archiving interactive sessions is still missing.

## Direction (model inference, not independently verified)

Target user: Museum, library, and independent web archivists who are authorized to preserve a site but may have only one remaining chance to log in. When standard downloaders leave blank pages, rebuilding every level manually is slow and prone to missing resources. They need to preserve key interactions they have personally verified, along with path evidence that can be reviewed later, rather than crawl more broadly.

Minimal entry point: Start with a Chromium-only desktop app that wraps a local Browsertrix Crawler. Users sign in themselves through an isolated profile, and the app never accesses plaintext passwords. Key actions can be saved as Chrome Recorder JSON User Flows. Playwright then adds durable locators, network events, and step assertions. Each path produces a WACZ file for offline replay in ReplayWeb.page. The first release will not automatically traverse every possible state; it will only expand links, buttons, and level entries near demonstrated paths. Failure records link the page, action, missing request, and screenshot so users can re-record only the affected section.

The strongest case against: Login-state files may contain sensitive cookies and request headers that could be used to impersonate an account if exposed. Local isolation, encrypted storage, and secure deletion must therefore be core design requirements. Games may also depend on WebSockets, real-time services, or server-side state, so a complete resource set may still not run offline. Path branches can multiply quickly with level and account state, making exploration nearly as costly as manual testing. Random animation and delayed loading can also create false failures. If the system repeatedly flags working archives as broken, archivists will return to checking pages one by one, eliminating the product’s time-saving value.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Initial users are already active in web-archiving communities and digital-preservation work. An August 25 r/internetarchive request provides both a reproducible site and a concrete failure mode. Start with a publicly verifiable sample package showing that login remains local, each step is accepted offline, and failures can be repaired in place. Then open-source the path validator to invite existing Browsertrix and ArchiveWeb.page users to import WACZ files and try it.

## Competitors & gaps (model inference)

- Browsertrix: Browsertrix supports interactive browser profiles that can reuse login state. It can also run Chrome DevTools Recorder JSON User Flows and export WACZ files. Its existing QA compares screenshots, text, and resources between capture and replay. These capabilities already cover authenticated capture, behavior scripts, and page-level checks. Its public workflow still centers on configuring crawl jobs, behavior files, and post-capture review. Archivists must decide which actions are worth recording and interpret why page metrics are anomalous. The opening is to turn a human demonstration directly into a path manifest, pinpoint an offline failure to a specific click, and let users re-record only the broken segment.
- ArchiveWeb.page: ArchiveWeb.page can record content a user sees in an existing Chromium browser, including authenticated sites. Archives remain on the local machine, can be replayed offline, and can be exported as WACZ files. It is well suited to collecting interactive pages while browsing, with a straightforward login experience. Its capture scope primarily follows content the user personally visits and triggers. Its community documentation notes that it cannot crawl automatically like Browsertrix. Complex games may therefore still require archivists to click through every level and determine for themselves which branches were missed. This product can build on its local-first approach by exploring branches around demonstrated paths, then validating each step offline and producing a failure list that can be repaired locally.

## How it makes money (model inference)

Sell the desktop app as a per-device license with a defined update period. Offer an institutional edition priced per archivist seat, with centralized policies, audit logs, and batch verification.

## Source context

Theme: Reliable archiving of authenticated interactive JavaScript sites
Trigger Reddit single-post demand observation: r/internetarchive — Help archiving starfall.com games

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Help archiving starfall.com games (https://www.reddit.com/r/internetarchive/comments/1vxr01v/help_archiving_starfallcom_games/)
- Browsertrix Crawler Docs (https://crawler.docs.browsertrix.com/)
- Announcing New ArchiveWeb.page App, Deprecating Older Tools (https://webrecorder.net/blog/2021-02-22-archiveweb-page-app-new-tools/)
- Playwright Documentation: Test generator, Authentication, Service Workers (https://playwright.dev/docs/codegen)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
