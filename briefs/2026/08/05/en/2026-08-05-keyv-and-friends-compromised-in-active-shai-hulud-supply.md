---
title: "Dependency Poisoning Incident Time Machine"
date: "2026-08-05"
canonical: "https://raytally.com/en/ideas/2026-08-05-keyv-and-friends-compromised-in-active-shai-hulud-supply/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Keyv and friends compromised in active Shai-Hulud supply chain attack"
  observed_at: "2026-08-05T00:33:30.316Z"
sources:
  - url: "https://www.aikido.dev/blog/keyv-and-friends-compromised-in-npm-supply-chain-attack"
    boundary: "Published at 2026-08-04T00:00:00.000Z. Observed at 2026-08-05T00:33:30.316Z."
  - url: "https://news.ycombinator.com/item?id=49166874"
    boundary: "Published at 2026-08-04T00:00:00.000Z. Observed at 2026-08-05T00:33:30.316Z."
  - url: "https://github.com/npm/registry/blob/master/docs/responses/package-metadata.md"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://docs.snyk.io/snyk-platform-administration/snyk-projects/view-project-history"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-05-keyv-and-friends-compromised-in-active-shai-hulud-supply/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Dependency Poisoning Incident Time Machine
After a dependency poisoning disclosure, import build evidence to determine which historical artifacts actually installed a malicious version and what needs isolation.

## Product concept

When a dependency poisoning incident is disclosed, a security engineer submits lockfiles, build timestamps, artifact digests, and CI cache records. Rather than substituting today’s dependency tree for the historical environment, the product reconstructs the versions that could have been installed on each build date and checks whether a briefly available malicious package actually entered an artifact. The results page starts with affected images, services, and customer-delivered versions. Each item expands to show the matching build number, dependency path, and evidence gaps. Engineers can mark an artifact as isolated, then generate the smallest required upgrade changes and rebuild steps—avoiding a blind rebuild of the entire release pipeline for a single alert. The initial release covers JavaScript projects with lockfiles and build logs, with a focus on short-lived malicious dependencies that later versions have superseded. It does not treat projects with missing historical evidence as safe, nor does it replace human-led key rotation and incident notification.

## Why now (backed by facts)

On August 4, malicious code capable of stealing credentials and continuing to spread was inserted into Keyv-related packages. As of August 5, the post ranked sixth on Hacker News with 227 points and 120 comments; security teams are urgently checking older artifacts.

## Direction (model inference, not independently verified)

Target user: The primary user is a security engineer handling supply-chain incident response. When a poisoning disclosure breaks, they must decide whether to take services offline, rotate keys, or notify customers. By then, the current branch has often already been upgraded, and ordinary scanning may miss the old version. Teams with lockfiles, build logs, or image digests are best positioned to reach a defensible conclusion.

Minimal entry point: Import package-lock.json, npm-shrinkwrap.json, and build logs. Treat the lockfile version, resolved field, and integrity field as strong evidence. Without a complete lockfile, read the npm Registry’s versions, time, and dist metadata. Use npm/semver for version-range resolution and pacote to retrieve package metadata. Save results by artifact digest rather than overwriting them based on the repository’s current branch. The first release supports npm and GitHub Actions only. It does not automatically rotate keys or send incident notifications.

The strongest case against: Historical evidence is often incomplete, and build logs may have expired or been deleted. Publication dates and version ranges alone support only a probabilistic assessment. If the product presents an inference as a confirmed hit, teams may take services offline unnecessarily. Missing a real installation, conversely, can delay key rotation. Private packages, multi-stage image builds, and cache reuse add further ambiguity. Mapping artifacts to customer versions also depends on internal release data. The first release must clearly label evidence levels, or its reports will be difficult to use for audits and incident notification.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users are already in technical discussions and remediation tickets for dependency-poisoning incidents. Release an open-source CLI that produces reviewable, per-artifact evidence reports. Maintain a malicious-version list and reproduction examples for each incident. Security consultants can use it for initial triage, while platform teams may upgrade to a hosted version for tracking artifacts at scale.

## Competitors & gaps (model inference)

- Snyk Open Source / Snyk Container: Snyk can read JavaScript lockfiles, build dependency trees, and continuously monitor them. Its CLI can also save project dependency snapshots and later match newly disclosed issues. That works for repositories already enrolled in monitoring and for checking images that remain accessible. Its public documentation emphasizes project scan results and a small number of historical snapshots. It does not describe reconstructing a past installation from build dates, cache records, and artifact digests. When a malicious version is quickly superseded, neither the current branch nor the latest image may still match. The opening is to make the artifact—not the project—the unit of incident investigation. The system must distinguish direct evidence, date-based inference, and missing evidence. It must also map affected artifacts to services and customer versions rather than merely listing project vulnerabilities.

## How it makes money (model inference)

Charge a monthly fee per connected repository, including a fixed number of historical artifact checks. Offer one-time emergency packages for major supply-chain incidents, priced by the number of imported artifacts.

## Source context

Theme: Shai-Hulud software supply-chain attack
Trigger Hacker News post (original English): Keyv and friends compromised in active Shai-Hulud supply chain attack
Heat at capture: ~227 points, 120 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Keyv and friends compromised in active Shai-Hulud supply chain attack (https://www.aikido.dev/blog/keyv-and-friends-compromised-in-npm-supply-chain-attack)
- Keyv and friends compromised in active Shai-Hulud supply chain attack (https://news.ycombinator.com/item?id=49166874)
- Package Metadata (https://github.com/npm/registry/blob/master/docs/responses/package-metadata.md)
- View Project history (https://docs.snyk.io/snyk-platform-administration/snyk-projects/view-project-history)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
