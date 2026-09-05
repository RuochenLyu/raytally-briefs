---
title: "Course Drop Impact Map"
date: "2026-09-05"
canonical: "https://raytally.com/en/ideas/2026-09-05-forward-prerequisite-checking-tool/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Forward prerequisite checking tool"
  observed_at: "2026-09-05T00:34:29.895Z"
sources:
  - url: "https://www.reddit.com/r/RPI/comments/1w4wyeh/forward_prerequisite_checking_tool/"
    boundary: "Published at 2026-09-02T00:00:00.000Z. Observed at 2026-09-05T00:34:29.895Z."
  - url: "https://github.com/quacs/quacs"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://registrar.rpi.edu/services/academic-planning/degree-works"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://info.stellic.jhu.edu/"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-09-05-forward-prerequisite-checking-tool/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Course Drop Impact Map
Before dropping or swapping a class, students can see which later courses it unlocks and how removing it could delay their degree path.

## Product concept

Before the add/drop deadline, a student enters a course they are considering dropping and imports their degree plan, completed coursework, and next-semester plans. The page first maps the courses that this class unlocks, then links every relationship back to the exact prerequisite language in the school’s course catalog. The student can temporarily remove the course from their plan. The product then shows courses they can no longer take immediately, paths blocked further downstream, and the semester to which a capstone or required major course may be pushed. If a course is offered only in the fall, the timeline marks the impact of waiting an additional year. For alternative conditions such as “A or B,” students can check the path they have already satisfied and recalculate the result. Advisors can open two course plans side by side and flag change-of-major rules or exception approvals that require human confirmation. Start with one school’s official catalog, course offering terms, and a few degree plans. The product’s job is to make the course chain visible; the final decision to drop remains with the student and the school’s advisor.

## Why now (backed by facts)

A September 2, 2026 post on r/RPI asked how to look up every downstream course that depends on a specified course. Commenters suggested QuACS data, Excel, advisors, and generative AI, but there is still no direct list that can be verified against the official catalog.

## Direction (model inference, not independently verified)

Target user: The primary user is an undergraduate nearing an add/drop deadline who is considering dropping a difficult class, switching courses, or changing academic direction but cannot see what later courses will be blocked. The closer they are to graduation, the less room they have to recover; fall-only courses can make delays worse. Advisors can also use it before meetings to compare two plans against the same official evidence.

Minimal entry point: Start with QuACS’s public repository and scraping tools for course data, then verify against the original language in RPI’s official catalog. Parse prerequisites into a directed graph with AND and OR branches, retaining the catalog sentence for every edge. When a student removes a course, recursively propagate unsatisfied nodes and layer in required positions from the degree plan. Model offering terms as separate time constraints and simulate semester by semester to show the earliest a course can be taken. The first version covers one school and a small set of degree plans; route complex waivers to human review. Students can import and verify completed coursework and future plans, but the product does not write directly to SIS or Degree Works.

The strongest case against: Catalog prerequisite rules often include electives, corequisites, minimum grades, and instructor permission, and parsing mistakes could directly distort a student’s path. Degree plans also vary by entering year, so identically named majors may not follow the same requirements. Offering terms can change, and historical schedules cannot be treated as future commitments. Without transfer-credit, waiver, and change-of-major rules, the product may falsely label a viable route as closed. If a student drops a course based on that error, the warning could cause a real semester delay. Maintaining catalog versions, rule tests, and links to original language is the main ongoing cost after launch.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

The first users are in the r/RPI community that raised the question and among existing QuACS users. Publish a public demo supporting common courses such as PHYS-1200, so students can directly verify reverse-prerequisite results. Then turn parsing errors and missing relationships into reproducible issues for the QuACS community to correct together. Near registration and add/drop deadlines, invite campus advisors to compare two real plans in usability tests.

## Competitors & gaps (model inference)

- QuACS: QuACS is already a familiar course-planning tool for RPI students. It pulls course and prerequisite information from SIS and can flag when a student lacks a prerequisite. Its code, data, and scraping tools are public, making it suitable for direct reuse. Its core job, however, is building semester-by-semester schedules. The current interface does not directly answer, “Which courses depend on this one?” In the September 2 post, a commenter said they had considered adding this feature to QuACS but had not completed it. The more important gap is calculating the chain reaction after a drop using a student’s completed coursework and degree plan. A reverse-filter page alone still cannot show how long a degree path would be delayed.
- Degree Works: RPI’s Degree Works already shows degree progress and completed and unmet requirements. Its What If feature supports reviewing another major or concentration and estimating the semesters needed to graduate. That makes it the official adjacent tool for checking degree requirements. Its public documentation focuses on degree audits, not path simulation around a course a student may drop. Students still have to work backward from unmet requirements to understand dependencies among courses. It is also unconfirmed whether it lists every downstream course blocked by that course and links each one back to the original prerequisite language. The opportunity is not to rebuild degree auditing, but to turn “remove this course” into a comparable impact list. Results should still be confirmed in Degree Works, the course catalog, and with an advisor.

## How it makes money (model inference)

Charge academic departments an annual access and maintenance fee covering catalog parsing, degree-plan configuration, and rule updates. Students and advisors use it free through the campus portal.

## Source context

Theme: Forward prerequisite checker
Trigger Reddit single-post demand observation: r/RPI — Forward prerequisite checking tool

This is one observation bounded by its publication and capture times. It is not evidence of market size or a broad trend and only explains “why now.”

## Sources

- Forward prerequisite checking tool (https://www.reddit.com/r/RPI/comments/1w4wyeh/forward_prerequisite_checking_tool/)
- quacs/quacs: Questionably Accurate Course Scheduler for RPI (https://github.com/quacs/quacs)
- Degree Works (https://registrar.rpi.edu/services/academic-planning/degree-works)
- JHU Stellic Information (https://info.stellic.jhu.edu/)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
