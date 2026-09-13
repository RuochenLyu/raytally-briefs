---
title: "Recover Photos That Failed to Import"
date: "2026-09-13"
canonical: "https://raytally.com/en/ideas/2026-09-13-failed-to-copy-photos-videos-error/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Failed to Copy Photos/Videos error"
  observed_at: "2026-09-13T00:34:29.948Z"
sources:
  - url: "https://www.reddit.com/r/PowerPhotos/comments/1wemywa/failed_to_copy_photosvideos_error/"
    boundary: "Published at 2026-09-12T20:14:22.000Z. Observed at 2026-09-13T00:34:29.948Z."
  - url: "https://support.apple.com/en-ie/guide/photos/phtae4e05c67/mac"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.fatcatsoftware.com/powerphotos/VersionedDocs/v9/PowerPhotosHelp.pdf"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://developer.apple.com/documentation/avfoundation/exporting-video-to-alternative-formats?changes=_1_2&language=objc"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-13-failed-to-copy-photos-videos-error/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Recover Photos That Failed to Import
When a photo migration triggers a copy failure, compare the source folder with Apple Photos, identify what is missing, repair incompatible files, and reimport only the failures.

## Product concept

When moving photos from an old hard drive into Apple Photos, the hardest part is not the failure itself but the vague “failed to copy” message. After the user selects the original photo folder and destination library, the product creates a comparison table: files that appear not to be in the library, same-named files with different contents, and files that already produce read errors. It does not reimport the entire collection. The user first reviews missing items grouped by date and folder, then retries imports in small batches. After each batch, the page retains lists of successful, still-failed, and unattempted files. If a file fails repeatedly, the user can see whether the issue is its format, corruption, path, or library write access. For legacy camera formats or videos that Photos cannot read, the app creates a compatible copy alongside the original and preserves metadata such as capture date and location where possible. Originals are never modified. The repaired copy returns to the comparison table, and only files confirmed to still be absent from the library proceed to the next import attempt, so users are not left guessing between duplicates and omissions. The initial release focuses on local Mac folders and Apple Photos libraries, with an exportable result record for every import. It never deletes photos from the library, automatically merges similar images, or attempts to fix iCloud sync failures. Simply identifying and filling in each failed file can replace the most painful option: starting the entire import over.

## Why now (backed by facts)

On September 12, 2026, someone posted in r/PowerPhotos after Apple Photos displayed “failed to copy” during a batch import, asking how to find the failed files and transcode them in bulk. As of September 13, the post still had a score of 1 and 0 comments, with no ready-made answer.

## Direction (model inference, not independently verified)

Target user: Household users organizing years of files from old hard drives, photography enthusiasts, and people migrating to a new Mac. They have decided to consolidate their files in Apple Photos, only to find that a few photos or videos are missing after a large import. The originals remain available, but rebuilding the library is not practical. They need a trustworthy list of omissions and a recovery path that leaves originals untouched.

Minimal entry point: The first release accepts only a user-selected local folder and a Photos library on the Mac. It builds a source-file index from file hashes, paths, and EXIF capture times, then reads visible items in the library to produce three lists: suspected omissions, content conflicts, and read failures. For images, macOS Image I/O can inspect file types, read metadata, and write compatible copies. For video, AVFoundation can assess export compatibility and create a new MOV or another target-format file using a fixed preset. Originals remain read-only, and repaired copies return to the comparison table. Each batch processes only files selected by the user and exports lists of successful, failed, and unattempted files.

The strongest case against: A photo library is not an ordinary folder: read state, write permissions, duplicate items, and iCloud settings can all make results hard to reproduce. Filename-only matching conflates renamed files, re-encoded files, and same-name conflicts. Transcoding can improve compatibility, but may change file size, encoding, and some metadata. A failed file may also be corrupted or inaccessible at its path, neither of which transcoding can fix. The product must preserve originals, record every attempt, and leave final confirmation to the user. Otherwise, one bad import can create fresh duplicates and erode trust.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users are already in communities such as r/PowerPhotos, where people discuss Apple Photos migrations. Short videos built around real error messages can show how a batch of failed files is identified, transcoded, and retried. The product page should directly target searches for “failed to copy,” “legacy format,” and “batch convert.” Offer a redacted sample failure report so users can judge whether it fits their own batch before committing.

## Competitors & gaps (model inference)

- Apple Photos: Apple Photos itself can import photos and videos from hard drives and other storage devices, while preserving folder organization. Users can import everything or preview and select individual files. But its import flow focuses on which items to add to the library, not on creating an auditable comparison between source files and imported items. After a “failed to copy” error, users still have to locate the original files, assess their formats, and reorganize the import themselves. It also offers no workflow for retrying failed items in batches or managing compatible copies. The opportunity is not to replace Photos, but to handle the verification, repair, and cleanup after an import fails.
- PowerPhotos: PowerPhotos already covers library copying, merging, deduplication, and import reports. Its operation reports can list the number of failed copies, and it supports rerunning interrupted operations while retaining processing results in logs. This shows that users will pay for more controlled library migration. Its core use case, however, remains copying or merging between Photos libraries rather than reconciling individual files in an old hard-drive folder against a destination library. Its documentation also treats missing, damaged, or incomplete items as files to skip, partially copy, or log as errors. A new product could turn failed items into a filterable queue, with format detection and side-by-side compatible copies. The distinction needs to stay this specific to avoid becoming another library manager.

## How it makes money (model inference)

One-time purchase: scan previews are free, while batch repair, transcoding, and result-report exports require payment.

## Source context

Theme: Failed photo and video imports
Trigger Reddit single-post demand observation: r/PowerPhotos — Failed to Copy Photos/Videos error

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Failed to Copy Photos/Videos error (https://www.reddit.com/r/PowerPhotos/comments/1wemywa/failed_to_copy_photosvideos_error/)
- Import from storage devices and DVDs in Photos on Mac (https://support.apple.com/en-ie/guide/photos/phtae4e05c67/mac)
- PowerPhotos Help (https://www.fatcatsoftware.com/powerphotos/VersionedDocs/v9/PowerPhotosHelp.pdf)
- Image I/O Programming Guide; Exporting video to alternative formats (https://developer.apple.com/documentation/avfoundation/exporting-video-to-alternative-formats?changes=_1_2&language=objc)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
