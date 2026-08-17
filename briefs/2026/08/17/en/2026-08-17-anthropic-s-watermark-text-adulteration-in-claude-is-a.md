---
title: "AI Edit Approval, Line by Line"
date: "2026-08-17"
canonical: "https://raytally.com/en/ideas/2026-08-17-anthropic-s-watermark-text-adulteration-in-claude-is-a/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Anthropic's 'Watermark' Text Adulteration in Claude Is a Perversion of Writing"
  observed_at: "2026-08-17T00:33:16.293Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49324087"
    boundary: "Published at 2026-08-16T21:53:43.000Z. Observed at 2026-08-17T00:33:16.293Z."
  - url: "https://daringfireball.net/2026/08/anthropics_watermark_text_adulteration_in_claude_is_a_perversion_of_writing"
    boundary: "Published at 2026-08-16T00:00:00.000Z. Observed at 2026-08-17T00:33:16.293Z."
  - url: "https://developers.google.com/workspace/docs/api/how-tos/suggestions"
    boundary: "Published at 2026-07-21T00:00:00.000Z."
  - url: "https://support.microsoft.com/en-US/Word/accept-or-reject-tracked-changes-in-word"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-17-anthropic-s-watermark-text-adulteration-in-claude-is-a/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

AI Edit Approval, Line by Line
A writing plugin that turns AI polishing into individually approvable text patches, preventing silent full-draft rewrites and hidden-character contamination.

## Product concept

When writers hand a nearly finished article to AI for polish, they usually want only a few better turns of phrase, not a passage silently replaced wholesale. For contracts, submissions, and public statements especially, they need to know where every surviving change came from. The editor plugin reads only the paragraph the user selects and requires the model to return suggestions as patches. Original and proposed text appear side by side, with deletions, replacements, and additions highlighted in separate blocks. Writers can accept or reject one sentence at a time, or edit manually before requesting the next suggestion. The AI can never overwrite the entire draft directly. After each acceptance, the plugin scans for invisible Unicode characters, anomalous formatting, and control characters introduced through copying. The change log retains the original sentence, acceptance time, and final text, while export can produce a clean version. When an editor or legal reviewer asks, the writer can account for each change they approved. An early version would provide a patch panel for browser writing contexts and common document editors, supporting polishing, shortening, and tone changes. It does not judge facts for the writer or replace collaborative approval; it simply turns AI editing into a sequence of visible, reversible text choices.

## Why now (backed by facts)

On August 16, an article argued that Claude’s text watermark could influence wording choices, making authorship of polished language a concrete concern. As of August 17 at 00:33 UTC, the post ranked 10th, with 121 points and 99 comments.

## Direction (model inference, not independently verified)

Target user: The core user is preparing to submit a contract, manuscript, or public statement. At this stage, the text is nearly final, and its facts and positions usually cannot be rearranged. They want AI to refine only a few phrases, but must verify that every word still reflects the intended meaning. When editors, legal teams, or clients ask where changes came from, they need a record of line-by-line approval rather than an unexplained rewritten draft.

Minimal entry point: The browser extension first reads the current selection and stores a hash of the original text. The model must return structured patches containing an anchor snippet, replacement text, and a brief rationale. The frontend uses text diffs to split patches into independently approvable sentence blocks. Before writing, it verifies the selection and hash again to prevent misalignment after the document changes. A separate control-character scan reports only actual code points and formatting anomalies. The first release covers standard web text fields, then integrates with Word’s revision APIs. Google Docs' API for writing suggestions remains in developer preview and can be supported later.

The strongest case against: An invisible-character scan can easily be mistaken for watermark detection. Claude’s described approach does not add hidden characters; it leaves statistical signals through word choice. Removing control characters can therefore address copy-and-paste contamination, but cannot verify or remove this kind of watermark. Footnotes, links, and comments in rich text also make patch anchoring fragile. Writing to the wrong location after a selection changes could directly damage a contract or statement. Models may also fail to report changes; a structured response does not make its content trustworthy. Retaining original sentences and acceptance times accumulates sensitive text, creating encryption, retention, and deletion costs. If the product cannot clearly distinguish character hygiene from watermark assessment, it will quickly lose users' trust.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users can come directly from the writers and developers in this Hacker News discussion. Build a no-login selection-diff demo that lets users see a full-paragraph rewrite broken into individual choices. Plugin-store listings should foreground before-and-after views of contract clauses and public statements. Then publish technical posts using anonymized edit samples to explain which characters are cleaned up and which watermarks cannot be detected.

## Competitors & gaps (model inference)

- Microsoft Word Track Changes and Document Inspector: Word already marks insertions and deletions and lets reviewers accept or reject them one at a time. Its Document Inspector can also find hidden text and other information. These capabilities work well for human collaboration and can handle externally generated revisions. The gap is that AI requests happen in a separate workflow: users still have to copy a passage, prompt a model, and paste the result back. If the model returns a full rewrite, Word can show the resulting diff but cannot constrain the scope of changes. Nor does it preserve the relationship among the prompt, original selection, and model patch. This product can connect pre-generation constraints with post-generation approval, tying every write to a text block the user explicitly accepted.
- Google Docs Suggesting mode: Google Docs Suggesting mode preserves edits as pending changes. Its official API can read suggestions inline, while creating suggestions and accepting or rejecting suggestion threads remain in developer preview. That gives a plugin a document-native interface to build on. Existing Suggesting mode primarily addresses how collaborators submit edits; it does not require a model to return only the smallest patches within a selection. Users can still paste a fully rewritten passage into a document and then inspect each difference. Suggestion threads are not a complete record of AI revisions, either. The product opportunity is to retain the request, original sentence, patch, and final written result. Even if the platform API fails, unapproved text must not enter the body of the document.

## How it makes money (model inference)

Monthly per-seat subscription. The free tier includes basic sentence-by-sentence approval and local undo. Paid tiers add cross-document history, audit exports, and team policies. Users can supply their own model keys so inference costs do not consume the subscription margin.

## Source context

Theme: Claude watermarking and writing-tampering debate
Trigger Hacker News post (original English): Anthropic's 'Watermark' Text Adulteration in Claude Is a Perversion of Writing
Heat at capture: ~121 points, 99 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Anthropic's 'Watermark' Text Adulteration in Claude Is a Perversion of Writing (https://news.ycombinator.com/item?id=49324087)
- Anthropic’s ‘Watermark’ Text Adulteration in Claude Is a Perversion of Writing (https://daringfireball.net/2026/08/anthropics_watermark_text_adulteration_in_claude_is_a_perversion_of_writing)
- Work with comments and suggestions (https://developers.google.com/workspace/docs/api/how-tos/suggestions)
- Accept or reject tracked changes in Word (https://support.microsoft.com/en-US/Word/accept-or-reject-tracked-changes-in-word)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
