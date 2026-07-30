---
title: "Mute Specific Videos on X"
date: "2026-07-30"
canonical: "https://raytally.com/en/ideas/2026-07-30-mute-specific-videos-on-x-like-muted-words/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "The hate he gets stems from misogyny and homophobia The hate he gets is from chewing fucking obnoxiously and then the video popping up everywhere on social media because people keep sharing it. I wish there was a way to mute a video in the same way you can mute words. Johnathan Irwin (@A2ZJIRWINKO) "
  observed_at: "2026-07-30T00:33:40.980Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-07-30-mute-specific-videos-on-x-like-muted-words/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Mute Specific Videos on X
Mute a video once on X, and its reposts, crops, and lightly edited variants are automatically collapsed in future feeds.

## Product concept

When an unwanted original video reappears in their X feed, the user selects “Mute this video” once from the post menu. The extension creates fingerprints of the selected visuals and audio locally, then replaces the original post with an expandable placeholder card that explains which personal rule it matched. When someone reposts the content from another account with a new title, cropped edges, mirrored footage, captions, or slight speed changes, the extension collapses it as the feed loads if it still contains the video. Users can choose to hide only the complete original or every version containing a particular clip, and set each rule to expire after seven days, one month, or never. A settings page lists hidden posts, allowing users to restore an individual post or delete an entire rule. Detection and matching happen on-device by default, without uploading full videos or viewing history; each placeholder retains the original post link for users who want to view it. The first version covers X feeds on desktop only, and a rule can be created only when the user personally selects a video. It does not decide what users should watch or mistake keyword muting for video recognition.

## Why now (backed by facts)

On July 28, X user @A2ZJIRWINKO documented a complaint that an unpleasant chewing video kept appearing everywhere as people repeatedly shared it, explicitly wishing for the ability to mute a specific video as one can mute words. The source also recorded 144 likes, 2 reposts, and 8,800 views accumulated since posting. This is a behavior observation with a clear source boundary that makes the use case for muting videos by content on X more concrete.

## Source context

Theme: Video-content muting on X
Trigger Web Trend observation: X @A2ZJIRWINKO — The hate he gets stems from misogyny and homophobia The hate he gets is from chewing fucking obnoxiously and then the video popping up everywhere on social media because people keep sharing it. I wish there was a way to mute a video in the same way you can mute words. Johnathan Irwin (@A2ZJIRWINKO) 
Source metric: 点赞 144 / 转发 2 / 浏览 8800 (发布后累计)

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
