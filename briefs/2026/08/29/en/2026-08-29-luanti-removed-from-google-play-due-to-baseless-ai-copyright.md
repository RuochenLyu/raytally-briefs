---
title: "Takedown Appeal Evidence Chain"
date: "2026-08-29"
canonical: "https://raytally.com/en/ideas/2026-08-29-luanti-removed-from-google-play-due-to-baseless-ai-copyright/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Luanti removed from Google Play due to baseless AI copyright notice"
  observed_at: "2026-08-29T00:33:06.143Z"
sources:
  - url: "https://blog.luanti.org/2026/08/27/luanti-dmca-tracer-ai/"
    boundary: "Published at 2026-08-27T00:00:00.000Z. Observed at 2026-08-29T00:33:06.143Z."
  - url: "https://news.ycombinator.com/item?id=49475079"
    boundary: "Published at 2026-08-28T06:33:57.000Z. Observed at 2026-08-29T00:33:06.143Z."
  - url: "https://docs.github.com/en/rest/actions/artifacts?apiVersion=2026-03-10"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://aboutcode.org/docs/getting_started/license-compliance/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-29-luanti-removed-from-google-play-due-to-baseless-ai-copyright/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Takedown Appeal Evidence Chain
After a copyright takedown notice, developers can reconstruct the removed app version and assemble verifiable source evidence for each disputed item into a ready-to-file appeal package.

## Product concept

When an independent app suddenly receives a copyright takedown notice, the appeal window may be only a few days. Before responding, the developer has to reconstruct which submission built the store package, where a particular asset came from, and whether a dependency’s license covered that version. Takedown Appeal Evidence Chain connects code repositories, build pipelines, asset directories, and license files, breaking the work, package name, or screenshots named in a notice into specific disputed items. After the developer selects the removed store version, the product reruns the matching commit’s build in an isolated environment. It extracts file hashes from the installation package, then traces them back to commit history, authors, first-introduced dates, asset licenses, and third-party dependency versions. Files without original supporting records are flagged separately rather than hidden in a generic appeal letter. Once the review is complete, the developer receives an appeal package organized by disputed item. Each item includes its package path, file hash, code history, license text, and instructions for reproducing the build. Reviewers can verify the material through a read-only link without access to the full private repository. If the developer fixes an asset that genuinely had a problem, the product clearly distinguishes the corrected version from the original. The first release supports Git repositories, common continuous-integration records, and Android application packages, exporting evidence as store-appeal attachments. It does not determine infringement liability or replace a lawyer’s legal opinion.

## Why now (backed by facts)

On August 27, Luanti said its Android app was removed from Google Play after a DMCA notice that did not identify any specific material, and that it had filed a counter-notification. As of August 29, the incident ranked sixth on Hacker News with 430 points and 135 comments, making it easier for independent developers to recognize the difficulty of tracing the provenance of an old package under time pressure.

## Direction (model inference, not independently verified)

Target user: Independent Android developers, small studios, and open-source maintainers. The critical moment is immediately after a store version is removed and the notice gives only a vague work title or screenshot. Revenue, updates, and user acquisition may be affected at once, while the team has no dedicated legal or compliance engineer. The owner first needs to determine what is actually in the complained-of package before choosing whether to file a counter-notification, replace an asset, or submit a fixed release.

Minimal entry point: Start with a GitHub App that requests read-only access to repository contents and Actions. Use the Actions artifact API to retrieve build packages, commit digests, and workflow details, and verify existing build attestations when available. Unpack APKs in isolated containers, calculate SHA-256 hashes for every file, and create an inventory by asset path. On the source side, use Git history to locate the first introducing commit, author record, and later changes. License detection can call ScanCode Toolkit, while manually uploaded authorization files are preserved unchanged. The initial release supports only Android projects whose commits and build scripts can be recovered; it does not promise that every old version can be reproduced.

The strongest case against: The first hard failure is that an old version may not be reproducible. If a build image, dependency repository, signing configuration, or Actions artifact has expired, a rerun cannot prove it matches the store package. A file hash can prove identical content, but not automatically establish a valid license or resolve fair use or copyright ownership. A Git author record may identify only the committer, not the asset’s creator. Bringing private source code and licensing contracts into the system also creates costly requirements for isolating, encrypting, and deleting highly sensitive data. If the output implies an incorrect legal conclusion, developers may stake a limited appeal opportunity on incomplete evidence.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Reach the first users through open-source Android projects facing Play Store removals, DMCA notices, or asset disputes. Publish anonymized examples of evidence packages from real takedown cases so developers can see the output format rather than hear generic compliance messaging. Offer a free APK inventory and license-gap check embedded directly in GitHub Actions. Users accumulate evidence routinely, then upgrade to full reconstruction and appeal export when an incident occurs.

## Competitors & gaps (model inference)

- ScanCode Toolkit / ScanCode.io: ScanCode Toolkit identifies license, copyright, author, and provenance clues in files. ScanCode.io can also analyze packages, dependencies, and binaries through pipelines, and match binaries to source code. They suit routine license inventories and can produce SBOMs and attribution materials. The gap is that their workflow remains centered on compliance scanning. After receiving a takedown notice, developers must still identify the complained-of store version, recover its build environment, and align APK files with historical commits. Scan results are not automatically organized around the disputed items in a notice. This product could reuse their findings but deliver a platform-reviewable appeal evidence package instead. What still needs to be filled in is version freezing, build reproduction, missing-evidence flags, separation of pre- and post-fix versions, and minimal disclosure for private repositories.
- GitHub Actions and Artifact Attestations: GitHub Actions already retains workflow-run records and build artifacts. Its artifact API can return the associated commit and digest, while build attestations can link a repository, workflow, and commit. These capabilities are useful for showing which automated process produced a binary. The gap is that the information is scattered across run pages, logs, artifacts, and repository history. Older artifacts may have expired, and asset licenses are often stored outside the repository. GitHub does not interpret the work title, screenshots, or package name in a store notice, nor does it determine which files should be attached. Developers still have to unpack the APK, trace each item’s provenance, and assemble reviewable materials manually. The product’s opening is to connect existing attestations to the appeal context and provide a restricted read-only review link.

## How it makes money (model inference)

Charge a per-app subscription. The base plan retains version evidence and generates appeal packages; a team plan adds private repositories, longer retention, and team review. Set monthly allowances for reconstruction jobs and charge per job beyond the limit to keep isolated-build costs under control.

## Source context

Theme: Luanti removed from Google Play over an AI copyright notice
Trigger Hacker News post (original English): Luanti removed from Google Play due to baseless AI copyright notice
Heat at capture: ~430 points, 135 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Luanti removed from Google Play due to baseless AI copyright notice (https://blog.luanti.org/2026/08/27/luanti-dmca-tracer-ai/)
- Luanti removed from Google Play due to baseless AI copyright notice (https://news.ycombinator.com/item?id=49475079)
- REST API endpoints for GitHub Actions artifacts (https://docs.github.com/en/rest/actions/artifacts?apiVersion=2026-03-10)
- License Compliance (https://aboutcode.org/docs/getting_started/license-compliance/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
