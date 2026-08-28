---
title: "Turn Review Feedback into Repository Rules"
date: "2026-08-28"
canonical: "https://raytally.com/en/ideas/2026-08-28-gitnexus-akon-labs/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "GitNexus (Akon Labs)"
  observed_at: "2026-08-28T00:33:12.774Z"
sources:
  - url: "https://www.producthunt.com/products/gitnexus-akon-labs"
    boundary: "Observed at 2026-08-28T00:33:12.774Z."
  - url: "https://docs.github.com/en/rest/pulls/reviews"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/add-custom-instructions/add-repository-instructions"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.greptile.com/docs/code-review-bot/custom-context"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-28-gitnexus-akon-labs/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Turn Review Feedback into Repository Rules
When teams repeatedly correct coding agents, this tool turns review and rollback history into testable repository rules that prevent the same mistakes from being generated again.

## Product concept

Once teams begin having coding agents write patches, reviewers often repeat the same feedback: use the internal wrapper, do not modify a particular directory, or add a specific test for every new interface. The product sits between code review and agent tasks, reading accepted, revised, and reverted machine-generated patches alongside their review comments. It grounds feedback in specific files, calling patterns, and test requirements instead of pasting entire comments back into a prompt. The system first proposes candidate rules, such as “payment modules must not access the database directly” or “new HTTP routes must include authorization tests.” Each rule is replayed against historical patches, showing which mistakes it would have caught and which legitimate changes it might have blocked. Maintainers can revise the applicable directories, add exceptions, or decline to promote a comment into a repository constraint. Rules that pass replay are compiled into the next agent task. If a patch in progress violates a constraint, the product identifies the team precedent it broke and provides an approved wrapper or test example. The review page also shows how much rework a rule has actually reduced, helping teams retire stale constraints. An early version would support GitHub pull requests and a single repository, focusing on rules that can be consistently inferred from revisions and reverts.

## Why now (backed by facts)

As observed on August 28, GitNexus (Akon Labs) ranked No. 11 in Product Hunt’s new-product feed and positions itself around an open-source coding-agent kernel. As teams bring this kind of infrastructure into everyday development, repeated reviews and reverts become a more immediate workflow burden.

## Direction (model inference, not independently verified)

Target user: Small platform and infrastructure teams, along with codebase maintainers, that already have coding agents continuously submitting PRs. The trigger is when the same review feedback keeps appearing in machine-generated patches, or a rollback exposes an architectural constraint that was never documented. At that point, maintainers remember the concrete cost and can judge whether a candidate rule reflects team precedent, making them more willing to define exceptions and accept the configuration work.

Minimal entry point: Connect a single repository through a GitHub App and subscribe to pull request, review, and comment events. GitHub’s API can provide review status, body text, commit versions, and line-level comments. The service stores each patch iteration and links it to subsequent changes to the relevant code. It first generates candidate rules from paths, call relationships, and test-file changes, then uses Tree-sitter for structural matching in a limited set of languages. Replay initially covers only high-confidence rules, such as bans on direct dependencies or required companion tests. Once approved, rules are exported as AGENTS.md or path-specific instruction files. The first version does not promise to understand every natural-language comment or automatically merge rules without maintainer confirmation.

The strongest case against: Incorrect attribution can promote a one-off review preference into a lasting constraint that repeatedly blocks valid changes. Reducing those false positives requires an evidence chain connecting comments, original patches, revised patches, and reverts. Tracking code moves and rewrites across commits adds indexing and semantic-matching costs. Private code, review text, and agent records also require strict permission isolation. Rules that are too broad create noise, while rules that are too narrow are hard to reuse. If maintainers still need to rewrite and debug every rule, the rework saved may not justify the maintenance burden.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Start with small engineering teams that publicly use coding agents and have visible PR rework. Open-source a read-only repository scanner that produces a recurring-review-feedback report with reproducible evidence from historical patches. Then route trials through the GitHub App installation page, where maintainers can select a candidate rule and replay it directly. Publicly showing how false positives are corrected will earn more technical trust than generic claims about reducing rework.

## Competitors & gaps (model inference)

- Greptile: Greptile already supports custom rules, style guides, and repository context, with rules scoped by repository and file path. It also learns from developers’ PR comments, replies, and reactions. When a rule fires, it can comment in a review, and its MCP can return related comments. That makes “learning rules from reviews” alone a weak differentiator. The opening here should narrow to three things: treat revised or reverted machine-generated patches as the primary evidence; replay candidate rules against historical patches to show both catches and false positives; then compile approved rules into the next generation task rather than merely flagging them after a PR is complete. Teams need to trace each rule back to its source changes and validate exceptions. If replay results are not more controllable than existing learning features, users have little reason to switch.
- GitHub Copilot Custom Instructions: GitHub Copilot code review already supports repository-level instructions, path-specific instruction files, and AGENTS.md for additional repository context. Teams can directly document architectural constraints, testing requirements, and review standards, then give generation and review the same context. Its advantage is that no separate control plane is needed, and rules can live with the code version. The adjacent opening is in how rules are created and validated: maintainers still have to spot recurring feedback and manually turn it into precise instructions. This product could automatically connect comments to later revisions and reverts, then propose evidence-backed candidate rules. Before an instruction file is committed, it should also replay the rule against historical patches and list false-positive cases. If it ultimately only drafts an instruction file, Copilot’s built-in capabilities will quickly absorb its value.

## How it makes money (model inference)

Charge a monthly fee per active repository, including rule extraction, historical replay, and pre-generation checks. Start with fixed usage caps so early pricing does not depend on hard-to-explain model-call counts.

## Source context

Theme: GitNexus’s open-source coding-agent kernel
Trigger Product Hunt launch: GitNexus (Akon Labs) — The open-source kernel for coding agents

This records only that the launch appeared in Product Hunt's public feed and when it was observed. The feed provides no vote count; do not describe feed order as popularity or market demand.

## Sources

- GitNexus (Akon Labs) (https://www.producthunt.com/products/gitnexus-akon-labs)
- REST API endpoints for pull request reviews (https://docs.github.com/en/rest/pulls/reviews)
- Adding repository custom instructions for GitHub Copilot (https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/add-custom-instructions/add-repository-instructions)
- Custom Context & Learning (https://www.greptile.com/docs/code-review-bot/custom-context)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
