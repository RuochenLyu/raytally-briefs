---
title: "Go Collection Proposal Sandbox"
date: "2026-08-01"
canonical: "https://raytally.com/en/ideas/2026-08-01-golang-proposal-container-generic-collection-types/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Golang proposal: container/: generic collection types"
  observed_at: "2026-08-01T00:33:26.395Z"
sources:
  - url: "https://github.com/golang/go/issues/80590"
    boundary: "Published at 2026-07-28T00:00:00.000Z. Observed at 2026-08-01T00:33:26.395Z."
  - url: "https://news.ycombinator.com/item?id=49127031"
    boundary: "Published at 2026-07-31T00:00:00.000Z. Observed at 2026-08-01T00:33:26.395Z."
  - url: "https://pkg.go.dev/golang.org/x/tools/go/packages"
    boundary: "Published at 2026-07-09T00:00:00.000Z."
  - url: "https://go.dev/gopls/analyzers"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-01-golang-proposal-container-generic-collection-types/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Go Collection Proposal Sandbox
Import a Go repository, trial-migrate it to candidate generic collection interfaces, and immediately compare compatibility, performance, and removable code.

## Product concept

When Go teams encounter a generics collection proposal, the hardest question is not whether the syntax looks good, but what migration would do to their own repository. Developers connect a code repository and select a proposal version. The product first scans in-house Sets, queues, tree structures, and duplicate helper functions. It groups results into changes that can be rewritten automatically, those requiring human judgment, and those not yet supported, so experimental interfaces never go straight into the main branch. After users select a set of candidates, the system creates a temporary migration branch. It replaces existing implementations with the proposal’s collection interfaces while preserving a before-and-after view of every change. It then runs compilation, tests, and benchmarks, comparing binary size, memory allocations, execution time, and the amount of maintenance code that can be removed. If a collection slows down or breaks an interface in a real project, the report points to the specific package and call site. Teams can switch between drafts to see how the same repository differs under alternative naming, iterator designs, or error-handling approaches. The discussion page shows more than abstract APIs: it can include functions simplified in real projects, adapter layers that must be added, and failed tests. Every finding can be exported as a link for maintainers to cite in proposal discussions. The initial release focuses on common collection wrappers and repositories with runnable public tests. Generated branches are read-only by default and never open pull requests. Rather than asking teams to bet on the language’s future, it lets an unadopted standard-library design compile, test, and undergo performance checks in their own code first.

## Why now (backed by facts)

On July 28, the Go Collections Working Group published multiple generic collection proposals for Go 1.28, and teams now need to assess migration compatibility and performance for their existing wrappers. At the time of collection on August 1, the link ranked 10th in Hacker News’s new submissions feed, with a snapshot of 115 points and 70 comments; the design trade-offs are drawing intense discussion.

## Direction (model inference, not independently verified)

Target user: Platform teams, foundational-library authors, and technical leads maintaining mid-sized to large Go repositories. Once a proposal enters public discussion, they need to decide whether to support it and estimate the eventual migration cost. Abstract API review is not enough; compilation results, test failures, and performance changes in real repositories make a stronger case. Open-source maintainers can also use reports to submit reproducible cases to proposal authors.

Minimal entry point: The first release supports public Go repositories and initially covers `map[T]struct{}`, `map[T]bool`, and common Set wrapper types. It uses `go/packages` to load source code, syntax trees, and type information rather than relying on text matching alone. The rewrite layer is based on ASTs and type-checking results, starting with `container/set` and `container/mapset`. Each draft is pinned to its corresponding implementation version, and a local temporary branch is created in an isolated workspace. The system then runs the repository’s existing build, test, and benchmark commands. Reports show patches, failed call sites, removable code, and before-and-after metrics. Queues, tree structures, and custom hash implementations whose semantics cannot be confirmed are flagged but not modified automatically.

The strongest case against: Drafts may be renamed, lose methods, or change semantics, requiring adapters to be repeatedly rewritten. Collection wrappers may look simple while actually carrying concurrency protection, ordering guarantees, or zero-value conventions. An incorrect automated replacement can produce a patch that compiles but changes behavior. Benchmarks are also vulnerable to machine load, caching, and insufficient samples, so a single result may mislead reviewers. The proposals themselves state that initial implementations do not yet aim for constant-factor optimization. Running against private repositories also creates isolation costs around source access, dependency credentials, and untrusted tests. If a team will not provide a runnable environment, the product can offer only a shallow scan, substantially weakening its core value.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first cases can come directly from public Go repositories. Select projects with clear in-house Set wrappers and runnable tests, then generate migration reports that can be publicly reviewed. Report links can feed back into the relevant proposal discussions and answer what a given API would mean in real code. Draft-comparison pages could also be cited by Go newsletters, language podcasts, and repository maintainers.

## Competitors & gaps (model inference)

- gopls and modernize: gopls is the official language server maintained by the Go team, with diagnostics, analysis, and refactoring capabilities. Some analyzers offer directly applicable fixes, and modernize targets newer language and standard-library usage. These tools are well suited to continuous code cleanup in the editor: feedback is fast, and developers can stay in their everyday workflow. But they primarily address settled language rules and library APIs, not proposals that are still under consideration. Their fixes generally follow individual diagnostics and do not produce parallel migration results for multiple drafts. Teams must still connect compilation failures, test changes, and benchmark differences themselves. The opportunity is to turn static fixes into a proposal-evaluation workflow. The product needs to retain evidence for every candidate site and clearly identify rewrites that cannot be automated. Its output should support team reviews and proposal discussions, rather than merely provide editor hints.

## How it makes money (model inference)

Charge per repository for a one-time trial migration to a proposal version, including a full test and benchmark report. A monthly team plan adds private repositories, historical comparisons, and shared reports.

## Source context

Theme: Go generic collection proposals
Trigger Hacker News post (original English): Golang proposal: container/: generic collection types
Heat at capture: ~115 points, 70 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- proposal: container/...: generic collection types (https://github.com/golang/go/issues/80590)
- Golang proposal: container/: generic collection types (https://news.ycombinator.com/item?id=49127031)
- packages package - golang.org/x/tools/go/packages (https://pkg.go.dev/golang.org/x/tools/go/packages)
- Gopls: Analyzers (https://go.dev/gopls/analyzers)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
