---
title: "Firmware Before the Boards Arrive"
date: "2026-08-07"
canonical: "https://raytally.com/en/ideas/2026-08-07-launch-hn-provenmetal-yc-s26-delivers-circuit-boards-in-days/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Launch HN: ProvenMetal (YC S26) delivers circuit boards in days instead of weeks"
  observed_at: "2026-08-07T00:33:32.790Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49198464"
    boundary: "Published at 2026-08-06T15:59:15.000Z. Observed at 2026-08-07T00:33:32.790Z."
  - url: "https://docs.kicad.org/7.0/en/cli/cli.html"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://renode.readthedocs.io/en/latest/introduction/testing.html"
    boundary: "Published at 2026-07-16T00:00:00.000Z."
  - url: "https://docs.wokwi.com/wokwi-ci/getting-started"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-07-launch-hn-provenmetal-yc-s26-delivers-circuit-boards-in-days/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Firmware Before the Boards Arrive
Upload a PCB design after manufacturing begins to create virtual hardware that runs real firmware tests before the physical boards arrive.

## Product concept

Once a PCB has been sent to the factory but physical boards are still in transit, firmware teams often have to wait until the boards arrive before they can begin validation. Engineers add PCB layouts, netlists, BOMs, and key component documentation exported from KiCad or Altium to a project. The product reads chip pins, bus connections, and peripheral relationships, then generates a virtual hardware layer that firmware can call. Developers can compile real firmware in CI while the simulator returns predefined responses for GPIO, I2C, SPI, sensor interrupts, and common peripherals. The interface links every simulated behavior back to the schematic and component documentation, distinguishing what came from the design files from what still needs engineering input. For the first power-on check, it generates runnable test sequences for power, communications, and critical pins. When the boards arrive, the same tests can run through a debugger and instruments instead. The product separately flags cases that passed in simulation but failed on the physical board, helping teams determine whether the issue is a schematic assumption, soldering problem, or firmware timing error. The days saved in hardware shipping do not get lost again to hurried test-environment setup. The first version prioritizes common microcontrollers and standard interfaces. It does not promise accurate simulation of complex analog circuits, RF effects, or every proprietary chip. Its purpose is to make firmware testable earlier and give teams a ready-made acceptance path for the first power-on of the physical board.

## Why now (backed by facts)

On August 6, ProvenMetal’s Hacker News post on delivering circuit boards in days rather than weeks drew discussion; at the August 7 observation, it had 183 points, 129 comments, and ranked ninth. As lead times shrink, firmware teams are more likely to face a specific mismatch: the boards are not yet in hand, but the software schedule is already counting down.

## Direction (model inference, not independently verified)

Target user: Embedded teams with schematics in hand that have just sent a first-revision or revised PCB to fabrication. Hardware connectivity is largely frozen, but firmware interfaces have not yet been validated across the full board. Firmware leads need to surface pin, bus, and boot-order issues early. Hardware leads want tests to move to the physical board as soon as it arrives, rather than having to explain the entire schematic again.

Minimal entry point: Start with KiCad projects, plus netlists and BOMs exported from Altium. KiCad CLI can already export several netlist formats and an XML BOM, providing a stable entry point. After parsing, build a graph of components, pins, nets, and buses, then have engineers confirm the main controller, power domains, and critical peripherals. Rather than building a full simulator, generate Renode platform descriptions and a small set of peripheral stubs. The first release covers only GPIO, UART, I2C, SPI, and timer interrupts. Tests use a common scenario format: the simulation side calls models, while the physical-board side connects to a debugger and serial proxy. Complex analog circuitry, RF, and unmodeled proprietary components are marked for physical testing only.

The strongest case against: Design files describe connectivity, not how components actually behave under every input. When datasheets are incomplete, generated models can hide incorrect assumptions about timing, resets, and electrical behavior. Each additional microcontroller or proprietary peripheral requires maintained models, examples, and regression tests. If teams mistake a passing simulation for a hardware guarantee, they may take greater risks during the first power-on. Physical-board execution can also be affected by differences in debuggers, instruments, and fixtures, making truly seamless test portability difficult. If early projects require extensive manual modeling, configuration costs may erase the time saved waiting for boards.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Acquire initial users through GitHub projects for embedded CI, KiCad automation, and Renode. Publish a runnable example repository showing the full commit history from netlist to CI test to rerun on a physical board. Create public templates for common development boards so engineers can validate the workflow on familiar designs first. The Hacker News audience discussing rapid PCB fabrication can also be reached with specific board-level case studies.

## Competitors & gaps (model inference)

- Renode: Renode can run unmodified embedded software and emulate processors, peripherals, and sensors. It integrates with Robot Framework for CI testing and lets users extend peripheral models in Python or C#. For teams experienced in simulation, it is already a mature foundation. The gap is that engineers must still configure platform descriptions and peripheral behavior themselves. It does not turn the netlist, BOM, and component documentation for a PCB already in production directly into a project model. It also lacks a hardware-review-oriented interface that traces schematic connections, model assumptions, and test results. This product could use Renode behind the scenes while focusing on design-file import, prompts for missing information, and switching to physical-board testing.
- Wokwi: Wokwi offers simulation for microcontrollers and common components, along with a logic analyzer, virtual sensors, and custom-chip capabilities. Its CLI can run firmware locally or in CI and evaluate tests based on serial output. That makes it quick to bring Arduino, ESP32, and similar projects into repeatable testing. Its workflow still centers on project configuration and virtual wiring diagrams, requiring users to prepare the hardware description needed for simulation. It does not treat manufacturing schematics, netlists, and BOMs as primary inputs, nor does it explain the basis for each model assumption. Teams must also build their own reuse path once physical boards arrive. The opening is a workflow for professional PCB projects that puts design-data conversion, assumption review, and before-and-after board comparison in one test chain.

## How it makes money (model inference)

Team subscriptions tiered by the number of active hardware projects and parallel CI usage. The base plan covers common microcontrollers and standard peripherals; higher tiers add private device models, physical-board test agents, and self-hosted execution environments.

## Source context

Theme: ProvenMetal rapid PCB delivery
Trigger Hacker News post (original English): Launch HN: ProvenMetal (YC S26) delivers circuit boards in days instead of weeks
Heat at capture: ~183 points, 129 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Launch HN: ProvenMetal (YC S26) delivers circuit boards in days instead of weeks (https://news.ycombinator.com/item?id=49198464)
- KiCad Command-Line Interface (https://docs.kicad.org/7.0/en/cli/cli.html)
- Testing with Renode and Peripheral Modeling Guide (https://renode.readthedocs.io/en/latest/introduction/testing.html)
- Wokwi for CI and GitHub Actions (https://docs.wokwi.com/wokwi-ci/getting-started)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
