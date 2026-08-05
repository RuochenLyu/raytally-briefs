---
title: "Character Skin-Tone Palette Plugin"
date: "2026-08-05"
canonical: "https://raytally.com/en/ideas/2026-08-05-show-hn-simple-algorithm-and-color-space-to-generate-diverse/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Show HN: Simple algorithm and color space to generate diverse skin tones"
  observed_at: "2026-08-05T00:33:30.316Z"
sources:
  - url: "https://news.ycombinator.com/item?id=49170165"
    boundary: "Published at 2026-08-04T15:16:22.000Z. Observed at 2026-08-05T00:33:30.316Z."
  - url: "https://toneyalexander.github.io/inclusive-color-space/"
    boundary: "Observed at 2026-08-05T00:33:30.316Z."
  - url: "https://developer.adobe.com/photoshop/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://colourconstructor.com/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-05-show-hn-simple-algorithm-and-color-space-to-generate-diverse/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Character Skin-Tone Palette Plugin
After an artist sets the visual style and lighting, the plugin generates diverse character skin-tone palettes that preserve highlight and shadow relationships and stay legible across backgrounds.

## Product concept

An illustrator selects a character’s baseline skin tone and specifies whether the scene is set at noon, under warm indoor lighting, or at night. The plugin reads the character’s existing highlight, midtone, and shadow relationships, then generates multiple skin-tone options across different depths and warm-cool balances. Each option preserves the same lighting logic rather than mechanically lightening or darkening the original color. Artists can overlay candidate colors directly on the character’s face, hands, and full body to see whether they remain distinct from the hair, clothing, linework, and background. If a color becomes hard to read in a night scene, the plugin identifies whether the background is too similar, the shadows are too heavy, or the line contrast is insufficient. Once an option is chosen, daylight, warm-light, and night versions are generated together so the character stays consistent across scenes. The first release serves 2D character illustration and delivers editable palettes and scene variants. It does not define a character’s identity or automatically repaint facial features and materials; artists can still adjust any color frame by frame.

## Why now (backed by facts)

On August 4, an algorithm for generating diverse skin tones reached Hacker News. When observed on August 5, it had 454 points and 85 comments and ranked No. 2, so more creators may experiment with it for character color design.

## Direction (model inference, not independently verified)

Target user: Freelance illustrators, comics colorists, and small game art teams working with established characters. It is most useful when a finalized character must move into night scenes, warm indoor lighting, or scenes across multiple chapters, where reworking skin tones affects shadows, linework, and separation from the background. Users need to preserve the original style while comparing multiple skin-tone options quickly.

Minimal entry point: Launch as a Photoshop UXP panel, built with JavaScript, HTML, and CSS. Users select a baseline skin tone and identify the skin-tone and linework layers. Candidate ranges can draw on the project’s published TUV-to-RGB equations. Colors are then transferred in groups according to the source image’s highlight, midtone, and shadow differences. Previews are created as new editable layers rather than overwriting the original artwork. The first release covers only noon, warm indoor light, and night, and exports a palette plus three variant sets.

The strongest case against: If skin areas are not separated into their own layers, cleaning up selections can consume substantial time before the workflow begins. Hair occlusion, blush, and reflected light can also contaminate color sampling. The original algorithm is based on subjective labels, and its author does not treat the results as an authoritative standard. Real skin is also shaped by blood flow, pigmentation, and local variation. Different displays and ambient lighting change what artists see as well. Overemphasizing numerical consistency could erase deliberately exaggerated colors. If conflict warnings produce frequent false positives, users will return to manual color testing. Before proceeding, validate layer conventions, night scenes with deep skin tones, and cases with strongly colored light.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Find the first users among participants and sharers in this Hacker News discussion. Publish reproducible character recoloring examples that compare the same character under three lighting conditions. Then invite skin-tone tutorial creators and character-design artists to contribute anonymized test artwork. Distribution should also show failure cases openly, especially misclassifications against dark backgrounds and heavy shadows.

## Competitors & gaps (model inference)

- Colour Constructor 2: Colour Constructor 2 already lets users set lighting and view color changes in real time. It offers skin-tone presets, scene previews, and tone mapping. Results can be exported as ASE or PNG, or copied into drawing software. It also supports custom objects and includes Blender templates. Its public feature set is oriented more toward a standalone workspace for color and lighting experiments. It does not state that it reads a character’s existing highlight, midtone, and shadow relationships, nor that it can compare candidate colors in place on the face, hands, and full body. The opening is to preserve the source artwork’s layer relationships while performing character-level color transfers. The plugin should also identify the specific conflict in the background, shadows, or linework. That makes the output a diagnostic result that can be applied back to the artwork, rather than another set of isolated swatches.

## How it makes money (model inference)

Sell it as a one-time purchase that includes the Photoshop plugin and core scene presets. Offer artist-made lighting packs and background-check templates separately, without charging per generation.

## Source context

Theme: Diverse skin-tone generation algorithms and color spaces
Trigger Hacker News post (original English): Show HN: Simple algorithm and color space to generate diverse skin tones
Heat at capture: ~454 points, 85 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Show HN: Simple algorithm and color space to generate diverse skin tones (https://news.ycombinator.com/item?id=49170165)
- What Colors Are We? Constructing A Good Enough Color Space For Skin Tones (https://toneyalexander.github.io/inclusive-color-space/)
- Photoshop APIs for developers and scripters (https://developer.adobe.com/photoshop/)
- Colour Constructor 2 (https://colourconstructor.com/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
