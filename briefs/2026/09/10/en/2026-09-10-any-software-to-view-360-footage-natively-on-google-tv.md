---
title: "Living-Room 360 Raw Footage Player"
date: "2026-09-10"
canonical: "https://raytally.com/en/ideas/2026-09-10-any-software-to-view-360-footage-natively-on-google-tv/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Any software to view 360 footage natively on Google TV?"
  observed_at: "2026-09-10T00:33:57.022Z"
sources:
  - url: "https://www.reddit.com/r/360Cameras/comments/1wahcei/any_software_to_view_360_footage_natively_on/"
    boundary: "Published at 2026-09-08T00:00:00.000Z. Observed at 2026-09-10T00:33:57.022Z."
  - url: "https://developer.android.com/reference/androidx/media3/exoplayer/video/spherical/package-summary"
    boundary: "Published at 2026-06-24T00:00:00.000Z."
  - url: "https://onlinemanual.insta360.com/developer/en-us/resource/sdk"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://images.videolan.org/vlc/download-android.html"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-10-any-software-to-view-360-footage-natively-on-google-tv/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Living-Room 360 Raw Footage Player
Play native 360-camera files directly on Google TV and use the remote to look around in real time, without exporting or casting.

## Product concept

After returning from a trip with a 360 camera, users connect the camera’s memory card, a USB drive, or home network storage to Google TV. The player recognizes native 360 video from devices such as Insta360 cameras, stitches it and renders it as a sphere on the TV, with no need to first export a long flat video. The family can sit down in the living room and immediately open the original footage from that dive, ski trip, or birthday party. During playback, the remote’s directional pad controls where viewers look: left to see what a child is doing, up toward the mountaintop, or Select to hold the current view. Remotes with gyroscope support can also change the camera direction with a turn of the wrist. Users can leave one or two view markers at memorable moments, then later jump in one tap to fixed views such as “look toward the fireworks” or “follow the cyclist.” Viewers can switch between free exploration and automated camera moves. On the first playback, the system uses voices and motion in the footage to generate a small set of suggested views; whenever the family wants to look for details themselves, they can take back control with the remote. Each marker can be saved as a short link, so distant friends or relatives opening the same footage begin from the same direction. The initial release supports Google TV, USB, and local-network files, covering the most common native 360 formats. It does not offer cloud editing or social uploads. The focus is making the living-room TV a panoramic window the whole family can take turns turning.

## Why now (backed by facts)

A September 8 post in r/360Cameras asked how to play native Insta360 footage directly on Google TV while changing the viewing direction in real time. Comments suggested YouTube, phone casting, VLC, and Vr-mediaplayer, but a native option that avoids export and is controlled directly by the TV remote is still missing.

## Direction (model inference, not independently verified)

Target user: 360-camera owners returning from a trip, sporting event, or family gathering. The footage has just come home, the family is already gathered around the TV, and no one wants to learn editing software or wait for an export. They do not want a finished video yet; they want to revisit the moment immediately, taking turns steering the view to find people and details. This also includes users who keep raw footage on USB drives or home storage.

Minimal entry point: Start with a native Google TV app that uses Media3 to decode standard panoramic MP4 files. Its spherical component can render video in a rotatable GL scene. Map the remote’s directional pad to yaw and pitch, and use Select to record a timestamp and viewing direction. Access USB files read-only through the system file interface, and support SMB only for local-network storage in the first release. Use the Insta360 Android Media SDK for native INSV files; it provides preview, display, stitching, and export capabilities, but requires an application for access. Enable support model by model based on testing with the approved SDK rather than claiming universal file compatibility. Initially, automated camera moves should generate only a small set of candidate views, with gyroscope-remote support added later.

The strongest case against: Native-file playback first runs into the application and licensing terms for manufacturer SDKs. Even with an Android SDK, it cannot be assumed that every Google TV device will run reliably. Differences in TV chipsets, hardware decoding, memory, and USB read speeds can amplify stuttering and heat issues. Camera models may also use different file combinations, lens parameters, and stabilization data. Incorrect stitch orientation or visible seams are more glaring on a large living-room screen. Maintaining a compatibility list and running regression tests on real devices will take ongoing development time. If automated views repeatedly focus on the wrong subject, they will interrupt family viewing and erode trust in the player.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first testers are already in r/360Cameras, r/Insta360, and camera-model communities. Demonstrate the difference between phone casting and opening the same raw clip directly on a TV, especially the ability to steer with the remote. Invite users to submit clips that fail to play, collecting only device model, file format, and error logs. Organize the app-store listing around specific search terms such as INSV, 360 video player, and Google TV, and publish a compatible-device list.

## Competitors & gaps (model inference)

- VLC for Android TV: VLC has an Android TV version and explicitly supports 360 video. In the thread, it was recommended for playing converted 360 videos. That solves big-screen replay once users have exported a panoramic MP4, but there is no evidence that it can parse native Insta360 files directly. Its documentation also does not confirm that a TV remote can continuously control the viewing direction. Users still need to stitch or convert footage first and determine whether the projection is correct. The opening is a single TV-native workflow for raw-footage recognition, real-time stitching, spherical rendering, and remote-controlled navigation. View markers could further differentiate the product from a general-purpose player for family rewatching.
- YouTube and Insta360 phone casting: Common options suggested in the thread are uploading 360 videos to YouTube or casting directly from the Insta360 mobile app. YouTube works well for already-exported standard 360 video and makes footage accessible to distant family and friends. Direct casting from a phone avoids export, with the phone handling stitching and view control. Neither approach keeps both the library and interaction fully on the TV. The first adds export and upload steps and does not suit people who simply want to watch raw footage at home. The second still depends on a connected phone, its processing power, and the casting session; the TV is only a display. The opportunity is to use a USB drive or home storage as the direct source and make the remote the primary controller. Short links need only save the timestamp and viewing direction, not upload the video.

## How it makes money (model inference)

Sell it as a one-time purchase per TV device. The base price covers local playback, remote-controlled viewing, and view markers. New camera-format support and automated camera moves can be offered as paid upgrades, with no charge based on footage volume.

## Source context

Theme: Native 360 playback on Google TV
Trigger Reddit single-post demand observation: r/360Cameras — Any software to view 360 footage natively on Google TV?

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Any software to view 360 footage natively on Google TV? (https://www.reddit.com/r/360Cameras/comments/1wahcei/any_software_to_view_360_footage_natively_on/)
- androidx.media3.exoplayer.video.spherical (https://developer.android.com/reference/androidx/media3/exoplayer/video/spherical/package-summary)
- Insta360 SDK Guide (https://onlinemanual.insta360.com/developer/en-us/resource/sdk)
- Official Download of VLC media player for Android (https://images.videolan.org/vlc/download-android.html)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
