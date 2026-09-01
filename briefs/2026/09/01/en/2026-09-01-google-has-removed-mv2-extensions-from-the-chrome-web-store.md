---
title: "MV2-to-MV3 Side-by-Side Replay"
date: "2026-09-01"
canonical: "https://raytally.com/en/ideas/2026-09-01-google-has-removed-mv2-extensions-from-the-chrome-web-store/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Google Has Removed MV2 Extensions from the Chrome Web Store, Including UBO"
  observed_at: "2026-09-01T00:33:19.377Z"
sources:
  - url: "https://developer.chrome.com/docs/extensions/develop/migrate/mv2-deprecation-timeline"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://playwright.dev/docs/next/chrome-extensions"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.browserstack.com/docs/automate/playwright/chrome-extension-testing"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-01-google-has-removed-mv2-extensions-from-the-chrome-web-store/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

MV2-to-MV3 Side-by-Side Replay
When migrating an extension to MV3, replay real browser flows side by side to pinpoint the exact step where the new version loses behavior the old version had.

## Product concept

After Chrome removed the installation channel for legacy MV2 extensions, maintainers are less worried about whether they can rewrite an API than whether an MV3 release quietly stops blocking a class of requests on a real page. MV2 and MV3 are two generations of Chrome extension rules. Teams upload the old package still in production and the new package awaiting release, then select the pages, login states, and click flows that best represent real user behavior. The product launches two isolated browsers and has the old and new versions shadow-run the same sequence: opening tabs, switching accounts, visiting dynamic pages, triggering network requests, and changing permission states. It aligns page outputs, request logs, storage changes, and console output from both sides. When results diverge, the report stops at the first differing action and includes the trigger conditions, relevant APIs, and a runnable minimal reproduction script. Maintainers can save a flow after a fix as a regression case and rerun it automatically on code submission. The first release focuses on network requests and background tasks common to ad blockers, script managers, and privacy extensions; it does not attempt to design a team’s entire migration plan. Its output is a list of behavioral differences that engineers can immediately reproduce and fix.

## Why now (backed by facts)

On August 31, 2026, the Chrome Web Store removed all remaining MV2 extensions. Installed legacy versions can no longer be updated or reinstalled, making maintainers more urgent to catch silent MV3 behavior regressions before release.

## Direction (model inference, not independently verified)

Target user: Small teams still maintaining ad-blocking, script-management, or privacy extensions. It is most useful just before an MV3 candidate package is submitted to the Chrome Web Store, or immediately after a migration fix is merged. At that point, unit tests usually pass, but teams worry about behavioral drift after login-state changes, on dynamic pages, or during permission changes. The on-call maintainer needs differences they can reproduce directly, not another migration checklist.

Minimal entry point: Use Playwright to control two isolated persistent browser profiles, loading one unpacked package into each. The initial dual-run setup pins both to the same Chrome 138 baseline and enables the official retention policy. Recorded actions cover only navigation, clicks, account switching, and permission changes. A collection layer uses Playwright events and CDP to capture DOM summaries, requests, console output, and storage snapshots. The aligner compares at action boundaries rather than seeking pixel-perfect page matches. Reports lead with the first divergence, then generate a rerunnable Playwright case. Once the versions match, the MV3 package gets a standalone smoke test in current Chromium.

The strongest case against: Dynamic sites can create a high volume of false differences. Ad rotation, A/B tests, timestamps, and API responses may diverge before the extension does. Normalize too aggressively and genuine missed blocking may disappear. Login flows also involve CAPTCHAs, two-factor authentication, and expired sessions, so replay stability directly affects report credibility. The legacy runner must remain pinned to Chrome 138; maintaining an outdated browser and a high-risk sandbox is not easy over time. Extension packages and login states are sensitive as well, so isolation, key destruction, and local deployment raise delivery costs. If the first-divergence report produces frequent false positives, engineers will quickly return to manual retesting.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users are extension repositories on GitHub that still maintain both MV2 and MV3 builds. Package the runner as a reusable GitHub Action that attaches the first behavioral divergence and a reproduction script to migration PRs. Select public ad-blocking or script-management projects and submit verifiable failing cases. Then publish a set of redacted difference reports so maintainers can judge whether it saves more investigation time than their existing E2E tests.

## Competitors & gaps (model inference)

- Custom Playwright extension E2E: Playwright can already load extensions in persistent Chromium contexts and access MV3 service workers. Teams can script logins, clicks, pop-ups, and page assertions, and plug them into existing CI. It suits engineering teams that already know what they need to verify. But test authors must still write expected outcomes and maintain environments for both the old and new packages. It does not automatically align requests, storage changes, and console logs across the two versions by action. When dynamic pages diverge, teams must still determine where the first causal divergence occurred. Scenarios such as service-worker suspension and permission changes also require fixtures tailored to the extension’s architecture. The opportunity is to make dual-version orchestration, noise reduction, and minimal-reproduction generation the default workflow.
- BrowserStack Automate: BrowserStack Automate supports uploading Chrome extension packages and running them in remote Playwright sessions. It can also retain network logs and session results. Its browser infrastructure, platform matrix, and team collaboration are mature. For cross-environment compatibility testing, it is more convenient than operating an in-house browser pool. Its existing workflow still centers on test scripts driving one extension package, with assertions written in the script. Its documentation does not provide synchronized MV2-versus-MV3 replay, state alignment, or first-divergence detection. Teams must still handle matching login states, page data, and noise reduction themselves. This product could serve as a migration-diagnostics layer on top, or use local runners for sensitive extensions and accounts.

## How it makes money (model inference)

Charge per team on a subscription that includes a fixed allowance of parallel replays and CI runs. Bill overages by browser runtime. Offer local deployment and private runners at higher tiers.

## Source context

Theme: Chrome Web Store removes MV2 extensions and uBlock Origin
Trigger Hacker News post (original English): Google Has Removed MV2 Extensions from the Chrome Web Store, Including UBO
Heat at capture: ~408 points, 328 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Manifest V2 support timeline (https://developer.chrome.com/docs/extensions/develop/migrate/mv2-deprecation-timeline)
- Chrome extensions (https://playwright.dev/docs/next/chrome-extensions)
- Test Chrome Extensions on Playwright tests in BrowserStack Automate (https://www.browserstack.com/docs/automate/playwright/chrome-extension-testing)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
