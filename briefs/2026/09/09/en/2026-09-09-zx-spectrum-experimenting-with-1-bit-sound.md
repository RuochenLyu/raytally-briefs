---
title: "ZX Spectrum 1-Bit Sound Workshop"
date: "2026-09-09"
canonical: "https://raytally.com/en/ideas/2026-09-09-zx-spectrum-experimenting-with-1-bit-sound/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "ZX Spectrum: Experimenting with 1-Bit Sound"
  observed_at: "2026-09-09T00:33:14.604Z"
sources:
  - url: "https://bumbershootsoft.wordpress.com/2026/09/05/zx-spectrum-experimenting-with-1-bit-sound/"
    boundary: "Published at 2026-09-05T00:00:00.000Z. Observed at 2026-09-09T00:33:14.604Z."
  - url: "https://news.ycombinator.com/item?id=49611230"
    boundary: "Published at 2026-09-08T00:00:00.000Z. Observed at 2026-09-09T00:33:14.604Z."
  - url: "https://github.com/gasman/jsspeccy3"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://github.com/z00m128/sjasmplus"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-09-zx-spectrum-experimenting-with-1-bit-sound/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

ZX Spectrum 1-Bit Sound Workshop
A browser-based workshop for ZX Spectrum musicians to compose 1-bit music, hear it as they work through processor-cycle overruns, and export code for real hardware.

## Product concept

People writing soundtracks for early home computers such as the ZX Spectrum must control the beeper using very little processor time. A melody that is only slightly too complex can take computation away from game logic. In the browser, creators choose a target machine or emulator configuration, then arrange notes, rhythms, and timbre changes on an auditionable timeline. The timeline’s smallest unit is not a conventional musical beat, but the processor cycles required to execute instructions. When a creator drags a rhythm segment, the interface immediately shows how many cycles it consumes, how the beeper will toggle, and where character movement or screen refreshes may be blocked. Sections that exceed their budget become apparent both in the waveform and by ear. Game programmers can freeze a rhythm segment into a machine-code phrase, along with its required cycles and calling conditions. When the musician revises the melody, the system flags the code sections that must be re-exported. A project page can also play emulator output beside real-hardware recordings, gathering differences in distortion across machines. The first release supports mono beepers, short looping music, and assembly-code exports that can be embedded directly. Its purpose is to let creators work through hardware constraints while listening; complex multi-chip audio arrangement can come later.

## Why now (backed by facts)

A September 5 experimental article broke beeper writes, delays, and pitch drift down to individual instruction cycles. When observed on September 9, it ranked 16th in Hacker News’s new submissions feed with 91 points and 26 comments, exposing more retro developers to the problem of sound and game logic competing for cycles.

## Direction (model inference, not independently verified)

Target user: The core user writes beeper music for ZX Spectrum 48K games or demos. The problem usually appears once a melody plays but must fit inside the game’s main loop, where each phrase competes for cycles with input, character movement, and screen updates. The musician and programmer may also be different people, so they need a reproducible cycle breakdown, not just an audio file.

Minimal entry point: Start in the browser with the ZX Spectrum 48K and its mono beeper. Use JSSpeccy 3's WebAssembly architecture to run the Z80, display, and audio emulation. The editor handles only short loops, note lengths, and port-toggle events. After every edit, it records instruction T-states, port writes, and frame boundaries. Programmers enter the cycle budget manually at first rather than having the tool infer the full game load. Use sjasmplus for export, producing readable assembly, machine code, and a cycle report. The first version does not support multi-chip arrangements or promise identical sound across emulators and every real machine.

The strongest case against: Instruction-by-instruction cycle previews can create false certainty. Memory contention, interrupts, code load addresses, and self-modifying code can all alter real timing. If the editor measures only isolated phrases, playback may still stutter or drift out of tune once embedded in a game. Raising confidence requires integrating full program snapshots and calling context, which quickly increases engineering complexity. Real-hardware recordings also vary with machine revision, the audio-capture chain, and volume processing, making the source of differences difficult to determine automatically. The audience is narrow, and many experienced users already have a tracker, assembler, and emulator workflow. They will not switch for a prettier timeline unless cycle diagnostics clearly reduce testing round trips.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Early users cluster in the ZX Spectrum retro-development community, demoparties, and the 1-bit music scene. Publish several downloadable projects that pair the same phrase’s cycle timeline with emulator output and real-hardware recordings. Then submit exported short loops to existing open-source games or competition entries to create verifiable examples. Import templates for specific engines will attract trials more effectively than broad claims about browser-based composition.

## Competitors & gaps (model inference)

- Beepola: Beepola already supports ZX Spectrum 48K beeper music through a traditional tracker grid. It includes several historical and modern playback engines, and can compile songs and export assembly code. For users comfortable with patterns, engines, and the Z80 toolchain, this is already a mature workflow. Its core abstraction is still notes, effect columns, and playback engines—not instruction-cycle visibility by section. Creators generally compile first, then use an emulator or the game itself to determine whether playback causes slowdowns. The effect of individual phrases on the main loop, screen refresh, and input scanning is not shown alongside the sound on one timeline. The opening is to make cycle budgets an editable musical constraint, then include calling conditions and affected code sections in the export to reduce back-and-forth between musicians and programmers.
- Bintracker: Bintracker is a programmable chip-music workstation supporting multiple platforms and engines, including the ZX Spectrum beeper. It uses MAME as its emulation backend and can export binaries, assembly, and ZX Spectrum TAP files. Its plugins, MDAL abstraction, and built-in command environment suit experimentation with new engines. But it remains centered on a general-purpose tracker and engine adaptation, with substantial configuration and extension capabilities. It does not directly map the Z80 cycles consumed by a phrase to a game’s main loop. Nor can musicians see, while dragging a rhythm, where beeper transitions may block screen updates. Its broad platform coverage leaves room for a focused 48K mono workflow. This product could combine auditioning, cycle diagnostics, and embeddable code in a narrower flow. The trade-off is that it would initially offer far fewer engines and less arranging freedom than Bintracker.

## How it makes money (model inference)

Sell a one-time personal license that includes the browser editor, offline projects, and assembly export. Offer annual upgrade packs for real-hardware comparisons, shared team projects, and support for additional machines.

## Source context

Theme: ZX Spectrum 1-Bit Sound Experiments
Trigger Hacker News post (original English): ZX Spectrum: Experimenting with 1-Bit Sound
Heat at capture: ~91 points, 26 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- ZX Spectrum: Experimenting With 1-Bit Sound (https://bumbershootsoft.wordpress.com/2026/09/05/zx-spectrum-experimenting-with-1-bit-sound/)
- ZX Spectrum: Experimenting with 1-Bit Sound | Hacker News (https://news.ycombinator.com/item?id=49611230)
- JSSpeccy 3 (https://github.com/gasman/jsspeccy3)
- sjasmplus (https://github.com/z00m128/sjasmplus)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
