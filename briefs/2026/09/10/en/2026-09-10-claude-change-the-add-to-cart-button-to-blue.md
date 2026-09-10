---
title: "Point-and-Edit Code Changes"
date: "2026-09-10"
canonical: "https://raytally.com/en/ideas/2026-09-10-claude-change-the-add-to-cart-button-to-blue/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Claude, change the “Add to Cart” button to blue"
  observed_at: "2026-09-10T00:33:04.919Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49623754"
    boundary: "Published at 2026-09-09T00:00:00.000Z. Observed at 2026-09-10T00:33:04.919Z."
  - url: "https://site.builder.io/web-apps"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://jam.dev/docs/creating-a-jam"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://docs.github.com/en/rest/pulls/pulls"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-10-claude-change-the-add-to-cart-button-to-blue/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Point-and-Edit Code Changes
On a test page, product managers can select a real UI element and describe the change, then receive a source-code patch, affected-page list, and interactive preview within minutes.

## Product concept

When a product manager spots the wrong color on an Add to Cart button in a pre-release site, they select the real element through a browser extension and describe the desired change in one sentence. The extension saves the element’s DOM path, current screenshot, and page, while connecting to the project repository and design-token library. Instead of becoming a circled screenshot followed by several rounds of clarification, the request enters development with an exact location. The agent traces the selected element to its component, style source, and token references, then makes the change on an isolated branch. If the button is reused across multiple pages, it lists every affected page and generates before-and-after screenshots for each one. When “blue” could refer to several brand shades, the product presents the candidates in a preview so the requester can choose on the spot. Once the change is ready, the requester receives an interactive preview link. Alongside the page are a change summary, affected files, visual differences, and automated test results. When an engineer opens the pull request, they can review the code and its scope directly; if they find a problem, they annotate the preview and the agent continues revising the same branch. The initial scope is React projects with component mappings already connected, prioritizing visual changes such as copy, color, spacing, and visibility. It never changes production directly or merges code for the team. The first goal is to compress “see the problem, describe the change, deliver a reviewable patch” into one continuous action.

## Why now (backed by facts)

On September 9, an interactive page built around the request “just change the Add to Cart button to blue” reached the top of Hacker News; as recorded on September 10, it had 982 points, 390 comments, and rank 1. The discussion directly exposed how agents can over-expand a simple UI change, making teams more attentive to precisely identifying the element, constraining the change scope, and retaining human review.

## Direction (model inference, not independently verified)

Target user: Primary users are product managers, designers, and front-end leads responsible for pre-release acceptance. When they see a specific visual mismatch on a test page, they often do not know the component name or file location. Screenshot tickets can lose page state and fail to show the reuse footprint. Close to release, they need a fast, bounded, reversible patch that an engineer can review.

Minimal entry point: Use a Chrome extension content script in the browser. On selection, capture the CSS selector, DOM fragment, computed styles, page URL, and screenshot. On the server, limit work to React components covered by an integrated mapping table rather than trying to infer source code from arbitrary DOM. Use a GitHub App to read the repository and create temporary branches and pull requests; the GitHub REST API provides the relevant endpoints. Restrict edits to copy, token references, spacing, and visibility. Replay registered routes with Playwright to generate before-and-after screenshots. When multiple token candidates exist, stop before editing code and ask the requester to choose.

The strongest case against: The mapping from an element to source code can easily break. Dynamic class names, conditional rendering, and micro-frontends can send a DOM path to the wrong component. Changing a shared token by mistake could turn a local button request into a site-wide change. Building and screenshotting every route can lengthen waits and consume continuous-integration resources. The extension also needs access to pages and private repositories, so permission reviews may slow adoption. If product managers repeatedly receive wrong candidates or unrelated changes, engineers will have to locate the issue again and trust will disappear quickly. The product should proceed only by achieving high confidence through explicit component mappings, not by trying to support every React project.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Find the first users among front-end agencies and small SaaS teams. They often have product managers accept pre-release pages directly and handle a high volume of small visual tickets. Build a public demo repository that shows element selection, the affected-page list, and the final pull request for each request. Then use the extension on real open-source React projects and submit small UI fixes confirmed by maintainers. Each merged example becomes a credible workflow case study.

## Competitors & gaps (model inference)

- Builder.io: Builder.io already connects to existing repositories and design systems, offering visual editing, AI code changes, pull requests, and live previews. Product, design, and engineering teams can all participate, and its public positioning spans the full workflow from prototype to deployment. That creates substantial overlap in core capabilities. The opening is a narrower pre-release feedback workflow: users do not enter a full canvas; they select a real element and describe the change. The system binds the task to the DOM, route, and screenshot captured at that moment, while surfacing component reuse locations and page-by-page visual diffs. The value proposition is not general-purpose generation, but constraining the agent to the issue that was pointed out.
- Jam: Jam’s browser extension already captures screenshots and recordings, with console logs, network requests, user actions, and device details attached to each report. Results can be shared through workflows including Slack, Jira, and GitHub. It substantially reduces the back-and-forth needed to reproduce an issue and fill in environment details. Its documented workflow ends with describing the problem and submitting the report; the documentation does not say it traces an issue back to React source code, creates isolated branches and code patches, or generates multi-page previews. The opportunity is to carry a high-quality issue record through to a reviewable change, while strictly limiting the scope of edits and preserving Jam-style raw evidence.

## How it makes money (model inference)

Charge per connected code repository. The base plan is a monthly per-repository subscription with a set number of change requests and preview builds; additional requests are billed per task, so product, design, and QA teams are not blocked by per-seat pricing.

## Source context

Theme: Claude, change the Add to Cart button to blue
Trigger Hacker News post (original English): Claude, change the “Add to Cart” button to blue
Heat at capture: ~982 points, 390 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Claude, change the “Add to Cart” button to blue (https://news.ycombinator.com/item?id=49623754)
- Ship Web Apps Faster with Builder.io (https://site.builder.io/web-apps)
- Creating a Jam (https://jam.dev/docs/creating-a-jam)
- REST API endpoints for pull requests (https://docs.github.com/en/rest/pulls/pulls)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
