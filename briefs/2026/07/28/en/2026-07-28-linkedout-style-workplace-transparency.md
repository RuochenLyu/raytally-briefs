---
title: "Offer Reality Check"
date: "2026-07-28"
canonical: "https://raytally.com/en/ideas/2026-07-28-linkedout-style-workplace-transparency/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Someone needs to build an app called LinkedOut where employees share what it was really like to work at these companies. Degen CPA (@DrewVento) July 26, 2026"
  observed_at: "2026-07-28T00:34:17.616Z"
sources:
  - url: "https://x.com/DrewVento/status/2081255878527783025"
    boundary: "Published at 2026-07-26T00:00:00.000Z. Observed at 2026-07-28T00:34:17.616Z."
  - url: "https://us.teamblind.com/faq"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.glassdoor.com/about/trust/protecting-user-anonymity/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.linkedin.com/help/linkedin/answer/a1359065"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-07-28-linkedout-style-workplace-transparency/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Offer Reality Check
Before signing an offer, candidates upload it and verify the reality of overtime, bonuses, and promotion with employment-verified workers in comparable roles.

## Product concept

After receiving an offer, candidates upload the job description, compensation package, and interview notes, then flag underspecified promises such as “flexible hours,” “high bonuses,” or “rapid promotion.” The product breaks these claims into answerable factual questions—for example, weekend on-call frequency over the past six months, the basis for calculating bonuses, and promotion timelines for comparable roles. Questions go only to current or former employees whose employment has been verified and whose team and role are sufficiently similar. Respondents remain anonymous and do not need to write lengthy reviews; they select ranges or add a brief note. The page also shows the period, department, and number of people covered by the sample, so a few individual experiences are not presented as the whole company. Before signing, the candidate receives a reality check: what the offer says, how respondents describe it, and where evidence remains insufficient. The first version covers four areas—overtime, bonuses, promotion, and management stability. It does not broker private chats, reveal employee identities, or tell candidates whether they should accept the job.

## Why now (backed by facts)

On July 26, a post calling for a “LinkedOut” brought demand for real workplace experiences into view. When checked on July 28, it had accumulated 57,287 likes, 5,183 reposts, and 1,476,408 views; the discussion also makes candidates more likely to recognize that vague promises in an offer lack verifiable factual answers.

## Direction (model inference, not independently verified)

Target user: The core user has already received an offer and is within the signing window. They broadly like the role but cannot verify the employer’s claims about flexible hours, bonuses, or promotion. Continuing to interview is costly at this point, while learning the truth after joining is too late. It is especially useful for people relocating for a job, lacking internal contacts, or comparing several offers.

Minimal entry point: Start with PDF parsing and OCR to extract the role, compensation, and exact promise language, then have candidates confirm each item to prevent model misreads. The question bank covers only overtime, bonuses, promotion, and management stability, using range-based response options. Current employees are verified with a work-email code; LinkedIn also uses work email and other methods to confirm a person’s company affiliation. Former employees can submit redacted employment materials for manual review. Matching filters by company, team, job family, and employment period. Results below a preset anonymity threshold are not shown, and open private messaging is not allowed.

The strongest case against: Once results are segmented by team and role, companies may be able to identify respondents. The platform must suppress free text, combine sparse samples, and handle deletion requests. A work email proves only that someone currently controls that inbox; former employment requires more costly manual verification. Respondents have little incentive to keep completing closed questionnaires, and candidates may not be willing to wait. A bad match can present another team’s experience as fact about the target role. If comparable samples remain unavailable over time, the verification page will repeatedly show insufficient evidence, and users will be unlikely to pay for it.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Recruit the first candidates through job-search forums, salary-negotiation groups, and layoff-support communities. Turn common promises into searchable verification checklists that attract people close to signing. Career coaches and compensation-negotiation advisers can embed the check in their service workflow. On the respondent side, start with alumni groups from the same company and offer small gift cards to compensate people for completing the questionnaire.

## Competitors & gaps (model inference)

- Glassdoor: Glassdoor already offers anonymous company reviews and lets reviewers hide some job-title or location information. It is useful for forming an initial view of a company’s overall reputation. But candidates still have to search long reviews for their own answers. Reviews are rarely organized around the exact language of a specific offer, and experiences from different teams, roles, and periods at the same company can easily be conflated. Questions such as bonus formulas and on-call frequency are hard to aggregate across reviews. The opening here is to parse the promises first, then send closed-ended questions to comparable employees. Results would also identify the department, period, and sample gaps. That is closer to the signing decision than another review site. However, the more finely the sample is segmented, the slower coverage grows and the harder anonymity becomes.
- Blind: Blind verifies that users are real employees through work email while keeping accounts anonymous, and it also offers company reviews. It has already validated the basic model of an anonymous professional community. Users can talk in public threads and company channels. Its strengths are real-time discussion, peer Q&A, and experience sharing. Candidates, however, still need to post their own questions and judge whether respondents are close to the target team. Open discussion can drift off topic and rarely produces comparable range-based answers. Former employees’ past employment also requires a separate verification process. The opportunity is to tie questions to specific offer promises, then route them by role, team, and employment period. The page would show only aggregated results rather than sending either side into public discussion. The trade-off is substantially narrower coverage than Blind, and early users may wait a long time without receiving answers.

## How it makes money (model inference)

Charge per verification. Submitting materials and viewing the questions are free; candidates pay to unlock the full comparison once enough responses are matched. There is no charge when the sample is insufficient. Do not charge employers initially, to avoid undermining trust in the results.

## Source context

Theme: Anonymous, verifiable workplace transparency
Trigger Web Trend observation: X @DrewVento — Someone needs to build an app called LinkedOut where employees share what it was really like to work at these companies. Degen CPA (@DrewVento) July 26, 2026
Source metric: 点赞 57287 / 转发 5183 / 浏览 1476408 (发布后累计)

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Someone needs to build an app called LinkedOut (https://x.com/DrewVento/status/2081255878527783025)
- Blind FAQ (https://us.teamblind.com/faq)
- Protecting Your Anonymity on Glassdoor (https://www.glassdoor.com/about/trust/protecting-user-anonymity/)
- Verifications on your LinkedIn profile (https://www.linkedin.com/help/linkedin/answer/a1359065)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
