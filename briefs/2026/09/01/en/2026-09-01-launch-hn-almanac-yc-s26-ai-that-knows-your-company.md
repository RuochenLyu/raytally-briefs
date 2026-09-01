---
title: "A Company Knowledge Base That Resolves Conflicts"
date: "2026-09-01"
canonical: "https://raytally.com/en/ideas/2026-09-01-launch-hn-almanac-yc-s26-ai-that-knows-your-company/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Launch HN: Almanac (YC S26) – AI that knows your company"
  observed_at: "2026-09-01T00:33:19.377Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49511007"
    boundary: "Published at 2026-08-31T15:34:34.000Z. Observed at 2026-09-01T00:33:19.377Z."
  - url: "https://www.usealmanac.com/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.getguru.com/features/verification"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://docs.glean.com/user-guide/assistant/glean-chat/glean-chat-citations/glean-citations"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-01-launch-hn-almanac-yc-s26-ai-that-knows-your-company/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

A Company Knowledge Base That Resolves Conflicts
When company policies conflict, employees get a cited provisional answer first, while the smallest possible adjudication task goes to the responsible owner.

## Product concept

When an employee asks the company AI, “Can I expense a rideshare on a business trip?” the hardest case is when it retrieves two valid documents with opposite answers. After a team connects policy pages, shared documents, and internal announcements, the product identifies the original sentences behind its answer and checks their effective dates, applicable departments, and owners. Rather than hiding the conflict, the answer page first presents a provisional explanation with citations. If the two provisions genuinely cannot coexist, the system turns the employee’s original question into a single adjudication card and sends it to the owner of that policy. Next to the original sentence, the owner simply chooses which rule to retain, specifies the conditions under which it applies, or enters a new unified policy. The confirmed result is written back to the knowledge base immediately, while the old passage is marked retired or pending revision. The next employee who asks will no longer receive the same contradictory material. Managers can also see which policies repeatedly cause disputes and which owners have been slow to respond. The first version handles conflicts among written policies; it does not interpret the law for a company or let the model decide benefits, compensation, or disciplinary matters. Each real question becomes an opportunity to close a knowledge gap that has gone unmaintained for years.

## Why now (backed by facts)

On August 31, a Launch HN post introduced Almanac’s enterprise knowledge AI; as recorded on September 1, it had 44 points, 41 comments, and ranked 16th. The discussion makes it easier for teams to move beyond “Can we find it?” toward how to answer and correct conflicts across multiple materials.

## Direction (model inference, not independently verified)

Target user: Mid-sized companies that have already connected policy pages, shared drives, and internal announcements to an AI system. Employees need an actionable answer immediately before filing an expense, requesting leave, or ordering equipment; waiting for HR delays the task, while blindly trusting the model can cause harm. Knowledge owners need a way to turn scattered follow-up questions into manageable revision work.

Minimal entry point: Start with travel, expense, and leave policies, which often contain dates and scope conditions. Connect one document source and one question entry point while preserving source permissions and version numbers. During parsing, extract titles, original sentences, publication dates, departments, and owners. Once retrieval returns candidate passages, assess conflicts only among provisions that answer the same question. When a contradiction is detected, withhold a definitive answer and show both citations with a provisional explanation. Adjudication cards should allow only three actions: retain a provision, limit its applicability, or enter a unified policy. Write results first to a separate override layer, then update source documents through controlled tasks.

The strongest case against: Policy documents often lack effective dates, applicable departments, and clear owners, so conflict detection may stall on missing metadata. Semantically similar language does not necessarily mean opposite policies, and false positives could burden owners with invalid adjudications. Permissions and version control in source systems also constrain automated write-backs, while an override layer could become another source of truth. If owners do not act promptly, provisional explanations may persist indefinitely. Incorrect guidance on benefits, compensation, or discipline could also trigger employment disputes. The product needs complete citations, approval records, and a human fallback; otherwise, one wrong adjudication could erode employee trust.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Recruit early users from HR, finance, and IT teams already deploying internal AI search. Offer a free policy-conflict scan that produces a verifiable list from existing documents. Demonstrate how the answer to the same question changes before and after adjudication, rather than emphasizing general chat capabilities. Anonymized collections of common conflict types can sustain acquisition through enterprise knowledge-management and internal-tools communities.

## Competitors & gaps (model inference)

- Guru: Guru already has a mature knowledge-verification system. Each knowledge card can have an assigned verifier, a status, and a review cycle. Unverified content remains searchable but is clearly labeled. Employees can flag problematic text and notify its owner. Its Knowledge Agents also log questions and answers and route questionable content to experts. That already covers content freshness and accountability. Public materials do not clearly show a narrower workflow that automatically places two conflicting policy passages side by side when a real question retrieves both. The system would also need to compare effective dates, departments, and applicability conditions before generating an adjudication card limited to that contradiction. After a decision, it would need to update the status of the original passages, not merely a knowledge card’s status. The opening is therefore not general verification, but conflict resolution triggered by individual questions.
- Glean: Glean can search across enterprise data sources and provide passage-level citations in its answers. Citations inherit permissions from the original system, so users can return to the source file to verify them. Its index also tracks content updates, deletions, and permission changes. This addresses fragmented information, invisible sourcing, and access control. Public materials do not clearly offer a paired adjudication workflow for contradictory clauses. After seeing two sources, an employee may still have to decide which one is in force. Administrators also lack a minimal approval task generated around the actual question. This product could add conflict classification, routing to the policy owner, and confirmation of applicability conditions. The confirmed result should also shape later retrieval and preserve the retirement status of the old clause.

## How it makes money (model inference)

Annual subscription priced per active employee seat. The base plan includes document sync, conflict alerts, and owner adjudication; higher tiers add single sign-on, audit exports, granular permissions, and custom retention policies.

## Source context

Theme: Almanac enterprise knowledge AI
Trigger Hacker News post (original English): Launch HN: Almanac (YC S26) – AI that knows your company
Heat at capture: ~44 points, 41 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Launch HN: Almanac (YC S26) – AI that knows your company (https://news.ycombinator.com/item?id=49511007)
- Almanac — the agent with a company brain (https://www.usealmanac.com/)
- Keep content accurate with Guru’s SME verification workflow (https://www.getguru.com/features/verification)
- Citations - Glean Help Center (https://docs.glean.com/user-guide/assistant/glean-chat/glean-chat-citations/glean-citations)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
