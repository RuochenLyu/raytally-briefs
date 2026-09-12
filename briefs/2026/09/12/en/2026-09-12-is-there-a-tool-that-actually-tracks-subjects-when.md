---
title: "Subject-Aware Auto Reframing"
date: "2026-09-12"
canonical: "https://raytally.com/en/ideas/2026-09-12-is-there-a-tool-that-actually-tracks-subjects-when/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Is there a tool that actually tracks subjects when reformatting video aspect ratios"
  observed_at: "2026-09-12T00:33:52.886Z"
sources:
  - url: "https://www.reddit.com/r/EntrepreneursGrind/comments/1wdwrzf/is_there_a_tool_that_actually_tracks_subjects/"
    boundary: "Published at 2026-09-11T00:00:00.000Z. Observed at 2026-09-12T00:33:52.886Z."
  - url: "https://helpx.adobe.com/premiere/desktop/add-video-effects/commonly-used-effects/add-auto-reframe-effect-to-a-sequence.html"
    boundary: "Published at 2026-04-15T00:00:00.000Z."
  - url: "https://ai.meta.com/research/sam2/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://developer.apple.com/documentation/professional-video-applications/describing-final-cut-pro-items-in-fcpxml"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-12-is-there-a-tool-that-actually-tracks-subjects-when/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Subject-Aware Auto Reframing
Editors converting landscape footage to vertical video get an editable camera path that follows the real speaker or action, while uncertain sections are flagged for human review.

## Product concept

When a short-form video editor converts a landscape interview, game, or livestream into vertical video, the hardest part is not cropping—it is keeping the frame on the wrong person. The user drops the video into a timeline, selects the main speaker, player, or current action, and the product generates an editable virtual-camera path. The path stays steady within a safe zone so it does not crop off heads or captions; when the system predicts that another person is about to speak or receive the ball, it also begins a smooth move in advance. Editors can drag key points on the timeline and adjust tracking strength and the safe zone. Every automated move remains editable camera-movement data rather than being baked into an irreversible crop. For conversations with multiple people, the editor can choose “prioritize the current speaker” or “keep everyone visible.” Action footage can follow a ball, car, hand, or another selected subject. When the subject is occluded, people overlap, the subject exits the frame quickly, or confidence drops sharply, the product stops making the decision automatically, marks the section for review, and shows the candidate subjects it detected. The first version focuses on common people and sports objects and outputs keyframe tracks that remain editable in Premiere, CapCut, or Final Cut. It does not handle captions, color grading, or the final edit.

## Why now (backed by facts)

A September 11, 2026 post on r/EntrepreneursGrind complained that after trying three landscape-to-vertical tools, the result was still just a centered crop; existing options had not reliably followed the speaker or action. As of September 12, the post had 2 points and 0 comments, and the problem surfaced at the delivery point where creators were converting landscape YouTube content into Reels.

## Direction (model inference, not independently verified)

Target user: The core users are editors who regularly reformat podcasts, interviews, courses, and sports footage for vertical video. They often receive Reels or Shorts deliverables only after the landscape master has been locked. At that point, captions, cuts, and pacing usually cannot be rebuilt, so they need to produce a reliable composition quickly. The longer the footage and the more often subjects change, the harder it is to finish shot-by-shot keyframing on deadline.

Minimal entry point: The technical core has three layers: subject tracking, shot planning, and export. After the user selects the subject in the first frame, SAM 2 propagates its mask forward. It supports point, box, and mask prompts and lets users correct the result in later frames. Interview footage then goes through offline speaker diarization, matched against face tracks. Shot planning generates only position, scale, and Bézier keyframes, with constraints for headroom, the caption area, and movement speed. The first version supports one subject and two-person interviews, but not catch prediction for arbitrary ball sports. Export starts with Final Cut Pro’s FCPXML format, which can describe a project timeline and lets applications exchange project data with Final Cut Pro.

The strongest case against: Speaker diarization and face matching can fail together, causing the camera to follow the wrong person continuously. If the system moves early toward the wrong next speaker, the finished video will contain an unexplained pan. Sports footage adds occlusion, cuts, and small fast-moving objects that are difficult for a single tracking model to cover. To reduce false positives, the system must retain confidence scores, candidate subjects, and edit history, increasing storage and interface complexity. Coordinates, scaling, and interpolation after FCPXML import also need validation across versions. If editors still have to watch all the footage, the time savings from automation fall sharply. Private interviews and unreleased sports footage may also restrict cloud processing, forcing the product to absorb the performance cost of local inference.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Find the first users among small editing teams that specialize in podcast clips, course distribution, and sports highlights. These teams handle repetitive footage and can directly compare the time required to reframe landscape video manually. Use the same multi-person interview to demonstrate centered cropping, automatic tracking, and the result after manual corrections. Then offer a small amount of free processing in exchange for failed sections and final keyframes, gradually covering the most common occlusion cases.

## Competitors & gaps (model inference)

- Adobe Premiere Pro Auto Reframe: Premiere Pro can duplicate a sequence, convert it to a target aspect ratio, and apply Auto Reframe. It offers three motion presets—Slow, Default, and Fast. Fast mode follows movement and generates more keyframes. When footage contains multiple points of interest or fast motion, editors still need to adjust keyframes manually. The current workflow mainly asks users to choose the frame shape and motion speed. Adobe’s documentation does not offer controls for selecting a lead subject, prioritizing the current speaker, or keeping everyone visible. It also does not isolate uncertain decisions or show the candidate subjects the system considered. Turn-taking interviews may still require a shot-by-shot review, while passes and fast exits in sports footage lack editor-facing ambiguity handling. The opportunity is to turn the result into a reviewable camera-movement track, so editors only handle genuinely ambiguous sections.

## How it makes money (model inference)

Charge a monthly per-seat subscription, with usage tiers based on the amount of video processed. The basic plan includes subject tracking and FCPXML export; higher tiers add team review, batch processing, and custom safe zones.

## Source context

Theme: Subject-aware video reframing
Trigger Reddit single-post demand observation: r/EntrepreneursGrind — Is there a tool that actually tracks subjects when reformatting video aspect ratios

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Is there a tool that actually tracks subjects when reformatting video aspect ratios (https://www.reddit.com/r/EntrepreneursGrind/comments/1wdwrzf/is_there_a_tool_that_actually_tracks_subjects/)
- Add Auto Reframe effect to sequences in Premiere (https://helpx.adobe.com/premiere/desktop/add-video-effects/commonly-used-effects/add-auto-reframe-effect-to-a-sequence.html)
- Introducing Meta Segment Anything Model 2 (SAM 2) (https://ai.meta.com/research/sam2/)
- Describing Final Cut Pro Items in FCPXML (https://developer.apple.com/documentation/professional-video-applications/describing-final-cut-pro-items-in-fcpxml)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
