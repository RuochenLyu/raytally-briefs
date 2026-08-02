---
title: "Verify Video Callers First"
date: "2026-08-02"
canonical: "https://raytally.com/en/ideas/2026-08-02-halo-by-scam-ai/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Halo by Scam AI"
  observed_at: "2026-08-02T00:33:18.427Z"
sources:
  - url: "https://www.producthunt.com/products/scam-ai"
    boundary: "Observed at 2026-08-02T00:33:18.427Z."
  - url: "https://consumer.ftc.gov/articles/scammers-use-fake-emergencies-steal-your-money"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://developer.android.com/reference/android/service/quicksettings/TileService.html"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://support.google.com/googleplay/android-developer/answer/10964491"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-02-halo-by-scam-ai/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Verify Video Callers First
When a video call suddenly asks for money or a verification code, mute it first and verify the caller independently through a known number or family group.

## Product concept

When a parent receives a video call from someone claiming to be a relative who urgently needs money, a verification code, or screen sharing, the most dangerous window is often the few seconds before they have time to think. A persistent Verify First button on the phone lets them act immediately: tapping it mutes the current call and hides payment entry points and verification-code content. The app then starts an independent check through a pre-registered known phone number, family group, or backup contact. It asks the person to answer a question that does not appear in the current video call, such as a family-agreed phrase or a detail from their last meeting. The process collects only whether someone responded and the response itself; it does not record the full family conversation. It shows only three statuses: verified through an independent channel, the person denied making the request, or unable to verify for now. If verification is unavailable, the app gives an ordered next step: hang up, call back using the known number, then contact another relative. It does not push users toward risk with a vague score. Families can set protection rules for older relatives in advance, such as automatically showing the verification button when transfer-related keywords appear. The first version focuses specifically on high-risk requests during video or voice calls. It does not determine whether a face is AI-generated or decide whether a family should send money. Its role is to move verification out of the same call that may be impersonated before an irreversible action is taken.

## Why now (backed by facts)

As of August 2, Halo by Scam AI ranked 15th in Product Hunt’s new-product feed and focuses on determining whether the person in a video call is real. Its launch highlights a specific gap: even if the image looks like a relative, users still need to verify through a known number or family group before sending money.

## Direction (model inference, not independently verified)

Target user: The core users are parents who live alone or are not comfortable with phone security settings, and the adult children who support them remotely. The key moment is when a familiar face suddenly asks for money, a verification code, or screen sharing. Family trust and urgency compress the time available for judgment. Adult children need to preconfigure known numbers, a family group, and backup contacts so parents do not have to find someone to verify with in the moment.

Minimal entry point: Start on Android, with Verify First as a Quick Settings tile. TileService lets users trigger a shortcut action while remaining in their current app. Tapping it opens a full-screen protection screen that first covers verification codes and payment entry points. For supported calling apps, an accessibility service performs a fixed mute action; control rules are maintained separately for each app. Accessibility use must be clearly disclosed, and automation is limited to fixed flows triggered by the user. Identity checks are sent through pre-registered SMS deep links or family-group links. The backend stores only challenge status, response text, and expiry time. The first release supports a small number of calling apps, does not use a real-versus-fake face model, and does not access full call audio or video.

The strongest case against: A third-party calling app can change its interface, causing mute-control targeting to fail. If the product still indicates that the call is muted, it creates a more dangerous false sense of safety. A full-screen overlay only blocks what is currently visible; it cannot ensure that system notifications or another device will not expose a verification code. If a pre-registered number has changed, the request may reach the wrong person. If a family-group account is compromised, the independent channel can fail as well. Private questions sourced from social media may not be truly private. In a genuine emergency, a backup contact may not respond promptly, leading users to bypass the process. The product requires ongoing device compatibility maintenance and repeated testing of failure states.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Recruit the first users through adult children who manage their parents' phones. Position the product as a family anti-scam drill: an adult child sends a simulated loan request in the family group, and the older relative practices pressing Verify First. A results page can generate a setup checklist without private answers, making it easy to share with siblings. Short videos about setting up known numbers and backup contacts for parents are likely to drive more installs than broad messaging about deepfakes.

## Competitors & gaps (model inference)

- Halo by Scam AI: Based on its public positioning, Halo by Scam AI focuses on determining whether the person in a video call is real. It addresses the credibility of the image or identity, which is a direct response to synthetic-face and face-swap attacks. But if a real scammer has taken over a relative’s account, content detection may not stop a transfer request. Even with an accurate result, the user still has to decide whom to contact next. It also does not establish a family verification order using known numbers, a family group, and backup contacts. This proposal’s opening is to bypass real-versus-fake detection and move high-risk requests onto a separate channel. It does not need to prove that the image is fake; it only needs a response from the relative or another family member before money is sent. The trade-off is that verification speed depends on whether family members are available, and the product must handle no response and invalid numbers.
- Family passphrases and callbacks to known numbers: The FTC recommends slowing down when faced with an emergency request for money from a family member: call back using a known number, or ask a question only that person would know. This approach is free and works on any phone. It also does not depend on face or voice authenticity models. The gap is that, under pressure during a call, people often cannot remember the full process. A victim may also stay on the original call, allowing the caller to prevent them from contacting family. Answers to ad hoc questions drawn from social media may already be exposed. A callback alone provides no clear status, and a missed call can be mistaken for reassurance. This proposal turns the advice into a button, fixed contacts, and three outcomes. It can also hide verification codes and payment entry points first, reducing the chance of acting while listening. The key question is whether the added steps will feel burdensome enough that older users bypass them.

## How it makes money (model inference)

Charge a family subscription covering older relatives, adult children, and backup contacts, with an allowance for SMS confirmations. The basic verification flow is free; automated protection rules and additional family members are paid features.

## Source context

Theme: Video-call identity verification with Halo
Trigger Product Hunt launch: Halo by Scam AI — Know who’s real on every video call

This records only that the launch appeared in Product Hunt's public feed and when it was observed. The feed provides no vote count; do not describe feed order as popularity or market demand.

## Sources

- Halo by Scam AI (https://www.producthunt.com/products/scam-ai)
- Scammers Use Fake Emergencies To Steal Your Money (https://consumer.ftc.gov/articles/scammers-use-fake-emergencies-steal-your-money)
- TileService API reference (https://developer.android.com/reference/android/service/quicksettings/TileService.html)
- Use of the AccessibilityService API (https://support.google.com/googleplay/android-developer/answer/10964491)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
