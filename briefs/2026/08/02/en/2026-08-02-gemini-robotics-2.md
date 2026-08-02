---
title: "Robot Job Trial"
date: "2026-08-02"
canonical: "https://raytally.com/en/ideas/2026-08-02-gemini-robotics-2/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Gemini Robotics 2"
  observed_at: "2026-08-02T00:33:18.427Z"
sources:
  - url: "https://www.producthunt.com/products/gemini-robotics-2"
    boundary: "Observed at 2026-08-02T00:33:18.427Z."
  - url: "https://deepmind.google/models/gemini-robotics/vla/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.intrinsic.ai/flowstate"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://robodk.com/simulation"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-02-gemini-robotics-2/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Robot Job Trial
Record a real task, mark the objects and constraints, and see which steps a robot can handle, where it may fail, and how the workstation needs to change.

## Product concept

For small factories and labs considering robots, the hard part is not watching a demo. It is determining whether a task can actually be done on their own bench, with their parts and safety constraints. A manager records an employee performing the real task on a phone, then marks the objects to pick up, target locations, no-touch zones, and completion criteria in the footage. The product breaks the recording into actions such as grasping, moving, aligning, and placing, then runs them once in a digital scene. Each step shows a confidence estimate and reasons it may fail: glare that obscures a label, a deformable pouch, too little room to reach in, or two parts that look too similar in view. Before buying a robot, the manager can see which part of the job is best suited to a pilot. The result is a site-specific feasibility card. It lists actions that can be automated, actions that need human handoff, and workstation changes needed to raise the chance of success, such as adding a locating fixture, adjusting the lighting, or clearing clutter from the pick-and-place area. The card can also be exported as a task specification for an integrator to quote or use in a physical-robot test. The first version analyzes only short tasks such as tabletop pick-and-place, sorting, and simple assembly. It does not promise direct control of production equipment. Its boundary is clear: record one specific job, identify what a robot can do and what the site still lacks, then decide whether a physical robot is worth pursuing.

## Why now (backed by facts)

As of August 2, Gemini Robotics 2 ranked 14th in Product Hunt’s new-product feed, and its official page has begun showing manipulation capabilities across robot embodiments. This is likely to shift more site managers' question from “Can robots do this?” to “Can they do it at my workstation?”

## Direction (model inference, not independently verified)

Target user: Small-factory supervisors, lab managers, and automation engineers without a dedicated robotics team. The key moment is when they receive a vendor proposal or prepare an automation budget request. They can describe the manual process but cannot tell whether occlusion, fixtures, or space constraints will make the plan fail. What they need is not full programming, but a site assessment that tells them whether to continue requesting quotes and arrange a physical-robot test.

Minimal entry point: On mobile, users first record video from a fixed camera position and include an object of known dimensions for calibration. They select objects, target positions, and no-go zones frame by frame. The service breaks the operation into grasping, carrying, alignment, and release. The first version does not reconstruct an entire factory from monocular video; it generates only simplified geometry for the workbench, containers, and obstacles. Users add object weight, material, and dimensions afterward, and any missing values are explicitly marked for validation. Paths, reachability, and collisions can be batch-checked through the RoboDK API. Gemini Robotics 2 remains in private preview, so the core workflow should not depend on public access to it. Output uses evidence tiers and does not present simulation results as real-world success rates.

The strongest case against: A single video view loses depth, scale, and structure behind occlusions. It also cannot reliably infer pouch friction, part weight, or fixture stiffness. If a simplified scene produces conclusions that are too strong, managers may underestimate integration difficulty. Yet collecting the missing parameters can force users through a burdensome round of measurements. Safety zones also depend on the robot model, speed, and site rules; video cannot replace that assessment. The product must put unknowns and conditions for physical-robot validation ahead of its conclusions. Otherwise, one bad recommendation could damage trust between integrators and factories.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Early users are most likely to come from robotics integrators' pre-sales teams. They often receive under-specified automation inquiries and need to decide whether an on-site visit is worthwhile. Offer branded feasibility cards that integrators can send prospective customers to collect recordings. Then select anonymized cases for before-and-after content showing the original workstation and the proposed modifications. Every card retains a handoff path to an integrator, linking customer acquisition to the actual quoting process.

## Competitors & gaps (model inference)

- Intrinsic Flowstate: Intrinsic Flowstate can create workstation digital twins and assess reachability and collisions. Developers can also compose skills through a graphical interface, Python, or C++, and switch between simulation and physical robots. It suits specialist R&D teams that already have a robot plan. Users must choose hardware, prepare 3D assets, and understand motion planning. It does not turn employee-recorded footage into a pre-purchase workstation-screening brief. What small factories need is an earlier decision: whether the task is worth modeling at all. This product can stay at the requirements-clarification layer rather than compete for deployment and control. Its exported task specification could instead feed a Flowstate project.
- RoboDK: RoboDK already supports industrial robot simulation, collision checking, and offline programming. Users can import models of parts, fixtures, and the environment, then generate programs for multiple controllers. Its strengths are its robot library, engineering precision, and mature programming workflow. But users must already know the robot, tool, and reference frames. A site manager still has to translate a manual operation into models and paths. The opening here is to begin with phone video. The product first identifies occlusion, look-alike parts, and workstation constraints, then determines whether to move into RoboDK. It does not replace precise simulation; it reduces the number of projects that are not worth modeling.

## How it makes money (model inference)

Charge per workflow assessment, including a feasibility card, workstation modification recommendations, and task-spec export. Integrators can buy team plans to manage projects for multiple customers and reuse report templates. Integrators quote physical-robot validation and on-site measurement separately; the platform does not sell equipment.

## Source context

Theme: Gemini Robotics 2 robot AI model
Trigger Product Hunt launch: Gemini Robotics 2 — Google's AI brain for the next generation of robots

This records only that the launch appeared in Product Hunt's public feed and when it was observed. The feed provides no vote count; do not describe feed order as popularity or market demand.

## Sources

- Gemini Robotics 2: Google's AI brain for the next generation of robots (https://www.producthunt.com/products/gemini-robotics-2)
- Gemini Robotics 2 (https://deepmind.google/models/gemini-robotics/vla/)
- Intrinsic Flowstate (https://www.intrinsic.ai/flowstate)
- Robot Simulation and Programming (https://robodk.com/simulation)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
