---
title: "2027 Cryptography Migration Map"
date: "2026-07-22"
canonical: "https://raytally.com/en/ideas/2026-07-22-france-s-anssi-will-block-pqc-free-products-from/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "France's Anssi Will Block PQC-Free Products from Certification Starting 2027"
  observed_at: "2026-07-22T00:33:19.791Z"
sources:
  - url: "https://cyber.gouv.fr/actualites/pour-lanssi-la-cryptographie-post-quantique-post-quantum-cryptography-ou-pqc-repr%C3%A9sente-la-voie-la-plus-prometteuse-pour-se-pr%C3%A9munir-contre-la-menace-quantique-la-transition-post-quantique-repose-notamment-sur-la-mise-%C3%A0-disposition-pour-les-uti/"
    boundary: "Published at 2025-10-16T00:00:00.000Z."
  - url: "https://news.ycombinator.com/item?id=48994116"
    boundary: "Published at 2026-07-21T16:02:04.000Z. Observed at 2026-07-22T00:33:19.791Z."
  - url: "https://www.aqtiveguard.com/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://cyclonedx.org/guides/OWASP_CycloneDX-Authoritative-Guide-to-CBOM-en.pdf"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-07-22-france-s-anssi-will-block-pqc-free-products-from/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

2027 Cryptography Migration Map
As products prepare for French certification, it scans live communications paths and produces a cryptography migration checklist prioritized by deadline and owner.

## Product concept

For engineering and compliance teams preparing to sell connected products in France, the hardest part of meeting the 2027 certification requirements is not knowing they need quantum-resistant cryptography. It is finding the real communications path that has not yet been migrated. Teams import a software bill of materials—the list of components used in the product—then connect domain names, cloud resources, code repositories, and owner information. The product begins by scanning the actual handshake results of live internet-facing interfaces, identifying the certificate and key algorithms used by each service. When it finds an interface still relying on traditional public-key cryptography, it follows deployment data to the gateway, dependent packages, code repository, and responsible owner. Rather than merely flagging a domain, the map shows which feature the connection serves, when certification must be submitted, and which clients may be affected by a replacement. Owners can prioritize migrations by certification date, exposure scope, and implementation difficulty, then generate assignable tickets. Each ticket includes scan evidence, the relevant components, and regression tests to validate. The first version inventories only external communications paths and product dependencies. It does not replace cryptographic review or claim that a product has received French certification.

## Why now (backed by facts)

ANSSI has made clear that, from 2027, at least some cryptographic products must integrate post-quantum cryptography when entering qualification. Related coverage reached Hacker News on July 21 and, as of July 22, had 85 points, 41 comments, and ranked 18th, making it easier for teams nearing submission to begin tracing the live paths that have not yet migrated.

## Direction (model inference, not independently verified)

Target user: The primary user is a product security lead preparing to seek ANSSI qualification. Their project has entered the submission schedule, yet domains, gateways, and dependencies are still tracked in spreadsheets. Any omission can lead to retesting, delays, or cross-team rework. Engineering leaders also need to turn an abstract requirement into assignable work.

Minimal entry point: Start by accepting a domain list and a CycloneDX SBOM. Use established TLS scanners to collect certificates, public-key algorithms, and negotiated handshake results. A CBOM can represent algorithms, certificates, protocols, and component dependencies, making it suitable as the correlation layer. Then use a GitHub App to read repositories, commit history, and CODEOWNERS. Initially, support tags and resource identifiers from one major cloud platform. Explainable rules link domains, gateways, components, and owners. The first version neither changes keys nor automatically determines certification outcomes. Its output should focus on evidence, gaps, owners, and retesting requirements.

The strongest case against: The largest risk is that the applicable market is narrower than the title suggests. ANSSI’s text concerns qualification for certain cryptographic products, not all connected products sold in France. If a customer’s product does not enter that regime, the deadline provides far less purchase motivation. A second risk is asset-correlation quality. Domains, gateways, and repositories often lack shared identifiers, so incorrect attribution could assign tickets to unrelated teams. Scanning can see externally negotiated results, but cannot prove every code path has been covered. Customers may also refuse to upload SBOM and infrastructure information. Self-hosting raises delivery and support costs. If consultants or evaluators cannot reuse the evidence, the product could become just another expensive asset spreadsheet.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Enter through French cybersecurity consultants and certification labs rather than broad paid acquisition. Offer a free self-hosted domain scanner that retains a branded path into the report. Publish French-language templates for cryptographic asset inventory before submission. Then partner with consultants preparing clients for ANSSI qualification and onboard customers project by project.

## Competitors & gaps (model inference)

- AQtive Guard: AQtive Guard already covers code, runtime environments, and networks, inventorying keys, certificates, and algorithms. It also maps owners, dependencies, and impact scope, and supports migration orchestration and compliance reporting. So discovering cryptographic assets is not a unique capability. The opening is a lightweight collaboration layer for French certification projects. The interface should be organized around product models, submission batches, and qualification dates. Each external connection must retain handshake evidence and link to its repository and owner. Ticket templates can align with French submission materials and regression testing. Its public product pages do not clearly present this French qualification workflow. Whether the wedge works depends on deploying faster than general-purpose platforms. It must also let mid-sized manufacturers deliver a reviewable migration list without buying a large cryptographic management platform.

## How it makes money (model inference)

Charge per product line included in the map, with continuous scanning, owner mapping, and evidence exports included. Base plans cap product lines and interfaces; collaboration seats can be purchased monthly during certification sprints.

## Source context

Theme: France’s 2027 post-quantum certification constraint
Trigger Hacker News post (original English): France's Anssi Will Block PQC-Free Products from Certification Starting 2027
Heat at capture: ~85 points, 41 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Premiers visas de sécurité incluant de la cryptographie post-quantique (https://cyber.gouv.fr/actualites/pour-lanssi-la-cryptographie-post-quantique-post-quantum-cryptography-ou-pqc-repr%C3%A9sente-la-voie-la-plus-prometteuse-pour-se-pr%C3%A9munir-contre-la-menace-quantique-la-transition-post-quantique-repose-notamment-sur-la-mise-%C3%A0-disposition-pour-les-uti/)
- France's Anssi Will Block PQC-Free Products from Certification Starting 2027 (https://news.ycombinator.com/item?id=48994116)
- Secure your Cryptographic Assets (https://www.aqtiveguard.com/)
- Authoritative Guide to CBOM (https://cyclonedx.org/guides/OWASP_CycloneDX-Authoritative-Guide-to-CBOM-en.pdf)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
