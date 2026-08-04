---
title: "Choreography-Controlled Electronic Music"
date: "2026-08-04"
canonical: "https://raytally.com/en/ideas/2026-08-04-gesture-live/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "gesture.live"
  observed_at: "2026-08-04T00:33:33.524Z"
sources:
  - url: "https://www.producthunt.com/products/gesture-live"
    boundary: "Observed at 2026-08-04T00:33:33.524Z."
  - url: "https://developers.google.com/edge/mediapipe/solutions/vision/pose_landmarker/web_js"
    boundary: "Published at 2026-05-28T00:00:00.000Z."
  - url: "https://unhands.app/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.algoriddim.com/gesturecontrol"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-04-gesture-live/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Choreography-Controlled Electronic Music
After a dancer demonstrates key movements, the system turns arm raises, turns, and crouches into real-time control of tracks and effects in a live electronic set.

## Product concept

Dancers, live performers, and music teachers often already have a complete movement routine in rehearsal, yet still need to free up a hand to tap a controller. They import stems such as drums, vocals, and ambience, then demonstrate key movements—for example, raising an arm to bring in vocals, turning to lengthen reverb, or crouching to lower the bass. The product identifies poses that are easy to confuse across the full rehearsal and defines more stable body regions for each control movement. It overlays gesture-recognition results on rehearsal video, showing which turn could accidentally trigger a track or when a hand is too far from the camera. Users can replace unreliable movements with clearer poses, then choose whether each trigger switches, fades, or briefly applies an effect. During performance, the camera tracks only the confirmed movement regions. A simple status bar at the edge of the screen shows the active tracks and what the next movement will change. Afterward, users can review a timeline of movements and musical changes to find the smoothest passages and the moments most prone to mistakes. The first version can support one performer, a fixed camera position, and four common music controls. It outputs a saveable track configuration, so the same choreography can be recalled in the next rehearsal or on stage.

## Why now (backed by facts)

As observed on August 4, gesture.live ranked third in Product Hunt’s new-product feed. More creators are therefore encountering camera-based hands-free music control, making them more likely to recognize the disruption of interrupting choreography to tap a controller.

## Direction (model inference, not independently verified)

Target user: Solo dancers, live performers, and music teachers who already have a complete choreography and are moving a rehearsal version to the stage or classroom. Their movements are hard to change at this point, but they still need to switch tracks and adjust effects. Repeated rehearsals with a fixed camera also give the system opportunities to calibrate and catch errors.

Minimal entry point: Build for the browser with MediaPipe Pose Landmarker, which returns body landmarks and visibility from video. Start with one performer, a fixed camera, and the full body in frame. Users record several examples of each movement. The system normalizes landmark sequences and compares their similarity, then uses leave-one-out validation to identify confusable movements and stable joints. Performance mode is limited to four controls, such as switching and fading. Output goes through local MIDI, while audio remains in the user’s existing DAW.

The strongest case against: One accidental trigger can ruin an entire performance. Similar turns, loose clothing, and body occlusion can all alter landmark detection. Lighting, camera height, and stage distance can also make a rehearsal configuration fail. Reducing these risks requires repeated recording and calibration, which may take longer than using a foot pedal. Continuously showing confidence levels may distract performers. Professional users will not hand over critical controls without a predictable fallback mode.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Recruit the first users through choreography teachers and live electronic performers. Create before-and-after clips using the same dance routine to show accidental triggers. Public demos should emphasize rehearsal diagnostics rather than generic gesture-control spectacle. Offer downloadable Ableton track configurations so users can try the product with work they already have.

## Competitors & gaps (model inference)

- Unhands: Unhands already lets users control a DAW with camera-detected movement. It supports custom gestures, MIDI mapping, and calibration, and users can save gesture sets for different songs. That already covers the core flow for general-purpose gesture control. The opening is rehearsal for choreography, not more mapping options. The product needs to identify similar movements within a full routine and flag occlusion, out-of-frame, and accidental-trigger risks. Trigger rules should be tied to body regions and phases of movement. Diagnostics overlaid on rehearsal video must also make choreography revisions easy. If it cannot do these reliably, users will choose the more general tool.
- Algoriddim Gesture Control: Algoriddim’s Gesture Control already offers hands-free operation. Its built-in gestures can control scratching, loops, effects, and transitions. It suits performances designed around DJ operations. Because its movement vocabulary is predefined, it has a lower learning curve. The opening is for dancers who already have a complete routine and do not want to re-choreograph it. The product can let them select control movements from the routine, compare the accidental-trigger risk of similar turns or arm raises, and save region constraints separately for each track. It does not need to replace DJ software; it should output reliable control signals. If it merely copies fixed gestures, its differentiation will quickly disappear.

## How it makes money (model inference)

Charge per track configuration. The free tier saves one configuration for rehearsal use. The paid tier unlocks more tracks, performance mode, and video review.

## Source context

Theme: Performing live electronic music with camera gestures
Trigger Product Hunt launch: gesture.live — Play live electronic music with your hands using your webcam

This records only that the launch appeared in Product Hunt's public feed and when it was observed. The feed provides no vote count; do not describe feed order as popularity or market demand.

## Sources

- gesture.live (https://www.producthunt.com/products/gesture-live)
- Pose landmark detection guide for Web (https://developers.google.com/edge/mediapipe/solutions/vision/pose_landmarker/web_js)
- Unhands - a browser-based, gesture-driven MIDI controller (https://unhands.app/)
- Gesture Control (https://www.algoriddim.com/gesturecontrol)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
