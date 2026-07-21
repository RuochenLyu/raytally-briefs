---
title: "Rough Sleeping Support Relay Card"
date: "2026-07-21"
canonical: "https://raytally.com/en/ideas/2026-07-21-andy-burnham/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "andy burnham"
  observed_at: "2026-07-21T03:07:51.902Z"
  active: false
  ended_at: "2026-07-21T00:30:00.000Z"
  window_hours: 168
sources:
  - url: "https://apnews.com/article/a13602b93d8f045f1cffd2bd05bf8e2b"
    boundary: "Published at 2026-07-20T00:00:00.000Z."
  - url: "https://thestreetlink.org.uk/about"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://homeless.org.uk/homeless-england/?service_types=accommodation"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/lawful-basis/special-category-data/what-are-the-rules-on-special-category-data/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Rough Sleeping Support Relay Card
A consent-based handover card lets street outreach workers match someone to a place that can take them tonight, then pass only authorised referral details to the next service.

## Product concept

When a street outreach worker meets someone who is willing to accept help, they first obtain consent and use a few short questions to record that night’s most urgent needs: somewhere to stay, whether they can bring a pet, whether medication needs to be stored, or whether they lack identification. The product filters services that still have capacity against those conditions, excluding organisations that do not accept pets, are full, or require referral paperwork. The worker sees the next location’s address, opening hours, admission requirements, and walking route. The person can choose which information is passed to the next organisation. Each referral generates a short-code card or paper QR code. The next worker scans it and sees only the information the person has authorised, so the person does not have to recount their experience from the beginning. If an organisation cannot accept them, staff select a reason such as no capacity, insufficient identification, or a medical-needs mismatch. The system then recommends the next viable route. The first version connects only local service organisations willing to provide live capacity and admission conditions. It does not replace emergency medical services, make decisions for the person, or share location or identity data with unrelated organisations. At handover, outreach teams can see which referrals have been completed and which people are still awaiting their next destination.

## Why now (backed by facts)

On 20 July, Andy Burnham became UK Prime Minister and pledged in his first speech to end rough sleeping. Searches for “andy burnham” reached 50,000+, up 800%; by the 21 July observation point, this surge had already subsided.

## Direction (model inference, not independently verified)

Target user: The core users are street outreach workers, night-shift supervisors, and temporary-accommodation coordinators in UK local government. The key moment is when someone sleeping rough has just agreed to accept help but still needs a destination for that night. Staff must quickly rule out organisations that do not accept pets, require referral paperwork, or cannot meet medical needs. Before handover, they also need to confirm whether referrals were completed, so leads do not remain stranded in phone calls and paper notes.

Minimal entry point: Start in one borough, building a closed directory with a small group of night outreach teams and receiving organisations. Organisations use a lightweight web page to update capacity, opening hours, and hard constraints. Make the outreach interface an offline-capable PWA that collects only the fields needed for that night’s match. Use transparent rules rather than predictive scoring, and initially open walking routes through address deep links in the phone’s built-in map. QR codes contain only short-lived signed tokens, never plaintext health information. A receiving organisation can read only the fields the person has explicitly authorised. The back end retains consent records, capacity-update times, and refusal reasons. The first version does not connect to each organisation’s full case-management system or make statutory eligibility determinations.

The strongest case against: The real bottleneck may be whether organisations will keep capacity data current, rather than matching itself. Stale capacity will send outreach workers on wasted trips and quickly erode trust among people seeking help. If staff still have to call each organisation to confirm availability, the product merely adds another data-entry task. Medication and medical needs may involve special category data, and verbal consent does not by itself resolve compliance. Controllers must still establish a lawful basis, a special-category condition, and the minimum necessary data scope. Organisations must also agree on data-controller responsibilities, deletion rules, and security-incident handling. Without reliable update commitments and shared accountability, abandon cross-organisation handovers at first and build an internal tool for a single team.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Run a short pilot in a borough that already has a night outreach shift. Focus on reducing fruitless calls, repeated retelling, and wasted journeys—not on promoting an algorithm. Give partners a weekly de-identified summary of refusal reasons, helping managers identify gaps in capacity information and admission rules. Once there are verifiable cases, reach neighbouring boroughs through local-government procurement exchanges, charity operations meetings, and sector online events.

## Competitors & gaps (model inference)

- StreetLink: StreetLink already routes public reports of people sleeping rough to local authorities or outreach teams. Users locate the person, describe the situation, and submit a report; people who request feedback receive an update within 10 working days. It is designed to identify people sleeping rough and initiate outreach, not to place someone during an encounter. Its public workflow does not show real-time bed-capacity filtering or exclude organisations based on pet, documentation, or medical requirements. Nor does it offer a consent-based handover card for the person seeking help. The relay card can begin after an outreach worker has made contact, shortening the path from “willing to accept help” to a place that can receive them rather than replacing public reporting.
- Homeless England: Homeless England offers a continuously updated service directory. Its public site says it lists 1,500 projects and can be filtered by location, service type, and support offered. It helps staff identify nearby candidate services, but primarily provides contact details and service descriptions. The public site does not show live capacity, that night’s cut-off times, or immediate refusal status. Outreach workers must still confirm acceptance organisation by organisation. The directory also does not carry a person’s field-by-field consented information handover. Rather than rebuilding a national directory, the better entry point is to layer organisation-confirmed capacity and constraints onto a partner borough. Failure reasons can then be written back to the current referral to guide the next route.

## How it makes money (model inference)

Charge local authorities or lead charities a monthly subscription priced by service area. Participating receiving organisations update capacity, requirements, and refusal reasons free of charge, lowering the barrier to joining the network.

## Trend background

Theme: Andy Burnham, UK prime ministership, and rough sleeping
Trigger query (original English): andy burnham
Approx. search volume: 50000+ (approximate)
Approx. increase: +800% (approximate)

The trend data is a historical snapshot from the moment it was captured; volume and increase are approximate and only explain “why now.” Do not write them into product copy as precise market numbers.

## Sources

- Andy Burnham becomes the UK's seventh prime minister in a decade after Starmer resigns (https://apnews.com/article/a13602b93d8f045f1cffd2bd05bf8e2b)
- About Us - What is StreetLink? (https://thestreetlink.org.uk/about)
- Homeless England (https://homeless.org.uk/homeless-england/?service_types=accommodation)
- What are the rules on special category data? (https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/lawful-basis/special-category-data/what-are-the-rules-on-special-category-data/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
