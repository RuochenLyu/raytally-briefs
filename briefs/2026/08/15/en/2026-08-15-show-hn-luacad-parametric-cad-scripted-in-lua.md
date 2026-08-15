---
title: "LuaCAD Pull Request Geometry Review"
date: "2026-08-15"
canonical: "https://raytally.com/en/ideas/2026-08-15-show-hn-luacad-parametric-cad-scripted-in-lua/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Show HN: LuaCAD – Parametric CAD Scripted in Lua"
  observed_at: "2026-08-15T00:33:26.882Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49301215"
    boundary: "Published at 2026-08-14T16:43:22.000Z. Observed at 2026-08-15T00:33:26.882Z."
  - url: "https://luacad.ad-si.com/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://github.com/openscad/openscad"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://github.com/eblanshey/HistoryWorkbench"
    boundary: "Published at 2026-06-09T00:00:00.000Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-15-show-hn-luacad-parametric-cad-scripted-in-lua/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

LuaCAD Pull Request Geometry Review
A GitHub pull-request checker for LuaCAD that renders geometry diffs and tests parameter bounds before hardware teams merge a change.

## Product concept

Once a hardware team stores LuaCAD models in a code repository, reviewers should be able to see what a part actually became whenever a commit changes a parameter or geometry algorithm. This service plugs into pull requests and automatically retrieves the before-and-after scripts, default parameters, and the adjustable ranges declared by the designer. A build renders both solids and produces rotatable overlays, cross-sections, and comparisons of key dimensions. Reviewers can drag a slider to see how far a screw hole moved or how much thicker a snap-fit became, then click a model region to jump to the relevant script line. For parts such as brackets and enclosures, visual changes no longer remain buried in hard-to-read parameter calculations. The service also batch-generates samples across the designer’s declared bounds, checking for disappearing holes, self-intersecting solids, and walls that are too thin. Each failure includes its parameter values and a render so developers can reproduce and fix it. Comments are pinned to specific geometry regions and retained with the code and model version after merge. The initial release integrates GitHub and LuaCAD, covering STL export and common FDM-printing constraints. It makes code changes visible and discussable; it does not replace material-strength calculations, machining-tolerance validation, or final physical inspection.

## Why now (backed by facts)

LuaCAD’s Show HN post appeared on August 14; as recorded on August 15, it had 67 points, 13 comments, and ranked 15th. This gives more scripted-CAD users a reason to bring Lua models into their existing code workflows, making pull-request geometry changes that are difficult to review more likely to surface.

## Direction (model inference, not independently verified)

Target user: The core user is a small hardware team that keeps LuaCAD part scripts in GitHub. The problem arises after a parameter or geometry function changes and a teammate is asked to merge it. Reviewers may be able to read Lua but cannot reliably judge hole locations, wall thicknesses, or assembly clearance from text alone. If they must install a local environment and render each parameter set themselves, review easily collapses into code-only review.

Minimal entry point: Ship as a GitHub App that listens for pull requests and subsequent commits. Runners check out the baseline and current versions, invoke the LuaCAD CLI to export STL files, and generate PNG previews. LuaCAD already provides stable commands for conversion, rendering, bounding boxes, and triangle counts, which the first version can reuse. The web view presents both meshes from the same camera, with section planes and dimension markers overlaid. Parameter ranges initially come from a declaration file in the repository rather than being inferred from arbitrary Lua code. Early checks cover build failures, empty solids, bounding-box jumps, and non-manifold output. Source links require designers to name parts and bind them to script lines in the declaration file; do not promise automatic tracing of faces through arbitrary Boolean operations.

The strongest case against: Arbitrary Lua scripts may access files or produce side effects, so cloud builds must isolate network access, permissions, and resources. Differences in dependencies, fonts, and renderer versions can produce different meshes from the same commit. Parameter combinations grow quickly; exhaustive enumeration would slow pull requests and raise compute costs. Thin-wall and printing constraints depend on nozzle, material, and orientation, so generic rules can generate false positives. After Boolean operations, mesh surfaces may not map reliably back to a source line. If comment locations drift or check results cannot be reproduced, teams will disable required checks and the product loses its value.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Reach the first users through the LuaCAD GitHub repository, Show HN participants, and scripted-CAD communities. Provide a copyable example repository so maintainers can see overlays and failing parameter sets in a real pull request. Generate shareable check pages free for public repositories, each with an installation link back to GitHub. Then publish a general workflow template that minimizes adoption work for existing LuaCAD projects.

## Competitors & gaps (model inference)

- History Workbench for FreeCAD: History Workbench can save iterations within FreeCAD and compare 3D geometry by color. It also compares model trees, dimensions, constraints, and properties, making it useful for designers reviewing versions locally. Its workflow, however, centers on FreeCAD documents and workbenches. GitHub remote push is still on the roadmap. It does not turn LuaCAD commits directly into pull-request checks or batch-build against declared parameter bounds. The opportunity is to keep review in GitHub and make every failing parameter set reproducible evidence. Teams do not need to migrate to another CAD document format or require every reviewer to install FreeCAD.
- OpenSCAD with self-hosted GitHub Actions: OpenSCAD offers an established approach to scripted solid modeling. Its code can expose configurable parameters and read and generate formats including STL. Teams can review scripts in Git and invoke the command line in CI to export models. This approach is inexpensive, open, and easy to extend with homegrown screenshots and artifacts. But a Git text diff does not show where a solid changed. Standard CI also does not automatically organize parameter-boundary tests, geometry overlays, or region-specific comments. Teams must still maintain render scripts, artifact pages, and a format for reproducing failures. A dedicated service for LuaCAD can consolidate those scattered steps into one review while preserving the link between parameter values and model versions.

## How it makes money (model inference)

Sell subscriptions per GitHub organization, with a set number of private repositories and monthly build capacity. Public repositories are free; additional parameter samples are billed by build minute. A team plan adds self-hosted runners, audit retention, and required merge checks.

## Source context

Theme: LuaCAD scripted parametric CAD
Trigger Hacker News post (original English): Show HN: LuaCAD – Parametric CAD Scripted in Lua
Heat at capture: ~67 points, 13 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Show HN: LuaCAD – Parametric CAD Scripted in Lua (https://news.ycombinator.com/item?id=49301215)
- LuaCAD (https://luacad.ad-si.com/)
- OpenSCAD – The Programmers Solid 3D CAD Modeller (https://github.com/openscad/openscad)
- History Workbench for FreeCAD (https://github.com/eblanshey/HistoryWorkbench)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
