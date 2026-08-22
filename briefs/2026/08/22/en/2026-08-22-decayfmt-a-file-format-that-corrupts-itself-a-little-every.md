---
title: "Digital Gifts That Fade with Every Opening"
date: "2026-08-22"
canonical: "https://raytally.com/en/ideas/2026-08-22-decayfmt-a-file-format-that-corrupts-itself-a-little-every/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Decayfmt – a file format that corrupts itself a little every time you open it"
  observed_at: "2026-08-22T00:33:14.683Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49390206"
    boundary: "Published at 2026-08-21T00:00:00.000Z. Observed at 2026-08-22T00:33:14.683Z."
  - url: "https://github.com/aravpanwar/decayfmt"
    boundary: "Observed at 2026-08-22T00:33:14.683Z."
  - url: "https://support.signal.org/hc/en-us/articles/360038443071-View-Once-Media"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://developers.cloudflare.com/r2/api/s3/presigned-urls/"
    boundary: "Published at 2026-04-24T00:00:00.000Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-22-decayfmt-a-file-format-that-corrupts-itself-a-little-every/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Digital Gifts That Fade with Every Opening
A shared, limited digital gift of photos, audio, or text that loses clarity for everyone each time someone opens it.

## Product concept

Some people want to give something other than a file that can be copied and saved forever: a gift that wears down through a shared experience. The sender places a photo, recording, or short note in a digital envelope, sets a total number of openings, and chooses how the work changes after each one. A photo progressively loses grain detail, an audio recording gradually picks up background hiss, and a text reveals fewer words. When recipients open the link, they do not download an original file. The service generates the version for that moment from a protected original, and deducts one shared opening only after it has been fully viewed or heard. Every recipient consumes the same pool of clarity, creating genuine small negotiations in a group of friends: who should open it next, and whether to wait until someone can be there to experience it together. The gift page keeps a restrained timeline showing when it was opened, how many openings remain, and what changed each time. Senders can specify what remains after the final opening: the blurriest photo, a recording reduced to its outline, or a letter missing a few key words. It suits birthdays, graduations, long-distance farewells, and private memories shared among several people. The first release supports browser-only viewing of images, audio, and text, while originals remain in an encrypted library controlled by the sender. It does not promise to prevent screenshots, screen recordings, or copying, and does not present degradation as a security mechanism. Instead, it offers a tangible shared act of consumption, making the opening itself part of the gift.

## Why now (backed by facts)

On August 21, Decayfmt became a working project built around the idea that every open causes permanent damage, and it reached Hacker News. As recorded on August 22, it had 44 points, 18 comments, and ranked 18th. The discussion makes it easier for people sharing digital gifts to notice that ordinary links can be copied indefinitely and that multiple opens do not affect one another, leaving such gifts without the ritual of shared consumption.

## Direction (model inference, not independently verified)

Target user: The core user is preparing a private gift for a birthday, graduation, or long-distance farewell. They have already chosen a photo, recording, or message, but a standard cloud-storage link feels like delivering a file. The gap is even clearer when several people are giving the gift together. They want recipients and friends to decide when to open it, and for every viewing to leave an irreversible trace.

Minimal entry point: The service must hold the state; a mutable counter cannot live in the link. Store originals in private object storage, upload directly from the browser through short-lived presigned URLs, and issue access credentials for a single action at a time. Each opening should first atomically reserve one allowance, then generate the corresponding version. Use Sharp for image downsampling, noise, and compression; FFmpeg to mix controllable background hiss into audio; and preset word positions to mask text. Do not support video or custom degradation algorithms in the first release. Offer only a small set of previewed transformation curves, and make concurrent reservations, playback-completion confirmation, and failure compensation reliable first.

The strongest case against: An incorrectly deducted opening can ruin the gift outright. Network interruptions, page refreshes, background preloading, and simultaneous opens can all make the allowance diverge from actual viewing. But if the count is deducted only at the end of playback, recipients can repeatedly leave early. Image loading completion is reasonably detectable; there is no dependable common standard for finishing an audio recording or reading a text. Screenshots, screen recording, and copying cannot be prevented, so even slightly overstated messaging will be mistaken for fake security. Storing originals, honoring deletion promises, and maintaining access logs also create privacy obligations. One erroneous notification or premature exhaustion is enough to make an entire group lose trust in the gift.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Early users are most likely to appear in graduation photo groups, long-distance friend groups, and birthday-planning groups. Offer public, no-signup sample gifts that let people open the same item repeatedly and watch it change. Keep a discreet product credit on the sharing page, so recipients can create a new gift directly after trying one. Independent photographers, sound artists, and digital card makers can also create transformation templates, using example works to drive long-tail sharing.

## Competitors & gaps (model inference)

- Decayfmt: Decayfmt has implemented “permanently corrupts with every open” as a working Rust file format. It supports images and text, with corruption speed controlled through filename parameters. The damage is written to disk before the file is shown, so every read carries a cost. But it relies on local files, with no recipients, shared allowance, or access timeline. Backups and hex editors can bypass its rules, and the project explicitly does not present itself as encryption or DRM. The current version does not support audio and has a race condition that can undercount corruption during concurrent opens. A digital-gift product can retain its irreversible experience while moving state back to the server. That makes it possible for multiple people to consume the same allowance and preserve a keepsake version after the final opening.
- Signal View Once Media: Signal’s View Once Media already keeps private photos and videos from remaining in a conversation after viewing. It works in one-to-one and group chats, and content is automatically deleted once opened. Senders cannot view it again after sending, while unopened media is also subject to timers or retention limits. This is designed to reduce traces, not create a shared memorial. Its core states are simply unseen and deleted; there is no gradual, opening-by-opening transformation. Nor does it offer a group-wide remaining count, a timeline of changes, or a final remnant. The opening here is to shift limited access from a privacy control into a group negotiation: recipients should see how their opening affects everyone who comes after them, rather than merely watching something disappear.

## How it makes money (model inference)

Charge per gift. Each purchase includes a gift with a shared opening limit, transformation rules, and a long-lived archive page. Images and text sit in the base tier; audio and longer retention periods cost more. Avoid subscriptions, since birthdays, graduations, and farewells are typically infrequent occasions.

## Source context

Theme: Decayfmt, a file format that damages itself on every open
Trigger Hacker News post (original English): Decayfmt – a file format that corrupts itself a little every time you open it
Heat at capture: ~44 points, 18 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Decayfmt – a file format that corrupts itself a little every time you open it (https://news.ycombinator.com/item?id=49390206)
- aravpanwar/decayfmt (https://github.com/aravpanwar/decayfmt)
- View Once Media (https://support.signal.org/hc/en-us/articles/360038443071-View-Once-Media)
- Presigned URLs · Cloudflare R2 docs (https://developers.cloudflare.com/r2/api/s3/presigned-urls/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
