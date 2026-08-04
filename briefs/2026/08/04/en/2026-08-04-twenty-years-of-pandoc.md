---
title: "Bring Word Revisions Back to the Source"
date: "2026-08-04"
canonical: "https://raytally.com/en/ideas/2026-08-04-twenty-years-of-pandoc/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Twenty Years of Pandoc"
  observed_at: "2026-08-04T00:33:33.063Z"
sources: []
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-04-twenty-years-of-pandoc/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Bring Word Revisions Back to the Source
When an edited Word document comes back, map every revision to the Markdown or LaTeX master file, then regenerate each delivery format from the updated source.

## Product concept

People who write long-form documents in Markdown or LaTeX dread receiving a Word file covered in revisions from a client, only to end up treating the DOCX as the new master copy. They provide the product with source files from the original text repository and the edited Word file. Instead of forcing a character-by-character match, it maps headings, paragraphs, and neighboring sentences to one another. Tracked changes, comments, deletions, insertions, and moved paragraphs are reconstructed as a reviewable set of patches. Users can accept a wording change sentence by sentence, see where a passage was moved, or retain an editor’s note as a comment beside the source text. Changes whose location cannot be determined are listed separately with the original Word paragraph, preventing silent edits to the wrong content. Once the patches are confirmed, the product writes the changes back to the Markdown or LaTeX master file, then regenerates Word, PDF, and web versions from that same source. Each export retains the current editing version, so authors can show clients which feedback has been adopted and which remains under discussion. The first version focuses on body text, headings, footnotes, and standard comments. Complex tables, embedded graphics, and heavily manual formatting remain in a review queue, letting authors decide whether to reconnect them manually.

## Why now (backed by facts)

Discussion of “Pandoc Turns Twenty” is currently at No. 12 on the Hacker News front page, with roughly 88 points and 11 comments (August 4 snapshot; figures are approximate at the time observed). That concentrates attention on related use cases right now.

## Source context

Theme: Twenty Years of Pandoc
Trigger Hacker News post (original English): Twenty Years of Pandoc
Heat at capture: ~88 points, 11 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
