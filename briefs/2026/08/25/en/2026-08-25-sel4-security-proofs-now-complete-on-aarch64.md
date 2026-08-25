---
title: "seL4 Proof-Boundary CI"
date: "2026-08-25"
canonical: "https://raytally.com/en/ideas/2026-08-25-sel4-security-proofs-now-complete-on-aarch64/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "SeL4 security proofs now complete on AArch64"
  observed_at: "2026-08-25T00:33:22.985Z"
sources:
  - url: "https://proofcraft.systems/news-2026/#2026-08-21"
    boundary: "Published at 2026-08-21T00:00:00.000Z. Observed at 2026-08-25T00:33:22.985Z."
  - url: "https://sel4.systems/news/2026.html"
    boundary: "Published at 2026-08-24T00:00:00.000Z."
  - url: "https://news.ycombinator.com/item?id=49418255"
    boundary: "Published at 2026-08-24T11:32:51.000Z. Observed at 2026-08-25T00:33:22.985Z."
  - url: "https://docs.sel4.systems/projects/microkit/manual/latest/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-25-sel4-security-proofs-now-complete-on-aarch64/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

seL4 Proof-Boundary CI
For ARM firmware teams integrating seL4, CI verifies that each real build remains within the assumptions covered by the security proof.

## Product concept

seL4 is a formally verified operating-system kernel. With its AArch64 proof now complete, embedded teams can finally bring that assurance to ARM devices. The challenge then shifts to real-world engineering: a new driver, board configuration, or build parameter may place a system outside the scope covered by the proof. Developers connect their firmware build to the service and submit the kernel version, driver inventory, device tree, and compiler options. After each build, the product compares the actual artifacts against the proof’s required assumptions, mapping the boundary between the verified kernel, external trusted components, and unverified code. Reviewers can see directly why a serial driver or memory mapping falls outside that boundary. If a commit disables an isolation setting or gives an unverified component privileges it should not have, the release pipeline stops at the relevant change. Developers receive specific configuration differences and remediation guidance rather than a generic security alert. Artifacts that pass include a version, configuration hash, and dependency relationships, allowing auditors to trace them back to the firmware actually flashed to the device. The first release supports AArch64 firmware projects using seL4, producing evidence packages around build-time configuration and component boundaries. It does not claim to formally verify drivers automatically; its purpose is to keep teams from quietly losing assurance they have already earned during integration.

## Why now (backed by facts)

From August 21 to 24, Proofcraft and the seL4 Foundation announced completion of the AArch64 confidentiality proof, filling the gap in the architecture’s security-isolation proof. As of August 25, the news ranked 11th on Hacker News, with 169 points and 37 comments; ARM teams may now be more likely to recheck whether their actual firmware still meets the proof’s assumptions.

## Direction (model inference, not independently verified)

Target user: Safety- and security-critical embedded teams already using seL4, especially systems engineers bringing up AArch64 boards. The need is greatest when changing boards, upgrading the kernel, adding drivers, or preparing a release review. At those moments, the proof must apply to an actual firmware image, while configuration differences are often scattered across build files, device trees, and component descriptions. Reviewers and developers need a shared view of which isolation properties still hold and which code has entered the trusted boundary.

Minimal entry point: Run after build artifacts are written. Collect the kernel commit, CMakeCache, and `_verified.cmake`, along with the system description, DTB, and component ELFs. First map the officially verified combinations, then use pyelftools and libfdt to extract artifact facts. Treat Microkit’s `report.txt` as an appendix only, since its format is not stable. Rules assess versions, configurations, permissions, and hardware assumptions; they do not attempt to prove drivers. On success, emit a JSON evidence package with the firmware hash; on an out-of-coverage build, return a CI failure code.

The strongest case against: If boundary rules are wrong, CI could label an uncovered build as safe—a more serious outcome than an ordinary false positive. If rules are too strict, they will repeatedly block releases and teams will soon bypass the checks. Device trees and build parameters describe only some hardware assumptions; they cannot prove actual peripheral behavior. For projects based on Microkit, the current MCS configuration remains under verification, so the newly completed result cannot be applied to it. Mappings across versions, boards, and configurations also require ongoing maintenance. If builds are not reproducible, an evidence package can establish only metadata consistency, not that the device is running that artifact.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Find initial users through engineering collaboration channels in the seL4 ecosystem. Release an open-source CLI and reproducible AArch64 example, with compliance and out-of-coverage results shown directly in pull requests. Then publish compatibility notes in the seL4 forum, developer chats, and relevant GitHub repositories. Integrators delivering certified systems can use the free scan to obtain an evidence package for review meetings.

## Competitors & gaps (model inference)

- seL4 Microkit and the capDL toolchain: Microkit accepts system descriptions, board configurations, and program images to generate loadable seL4 system images. It reports key system information and can produce capability-table descriptions for each protection domain. The official documentation explicitly warns that a release build does not mean a verified kernel is in use. These capabilities address static-system construction and permission expression. Public tools remain focused on generating systems and supporting verification. Teams must still check kernel versions, build configurations, and proof prerequisites themselves. There is also no unified traceability across driver inventories, device trees, and final firmware. The opportunity is not to rebuild Microkit, but to add artifact-level checks around it and bind out-of-coverage differences to a firmware hash.

## How it makes money (model inference)

Charge an annual fee per private firmware project, including CI checks, evidence-package retention, and verified-baseline updates. Offer self-hosted deployment as a higher-priced tier of the same product.

## Source context

Theme: seL4 completes its AArch64 security proof
Trigger Hacker News post (original English): SeL4 security proofs now complete on AArch64
Heat at capture: ~169 points, 37 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- seL4 security proofs now complete on AArch64 (https://proofcraft.systems/news-2026/#2026-08-21)
- seL4 security proofs now complete on AArch64 (https://sel4.systems/news/2026.html)
- SeL4 security proofs now complete on AArch64 (https://news.ycombinator.com/item?id=49418255)
- Microkit User Manual (v2.3.0) (https://docs.sel4.systems/projects/microkit/manual/latest/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
