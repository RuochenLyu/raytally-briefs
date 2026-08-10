---
title: "Try Competitors Before You Build"
date: "2026-08-10"
canonical: "https://raytally.com/en/ideas/2026-08-10-startup-idea-existence-check/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "we need an app that tells you your startup already exists before you spend 6 months building it Priyanka Lakhara (@codewithpri) August 8, 2026"
  observed_at: "2026-08-10T00:34:05.730Z"
sources:
  - url: "https://x.com/codewithpri/status/2086026260296401149"
    boundary: "Published at 2026-08-08T09:46:31.000Z. Observed at 2026-08-10T00:34:05.730Z."
  - url: "https://docs.browserbase.com/use-cases/agents"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://preuve.ai/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://participant-support.usertesting.com/hc/en-us/articles/45198416028179-FAQ-Task-based-tests"
    boundary: "Published at 2026-06-18T00:00:00.000Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-10-startup-idea-existence-check/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Try Competitors Before You Build
Before development begins, founders define a target user and key task, then an agent trials existing products and returns replayable evidence of overlap and gaps.

## Product concept

Before asking a coding agent to build a first version, a founder writes down the target user, the specific problem they face, and the action they should be able to complete in a few minutes. For example: “After receiving client comments, an independent designer changes the color of a specified object while preserving the rest of the image,” rather than simply entering “AI design tool.” They can also attach sketches, competitor links, or screenshots of the intended result to ground the research in a real workflow. A research agent looks for candidates through product websites, app stores, help documentation, and public demos. It enters environments that permit trials and performs the task itself: creating an account, importing materials, taking the core action, and saving screenshots, recordings, and results from every key step. When it encounters a paywall, a requirement to speak with sales, or insufficient permissions, it stops there and marks the unverified portion rather than treating marketing copy as feature evidence. The results page separates products into “fully completed,” “partially completed,” “discontinued,” and “serves a similar audience through a different workflow.” Opening any product lets the founder replay what the agent clicked and entered, where it got stuck, and whether the output could actually be delivered to the user. The page also groups steps that several products miss into hypotheses to validate, then turns them directly into a first-version task list. The initial release covers only publicly accessible web products and trial software; it does not replace legal, market, or fundraising due diligence. Its deliverable is a team-reviewable hands-on test of competitor tasks, not a list generated from keyword similarity.

## Why now (backed by facts)

On August 8, an X post asked to know whether a startup idea already exists before spending months building it; by August 10, it had accumulated 245 likes, 10 reposts, and 22,065 views. That makes founders preparing to put coding agents to work more likely to ask for replayable evidence of competitor tasks before they write code.

## Direction (model inference, not independently verified)

Target user: Independent founders and teams of two or three preparing to have a coding agent build their first version. They already have a specific user and workflow in mind but have not yet written stable requirements. The critical moment is before they submit the first round of development instructions, when revising the task or reviewing hands-on competitor tests is inexpensive and can most readily lead to cutting features or changing the entry point.

Minimal entry point: First, parse the user description into a role, input materials, core action, and verifiable outcome, then generate a short task script. Candidate discovery initially searches only official websites, help documentation, app stores, and public demos, avoiding costly databases. The execution layer can use Browserbase and Stagehand, which support persistent browser sessions, live viewing, and session recordings. Save the URL, action, screenshot, and output at every step, and label whether login, payment, or human approval is required. The first version tests web products only, excluding desktop software and high-risk transactions. Results use explicit checks so founders can replay and manually revise a judgment.

The strongest case against: Automated trials will often encounter CAPTCHAs, regional restrictions, invite-only access, and paywalls, leaving many critical flows impossible to verify end to end. Registering multiple accounts also creates email, credential, and subscription-management overhead. If an agent accidentally clicks purchase, publish, or delete, it could cause real loss, so execution permissions must be tightly constrained. Output quality also varies across products and is difficult to judge with universal rules; users still need to confirm the acceptance criteria. Recordings may contain personal information or third-party content, so storage and sharing require redaction and access controls. If reports mistake an agent failure for a missing product capability, a few wrong conclusions could undermine founders’ trust in the entire evidence base.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Acquire the first users through indie developer, coding-agent, and startup-validation communities. Select publicly discussed startup ideas and create a small number of free examples that run the same task across multiple products. Publish short replays, sticking points, and missed steps rather than just competitor lists. Then reply with these examples to posts asking whether an idea already exists, inviting the authors to submit their own task descriptions.

## Competitors & gaps (model inference)

- Preuve AI: Preuve AI already compiles market, demand, and competitor information from public sources and produces cited validation reports. It is suited to research questions such as which competitors exist, what market signals indicate, and how companies are priced or funded. Its closest overlap with this concept is helping founders spot blind spots before they build. The gap is that its evidence primarily comes from websites and databases, rather than a full hands-on run of the target task. Founders still cannot easily tell whether a feature is merely described on a website or can actually deliver a usable result. It also does not turn steps such as signing in, importing, editing, and exporting into a replayable trail. This product can avoid generic market scoring and focus on validating a real workflow. Report conclusions should be tied to action logs and clearly identify paywalls, permissions, and failure points.
- UserTesting: UserTesting lets participants complete directed tasks on websites while recording their screens, voices, and interactions. Tasks can begin from a specified URL and can include a success URL to determine whether the flow was completed. This approach provides more credible behavioral evidence than a feature list and can explain why users get stuck. It primarily serves research on a company’s own product, prototype, or user experience, and requires test design and participant recruitment. For founders who have not started building, finding competitors one by one, registering accounts, and applying a consistent task definition still requires manual work. Differences in how participants operate also make side-by-side comparisons more costly. The opening for this product is to have the same agent test multiple public products against the same task script, then display the steps and outcomes side by side. It cannot replace research with real users, but it can complete a low-cost initial screen for functional overlap.
- Manual search, trials, and competitor spreadsheets: The common alternative is for founders to search for competitors themselves and track features, pricing, and positioning in a spreadsheet. Those with the patience may also sign up for trials, take screenshots or recordings, and turn findings into product requirements. This approach stays close to the real task and makes it easy for a team to question the evidence. But testing criteria often change from product to product, while failed steps and input materials are easily omitted. Website claims, help documentation, and actual usable capabilities can end up in the same column. Once research is interrupted, later team members struggle to reproduce the original judgment. This product can retain the explainability of manual research while standardizing tasks, inputs, and completion criteria. The point of surpassing a spreadsheet is not to generate more competitor names, but to automatically preserve every action and distinguish success, partial success, restrictions, and discontinued products.

## How it makes money (model inference)

Charge per completed hands-on competitor task test. Each report includes candidate screening, action replays, key screenshots, failure points, and recommendations for the first-version task list; teams that need ongoing monitoring can buy recurring retest credits.

## Source context

Theme: Early duplicate-checking for startup ideas and existing products
Trigger Web Trend observation: X @codewithpri — we need an app that tells you your startup already exists before you spend 6 months building it Priyanka Lakhara (@codewithpri) August 8, 2026
Source metric: 点赞 245 / 转发 10 / 浏览 22065 (发布后累计)

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- we need an app that tells you your startup already exists before you spend 6 months building it (https://x.com/codewithpri/status/2086026260296401149)
- Browser agents - Browserbase Documentation (https://docs.browserbase.com/use-cases/agents)
- AI Startup Idea Validator in 60s - Real Data, Not Opinions (https://preuve.ai/)
- FAQ: Task based tests (https://participant-support.usertesting.com/hc/en-us/articles/45198416028179-FAQ-Task-based-tests)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
