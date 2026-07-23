---
title: "AI Math Reasoning Checker"
date: "2026-07-23"
canonical: "https://raytally.com/en/ideas/2026-07-23-terrence-tao-s-chatgpt-conversation-about-the-jacobian/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Terrence Tao's ChatGPT Conversation about the Jacobian Conjecture Counterexample"
  observed_at: "2026-07-23T00:33:12.762Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49010345"
    boundary: "Published at 2026-07-22T17:30:40.000Z. Observed at 2026-07-23T00:33:12.762Z."
  - url: "https://terrytao.wordpress.com/2026/07/21/a-digestion-of-the-jacobian-conjecture-counterexample/"
    boundary: "Published at 2026-07-21T00:00:00.000Z."
  - url: "https://lean-lang.org/learn/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://arxiv.org/abs/2606.25363"
    boundary: "Published at 2026-06-24T00:00:00.000Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-07-23-terrence-tao-s-chatgpt-conversation-about-the-jacobian/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

AI Math Reasoning Checker
Paste in an AI mathematics conversation to get a claim-dependency graph, runnable checks, and the earliest suspicious reasoning step.

## Product concept

Researchers paste in a full conversation with an AI about a mathematical problem, optionally attaching the theorems and notes they cited. The system separates definitions, assumptions, lemmas, calculations, and conclusions into collapsible claim nodes, then connects them in a reasoning dependency graph. Each node follows a different review path. Derivations that can be tested numerically produce small-scale counterexample searches or computation scripts; claims invoking external theorems require precise citations; and textual leaps are flagged for human review. Opening any conclusion lets users trace it back through the exact lines of the conversation on which it depends. The key output is not a true-or-false score for the whole response, but the earliest suspicious step. If a definition shifts or a condition disappears along the way, every polished derivation that depends on it is flagged in turn. After correcting a node, researchers need recheck only the branches it affects. The initial version focuses on symbolic reasoning and mathematical conversations whose premises can be stated explicitly. It does not replace peer review or claim to prove or disprove conjectures automatically. It helps researchers identify the one step most worth checking by hand first.

## Why now (backed by facts)

On July 22, Terence Tao’s published conversation reached second place on Hacker News, where the snapshot recorded 549 points and 349 comments. Researchers are more likely to read and reuse long AI mathematics conversations directly, and they need to locate the earliest failed premise or derivation.

## Direction (model inference, not independently verified)

Target user: The core users are researchers, PhD students, and formal-mathematics engineers who use large language models to explore proof ideas. Once a conversation runs for dozens of turns and conclusions begin to rely on early definitions, they can lose sight of the whole argument. Rereading it all is costly, while formalizing the entire exchange is too slow. They need to identify the node most worth checking by hand before deciding whether to invest in a complete proof.

Minimal entry point: Start by having a model extract definitions, assumptions, lemmas, and conclusions into a fixed JSON schema. Each node must retain its original location and declare its direct dependencies. Maintain a directed acyclic graph in NetworkX, rerunning only downstream branches after a node changes. Send polynomial identities, finite enumerations, and numerical substitutions to SymPy in a restricted container. For external theorems, first query the TheoremGraph API or LeanSearch for candidate sources. The first release will not attempt to translate an entire conversation into Lean automatically; users can send only key nodes to Lean for review. This tests whether identifying the earliest suspicious step actually saves verification time.

The strongest case against: The greatest risk is that claim extraction itself is wrong. A misdrawn dependency edge can label an innocent step as the source of the problem and waste even more of a researcher’s time. Converting natural language into symbolic form can also omit quantifiers, domains, and exceptional conditions. External theorems may have similar names, and a mistaken match can create a false sense of citation. Generated scripts require isolated execution, with limits on resources and accessible files. If the system repeatedly treats abbreviated exposition as mathematical error, users will quickly ignore its warnings. Before proceeding, validate the accuracy of nodes, dependency edges, and earliest errors against expert-annotated conversations.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Start with public AI-mathematics conversations and publish interactive reasoning graphs with their review trails. Show only one identified premise gap per case, so researchers can judge the value quickly. Build a ChatGPT shared-link importer to reduce first-use friction. Then publish technical postmortems in Lean Zulip, the Mathlib community, and relevant Hacker News threads, and invite anonymous submissions of failed cases.

## Competitors & gaps (model inference)

- Lean 4 and Mathlib: Lean 4 and Mathlib can send formalized statements to a kernel for verification, while companion tools support theorem search and machine interfaces. They are well suited to confirming whether a formal proof is valid, but require users to formalize it precisely first. Definition drift, implicit assumptions, and missing citations in a raw chat do not automatically become checkable objects. Researchers must still decide what proposition each sentence represents. When a proof fails, the error location may not be the earliest error in the reasoning. The opening is to organize an informal conversation first, then send suitable nodes to Lean. Other nodes remain subject to human review and computational checks, rather than making full formalization a prerequisite.
- TheoremGraph: TheoremGraph already organizes informal paper statements and Lean declarations into dependency graphs, with API and MCP interfaces. It is strong at cross-literature search, attribution, and theorem linking, and can provide infrastructure for citation checks. Its primary inputs are paper corpora and formal libraries, not a user’s newly completed multiround conversation. Its informal dependency extraction is itself approximate. It does not track when an assumption is dropped during a chat or generate counterexample scripts for a particular calculation. Rechecking affected branches after a user edits a conversation node is not its core workflow. The opening is to serve a single research process, retaining original wording, node versions, and verification results. TheoremGraph is better used as a theorem-retrieval backend than as a direct substitute.

## How it makes money (model inference)

Charge per-user workspace subscriptions with a fixed allowance for conversation parsing and rechecking. Bill additional tasks by usage, and offer team plans with shared annotations and private libraries.

## Source context

Theme: Terence Tao and ChatGPT on a Jacobian conjecture counterexample
Trigger Hacker News post (original English): Terrence Tao's ChatGPT Conversation about the Jacobian Conjecture Counterexample
Heat at capture: ~549 points, 349 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Terrence Tao's ChatGPT Conversation about the Jacobian Conjecture Counterexample (https://news.ycombinator.com/item?id=49010345)
- A digestion of the Jacobian conjecture counterexample (https://terrytao.wordpress.com/2026/07/21/a-digestion-of-the-jacobian-conjecture-counterexample/)
- Learn Lean (https://lean-lang.org/learn/)
- TheoremGraph: Bridging Formal and Informal Mathematics (https://arxiv.org/abs/2606.25363)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
