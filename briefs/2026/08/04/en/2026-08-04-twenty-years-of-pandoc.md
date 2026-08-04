---
title: "Bring Word Tracked Changes Back to the Source"
date: "2026-08-04"
canonical: "https://raytally.com/en/ideas/2026-08-04-twenty-years-of-pandoc/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Twenty Years of Pandoc"
  observed_at: "2026-08-04T00:33:33.063Z"
sources:
  - url: "https://pandoc.org/twenty-years-of-pandoc.html"
    boundary: "Published at 2026-08-02T00:00:00.000Z. Observed at 2026-08-04T00:33:33.063Z."
  - url: "https://news.ycombinator.com/item?id=49156750"
    boundary: "Published at 2026-08-03T00:00:00.000Z. Observed at 2026-08-04T00:33:33.063Z."
  - url: "https://pandoc.org/MANUAL.html"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://sidedoc.io/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-04-twenty-years-of-pandoc/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Bring Word Tracked Changes Back to the Source
When an edited Word document comes back, map every change to the Markdown or LaTeX master, then regenerate each deliverable from the updated source.

## Product concept

People who write long documents in Markdown or LaTeX dread receiving a Word file covered in tracked changes from a client, only to end up treating the DOCX as the new master. The product takes the original source files from a text repository and the edited Word file, then maps them by headings, paragraphs, and neighboring sentences rather than forcing a character-position match. Tracked changes, comments, deletions, and paragraph moves are reconstructed as a reviewable set of patches. Authors can accept a wording change sentence by sentence, see where a passage was moved, or retain an editor’s note as a comment alongside the source. Changes whose location cannot be determined are listed separately with the original Word paragraph, so content is never changed silently in the wrong place. Once patches are confirmed, the product writes them back to the Markdown or LaTeX master and regenerates Word, PDF, and web versions from that same source. Each export retains the current editing version, making it easy for authors to show clients which feedback has been adopted and which points remain open. The first release focuses on body text, headings, footnotes, and ordinary comments. Complex tables, embedded graphics, and heavily manual formatting stay in a review queue, where the author can decide whether to reconnect them manually.

## Why now (backed by facts)

Pandoc’s twentieth-anniversary retrospective was published on August 2, bringing DOCX round trips and tracked-change recognition back into discussion. When observed on August 4, the post ranked 12th on Hacker News, with 88 points and 11 comments, making it easier for source-manuscript authors to encounter the problem of writing Word feedback back into their source files.

## Direction (model inference, not independently verified)

Target user: People maintaining long-form work in Markdown, Quarto, R Markdown, or LaTeX. After delivery, clients or collaborators will only make tracked changes in Word. By the time the file returns, the source repository may have moved on. The author needs to absorb the feedback without letting DOCX replace the buildable, traceable master.

Minimal entry point: Start with the original Markdown or LaTeX file and the DOCX returned by the client. Use Pandoc’s DOCX reader and `--track-changes=all` to extract revisions, comments, authors, and timestamps. Split the source into headings, paragraphs, sentences, and footnotes while retaining byte ranges. First narrow candidates by heading path and neighboring paragraphs, then use textual similarity to identify rewrites and moves. Patches modify only matched source ranges rather than rewriting the whole document. The first release supports Pandoc Markdown and consistently structured LaTeX; tables, drawing environments, and cross-paragraph comments go to manual review.

The strongest case against: A mistaken paragraph match can write valid wording into a similar but unrelated location. Repeated sentences, renamed headings, and moves across chapters make mismatches more likely in long documents. LaTeX macros, citation commands, and conditional compilation can also make visible text diverge from source. To prevent silent corruption, low-confidence changes must be confirmed one by one, reducing the time-saving feel of automation. If complex DOCX structures lose information during conversion, users must also maintain a manual-fix list. Ultimately, the product depends not on conversion success rates but on whether authors trust it enough to write patches back to the main branch.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Reach initial users through Pandoc, Quarto, R Markdown, and academic-writing communities. Release a local command-line version so users can test real papers and technical white papers against it. Use before-and-after examples to show comments, paragraph moves, and footnotes returning as Git commits. Then offer a GitHub Action that automatically generates a downloadable patch-review page when a DOCX arrives.

## Competitors & gaps (model inference)

- Pandoc with manual diffing: Pandoc can already read DOCX and preserve insertions, deletions, and comments with `--track-changes=all`. Reviewer names and timestamps also enter its intermediate representation, where filters can further process those nodes. It excels at format conversion and can generate DOCX, PDF, and web output from the same source. But its official workflow does not realign an edited DOCX with the original source file. Users must either accept the entire Word output or parse the markup and compare text themselves. Complex structures such as tables may also lose detail in conversion. The opening is paragraph-level correspondence, move detection, and item-by-item write-back while preserving the original repository files' local style.
- Sidedoc: Sidedoc already offers DOCX extraction, synchronization, diffing, and rebuilding. It separates body text, structure, styles, and assets into a `.sidedoc` directory, and supports attributed insertions and deletions. This covers many Word round-trip editing needs and supports a broader range of table and image fidelity. Its public workflow currently extracts content from DOCX and syncs it back into the Sidedoc document system. Comments and footnotes remain unsupported, and an existing Markdown or LaTeX repository is not an explicit starting point for the workflow. The opportunity is the asymmetric case where the source manuscript comes first and Word returns later, with uncertain matches left for the author to confirm.

## How it makes money (model inference)

Charge a per-project subscription that includes local processing, version retention, and a set number of active documents. Put complex tables, bulk migrations, and team review permissions on higher-tier plans.

## Source context

Theme: Pandoc’s twentieth anniversary
Trigger Hacker News post (original English): Twenty Years of Pandoc
Heat at capture: ~88 points, 11 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Twenty Years of Pandoc (https://pandoc.org/twenty-years-of-pandoc.html)
- Twenty Years of Pandoc (https://news.ycombinator.com/item?id=49156750)
- Pandoc User's Guide (https://pandoc.org/MANUAL.html)
- Sidedoc (https://sidedoc.io/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
