---
title: "Editable Gaussian Strokes"
date: "2026-08-06"
canonical: "https://raytally.com/en/ideas/2026-08-06-painting-with-gaussians/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Painting with Gaussians"
  observed_at: "2026-08-06T00:33:22.015Z"
sources:
  - url: "https://yogthos.net/posts/2026-08-03-splat-painter.html"
    boundary: "Published at 2026-08-03T00:00:00.000Z. Observed at 2026-08-06T00:33:22.015Z."
  - url: "https://news.ycombinator.com/item?id=49182695"
    boundary: "Published at 2026-08-05T00:00:00.000Z. Observed at 2026-08-06T00:33:22.015Z."
  - url: "https://helpx-origin-uw2.aws116.adobeitc.com/fresco/desktop/draw-paint-animate-and-share/pixel-brushes.html"
    boundary: "Published at 2026-05-07T00:00:00.000Z."
  - url: "https://developer.mozilla.org/en-US/docs/Web/API/PointerEvent/pressure"
    boundary: "Published at 2025-11-03T00:00:00.000Z."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-06-painting-with-gaussians/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Editable Gaussian Strokes
Paint photos or sketches with Gaussian strokes that can be moved, tightened, and remixed at any time, producing editable illustrations that scale up cleanly.

## Product concept

Illustrators seeking a soft, hazy texture often keep smudging in conventional raster software, then have to erase and repaint when an edge lands in the wrong place. This canvas represents every mark as an oval color blob whose edges fade naturally. Start with a photo, a sketch, or a blank canvas, then build up color in mist-like layers. After a mark is placed, its color blob remains editable. Select it to drag its center, stretch its direction, tighten its diffusion, or reduce its opacity; nearby colors remix immediately, so facial cheeks, clouds, and plant edges do not need to be repainted. Layers show thumbnail collections of color blobs, making it easy to lock the background while adjusting only a few foreground strokes. The canvas offers two editing modes: Preserve Edges and Let Edges Diffuse. The first suits eyes, text, and architecture; the second suits light, shadow, and atmosphere. Users can also package groups of color blobs into reusable brushes for skin highlights, sunsets, or smoke. Export a standard image, or retain every adjustable stroke so the work can later be resized for a poster without turning blurry. The initial release focuses on 2D illustration and static posters, with tablet pressure support and common image imports. It does not automatically paint a photo for the user; it makes “I can still change this stroke after painting it” part of the painting process.

## Why now (backed by facts)

An open-source experiment released on August 3 demonstrated a Gaussian painting workflow with interactively adjustable parameters. As of August 6, the post ranked 17th in Hacker News’ new submissions feed, with 88 points and 14 comments, bringing the problem of raster brushstrokes being hard to reshape after placement into a concrete discussion.

## Direction (model inference, not independently verified)

Target user: Illustrators who regularly paint soft-lit portraits, plants, clouds, and atmospheric posters. It is most useful near the end of a piece, when a highlight, smoke effect, or background color blob is misplaced. At that point, the overall palette is settled, and erasing and repainting can leave visible breaks. Movable strokes preserve the existing blend while letting artists correct local shape and depth.

Minimal entry point: Store each mark as a 2D Gaussian object with its center, covariance, color, opacity, and layer order. Render with standard alpha-over compositing so color blobs occlude and blend in sequence. Use WebGL2 instancing to draw batches on the canvas while retaining stroke data in GPU buffers. The prototype should first support painting, selection, moving, scaling, rotating, and opacity adjustment. For tablet input, map Pointer Events pressure to blob size or opacity. Project files save object parameters and groups; exports rerender at the target size. Start contour protection with layer-level masks rather than rushing into automatic photo-to-paint conversion.

The strongest case against: As stroke counts grow, real-time remixing quickly increases GPU memory and rendering demands. Selecting within overlapping soft edges is also error-prone, requiring cycling selection, layer locks, and clear selection outlines. Moving a lower color blob changes all the blending above it, potentially creating a larger result than the user expects. If contour protection relies on masks, hair, leaves, and text edges will require extensive cleanup. A proprietary project format also creates migration costs, since common formats such as PSD cannot fully preserve these object semantics. If exports cannot reliably reproduce color and stacking order, the promise that work remains editable later loses credibility.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Recruit the first users from illustrators who publish tutorials on soft-lit portraits, plants, clouds, and mist. In short videos, contrast a single cheek highlight: a conventional canvas requires erasing and repainting, while this one lets the artist drag and tighten it directly. Offer downloadable sunset, skin-highlight, and smoke projects so creators can inspect each color blob and learn from it. Let exported work include optional attribution that leads viewers to the matching editable project.

## Competitors & gaps (model inference)

- Adobe Fresco: Adobe Fresco already offers pixel, live, and vector brushes. Its pixel brushes support hardness, spacing, angle, blend modes, stylus pressure, and natural blending with mixer brushes. It also supports reference images, layered editing, and PSD export, making it suitable for a full workflow from sketch to finished work. However, Adobe’s tutorials primarily use undo, erasing, and layers to fix line flaws. They do not describe a laid-down soft-edge pixel stroke as something that can be individually moved, rotated, or tightened to reduce its spread. Vector brushes preserve crisp lines, but they are not built around soft-edge color blobs that remix as they move. The opportunity is not more brushes, but making every soft-edge stroke a selectable object. Artists can reposition a cheek highlight or cloud edge without erasing and repainting it. The trade-off is that it is unlikely to replace Fresco’s full toolchain; it fits better as a specialized canvas or an upstream creation tool.

## How it makes money (model inference)

Sell it as a one-time-purchase desktop app, with paid upgrades for major future versions. The free version limits the number of editable projects and exports watermarked images. The paid version unlocks full project saving, watermark-free high-resolution export, and custom Gaussian-stroke brush packs.

## Source context

Theme: Gaussian painting
Trigger Hacker News post (original English): Painting with Gaussians
Heat at capture: ~88 points, 14 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Painting with Gaussians (https://yogthos.net/posts/2026-08-03-splat-painter.html)
- Painting with Gaussians | Hacker News (https://news.ycombinator.com/item?id=49182695)
- Pixel brushes and vector drawing in Adobe Fresco (https://helpx-origin-uw2.aws116.adobeitc.com/fresco/desktop/draw-paint-animate-and-share/pixel-brushes.html)
- PointerEvent: pressure property (https://developer.mozilla.org/en-US/docs/Web/API/PointerEvent/pressure)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
