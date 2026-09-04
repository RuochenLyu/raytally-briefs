---
title: "Retro Game Dual-Run Porting Bench"
date: "2026-09-04"
canonical: "https://raytally.com/en/ideas/2026-09-04-porting-my-1993-amiga-game-to-godot-with-an-llm-reading-the/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Porting my 1993 Amiga game to Godot, with an LLM reading the 68000 assembly"
  observed_at: "2026-09-04T00:33:18.586Z"
sources:
  - url: "https://babyloniantwins.com/blog/porting-a-1993-amiga-game-to-godot/"
    boundary: "Published at 2026-09-01T00:00:00.000Z. Observed at 2026-09-04T00:33:18.586Z."
  - url: "https://news.ycombinator.com/item?id=49550375"
    boundary: "Published at 2026-09-03T00:00:00.000Z. Observed at 2026-09-04T00:33:18.586Z."
  - url: "https://docs.godotengine.org/en/4.7/tutorials/inputs/controllers_gamepads_joysticks.html"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://kb.gamedriver.ai/gamedriver-test-assistant"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-04-porting-my-1993-amiga-game-to-godot-with-an-llm-reading-the/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Retro Game Dual-Run Porting Bench
Run an original retro game and its modern port side by side, then pinpoint the first code-level divergence in feel or logic under identical input.

## Product concept

When porting 68000 assembly logic to Godot, the hardest part for a retro-game author is often not getting the new version to run, but confirming that it still feels like the original. The developer connects the original to an emulator, uploads a runnable build of the modern port, and records a sequence of keyboard or controller actions. The product feeds both versions the exact same input and records frame-by-frame video, collisions, audio timing, and key memory states. As soon as the two versions diverge, the interface does more than report a failed test. It stops at the first mismatching frame, shows the two outputs side by side for a few seconds before and after it, and places the relevant assembly, modern code, and execution traces together. The model explains possible behavioral differences only within this narrow context, and the developer can export a minimal reproduction package for collaborators in one click. The first release prioritizes relatively deterministic 2D games, along with keyboard and common controller input. It does not automatically translate an entire assembly codebase into a new engine, nor does it decide which old bugs should remain. Its job is to reduce “it feels different” to a specific discrepancy that can be replayed, discussed, and fixed.

## Why now (backed by facts)

On September 1, an author published their process for porting a 68000 assembly game to Godot with an LLM, yet still judged the new version’s feel manually. When captured on September 4, the related Hacker News discussion ranked 10th, with 177 points and 57 comments; one commenter directly asked whether the port could use the same inputs as UAE.

## Direction (model inference, not independently verified)

Target user: Independent authors with original source code, disk images, or old builds. The key moment comes when the new version is playable from start to finish, yet jumps, collisions, or sound effects still feel wrong. Standard unit tests can show that new code is internally consistent, not that it remains faithful to the original. Collaborators may not understand the old assembly, so locating the discrepancy often collapses into repeated playtesting and subjective tuning.

Minimal entry point: Start with a desktop local runner limited to FS-UAE and Godot 4. On the original-game side, inject frame-by-frame input and read designated memory regions. On the Godot side, replay keyboard and controller events through Input.parse_input_event(). Both sides produce a shared frame number, screen hash, and user-declared state fields. The first version does not infer the meaning of all memory; it compares only addresses and variables marked by the author. Once a divergence is found, retain a short before-and-after clip, the input sequence, and logs from both sides. Initially, code linkage relies on address maps, symbol tables, and user-selected files, without promising automatic understanding of an entire assembly codebase.

The strongest case against: Cross-system determinism could consume substantial engineering time before anything else works. The original may update at 50 Hz while the port processes physics and input at another rate. Audio buffers, floating-point error, and visual effects can all create meaningless differences. An emulator’s per-frame input may not match the moment when the original game actually reads controller state. Without memory addresses from the author and modern state fields, the system can see only pixel divergence and cannot reliably point to code. ROMs, Kickstart, and commercial assets also introduce licensing boundaries, while cloud hosting adds compliance burden. If false attribution repeatedly mistakes visual noise for game-feel problems, authors will quickly return to manual playtesting.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Reach the first users through Amiga, Atari ST, and retro-game porting communities. Use an open-source example repository to show the complete process of finding the first divergence in a jump arc. Then list the runner in the Godot plugin directory and release reusable test fixtures. Each public reproduction package should retain a link to the original author’s project, letting the tool spread through real porting cases rather than generic AI coding promotion.

## Competitors & gaps (model inference)

- GameDriver Test Assistant: GameDriver can connect to a running game, query objects, record inputs, and replay steps. It can also inspect engine logs and export to .NET test frameworks. These capabilities suit automated regression testing for modern games and cover Unity and Unreal. Its recorded steps may still need adjustment because games can be nondeterministic. The available materials do not show that it can lock an original game in an emulator and a modern port to the same input sequence, or identify the first frame where the two implementations diverge. Teams would still need to build the mapping among assembly addresses, emulator memory, and Godot node state themselves. The opening for a retro-game dual-run porting bench is to make cross-runtime comparison the core workflow rather than offer another general-purpose test recorder.
- FS-UAE, command-line probes, and custom comparison scripts: The author already uses command-line parameters for frame-by-frame keyboard input, state probes, and screenshots. They also use FS-UAE to launch the original and vasm to rebuild the binary. This shows that authors familiar with the toolchain can build part of the validation setup themselves. Pixel comparisons can be assembled with standard image tools, while key variables can be compared manually through logs from both versions. The gap is that these scripts are scattered across individual projects, and authors must instrument state fields one by one. The original and port may run on different clocks, and their input sampling points may not naturally align. When a discrepancy appears, developers still have to roll back manually and search for the relevant code. The product needs to turn clock calibration, first-frame detection, and minimal reproduction packaging into a reliable end-to-end workflow. If it cannot substantially reduce this glue work, homegrown scripts will be cheaper and more controllable.

## How it makes money (model inference)

Charge a per-project subscription that includes the local runner, a set number of collaborator seats, and test history. Customers provide their own emulator images, ROMs, and game assets. Teams that need to retain builds and regression records over time can upgrade to a higher storage tier.

## Source context

Theme: Porting a 1993 Amiga game to Godot with an LLM reading 68000 assembly
Trigger Hacker News post (original English): Porting my 1993 Amiga game to Godot, with an LLM reading the 68000 assembly
Heat at capture: ~177 points, 57 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Porting my 1993 Amiga game to Godot, with an LLM reading the 68000 assembly (https://babyloniantwins.com/blog/porting-a-1993-amiga-game-to-godot/)
- Porting my 1993 Amiga game to Godot, with an LLM reading the 68000 assembly | Hacker News (https://news.ycombinator.com/item?id=49550375)
- Controllers, gamepads, and joysticks (https://docs.godotengine.org/en/4.7/tutorials/inputs/controllers_gamepads_joysticks.html)
- GameDriver Test Assistant (https://kb.gamedriver.ai/gamedriver-test-assistant)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
