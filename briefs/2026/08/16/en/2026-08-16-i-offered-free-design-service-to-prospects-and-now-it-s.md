---
title: "Upfront Design Fees for Custom Orders"
date: "2026-08-16"
canonical: "https://raytally.com/en/ideas/2026-08-16-i-offered-free-design-service-to-prospects-and-now-it-s/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "I offered free design service to prospects and now it's costing me time. What should I do?"
  observed_at: "2026-08-16T00:36:31.592Z"
sources:
  - url: "https://www.reddit.com/r/EtsySellers/comments/1voyfl6/i_offered_free_design_service_to_prospects_and/"
    boundary: "Published at 2026-08-15T00:00:00.000Z. Observed at 2026-08-16T00:36:31.592Z."
  - url: "https://docs.stripe.com/payments/checkout-sessions"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://help.etsy.com/hc/en-us/articles/115015663107-How-to-Offer-Custom-Items"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://help.filestage.io/en/articles/9112719-how-to-track-the-progress-of-your-projects-and-files"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-16-i-offered-free-design-service-to-prospects-and-now-it-s/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Upfront Design Fees for Custom Orders
A paid design stage for custom-product sellers that caps revision rounds, credits the fee toward the order, and converts an approved proof into a production-ready record.

## Product concept

Small sellers of custom clothing labels, printed goods, or gifts often face the same problem: customers keep sending more images, changing copy, and switching directions in DMs, then neither place an order nor pay for the design time. The seller sends a dedicated link, where the customer first chooses a defined design scope—such as adapting an existing logo, laying out a card, or creating a pattern from scratch—then pays a design fee that can be credited toward the physical product. On the same page, customers upload images and specify dimensions and intended use. The seller’s included revision limit appears beside the proof. Every comment must be pinned to a specific spot. After the seller delivers a new version, the customer can only approve it, submit that round’s changes, or buy additional revisions. No more "just one more small change" scattered across chat history. Once the proof is final, the customer approves the production version directly on the preview. The page then unlocks product specifications, quantity, and the remaining balance. The design fee is automatically applied as a credit, and the seller receives a versioned production file and proof of approval. If the customer wants to restart in a different direction, they enter a new paid design phase rather than quietly expanding the original order. Start with custom sellers whose work is limited to one-sided layouts and image swaps, and get four things right: payment, annotations, versions, and production approval. Complex illustration work, real-time collaborative editing, and print-shop scheduling integrations can come later.

## Why now (backed by facts)

An August 15 r/EtsySellers post complained that designing clothing labels for prospective customers for free was continually consuming time. Commenters recommended charging upfront, crediting the fee toward the purchase, and limiting revisions, but a complete flow through to production approval is still missing.

## Direction (model inference, not independently verified)

Target user: The core users are sellers of custom clothing labels, cards, and small gifts who take orders through Etsy, their own storefronts, or DMs. When customers arrive with an old image, a vague idea, or last-minute copy, sellers are most likely to invest unpaid time in layout work. By the second revision, a change in direction, or the move into production, scope and accountability quickly become unclear. They need to collect a design fee first, then turn the approved proof into the basis for production.

Minimal entry point: The entry point is a dedicated link the seller creates for an individual inquiry, not a general project-management tool. The form first collects the design type, dimensions, intended use, reference images, and editable files, then shows the included revision rounds. Payments use Stripe Checkout Sessions, with an order ID linking the design stage. Proof upload and annotation open only after a webhook receives the completed-payment event. The proof area initially supports PNG, JPEG, and PDF previews, stores comments by coordinates, and freezes prior versions when a new one is uploaded. Final approval creates a record containing the version number, approval time, and file hash. The first release excludes real-time editing and print-shop scheduling integrations.

The strongest case against: If sellers do not clearly define what counts as one revision, the product will simply move the existing dispute onto a page. A customer may see several small edits as one round, while the seller may require an add-on based on the work involved; the payment checkpoint could instead trigger abandonment or refund requests. Crediting a design fee against the physical product also raises questions around cancellations, partial refunds, taxes, and reconciliation with platform orders. If previews contain substituted fonts, bleed issues, or color discrepancies, customer approval cannot ensure that the print file is correct. If sellers treat the approval record as a liability waiver, it will undermine post-sale trust and may intensify disputes. Continue only by limiting the product to low-complexity categories first and turning scope, refunds, and production responsibility into enforceable rules.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Find the first users in r/EtsySellers, custom-printing communities, and seller discussions at local label makers. Focus on their own language about time lost to free proofs and customers who never order. Offer a ready-to-forward fee explanation and approval link so sellers can trial it on current inquiries. Public, anonymized revision timelines and extra-payment milestones will make the value clearer to peers than generic project-management messaging. Etsy DM quick-reply templates can also embed the link in sellers' existing intake habits.

## Competitors & gaps (model inference)

- Etsy Custom Orders and Personalization Fields: Etsy already lets buyers submit custom-order requests, and sellers can create a private custom listing for that buyer from a message thread. Personalization fields can collect text, options, and image files and carry that information into the order. This covers requirements gathering and final payment while fitting sellers' existing sales workflow. What is missing is a separately paid design stage that can be credited toward the product purchase. Etsy also does not show remaining revision rounds alongside each proof or let customers leave feedback anchored to a specific location. Sellers still have to decide what counts as one revision and manually create an extra-charge listing. Final approval is not a separate proof-locking step, so agreement in a message can become disconnected from the production file. The product should treat Etsy as the checkout destination rather than replace its storefront, reviews, or platform payments.
- Filestage: Filestage supports pinned comments on images, PDFs, and other files; version management; and reviewer approval or change requests. It can also compare versions, restrict comments on approved files, and export review reports with timestamps. Its annotation, version-tracking, and approval records are therefore already mature. But its core unit is a file-review project, not a custom-product order for a small seller. Design fees, credits against the product price, purchases of extra revisions, and final payment must still be handled separately in a payment or e-commerce system. Review rounds can be controlled, but they do not automatically reconcile the seller’s included revision allowance. Nor does approval directly unlock product specifications, quantity, and the production file. The opportunity is to embed lighter-weight proofing in the payment flow, so customers manage everything from a single order page.

## How it makes money (model inference)

Charge shops a monthly subscription that includes a set number of active design jobs. Charge per job beyond that allowance, with payment-processing fees billed separately.

## Source context

Theme: Paid custom design, revision limits, and production approval
Trigger Reddit single-post demand observation: r/EtsySellers — I offered free design service to prospects and now it's costing me time. What should I do?

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- I offered free design service to prospects and now it's costing me time. What should I do? (https://www.reddit.com/r/EtsySellers/comments/1voyfl6/i_offered_free_design_service_to_prospects_and/)
- The Checkout Sessions API (https://docs.stripe.com/payments/checkout-sessions)
- How to Offer Custom Items (https://help.etsy.com/hc/en-us/articles/115015663107-How-to-Offer-Custom-Items)
- How to track the progress of your projects and files (https://help.filestage.io/en/articles/9112719-how-to-track-the-progress-of-your-projects-and-files)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
