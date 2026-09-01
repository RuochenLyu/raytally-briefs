---
title: "Offline Video On-Deck Queue"
date: "2026-09-01"
canonical: "https://raytally.com/en/ideas/2026-09-01-video-player-with-reserve-next-video-function/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Video Player with Reserve Next Video function?"
  observed_at: "2026-09-01T00:36:00.185Z"
sources:
  - url: "https://www.reddit.com/r/androidapps/comments/1w3vu1y/video_player_with_reserve_next_video_function/"
    boundary: "Published at 2026-09-01T00:00:00.000Z. Observed at 2026-09-01T00:36:00.185Z."
  - url: "https://developer.android.com/media/media3/exoplayer/playlists"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://mpv.io/manual/master/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://kodi.wiki/view/Settings/Media/Videos"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-01-video-player-with-reserve-next-video-function/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Offline Video On-Deck Queue
While one local video plays, a separate on-deck queue lets operators search, order, and temporarily insert multiple files, then continues automatically through the queue.

## Product concept

Karaoke hosts, teachers, and event video operators are often handed the next song or another clip before the current video has finished. They cannot interrupt the full-screen output, yet must browse folders, remember the order of requests, and make a rushed switch at the end. This offline player moves on-deck work to a separate sidebar while the current video keeps playing. Hosts can search local files, preview thumbnails, and add multiple videos in succession. Each queued item is a draggable card showing file duration, audio tracks, and estimated playback time. A last-minute request can be marked as a one-time insert: it plays after the current clip, then the player automatically returns to the original queue. To skip a segment, the operator changes only the queue, without risking the projected image. Files likely to fail playback are flagged before their turn, leaving time to swap in backup material. After an event, the queue can be exported as a reusable playlist or retained as a record of who requested which clip and when. The first release starts with local folders and common video formats, with no streaming song requests or cloud collaboration. It addresses a specific live-use problem: handling a steady flow of next-video requests calmly while one offline computer keeps playing video.

## Why now (backed by facts)

A September 1, 2026 post in r/androidapps asked whether multiple local videos could be queued while the current video is playing. When recorded that day, the comments had not identified an existing solution, leaving an unmet need for an editable offline on-deck queue.

## Direction (model inference, not independently verified)

Target user: The primary users are karaoke hosts, classroom teachers, and small-event video operators. They need an on-deck sidebar when a video is already output full-screen and someone hands them the next clip. Opening a new file directly can interrupt the image, while managing the order from memory can cause clips to be missed. Remote and touchscreen use also demands few controls and an unambiguous sequence.

Minimal entry point: Build the first release as a landscape Android app in Kotlin and Jetpack Compose, with a playback area and fixed on-deck sidebar. Use Media3 ExoPlayer as the playback engine; it supports adding, moving, removing, and replacing items during playback. Let the app read user-selected local files through system directory permissions. Keep the original queue and one-time inserts as separate business-layer state rather than merging them into one list. Read thumbnails and durations one file at a time in the background, checking files that are about to play first. Exclude streaming, accounts, and cloud sync; export playlists as local files first.

The strongest case against: Recognizing a local file does not guarantee smooth playback at an event. Unusual containers, corrupted files, or hardware-decoding differences may only surface when playback switches. Checking every file in advance adds battery use, waiting time, and cache-management overhead. If a one-time insert resumes at the wrong position, the rest of the queue shifts out of order. Full-screen output and sidebar focus must also be isolated, or remote-control buttons may accidentally trigger playback controls. When event logs include requester information, users must be able to disable and clear them. Unless recovery from failures is simple enough, this kind of tool will struggle to earn trust in live settings.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users are already active in offline-player, Android app, and home karaoke communities. Demonstrate the workflow in a real landscape screen recording: video keeps playing while clips are added in the sidebar, then a one-time insert plays and the original queue resumes. Return to the original help post to collect feedback on file formats and remote-control use. App store copy built around “queue the next video without interrupting the current one” should better match related searches.

## Competitors & gaps (model inference)

- mpv and its script-based front ends: mpv already offers comprehensive playlist commands: it can append files, insert them as the next item, move entries, and delete entries. Adjusting the queue does not have to stop the current playback, making it a viable playback engine. Its JSON IPC also lets external programs control playback and receive events. But these are command-level capabilities. Developers still need to build file search, thumbnails, drag-to-reorder, and estimated start times. One-time inserts require separate state management and restoration of the original queue after playback. Failure preflight, safeguards against accidental actions, and event logs also need to be built separately. The gap is not decoding capability, but a complete control desk for live operators.
- Kodi temporary playlists: Kodi can add selected videos to a temporary playlist and open that playlist from the sidebar. It can also read file details such as duration, audio tracks, and codecs. These capabilities work well for organizing content in a media library ahead of time. But the official documentation centers on browsing pages and sidebars, so a live operator must switch among finding files, checking the queue, and monitoring playback. The documentation also does not describe request sources, estimated start times, or one-time insert behavior. This product can consolidate those actions in a persistent on-deck panel. The current image stays stable, and queue edits do not become playback controls. Reusable playlists and failure alerts further fit classroom and event playback.

## How it makes money (model inference)

Use a one-time purchase model. The base version includes local playback, queue ordering, and playlist export; the premium version unlocks dual-screen output, queue templates, and full event logs.

## Source context

Theme: Editable offline video queueing
Trigger Reddit single-post demand observation: r/androidapps — Video Player with Reserve Next Video function?

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Video Player with Reserve Next Video function? (https://www.reddit.com/r/androidapps/comments/1w3vu1y/video_player_with_reserve_next_video_function/)
- Playlists | Android media (https://developer.android.com/media/media3/exoplayer/playlists)
- mpv Reference Manual (https://mpv.io/manual/master/)
- Settings/Media/Videos (https://kodi.wiki/view/Settings/Media/Videos)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
