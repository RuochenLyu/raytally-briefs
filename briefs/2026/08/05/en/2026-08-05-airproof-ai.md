---
title: "Purifier Placement Test"
date: "2026-08-05"
canonical: "https://raytally.com/en/ideas/2026-08-05-airproof-ai/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "AirProof AI"
  observed_at: "2026-08-05T00:33:30.726Z"
sources:
  - url: "https://www.producthunt.com/products/airproof-ai"
    boundary: "Observed at 2026-08-05T00:33:30.726Z."
  - url: "https://airproofai.com/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.epa.gov/sites/default/files/2018-07/documents/residential_air_cleaners_-_a_technical_summary_3rd_edition.pdf"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.iqair.com/products/air-quality-monitors/airvisual-pro-indoor-monitor"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-05-airproof-ai/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Purifier Placement Test
When moving, rearranging a room, or facing smoke, use one sensor for a short test to find the purifier location, outlet direction, and door-closing setup that clears particles fastest.

## Product concept

After moving, rearranging furniture, or during a smoke event, the user selects their purifier model and places a portable air-quality monitor in the center of the room. The app first asks them to measure a baseline with doors and windows closed and fan speed held constant. It then guides them through placing the same purifier in two or three candidate locations, running each location for the same number of minutes. After each round, the app plots the particle-reduction rate as a simple curve, making it clear which location clears particles fastest and which is affected by door gaps or HVAC supply airflow. Users can also note whether a door was open, the AC was running, or people were moving through the room. The final result recommends the best placement, outlet direction, and any door to close or furniture to move. The first version answers only where to place one purifier in one room; it does not present short-term measurements as a whole-home air diagnosis. Users can retest the same candidate locations when the season changes, they replace a sofa, or the HVAC airflow direction changes.

## Why now (backed by facts)

As observed on August 5, AirProof AI ranked fourth in Product Hunt’s new-product feed, making purifier placement a direct interactive problem. That makes users who have just moved, rearranged furniture, or encountered smoke more likely to ask exactly where their purifier should go in their own room.

## Direction (model inference, not independently verified)

Target user: Primary users are renters and households that already own an air purifier and a portable particle monitor. A move, new furniture, or a change in HVAC airflow can invalidate their previous placement assumptions. During smoke events, they do not want to spend days relying on subjective impressions to find the right setup. They need to compare candidate locations quickly in one room and retain evidence they can retest.

Minimal entry point: The first release accepts timestamped PM2.5 data exported from a sensor and also allows manual readings. It can begin by supporting AirVisual Pro export files. The browser reads CSV files through its file interface and stores experiment records locally. Each round marks the purifier start time, then fits a decline slope to the logarithm of particle concentration. The baseline round estimates natural settling, while candidate locations are compared only on their adjusted decay rates. It will not initially simulate room airflow or claim to provide health diagnoses. The model catalog stores only the model name, fan-speed setting, and user notes, avoiding dependence on incomplete device specifications.

The strongest case against: Short-term curves can be easily skewed by sensor noise and differences in starting concentration. Foot traffic, an open door, or HVAC cycling can make candidate locations incomparable. Controlling these variables requires a baseline round and multiple waiting periods, which may feel cumbersome. If the app presents an overly certain best location, users may mistake random variation for a stable conclusion. Different sensor sampling rates and export formats will also create ongoing integration costs. The product must show data quality and repeat-test results; otherwise, one incorrect recommendation could undermine trust.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Recruit the first users through air-purifier forums, smoke-event mutual-aid groups, and communities of portable-sensor users. Publish before-and-after curves from moving a purifier within the same room, rather than generic placement advice. Create export guides for several common sensors to reach people already searching for ways to analyze their data. Let users generate anonymous comparison charts to share directly in placement discussions.

## Competitors & gaps (model inference)

- AirProof AI: AirProof AI lets users choose a preset room, drag a purifier into place, and view predicted airflow. Its advanced features can also automatically identify positions with better coverage. Its advantage is that users can compare multiple placements in seconds without a sensor. Its public pages mainly show standard room layouts and simulated results, rather than measured calibration in a user’s own room. When furniture gaps, door and window conditions, or HVAC airflow differ from the presets, the predictions may not explain real-world differences. The opening for the Purifier Placement Test is a short, controlled comparison using the same purifier and sensor. It does not need to outperform airflow simulation; it only needs to answer which candidate location clears particles faster in the current room. The two can also complement one another: simulation narrows the candidates, then measurement confirms them.
- IQAir AirVisual Pro: IQAir AirVisual Pro measures indoor PM2.5 and displays real-time and historical data in its app. Device data can also be exported for users to analyze themselves. It already handles continuous monitoring, trend viewing, and anomaly alerts. Users can observe changes after opening windows, cooking, or running a purifier. The gap is that its charts are not structured as placement-comparison experiments. Users still need to remember when they moved the purifier, its fan speed, and door or window conditions, then decide whether two decline periods are comparable. The Purifier Placement Test can build on existing data rather than creating another sensor. Timed steps, condition checks, and a consistent score turn monitoring data into a placement conclusion. Supporting only one export format at launch limits coverage, but allows the analysis workflow to be made robust first.

## How it makes money (model inference)

The free version includes one single-room comparison test. A one-time paid upgrade unlocks multi-room profiles, historical retest comparisons, and shareable reports. It will not charge by purifier model initially, so maintaining the device catalog does not become the main cost.

## Source context

Theme: Air purifier placement optimization
Trigger Product Hunt launch: AirProof AI — Find the best spot for your air purifier in seconds

This records only that the launch appeared in Product Hunt's public feed and when it was observed. The feed provides no vote count; do not describe feed order as popularity or market demand.

## Sources

- AirProof AI (https://www.producthunt.com/products/airproof-ai)
- AirProof AI - Find the best air purifier placement in seconds (https://airproofai.com/)
- Residential Air Cleaners: A Technical Summary (https://www.epa.gov/sites/default/files/2018-07/documents/residential_air_cleaners_-_a_technical_summary_3rd_edition.pdf)
- AirVisual Pro Indoor Monitor (https://www.iqair.com/products/air-quality-monitors/airvisual-pro-indoor-monitor)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
