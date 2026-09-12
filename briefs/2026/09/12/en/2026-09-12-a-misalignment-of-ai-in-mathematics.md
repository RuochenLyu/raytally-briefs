---
title: "Adversarial Proof Review Room"
date: "2026-09-12"
canonical: "https://raytally.com/en/ideas/2026-09-12-a-misalignment-of-ai-in-mathematics/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "A misalignment of AI in mathematics"
  observed_at: "2026-09-12T00:33:09.006Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49662371"
    boundary: "Published at 2026-09-11T17:45:12.000Z. Observed at 2026-09-12T00:33:09.006Z."
  - url: "https://mathandai.org/"
    boundary: "Observed at 2026-09-12T00:33:09.006Z."
  - url: "https://lean-lang.org/doc/reference/latest/ValidatingProofs/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://arxiv.org/abs/2607.09217"
    boundary: "Published at 2026-07-10T00:00:00.000Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-12-a-misalignment-of-ai-in-mathematics/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Adversarial Proof Review Room
When a researcher receives an AI-generated mathematical proof, independent review agents probe its weakest reasoning nodes and attach reproducible counterexamples or failure traces.

## Product concept

A mathematics researcher receives a polished AI-generated proof but suspects that one lemma is being concealed by elegant wording. The user uploads the proof, its definitions and dependencies, and runnable code. The product breaks the argument into a checkable dependency chain, then sends it to multiple isolated review agents. Each agent has a distinct assignment: find counterexamples, inspect implicit assumptions, try to reconstruct a lemma, or validate critical steps through small-scale enumeration. A review agent cannot simply say, “There may be a problem here.” It must identify a specific reasoning node and provide an input that triggers failure, an unmet premise, or a search program that can be rerun. The interface displays disputed points within the proof structure. When a researcher selects a node, they can see which agents independently found the same issue and which only raised an unverified suspicion. When the author revises the proof, the system reruns only the affected branches and preserves the previous round’s conclusions. Passing sections show the verification method and execution range, while uncovered sections are clearly marked with their boundaries. The first version focuses on proofs with a relatively high degree of formalization, where symbolic computation or finite search can check the mathematics. It does not promise to replace peer review, and it does not treat an agent majority as proof of correctness.

## Why now (backed by facts)

On September 11, a Hacker News post about a mathematics-and-AI statement sparked discussion; as of September 12, the post ranked first with 580 points and 640 comments. The statement also notes that some AI mathematics results have been announced hastily, without sufficient writing or methodological refinement, leaving researchers more often with proofs that are difficult to verify quickly.

## Direction (model inference, not independently verified)

Target user: Mathematics researchers reviewing AI-generated proofs. They have usually understood the main idea but are stuck on a lemma that looks suspiciously smooth. Manually checking every dependency is slow, while asking the model to prove itself can repeat the original error. The product fits use in seminars, before submitting a preprint, or before responding to peer-review comments. Users need rerunnable failure evidence, not another overall confidence score.

Minimal entry point: The workflow accepts a numbered proof with attached definitions, cited lemmas, and code. The model first extracts the propositions, premises, and citation relationships; the user then confirms the dependency graph. Nodes that can be formalized are converted into Lean 4 files and checked by the kernel, including with `#print axioms`. The remaining nodes are assigned to isolated agents for counterexample search, premise auditing, and lemma reconstruction. Checks over finite objects run in restricted containers that save the random seed, inputs, and outputs. The first version supports only Lean 4 and executable scripts, not purely diagrammatic proofs. Node contents are cached by hash, and changes trigger reruns according to the dependency graph.

The strongest case against: Turning a natural-language proof into a correct dependency graph can itself introduce misreadings. If the node boundaries are wrong, later agents may precisely inspect the wrong object. Counterexample searches cover only the specified range, and failing to find a counterexample can easily be misread as a pass. Formalization may also change the original proposition into an easier one to prove. Running multiple agents creates significant model and compute costs. Uploading unpublished proofs to the cloud raises confidentiality and priority-publication concerns. The product should proceed only if authors confirm the proposition mapping and the interface strictly separates “checked” from “proved.”

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users are most likely to come from the open-source communities around Lean, Mathlib, and AI mathematics tools. A set of deliberately flawed short proofs could let users rerun the review results directly. Another entry point is the collection of AI-proof review cases publicly shared by mathematicians. Each case should show the earliest failing node rather than promote the number of agents. Open-source Lean adapters and a standard review-report format would help the product enter existing research workflows.

## Competitors & gaps (model inference)

- Lean 4 and Mathlib: Lean can have a small kernel check formal proofs and list the axioms on which they depend. It can identify unfinished proofs, custom axioms, and some paths that do not meet its trust requirements. For conclusions that are already fully formalized, this is more reliable than an agent vote. The gap is that the material researchers receive often combines natural language, code, and partially formalized arguments. Lean does not determine whether a formal statement faithfully captures the original intent, nor does it proactively search for a concrete input that breaks a nonformal lemma. The product should use Lean as the final checker, not reimplement its proof kernel. Its real distinction is placing formal checking, counterexample search, and dispute localization on one dependency graph.,
- OpenProver: OpenProver is an open-source automated theorem-proving system for Lean 4. It uses a Planner, Worker, and Verifier architecture and supports human intervention in proof search. It already provides parallel workers, a result repository, and formal verification. Its primary task is finding proofs, not reviewing externally submitted proofs in mixed formats. Generation-oriented agents can keep advancing around the same proof plan. This product instead requires agents to work in isolation and prioritize attempts to disprove the specified node. The review evidence is also presented differently: failed inputs, missing premises, and rerunnable programs must be attached to the original proof node. After an author makes changes, only affected branches are rerun, which fits everyday review workflows more closely.

## How it makes money (model inference)

Charge per review project, with tiered plans based on compute usage. The basic tier covers dependency mapping and bounded searches; higher tiers add more isolated agents and longer runtimes. Research teams can purchase private deployment or annual seats for confidential, unpublished proofs.

## Source context

Theme: AI misalignment in mathematics
Trigger Hacker News post (original English): A misalignment of AI in mathematics
Heat at capture: ~580 points, 640 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- A misalignment of AI in mathematics (https://news.ycombinator.com/item?id=49662371)
- A Severe Misalignment of AI in Mathematics (https://mathandai.org/)
- Validating a Lean Proof (https://lean-lang.org/doc/reference/latest/ValidatingProofs/)
- OpenProver: Agentic and Interactive Theorem Proving with Lean 4 (https://arxiv.org/abs/2607.09217)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
