---
title: "Slow-Query Shadow Testing"
date: "2026-09-17"
canonical: "https://raytally.com/en/ideas/2026-09-17-training-a-4b-model-to-produce-81-faster-query-plans-than/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Training a 4B model to produce 81% faster query plans than Postgres"
  observed_at: "2026-09-17T00:33:30.523Z"
sources:
  - url: "https://rohanbansal.com/qorl"
    boundary: "Published at 2026-09-16T00:00:00.000Z. Observed at 2026-09-17T00:33:30.523Z."
  - url: "https://news.ycombinator.com/item?id=49731285"
    boundary: "Published at 2026-09-16T00:00:00.000Z. Observed at 2026-09-17T00:33:30.523Z."
  - url: "https://pganalyze.com/docs/query-advisor/getting-started"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://rmarcus.info/bao_docs/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-17-training-a-4b-model-to-produce-81-faster-query-plans-than/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Slow-Query Shadow Testing
When a slow query appears, race AI-generated plans against PostgreSQL on a production-shaped replica and deliver only verified winners with a rollback path.

## Product concept

Database teams may see that a new generation of small models can propose faster query execution paths, yet still hesitate to send those suggestions straight to production. A plan that looks faster can exhaust memory for a particular parameter set or leave other requests waiting, so it must first beat the existing plan under the shape of the real workload. The team connects slow-query logs and provides a non-writing replica with the same structure as production. The system selects costly queries from the logs, then replays the same parameter sets and data distributions against both PostgreSQL’s original plan and model-proposed candidate plans. Each comparison verifies that returned results are exactly identical, while recording latency, memory usage, and whether other requests slow down. Only candidates that win consistently receive a patch card stating the applicable parameter range, expected savings, and a one-click switch back to the original plan. Engineers can approve one class of queries first, then expand coverage gradually. The initial scope is read-only queries only: no writes, schema changes, or automatic deployment. The model proposes candidates, but the team still decides whether they enter production. The product delivers execution plans that have passed measured tests, not an optimization suggestion that someone must adopt on instinct.

## Why now (backed by facts)

On September 16, an experiment showed that a 4B model selected query plans with a 1.81x speedup in the JOB benchmark from as many as 15 candidates. As observed on September 17, the article ranked fifth on Hacker News with 370 points and 75 comments; discussion quickly turned to whether those results could withstand real production workloads.

## Direction (model inference, not independently verified)

Target user: Platform engineers, DBAs, and backend leads running PostgreSQL analytical workloads. The trigger is a recurring slowdown in a class of read-only queries: the team has a model-generated optimization suggestion, but no one is willing to alter the production plan directly. Reading EXPLAIN manually no longer proves the benefit, because parameter distributions, cache state, and concurrency can all change the outcome. They need repeatable testing on a replica instead of a deployment debate.

Minimal entry point: Start with read-only SELECT queries on a single PostgreSQL major version. Use slow-query logs or `pg_stat_statements` to identify costly query fingerprints, then collect available bound parameters. Candidate generation can reuse qorl’s structured PlanAction approach, while `pg_hint_plan` controls join order, scans, and parallelism. The replayer runs `EXPLAIN (ANALYZE, BUFFERS, FORMAT JSON)` and records planning, execution, and temporary-block metrics separately. Client-side streaming writes result sets to disk, then verifies them row by row against the same data snapshot. The first release should not claim to measure peak execution-time memory precisely; instead, it sets hard limits for `work_mem`, timeouts, and temporary files. Each candidate alternates with the native plan to reduce bias from cache warmth and background variance.

The strongest case against: A winner on a replica may simply fit the current cache state and statistics. Its advantage can reverse as data grows, parameters shift, or PostgreSQL is upgraded. To cover those changes, teams must retain representative parameters and periodically rerun the full candidate set. Replay itself consumes substantial compute and storage, and long queries can slow replica synchronization. Result verification is also difficult: unordered results, floating-point values, and volatile functions each require special handling. PostgreSQL offers incomplete visibility into peak execution-time memory, so latency and temporary-block metrics alone can miss resource risk. If production deployment depends on `pg_hint_plan`, teams also take on the operational cost of installing the extension, maintaining version compatibility, and handling invalidated hints. Once candidate counts grow, verification may cost more than the database savings.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Find the first users among PostgreSQL performance consultants, data-platform engineers, and self-hosted SaaS teams. They often already have sanitized replicas and can judge whether a speedup is worth deploying. Open-source a local replayer that produces shareable plan-comparison reports. Publish reproducible experiments on real slow queries, including why failed candidates were rejected. The original Hacker News discussion and the PostgreSQL community are suitable channels for reaching early users willing to experiment.

## Competitors & gaps (model inference)

- pganalyze Query Advisor and Workbooks: pganalyze Query Advisor continuously analyzes execution plans to identify issues such as inefficient nested loops. It can also generate query rewrites or planner hints, and Workbooks can benchmark different parameter sets. Users still control whether an optimization reaches production. This already covers much of the discovery, recommendation, and manual-validation workflow. Its public documentation remains focused on known anti-patterns and deterministic rules. The opening for a slow-query shadow lane is to accept a broader set of model-generated candidates and eliminate them one by one against real data distributions. Evaluation would also account for harm to concurrent requests, resource limits, and a requirement to win consistently. The deliverable is not a recommendation but a patch card with a defined parameter range. If pganalyze expands its candidate generation and workload replay capabilities, this opening will narrow quickly.
- Bao for PostgreSQL: Bao is a learning-based query optimizer for PostgreSQL. It uses coarse-grained hints to influence the native planner and updates its model from execution feedback. It can either choose automatically or act as an advisor that suggests hints. Bao also offers a pre-exploration mode that tests queries for a specified time and prevents pre-explored queries from using fallback plans. It has already demonstrated the basic explore-before-exploit path. Its public implementation targets PostgreSQL 12 and requires a database extension and a separate service. A slow-query shadow lane can instead center on team approval rather than online exploration. It would also verify full result sets, reproduce real parameter distributions, and test whether candidates slow other requests. Patch cards need to state their applicable range, resource evidence, and a disable switch. Those operational safeguards are closer to a production buying rationale than simply predicting the faster plan.

## How it makes money (model inference)

Charge a subscription per managed database instance. The base tier includes read-only replica replay, candidate comparison, and patch cards. Higher tiers add concurrent load testing, approval controls, historical regression testing, and private deployment. Set monthly allowances for model calls and replay compute so expensive queries do not make costs unmanageable.

## Source context

Theme: Training a 4B model to produce 81% faster query plans than Postgres
Trigger Hacker News post (original English): Training a 4B model to produce 81% faster query plans than Postgres
Heat at capture: ~370 points, 75 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Training a 4B model to produce 81% faster query plans than Postgres (https://rohanbansal.com/qorl)
- Training a 4B model to produce 81% faster query plans than Postgres (https://news.ycombinator.com/item?id=49731285)
- Getting Started with Query Advisor (https://pganalyze.com/docs/query-advisor/getting-started)
- Bao for PostgreSQL (https://rmarcus.info/bao_docs/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
