---
title: "Train Window Slit-Scan Scroll"
date: "2026-08-19"
canonical: "https://raytally.com/en/ideas/2026-08-19-using-the-railway-network-as-a-flatbed-scanner/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Using the railway network as a flatbed scanner"
  observed_at: "2026-08-19T00:33:30.390Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49344825"
    boundary: "Published at 2026-08-18T00:00:00.000Z. Observed at 2026-08-19T00:33:30.390Z."
  - url: "https://philo.gay/linecam/"
    boundary: "Observed at 2026-08-19T00:33:30.390Z."
  - url: "https://apps.apple.com/us/app/stratum-slit-scan/id1525313915"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://play.google.com/store/apps/details?id=com.jp.koyoarai.SliceTimeCam"
    boundary: "Published at 2026-05-17T00:00:00.000Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-19-using-the-railway-network-as-a-flatbed-scanner/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Train Window Slit-Scan Scroll
Mount a phone beside a train window to turn continuous scenery into a scrollable, poster-ready panorama of the route.

## Product concept

As a train passes uninterrupted farmland, coastline, or the edge of a city, the view outside naturally lends itself to a single extra-long image. Yet passengers can usually take home only ordinary video: shake, station stops, and tunnels break the journey apart, while turning all that footage into a finished piece later means sorting through a large volume of material. The user mounts a phone by the window, chooses the framing height, and starts recording. Rather than saving a conventional landscape clip, the app takes a narrow pixel line from the center of each frame and stitches those lines together in train-travel order. It automatically compresses sections when motion is too slow and compensates for sudden acceleration, so ridgelines, platforms, and power lines are not stretched out of proportion. During recording, the interface resembles an unfurling paper scroll. Users can see the portion already created and tap once to mark a section to keep; sampling pauses when the train stops, enters a tunnel, or reflections on the glass become severe. After arrival, they can drag to remove cluttered sections, adjust the scroll’s orientation and height, and preview it as a hanging poster or an embedded web piece. The first version can focus on local video processing and a single horizontal scroll, designed for a phone fixed beside a train window. It does not promise to turn every window recording into cinematic footage. Instead, it makes a steadily moving train into a visual experiment that can be completed on the journey.

## Why now (backed by facts)

On August 19, this railway slit-scan experiment ranked 6th in Hacker News’s new submissions feed, with 388 points and 61 comments. In the discussion, passengers were already sharing that they use similar tools on trains, bringing the question of how to create a controllable route scroll to more creators.

## Direction (model inference, not independently verified)

Target user: The core user is a photography enthusiast traveling on a scenic railway, intercity train, or commuter line. Their one chance to make the work comes when they have a window seat and the scenery is about to unfold continuously. Ordinary video rarely conveys the full route, while editing afterward can exhaust the patience left after a trip. The tool suits people willing to secure their phone and make a few framing choices, as well as travelers who want to turn a journey into a poster, a long web image, or a keepsake.

Minimal entry point: At capture time, use the system camera to lock exposure, focus, and white balance, preventing continuous color banding as light changes through the glass. Keep only a narrow center strip from each frame for a low-resolution live preview. Store the original video or essential frames in the background, then generate the high-quality scroll after arrival. Use phone motion sensors as a prior for displacement estimation, then estimate global inter-frame motion with OpenCV feature points and optical flow. Pause sampling when the flow rate is too low, and flag sudden darkening as a possible tunnel. The first release should not attempt to automatically repair all parallax; offer segmented speed correction and manual keep markers instead. Support tiled rendering first so the full long image does not need to remain in memory.

The strongest case against: Train speed alone cannot determine the displacement of every object in the image. Nearby utility poles, distant mountains, and interior reflections move differently, so uniform stretching can still distort the subject. If stop detection responds too slowly, the same scenery can be repeated as broad bands of color. Tunnels, platform obstructions, and auto-exposure shifts can also leave visible seams. Live preview, original-video storage, and high-quality compositing will compete for compute, storage, and battery. Ultra-long images may also break memory limits, file formats, and sharing flows. If users still need extensive segment-by-segment adjustment after a single journey, the product becomes a professional post-production tool rather than casual creation. First validate whether common phones can reliably produce a scroll worth keeping at typical train speeds.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Reach initial users through railway photography, slow-travel, and experimental-photography communities. The most effective content is not a feature walkthrough but a side-by-side comparison of ordinary video and a finished scroll from the same route. Let users publish zoomable web scrolls carrying the route name and a creation-tool credit. Strong work can be collected into route-based online galleries, allowing people searching for particular train services, bridges, or coastal routes to encounter the product naturally. Publish mounting and window-reflection-reduction shooting templates as well, lowering the odds that a first attempt fails.

## Competitors & gaps (model inference)

- STRATUM Slit Scan: STRATUM offers real-time slit-scan capture on iPhone and iPad, with adjustable scan direction, slice size, exposure, and focus. It can also record the live composite as video, making it suitable for performances and visual experiments. Its product page emphasizes general time-displacement effects for people or any scene. It does not describe train-speed compensation, stop detection, or tunnel exclusion, nor does it show a route-based long-scroll editing workflow. The distinction should be the finished journey piece, not a larger filter set: previews should center on route progress, flawed sections, and poster cropping. The real bar is enabling ordinary passengers to produce a clearly structured route image without understanding slit-scan parameters.
- SliceTimeCam: SliceTimeCam captures slit-scan video on Android and lets users move the scan line and adjust filters, resolution, and slice size. It already covers the core appeal of instant creation and visual effects. Its official page recommends keeping the device steady, with examples focused mainly on people, animals, and vehicles. It does not explain how vehicle motion can preserve the proportions of scenery, or how to handle bad sections caused by stops, reflections, and tunnels. The opening is railway-specific automatic judgment and an output that shifts from an effects video to an inspectable route image. The editor should retain original time positions so users can quickly remove station stops and occlusions rather than hunt for them frame by frame in a conventional video editor.

## How it makes money (model inference)

A one-time paid download that unlocks all core recording and local export features. Poster-size templates and lossless ultra-long-image export can be sold as one-off premium packs, with no account or cloud subscription required.

## Source context

Theme: Using the railway network as a flatbed scanner
Trigger Hacker News post (original English): Using the railway network as a flatbed scanner
Heat at capture: ~388 points, 61 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Using the railway network as a flatbed scanner (https://news.ycombinator.com/item?id=49344825)
- Using the railway network as a flatbed scanner (https://philo.gay/linecam/)
- STRATUM Slit Scan (https://apps.apple.com/us/app/stratum-slit-scan/id1525313915)
- SliceTimeCam (https://play.google.com/store/apps/details?id=com.jp.koyoarai.SliceTimeCam)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
