---
title: "Private Distribution of Keepsakes"
date: "2026-07-22"
canonical: "https://raytally.com/en/ideas/2026-07-22-inheritance/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "inheritance"
  observed_at: "2026-07-22T00:33:19.204Z"
  active: true
  window_hours: 168
sources:
  - url: "https://manual.fairsplit.com/about/concepts.html"
    boundary: "Published at 2025-06-04T00:00:00.000Z."
  - url: "https://www.gov.uk/guidance/a-guide-to-civil-mediation"
    boundary: "Published at 2021-07-20T00:00:00.000Z."
  - url: "https://docs.expo.dev/versions/latest/sdk/imagepicker/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://supabase.com/docs/guides/database/postgres/row-level-security"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-07-22-inheritance/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Private Distribution of Keepsakes
Before dividing a loved one’s belongings, family members privately record what matters to them, so only the few genuinely contested items need to be discussed together.

## Product concept

After a loved one dies, families sorting through photos, watches, furniture, or old books often want neither an open bidding process nor ownership determined by whoever speaks up first. Each person photographs items on their phone, then notes whether they want to keep them, are willing to trade them, or do not mind either way. They can also add a sentence or two privately explaining why, such as a childhood memory, care they provided, or whether they have room at home. No one sees anyone else’s choices before submitting. Once everyone has submitted, the product groups unclaimed items and items with complementary preferences into suggested allocations—for example, one person wants the photo album while another cares more about the frames. Family members can confirm, revise, or defer these low-conflict outcomes without putting every item on the negotiating table at once. Only items wanted by multiple people move to a discussion page. It shows the memorial reasons each person is willing to make public, alongside possible exchanges, such as trading a piece of furniture for several letters. The first version does not value items, determine legal effect under a will, or decide who owns anything. It simply shifts a sensitive distribution away from racing to speak first: settle the uncontested majority, then give the few conflicts proper attention.

## Why now (backed by facts)

UK searches for “inheritance” have reached 10,000+, up 1,000%; as observed on July 22, this search surge was still ongoing. More families are seeking inheritance information now, and are therefore more likely to encounter the difficult question of how to raise the issue of who receives keepsakes.

## Direction (model inference, not independently verified)

Target user: The core user is an executor or adult child just beginning to inventory a loved one’s belongings. After the funeral, the family needs to clear a home or storage space but is not ready to argue openly. There may be many items, relatives may live apart, and emotions can turn on a single remark. They need to collect genuine preferences first, then decide what is worth discussing as a family.

Minimal entry point: Build mobile intake with Expo, using the device camera or photo library directly. The backend can use Supabase Auth, Postgres, and private Storage. Apply row-level access rules to every family, member, and item, and isolate photos by family. The initial data model stores items, preferences, public reasons, and submission status. Only after everyone has submitted does the server run deterministic matching. The first version outputs only three categories: unclaimed, wanted by one person, and wanted by multiple people. Exchange suggestions enumerate only items both parties explicitly offer to give up; they do not value items or make automatic decisions.

The strongest case against: The main risk is not the matching algorithm but whether the family accepts the process. Where a will, ownership, or an executor’s authority is disputed, suggested allocations may be mistaken for legal conclusions. Civil mediation can be used for will and probate disputes, with a neutral party helping the parties negotiate. The product must therefore repeatedly state that results require family confirmation, while allowing families to pause and export their records. Hidden preferences can also create a different kind of suspicion: someone may worry that an administrator can see them early. Permission logs, simultaneous disclosure, and the ability for members to leave must be trustworthy. If a family already faces threats, misappropriation, or disputes over high-value property, continued self-service negotiation would only increase liability; refer them to a lawyer or mediator.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Start with UK will writers, estate-clearance professionals, and civil mediators. Before a formal dispute arises, they can send families a private-distribution link. A second entry point is a printable checklist on how to divide parents' belongings fairly, ending with an invitation to create one free distribution. This avoids relying on broad inheritance-keyword advertising.

## Competitors & gaps (model inference)

- FairSplit: FairSplit already lets users create photo-based item inventories and lets heirs privately mark their interest. It can identify unclaimed items, then distribute belongings through sentimental-point bidding and preference-ranked rounds. Simply offering photos and blind selections would therefore not be enough to differentiate. The opening is a lighter, earlier way to handle low-conflict items. It identifies items wanted by one person, wanted by no one, or open to exchange without requiring the family to accept valuations or bidding rules first. Its conflict page centers on memorial reasons participants choose to share and allows items to be deferred. It promises neither mathematical fairness nor a system-imposed decision. The trade-off is that it is less suited to executors focused on balancing shares, but better suited to families that have not yet entered a formal dispute.
- Family group chats, shared spreadsheets, and taking turns: Common approaches include choosing items together, taking turns, drawing lots, or having an executor track requests in a spreadsheet. They require no new tool, and small sets of items can be handled on the spot. But when relatives live apart, photos, preferences, and revision histories can become scattered across chat apps. Whoever speaks first may also unintentionally shape everyone else’s choices. Memorial reasons posted directly in a group chat can feel like pressure or a comparison of closeness. This product’s opening is not to replace legal process, but to separate independent expression from collective discussion. It can also record who confirmed a suggestion, which items were deferred, and who ultimately received each item. The real barrier is that families may not want a process tool involved in grief, so invitation copy and a clear exit option matter more than sophisticated algorithms.

## How it makes money (model inference)

Charge per family distribution. The base plan covers one family, a limited number of members, and a set number of items. Once complete, families can export a photo inventory, the proposed distribution, and items still awaiting discussion. Neutral facilitation and longer retention are paid add-ons.

## Trend background

Theme: UK inheritance
Trigger query (original English): inheritance
Approx. search volume: 10000+ (approximate)
Approx. increase: +1,000% (approximate)

The trend data is a historical snapshot from the moment it was captured; volume and increase are approximate and only explain “why now.” Do not write them into product copy as precise market numbers.

## Sources

- FairSplit concepts (https://manual.fairsplit.com/about/concepts.html)
- A guide to civil mediation (https://www.gov.uk/guidance/a-guide-to-civil-mediation)
- ImagePicker - Expo Documentation (https://docs.expo.dev/versions/latest/sdk/imagepicker/)
- Row Level Security | Supabase Docs (https://supabase.com/docs/guides/database/postgres/row-level-security)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
