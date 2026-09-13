---
title: "Guest-Voted Projection Wall"
date: "2026-09-13"
canonical: "https://raytally.com/en/ideas/2026-09-13-voxelwall/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "VoxelWall"
  observed_at: "2026-09-13T00:33:34.639Z"
sources:
  - url: "https://www.producthunt.com/products/voxelwall"
    boundary: "Published at 2026-09-13T00:33:34.639Z. Observed at 2026-09-13T00:33:34.639Z."
  - url: "https://developer.apple.com/documentation/screencapturekit"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://app.synesthesia.live/docs/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://magicmusicvisuals.com/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-13-voxelwall/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Guest-Voted Projection Wall
For a small Mac-and-projector party, beat-reactive visuals let guests scan a QR code to vote on the next color palette, which takes over as the next music segment begins.

## Product concept

At a small living-room gathering, friends often connect a Mac to a projector only to loop a preset video. This product opens as a projection wall that changes with the music in the room. The host chooses the visual density and several base palettes; the Mac captures beats from its audio input, and blocks of color, lines, and particles rise and fall with the drums. A QR code remains in the corner of the wall. When guests scan it, they do not enter a complicated color-grading tool; they see three or four color combinations for the next visual segment. Voting opens briefly before each song ends, and the winning palette takes over when the next track begins. Participants immediately see their choice appear on the wall, without taking turns at the host’s computer. The host can lock a color family to prevent a jarringly bright look and set a cap on participants in each voting round. The projection shows the active palette and a countdown to the next round; phones show only voting buttons, with no registration or photo uploads required. When the music pauses, the visuals naturally dim into a low-brightness standby state rather than continuing to flash across the room. Start with one Mac, one projector, and phones on the same local network, focusing on beat-driven graphics and round-based voting. The first release will not support collaborative song requests, livestreaming, or a professional stage-control positioning. The goal is to give any small gathering, within minutes, a wall that everyone can change together.

## Why now (backed by facts)

VoxelWall’s product page was created on September 10, 2026, and ranked seventh in Product Hunt’s new-product feed when observed on September 13. That makes Mac audio-driven visuals a newly visible entry point, while leaving room in party settings for a product that gives guests control over the visuals.

## Direction (model inference, not independently verified)

Target user: The user is someone organizing a small gathering, typically with a Mac and projector. When the music is ready but the visuals can only loop a video, the room can feel less participatory. This usually happens once friends have arrived and the host no longer wants to operate a computer. Guests need no visual-software knowledge: they scan, choose a color, and see that choice shape the next visual segment.

Minimal entry point: Build a native fullscreen Mac projection app. Start with ScreenCaptureKit for system-audio capture, then use FFT and beat detection to extract low-frequency energy, transients, and overall loudness. Render blocks, lines, and particles in Metal, beginning with a small set of stable, parameter-controlled preset scenes. Do not build a native voting app: the QR code opens a local-network web page. Local HTTP and WebSocket connections push voting results to the Mac. Version one supports only one Mac, one projection output, and devices on the same local network, addressing disconnect notices, vote cutoffs, and dimming when music pauses first.

The strongest case against: Audio sources at projected events vary widely, and system-audio permissions, output devices, and beat detection can all fail. Incorrect beat detection makes visuals feel sluggish, while overreaction can create harsh flashing. Group voting also introduces vote manipulation, duplicate submissions, and congestion in the final seconds. The QR code must be prominent without damaging the projected image. The product has to balance stable host control with immediate guest feedback; otherwise, voting becomes an extra chore. For users who simply want to play a video, existing options are cheaper and easier.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Early users will include people hosting birthday parties, board-game nights, and small house parties in rented spaces. Make 30-second live demos centered on a scan changing the colors for the next music segment immediately. Place a free trial in Mac party, projection, and DJ communities so people can bring it to their next event. Local event planners and projector-rental providers could also offer single-event licenses with branded palettes.

## Competitors & gaps (model inference)

- Synesthesia: Synesthesia already turns live audio into performance-ready visual scenes. It targets VJs, musicians, and creative coders, with support for custom GLSL scenes. Users need to learn scene creation to achieve reliable performance results. Guest participation is not a default workflow: mobile voting, QR-code entry, and automatic color changes for the next track would all need to be assembled by the host. It is more a live-visual instrument than an interactive party installation. The opportunity is to move visual control from a skilled operator to everyone in the room.
- Magic Music Visuals: Magic Music Visuals supports audio, MIDI, OSC, video, and 3D models. It can run fullscreen performances and map sound to geometry, shaders, and video effects. Those capabilities suit professional shows, but require module configuration, asset preparation, and live setup. Most casual party hosts want to choose a few color palettes and let the visuals follow the music. Magic does not make voting rounds, participant limits, and palette locks part of a party workflow. This product can preserve controlled visual quality while hiding creative complexity behind preset scenes.
- Looping video and projection software: The conventional approach is to prepare a looping video and play it fullscreen through projection software. It is reliable: visuals do not suddenly lose control when audio fluctuates. But guests cannot affect what comes next, and the host must edit and organize assets in advance. Even Mac tools with audio-reactive visuals usually keep participation on the computer. This product does not need to match professional VJ software in depth. It only needs to combine a QR code, color voting, and beat-driven visuals into a party flow that starts in minutes.

## How it makes money (model inference)

Sell the Mac app as a one-time purchase with core visual scenes and party voting. Later, offer theme packs or one-off event licenses for venues.

## Source context

Theme: VoxelWall
Trigger Product Hunt launch: VoxelWall — Music-reactive live wallpapers for Mac

This records only that the launch appeared in Product Hunt's public feed and when it was observed. The feed provides no vote count; do not describe feed order as popularity or market demand.

## Sources

- VoxelWall — Music-Reactive Live Wallpapers for Mac (https://www.producthunt.com/products/voxelwall)
- ScreenCaptureKit (https://developer.apple.com/documentation/screencapturekit)
- Synesthesia Docs (https://app.synesthesia.live/docs/)
- Music Visualizer, VJ Software & Beyond (https://magicmusicvisuals.com/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
