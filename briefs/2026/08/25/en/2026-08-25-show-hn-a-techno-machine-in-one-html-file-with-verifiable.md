---
title: "HTML Remix Relay"
date: "2026-08-25"
canonical: "https://raytally.com/en/ideas/2026-08-25-show-hn-a-techno-machine-in-one-html-file-with-verifiable/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Show HN: A techno machine in one HTML file, with verifiable renders"
  observed_at: "2026-08-25T00:33:22.985Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49419351"
    boundary: "Published at 2026-08-24T00:00:00.000Z. Observed at 2026-08-25T00:33:22.985Z."
  - url: "https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://support.soundtrap.com/hc/en-us/articles/115002725805-How-to-Restore-Previous-Project-Versions-in-Soundtrap"
    boundary: "Published at 2026-07-29T00:00:00.000Z."
  - url: "https://soundation.com/studio-tools/collaborate"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-25-show-hn-a-techno-machine-in-one-html-file-with-verifiable/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

HTML Remix Relay
A single runnable HTML file carries the instruments, stems, and version lineage of a remote remix, so the next musician can open it and keep creating immediately.

## Product concept

Musicians collaborating remotely often send a beat as audio, but struggle to hand the project, sounds, and rationale for changes to the next person. This product packages an electronic-music sketch as a single HTML file. Open it in a browser to play it offline; its synth settings, beat grid, and current stems remain inside the file. After dragging in vocals, drums, or a melody, a creator can adjust tempo, loop length, and effect settings, then export a new version. The recipient does not need the same software or plug-ins: they can double-click the file to listen, revise it, and carry the track forward. Each part appears as a small toggleable track, so the next collaborator can see what still needs overdubs and what has been locked. Every export records a parent-version fingerprint, the editor’s notes, and rendering parameters. Anyone opening the new file can trace which version it came from or return to any earlier version and branch again. Competition submissions or class assignments can also include verification information showing which set of rules and parameters rendered the final audio. The first release offers four-track loops, a basic synthesizer, audio import and export, and an offline version chain. It does not aim to be a full recording-studio application. Its first job is to make an idea a runnable work file that friends can repeatedly open, revise, and send back.

## Why now (backed by facts)

On August 24, a techno machine contained in a single HTML file appeared on Hacker News. As of August 25, it ranked 13th on the Show HN feed with 156 points and 29 comments; portability, installation-free use, and reproducible rendering were central to the discussion.

## Direction (model inference, not independently verified)

Target user: The core user is an electronic musician working across time zones who has just received a beat and wants to build on it before the idea fades. Installing software, finding plug-ins, or chasing down the correct project version is the last thing they want. Music teachers and competition organizers also fit: when collecting assignments or submissions, they need playable work, parameters, and edit provenance together.

Minimal entry point: Build the four-track audio graph with the Web Audio API. Browsers already provide source nodes, filters, compression, and precise scheduling. Read dropped audio bytes through the File API. Store project state as normalized JSON embedded in the exported HTML. Assets can be encoded into the file, though the first release should cap both duration and total size. On export, compute SHA-256 hashes for the state, assets, and parent fingerprint. Use OfflineAudioContext for offline rendering. The verification page should first validate inputs, parameters, and the version chain; it should not promise byte-identical audio across browsers. Keep the scope to four tracks, loops, and basic effects. Defer real-time collaboration, plug-in compatibility, and unlimited undo.

The strongest case against: Embedding audio assets in HTML can make files large quickly. Email, chat apps, and browsers may reject them or slow down as a result. Browser differences in decoding and audio implementation can also create rendering variations. If it is presented as verifiable audio, inconsistent bytes would directly undermine trust. A safer initial promise is verification of the assets, parameters, and processing chain. External vocals and samples also raise licensing and privacy issues. Once a file is forwarded, the original creator may have no way to retract its assets. Version trees can become hard to follow after repeated branching. And if users ultimately return to a professional DAW for mixing, the need to reorganize stems can erode the convenience.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Reach early users through browser-instrument, single-file software, and electronic-music communities. Launch with a downloadable HTML track that people can continue remixing, not just a demo video. Then run a timed remix relay in which participants submit their own forked files. A version tree can generate a static showcase page so creators can compare divergent directions publicly. Course templates can spread it among educators, with every assignment carrying its provenance and parameters by default.

## Competitors & gaps (model inference)

- Soundtrap: Soundtrap already offers browser recording, virtual instruments, and mixing tools. It supports real-time collaboration, chat, video, and timeline comments, while project changes are automatically saved to the cloud. Paid plans can also display earlier versions and save an old version as a separate project. That experience suits teams producing together online over time. Its documentation emphasizes cloud projects, invited collaborators, and audio downloads. There is no evident self-contained, offline-transferable project file. Recipients still need access to the platform and its project-permission system. HTML Remix Relay fills the gap in asynchronous file handoffs: the work state, assets, and parent version travel with the attachment. It does not replace a full studio; it reduces the coordination required around accounts, plug-ins, and project formats.
- Soundation: Soundation is a cloud-based collaborative studio in the browser. It supports audio and MIDI uploads, along with synthesizers and effects. Collaborators can see one another’s actions in the same project in real time, and projects can be shared through invitations or public links. These capabilities cover online co-creation and full-song production. But its core unit is still a shared project hosted on the platform. Its official site does not show a downloadable, self-contained editing project. A broken link, changed permission, or offline setting can interrupt the handoff. HTML Remix Relay makes the work itself the collaboration vehicle: recipients can inspect the tracks and edit history as soon as they receive the file. Its advantage is not feature breadth, but durable preservation and transfer across tools. The trade-off is strict limits on track count, asset size, and effects.

## How it makes money (model inference)

Use a one-time creator purchase. Receiving, listening, and continuing a remix stay free; paid unlocks add verifiable version chains and higher file-size limits.

## Source context

Theme: Electronic music machine in a single HTML file
Trigger Hacker News post (original English): Show HN: A techno machine in one HTML file, with verifiable renders
Heat at capture: ~156 points, 29 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Show HN: A techno machine in one HTML file, with verifiable renders (https://news.ycombinator.com/item?id=49419351)
- Web Audio API (https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
- How to Restore Previous Project Versions in Soundtrap (https://support.soundtrap.com/hc/en-us/articles/115002725805-How-to-Restore-Previous-Project-Versions-in-Soundtrap)
- Online music collaboration in real-time (https://soundation.com/studio-tools/collaborate)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
