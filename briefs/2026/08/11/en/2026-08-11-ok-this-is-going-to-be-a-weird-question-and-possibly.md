---
title: "Dual-Screen App View Splitter"
date: "2026-08-11"
canonical: "https://raytally.com/en/ideas/2026-08-11-ok-this-is-going-to-be-a-weird-question-and-possibly/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Ok this is going to be a weird question and possibly impossible"
  observed_at: "2026-08-11T00:36:13.925Z"
sources:
  - url: "https://www.reddit.com/r/AynThor/comments/1vk70jp/ok_this_is_going_to_be_a_weird_question_and/"
    boundary: "Published at 2026-08-10T00:00:00.000Z. Observed at 2026-08-11T00:36:13.925Z."
  - url: "https://developer.android.com/media/grow/media-projection"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://developer.android.com/reference/android/accessibilityservice/GestureDescription.Builder"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://github.com/Thor-Wayfinder/thor-wayfinder"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-11-ok-this-is-going-to-be-a-weird-question-and-possibly/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Dual-Screen App View Splitter
On dual-screen handhelds, an unsupported Android app can be rearranged so video, comments, and other regions occupy the top and bottom screens as independently controllable views.

## Product concept

When users of dual-screen handhelds such as the Ayn Thor open a video app, they often want the video on the top screen and comments, a playlist, or chat on the bottom. Many Android apps still treat themselves as a single display, while standard split-screen shrinks the whole app and makes both video and comments difficult to use. After launching an app, the user selects “Expand Across Two Screens” and marks the two regions they want to separate. A local compositing layer crops the original app output into two independent viewports and scales them onto the top and bottom displays. The user can lock the video region to the top screen while scrolling comments independently below. Touch coordinates are mapped back to the original app according to each viewport’s crop ratio, so tapping a comment, dragging the seek bar, or opening a menu still operates the original app. Once configured, the layout is saved as a launch preset for that app. Users can keep “article text on top, table of contents below” for readers, or “stream on top, chat below” for livestreaming apps. If an app update shifts its controls, the product asks the user to reselect the regions rather than silently sending touch input to the wrong place. Initial support would focus on video, reading, and community apps, with shareable layout templates. It neither modifies app packages nor attempts to bypass protected video content. The point is to give the two screens already present on dual-screen devices distinct jobs, rather than waiting for every Android app to redesign its interface.

## Why now (backed by facts)

A post in r/AynThor on August 10, 2026 asked whether Homestuck’s images and text, or a YouTube video and its comments, could be split across the top and bottom screens; the comments offered no usable solution. As recorded on August 11, it had 4 points and 16 comments, showing how quickly the inability to split a single app’s regions arises when people use the Thor for web reading or video comments.

## Direction (model inference, not independently verified)

Target user: The first users are tinkering-oriented gamers and heavy readers who already own an Ayn Thor. While watching long videos, livestreams, or visual-text works, they frequently consult comments, chat, a table of contents, or the text itself. Standard split-screen shrinks the entire app and undermines the readability of the main content. This rearrangement is more valuable than opening two apps only when two regions within the same app are used together over time.

Minimal entry point: First, verify the logical display IDs for both screens on a physical Thor device. Use MediaProjection to capture the user-selected app’s output to a SurfaceTexture, then use OpenGL ES to crop the same texture into two regions. Each screen hosts its own rendering surface; store only the crop rectangles, scale ratios, and app version. The touch layer reverses the coordinate mapping from those rectangles, then sends gestures back to the selected display through AccessibilityService. Version one supports only single-finger taps, drags, and scrolling, not multi-touch zooming. Pause mapping for protected content, the keyboard, or system dialogs, and require the user to return to the original app.

The strongest case against: Continuous capture and dual rendering add battery drain, heat, and visual latency; long videos will expose these problems most clearly. MediaProjection also requires user consent, so launch presets cannot be entirely frictionless. Reliable touch mapping is harder still: dialogs, rotation, the keyboard, and shifting controls all change coordinates. Accidentally seeking through a video or pressing Send would quickly destroy trust. AccessibilityService also requires users to enable a permission, which will hurt installation conversion. After an app update, the product can only request that regions be selected again; it cannot guarantee that templates remain valid. If Thor’s display management restricts capture or gesture return, the core loop may be impossible with ordinary app permissions, so this must be verified on a physical device before further investment.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first testers are already asking for tools and discussing dual-screen apps in r/AynThor. Start with two or three reproducible templates, such as Homestuck reading, YouTube comments, and livestream chat. Include the supported version and a recording from a physical device with each template so users can decide whether installation is worthwhile. A public repair history when templates break can also drive ongoing search traffic and encourage users of other dual-screen devices to submit configurations.

## Competitors & gaps (model inference)

- Thor Wayfinder: Thor Wayfinder can send an app to the other display or swap apps between the top and bottom screens. It is triggered with a Back-button gesture and recommends Shizuku to preserve app state. The project also tracks which app is running on each screen. That solves the management problem of where an app should open. However, it still moves an entire app window rather than extracting two regions from one app. Video and comments cannot occupy separate screens, nor can text and images be scaled independently. The project also notes that some apps may crash, lose state, or refuse to move. The opening here is not faster screen switching, but keeping one app instance alive while providing two interactive partial views.

## How it makes money (model inference)

Sell the core split-view capability and basic templates as a one-time purchase. Later, offer separately priced template packs validated on real devices. Template authors must explicitly opt in before their community configurations are commercialized.

## Source context

Theme: Splitting Android app views across the Ayn Thor’s two screens
Trigger Reddit single-post demand observation: r/AynThor — Ok this is going to be a weird question and possibly impossible

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Ok this is going to be a weird question and possibly impossible (https://www.reddit.com/r/AynThor/comments/1vk70jp/ok_this_is_going_to_be_a_weird_question_and/)
- Media projection (https://developer.android.com/media/grow/media-projection)
- GestureDescription.Builder (https://developer.android.com/reference/android/accessibilityservice/GestureDescription.Builder)
- Thor Wayfinder (https://github.com/Thor-Wayfinder/thor-wayfinder)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
