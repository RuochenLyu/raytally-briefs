---
title: "Hiring Receipt"
date: "2026-08-22"
canonical: "https://raytally.com/en/ideas/2026-08-22-ghost-job-ads-are-getting-so-bad-that-lawmakers-want-to-ban/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "'Ghost Job' Ads Are Getting So Bad That Lawmakers Want to Ban Them"
  observed_at: "2026-08-22T00:33:14.683Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49394373"
    boundary: "Published at 2026-08-21T22:15:46.000Z. Observed at 2026-08-22T00:33:14.683Z."
  - url: "https://developer.greenhouse.io/job-board.html"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://github.com/lever/postings-api"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.linkedin.com/help/linkedin/answer/a1698113"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-22-ghost-job-ads-are-getting-so-bad-that-lawmakers-want-to-ban/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Hiring Receipt
Before completing an application, job seekers can view a system-issued Hiring Receipt; if the hiring owner fails to reconfirm on time, the role automatically stops accepting applications.

## Product concept

When a job seeker opens an application that will take 30 minutes to complete, the first thing they should see is not the company’s marketing copy, but whether the role is genuinely active. At the top of the job page, the hiring site displays a Hiring Receipt issued by the recruiting system: whether the requisition is open, the date the hiring owner last confirmed it, and the deadline they have committed to for the next round of résumé review. Applicants can decide whether the role merits their time instead of guessing from the posting date whether it has long been left open without a real search. A hiring owner confirms the role once in the existing ATS, and the system updates the receipt. If the role is frozen, its budget is withdrawn, or the owner does not respond by the deadline, the page clearly changes to “Status pending confirmation” and stops accepting new applications. People who have already applied can opt into status-change notifications and see whether the role is paused, reopened, or closed instead of hearing nothing. HR teams get an exceptions-only dashboard: roles nearing expiry, owners who have not confirmed, and jobs automatically paused because of headcount changes. Employers can also publish a short explanation—for example, that they are still collecting candidates or have moved into interviews—so applicants know whether it is worth waiting. The first version integrates with systems such as Greenhouse and Lever. It verifies only job status and the review commitment; it does not assess candidates, screen résumés for employers, or present a receipt as an offer probability. It addresses the most basic trust question before someone begins an application: is anyone actually hiring for this job right now?

## Why now (backed by facts)

On August 21, reporting that lawmakers may ban “ghost job” ads reached discussion on Hacker News. In the snapshot recorded on August 22, it ranked 16th, with 51 points and 26 comments.

## Direction (model inference, not independently verified)

Target user: The core users are job seekers about to complete lengthy applications, especially recent graduates, career changers, and unemployed candidates without referral channels. They have found a relevant role but cannot tell whether a live page means the employer is actively hiring. Each application also takes time to tailor a résumé, write responses, and prepare a portfolio. Before investing, they need to see exactly what a responsible owner has recently confirmed and when that confirmation expires.

Minimal entry point: Start with Greenhouse and Lever customers that use custom career pages. Use the Job Board API and Postings API to read public jobs and create receipt records by job ID. Hiring owners use a separate dashboard to confirm headcount status, the confirmation date, and the review deadline. Job changes trigger rechecks through webhooks or scheduled syncs. When a receipt expires, the career-page component disables the application entry point and displays “Status pending confirmation.” The first release does not infer recruiting activity or read candidate scores; it accepts only owner declarations and explicit ATS job statuses.

The strongest case against: Hiring owners may click confirm mechanically even when the budget is still unsettled, creating false reassurance. Truly verifying headcount often requires connections to finance approvals or HR systems, expanding access requirements and integration costs. Automatically stopping applications could also wrongly affect evergreen roles, talent pipelines, and compliance postings. Publishing a review deadline creates an accountable commitment that some employers may refuse to make. The product must also handle exception approvals, ownership handoffs, and a complete audit trail. If only process-mature employers participate, most jobs will still lack receipts, and value will be constrained by coverage.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Find initial customers among small and mid-sized recruiting teams with custom Greenhouse or Lever career pages. Offer an embeddable receipt component and status page that recruiting operations teams can trial-install in a day. Give recruiting-process consultants audit-export templates so they can include receipts in client remediation work. Feedback generated when job seekers encounter expired receipts can also encourage more employers to enable the product.

## Competitors & gaps (model inference)

- LinkedIn hiring transparency signals: LinkedIn already shows signals such as job-poster verification, actively reviewing applications, and typical review times. These can help job seekers tell whether a recruiter has acted recently. Some statuses are based on on-platform activity rather than a hiring manager’s confirmation of headcount for a specific role. When applications are handled through an external ATS, LinkedIn may only say that the process is managed off LinkedIn. It does not require a manager to commit to a next-review deadline or automatically stop accepting applications when that commitment expires. A verified poster does not mean the budget remains available or that the role is still being filled. Hiring Receipt adds role-specific human confirmation, an expiry date, and a record of status changes. The challenge is that it must enter employer workflows, so adoption will be slower than for platform-generated labels.
- Greenhouse and Lever native job pages: Greenhouse and Lever already provide public job data for employer career sites and support custom application flows. Recruiting teams can close roles in the ATS, after which their career sites no longer display them or accept applications. These existing statuses primarily serve internal employer workflows; applicants usually see only whether a job remains accessible. If a page is still live, they cannot distinguish an active requisition from a talent-pipeline role or a job that was never closed. Neither system presents the hiring manager’s latest confirmation or review commitment as public evidence. Hiring Receipt does not replace the ATS; it adds manager attestation and expiry rules on top of job status. The gap is clear, but implementation depends on customers allowing the product to control the application entry point and continuously handle differences in ATS statuses.

## How it makes money (model inference)

Charge employer recruiting teams a subscription priced by active-job tier. Plans include receipt display, expiry reminders, automatic pausing, applicant notifications, and audit records.

## Source context

Theme: Lawmakers seek to ban ghost job ads
Trigger Hacker News post (original English): 'Ghost Job' Ads Are Getting So Bad That Lawmakers Want to Ban Them
Heat at capture: ~51 points, 26 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- 'Ghost Job' Ads Are Getting So Bad That Lawmakers Want to Ban Them (https://news.ycombinator.com/item?id=49394373)
- Job Board API and Recruiting Webhooks (https://developer.greenhouse.io/job-board.html)
- Lever Postings API (https://github.com/lever/postings-api)
- Hirer responsiveness insights FAQ (https://www.linkedin.com/help/linkedin/answer/a1698113)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
