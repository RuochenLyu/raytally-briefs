---
title: "Encrypted Contact Vault"
date: "2026-09-02"
canonical: "https://raytally.com/en/ideas/2026-09-02-google-deleted-all-my-contacts-looking-for-an-contact-app/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Google deleted all my contacts, looking for an contact app"
  observed_at: "2026-09-02T00:36:27.616Z"
sources:
  - url: "https://www.reddit.com/r/androidapps/comments/1w4k3fj/google_deleted_all_my_contacts_looking_for_an/"
    boundary: "Published at 2026-09-01T18:14:35.000Z. Observed at 2026-09-02T00:36:27.616Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-02-google-deleted-all-my-contacts-looking-for-an-contact-app/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Encrypted Contact Vault
An encrypted, cross-device contact vault that keeps private contacts out of the system address book while letting users call, message, and restore them from earlier versions.

## Product concept

After an accidental deletion through cloud sync—or simply to keep every social app from casually reading an entire address book—users can import contacts into a separate encrypted vault. The contacts are never written to the Android or iOS system address book, so even social apps permitted to read contacts cannot see this data. When users need to call, text, or open a chat app, they select the person from the vault. The product temporarily passes only the required number to that specific action, then revokes access when it is complete. Frequent contacts remain searchable by name, tag, and relationship, rather than requiring users to recognize a string of digits. Every addition, merge, and edit creates an encrypted version. After accidental deletion, a sync conflict, or the loss of a device, users can restore the vault to a point before a given change and see which device made it. Cross-device sync transfers ciphertext only; users retain the decryption key and recovery phrase. The first release covers contacts, groups, encrypted backups, and system-level calling and sharing entry points. It does not replace a work address book or promise to bypass every chat app’s permission restrictions. Its purpose is to let private contacts remain usable and recoverable after leaving the system address book.

## Why now (backed by facts)

A September 1 post on r/androidapps asked for a trustworthy cross-platform contacts app with isolated storage, optional encryption, no self-hosting, and no syncing to device contacts. Comments suggested Google Contacts, Simple Contacts, Universal Android Debloater, and SIM-card storage, but did not identify a trustworthy Android-and-iOS contact vault with its own storage, optional encryption, no self-hosting, and device-contact syncing disabled by default so other apps cannot access stored contacts. This is a single-post observation of user friction, not evidence of a trend or market size.

## Source context

Theme: A contact app after Google deleted my contacts
Trigger Reddit single-post demand observation: r/androidapps — Google deleted all my contacts, looking for an contact app

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Google deleted all my contacts, looking for an contact app (https://www.reddit.com/r/androidapps/comments/1w4k3fj/google_deleted_all_my_contacts_looking_for_an/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
