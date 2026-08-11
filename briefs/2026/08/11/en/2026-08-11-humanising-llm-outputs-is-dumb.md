---
title: "Facts and Actions in AI Responses"
date: "2026-08-11"
canonical: "https://raytally.com/en/ideas/2026-08-11-humanising-llm-outputs-is-dumb/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Humanising LLM Outputs Is Dumb"
  observed_at: "2026-08-11T00:33:09.142Z"
sources:
  - url: "https://kuber.studio/blog/Reflections/Humanising-LLM-Outputs-is-Actually-Dumb"
    boundary: "Published at 2026-08-10T00:00:00.000Z. Observed at 2026-08-11T00:33:09.142Z."
  - url: "https://news.ycombinator.com/item?id=49243474"
    boundary: "Published at 2026-08-10T00:00:00.000Z. Observed at 2026-08-11T00:33:09.142Z."
  - url: "https://elements.ai-sdk.dev/components/sources"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://docs.langchain.com/langsmith/view-traces"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-11-humanising-llm-outputs-is-dumb/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Facts and Actions in AI Responses
A frontend component that separates sourced facts, model speculation, and completed actions in AI responses, so conversational language cannot hide the system’s actual state.

## Product concept

Customer service, operations, and internal assistants increasingly deliver results through chat interfaces, yet users struggle to distinguish model speculation from retrieved facts and actions the system has actually completed. “I submitted your refund” can easily be mistaken for a completed task when no corresponding execution record exists. Once a team connects model text, cited sources, and tool-call logs to this frontend component, every passage is classified before display. Facts mentioned by the model get clickable source cards; unsupported judgments are labeled as suggestions or speculation. For actions such as changing a price, issuing a refund, sending an email, or restarting a service, the component shows “executed” only after it receives the matching tool log, object ID, and returned result. Any statement without a matching log becomes “suggested action,” returning the next step to the user or workflow. Users can open any conclusion to see which material it cites, which tool it called, and whether the request returned successfully. Designers can assign clearly distinct colors, icons, and buttons to each state, so conversational tone cannot disguise uncertain content as a promise. Customer-service leads can also filter for recurring patterns where the model claims completion but nothing was actually executed, then use them to improve prompts or integration flows. The initial version supports text with source IDs and structured tool logs. It does not determine whether the underlying material is true or execute any actions itself. Its first job is honest expression in the interface: users should be able to distinguish at a glance what the model said, what supports it, and what the system actually did.

## Why now (backed by facts)

On August 10, an article criticized anthropomorphic language for concealing failures. As of August 11, it ranked 10th on Hacker News, with 143 points and 85 comments; teams may be more ready to confront the gap between model promises and execution records.

## Direction (model inference, not independently verified)

Target user: Product teams deploying customer-service, operations, or internal agents, especially as actions expand from read-only queries to refunds, price changes, or email. At that point, a false completion claim directly creates tickets and erodes trust. Frontend leads need consistent state language, while managers need to identify replies whose promises do not match their logs.

Minimal entry point: Start with a React component and a strict message protocol. Each sentence carries a type, source ID, and tool-call ID. Tool logs must include at least the call ID, object ID, status, result, and error. It can directly support AI SDK UIMessage and typed tool parts. “Executed” is generated only by deterministic rules, never by the model’s judgment. Source cards map by ID, and sentences with unclear classification are consistently shown as speculation. The first release accepts structured input only; it does not parse arbitrary chat text or assess source reliability.

The strongest case against: Sentence-level classification introduces its own errors. Labeling a real fact as speculation can make a response seem slow or evasive; labeling a suggestion as an action recreates the original problem. Log fields, retries, and asynchronous callbacks also vary widely across systems. A source existing does not mean it supports the conclusion, and the component cannot validate the evidence for a team. Showing object IDs and error details creates permission and privacy concerns. If integration costs exceed the time saved on complaints and investigation, teams will stick with standard chat components.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Reach the first users through frontend engineers building customer-service agents. Release an open-source React package with runnable examples for refunds, email sending, and service restarts. Center the examples on the contrast between a model claiming success and a failed tool response. Then publish through npm, GitHub, and the AI SDK community to build organic traffic around terms such as tool result, agent UI, and citation UI.

## Competitors & gaps (model inference)

- Vercel AI SDK and AI Elements: AI Elements already offers UI components for sources, tools, and confirmations. AI SDK can also break text, tool calls, and results into typed message parts. This lowers the cost of building chat interfaces while retaining call state. But it is primarily a set of rendering primitives. Teams must still define when they can say “completed.” It does not automatically check whether a natural-language promise matches a tool result, downgrade an action to a suggestion when no result exists, or provide cross-message reporting on false completion claims. The opening is a tightly constrained state semantics layer, not merely a way to display different message types.
- LangSmith: LangSmith lets users inspect model responses, tool calls, and returned results by conversation. They can drill into an individual run to examine inputs, outputs, errors, and metadata. It is well suited to engineers troubleshooting agent workflows, and its annotation and dataset capabilities support later evaluation. Its main interface, however, is designed for development and operations teams. End users generally do not see this trace data. Nor does it verify action claims sentence by sentence before a reply is shown. Teams must still connect trace IDs, business objects, and chat text themselves. This product could compress trace evidence into user-facing status and block “executed” language when the evidence is missing.

## How it makes money (model inference)

Monthly team subscription priced by the volume of verified messages. The base plan includes components, state rules, and log filtering; enterprise adds private deployment, access controls, and custom state mappings.

## Source context

Theme: Against anthropomorphizing LLM output
Trigger Hacker News post (original English): Humanising LLM Outputs Is Dumb
Heat at capture: ~143 points, 85 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Humanising LLM Outputs is Dumb (https://kuber.studio/blog/Reflections/Humanising-LLM-Outputs-is-Actually-Dumb)
- Humanising LLM Outputs Is Dumb | Hacker News (https://news.ycombinator.com/item?id=49243474)
- AI Elements Sources and AI SDK Tool Usage (https://elements.ai-sdk.dev/components/sources)
- View traces | LangSmith (https://docs.langchain.com/langsmith/view-traces)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
