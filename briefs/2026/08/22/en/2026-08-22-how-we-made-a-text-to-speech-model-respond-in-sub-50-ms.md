---
title: "Speak While You Type AAC Board"
date: "2026-08-22"
canonical: "https://raytally.com/en/ideas/2026-08-22-how-we-made-a-text-to-speech-model-respond-in-sub-50-ms/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "How we made a text-to-speech model respond in sub-50 ms"
  observed_at: "2026-08-22T00:33:14.683Z"
sources:
  - url: "https://nari-labs.com/blog/qwen3-tts-speed-cost-frontier/"
    boundary: "Published at 2026-08-19T00:00:00.000Z. Observed at 2026-08-22T00:33:14.683Z."
  - url: "https://news.ycombinator.com/item?id=49389952"
    boundary: "Published at 2026-08-21T15:51:10.000Z. Observed at 2026-08-22T00:33:14.683Z."
  - url: "https://developer.apple.com/documentation/AVFAudio/AVSpeechSynthesizer"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://apps.apple.com/us/app/proloquo4text-aac/id751646884"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-22-how-we-made-a-text-to-speech-model-respond-in-sub-50-ms/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Speak While You Type AAC Board
An AAC speech device that starts voicing a settled phrase before the sentence is finished, while keeping unsaid words editable so synthesized speech can keep pace with face-to-face conversation.

## Product concept

People who use speech-generating devices in face-to-face conversation often know what they want to say; the problem is that entering a whole sentence and then playing synthesized speech takes so long that the topic has already moved on. A low-latency speech model lets the device begin speaking once a phrase is settled. For example, when the user types “I want to,” the device can speak that opening while the rest of the sentence remains editable on screen. The user selects words through touch, eye gaze, or a keyboard, and the device speaks committed text with natural pauses. The unsaid tail remains editable, like a message still being composed. If the user changes “a drink” to “a break,” the portion already spoken is not replayed; the following audio simply continues as the new sentence. If someone interrupts, the user can hold a pause button to stop speech and immediately prepare a response. The interface divides each sentence into what has already been spoken and what can still be rewritten, with a subtle progress indicator showing where the audio is. Frequently used phrases can be added to a personal phrasebook, while speaking rate, pauses, and pronunciation are set by the user. Caregivers and conversation partners can see that the person is still composing, rather than rushing to speak for them or move on. The first release supports typed text and touch-selected words, with the work focused on changing words mid-sentence, pausing, and resuming speech. It does not diagnose language impairments or predict what users want to say. Its purpose is to turn synthesized speech from playback of a finished statement into a voice that can take part in real conversational turns.

## Why now (backed by facts)

On August 19, Nari Labs released an open-source Qwen3-TTS implementation with response time under 50 ms, making phrase-level streaming speech a technical path that can be tested directly. On August 21, the implementation reached Hacker News and was still under discussion as of August 22, as developers began evaluating its viability for real-time speech and consumer devices.

## Direction (model inference, not independently verified)

Target user: Primarily AAC users who can compose sentences with a keyboard or touch input. It is especially suited to rapid-turn conversations in classroom discussions, work meetings, and family arguments, when users know what they want to express but lose their chance to enter the conversation before a full sentence is complete. Caregivers and conversation partners also need to see that someone is still forming a sentence, so they do not speak for them or change the subject too soon.

Minimal entry point: Start with a landscape iPad app offering only keyboard input and touch-based word tiles. Split text state into a spoken prefix, a queued-to-speak segment, and an editable tail. After a pause or punctuation mark, submit a short phrase chunk. The backend can run Nari Labs’ open-source Qwen3-TTS implementation and stream audio back. The playback layer tracks the start and end of each phrase chunk and permits deletion only for chunks that have not yet been sent. Use AVSpeechSynthesizer’s established pause, resume, and queue-clearing semantics as a control reference. The first testing round should validate only word changes, interruptions, and continued speech—not prediction, eye gaze, or a complex phrasebook.

The strongest case against: Committing a phrase too early can speak words the user has not settled on, and speech cannot truly be taken back. Commit too late, and the product returns to waiting for whole sentences, losing its value. Splitting a sentence into audio chunks can also create problems with pauses, emphasis, and voice continuity. Network jitter may cut speech off mid-sentence, while cloud synthesis introduces privacy concerns and ongoing compute costs. When a user rewrites the tail after pausing, the system must precisely distinguish played audio from audio that is merely buffered. Any mismatch can cause omitted words, replayed speech, or a reversal of meaning. Repeated testing with AAC users is necessary before real-world use, because incorrect prompts or speech will quickly erode trust.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Recruit AAC users who can type through TestFlight, prioritizing people who regularly take part in classes, meetings, or family discussions. Demo materials should directly contrast full-sentence playback with incremental speech in a real interruption or turn-taking scenario. Share testing invitations in AAC communities, assistive-technology forums, and speech-language therapist networks. In each session, record only where phrases were committed too early and where users still waited too long, then adjust phrase boundaries accordingly.

## Competitors & gaps (model inference)

- Proloquo4Text: Proloquo4Text already covers the core text-based AAC workflow, including single-screen typing, common phrases, word prediction, playback, pausing, and speak-as-you-type. It can also determine where to begin reading from the cursor position and highlight text as it is spoken. Users may not switch solely to speak sooner, because the established product already handles many everyday details. Its public materials do not confirm a finer-grained state model in which the spoken prefix is locked while the unspoken tail remains editable. Nor do they say whether, after an edit, later audio can continue naturally without replaying what was already spoken. The opening is not ordinary speak-as-you-type, but explicitly binding the commit boundary, audio position, and editable range. If that difference is not clear in real conversation, a standalone product will struggle against existing phrasebooks, offline capability, and personalized voices.

## How it makes money (model inference)

Monthly subscription covering low-latency cloud speech and personal phrasebook sync. Schools and rehabilitation providers pay annually per device seat, with a basic offline voice retained so users are not left without speech when connectivity drops.

## Source context

Theme: Sub-50 ms text-to-speech
Trigger Hacker News post (original English): How we made a text-to-speech model respond in sub-50 ms
Heat at capture: ~97 points, 24 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Pushing the Speed-Cost Frontier for Qwen3-TTS (https://nari-labs.com/blog/qwen3-tts-speed-cost-frontier/)
- How we made a text-to-speech model respond in sub-50 ms (https://news.ycombinator.com/item?id=49389952)
- AVSpeechSynthesizer (https://developer.apple.com/documentation/AVFAudio/AVSpeechSynthesizer)
- Proloquo4Text AAC (https://apps.apple.com/us/app/proloquo4text-aac/id751646884)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
