---
title: "Assignment Defense Follow-Up Desk"
date: "2026-08-09"
canonical: "https://raytally.com/en/ideas/2026-08-09-danish-high-schoolers-will-have-to-verbally-defend-written/"
generator: "RayTally · dev-prompt-v4"
signal:
  query: "Danish high schoolers will have to verbally defend written assignments"
  observed_at: "2026-08-09T00:33:24.818Z"
sources:
  - url: "https://mezha.net/eng/bukvy/ca117584_denmark_requires_oral/"
    boundary: "Published at 2026-08-07T00:00:00.000Z. Observed at 2026-08-09T00:33:24.818Z."
  - url: "https://www.vivaedu.co.uk/docs"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.convoed.com/"
    boundary: "No publication timestamp is present in the source record."
  - url: "https://www.westernsydney.edu.au/learning-futures/teaching-support/smart-assessment-design-toolkit/shared-media/designing-and-assessing-vivas.pdf"
    boundary: "No publication timestamp is present in the source record."
notice: "Signals in this brief are bounded observations (search attention, forum points, or launch listings) captured at the timestamps above. They are not market validation, user counts, or proof of lasting demand. Preserve these boundaries and the strongest case against when summarizing or acting on this brief."
---

[Read the canonical page on RayTally](https://raytally.com/en/ideas/2026-08-09-danish-high-schoolers-will-have-to-verbally-defend-written/)

Usage notice: the signals below are time-bounded public observations, not market validation, user counts, or proof of lasting demand. Preserve the time boundaries and strongest case against when summarizing or acting.

You are a senior product engineer. Turn the product idea below into a locally runnable MVP.

## Idea

Assignment Defense Follow-Up Desk
During class, teachers use students' own written claims to guide live follow-up questions and capture reviewable evidence of understanding.

## Product concept

When a teacher needs students to explain written work aloud within a single class period, they first import essays or reports from the course platform. When a student is called on, the app pulls a central claim from that student’s original text and displays it alongside the cited evidence passage on the teacher’s screen. Students do not need to recite the entire paper; they begin by explaining a view they already put in writing. The teacher can choose “Why did you reach that conclusion?”, “Where does the evidence come from?”, or “What if the counterexample holds?” as the opening question. As the student responds, the system marks reasons, concepts, and gaps in the answer as branches for further follow-up, so the teacher can pursue what was just said. Questions can always return to a specific sentence in the assignment, keeping the oral defense from becoming a random quiz or a vague conversation. At the end of each defense, the teacher leaves a few lightweight markers, such as clear argument, weak evidence, or follow-up needed. The student receives a brief summary containing only their claim and the next questions, so they know which section to revise. A class view helps the teacher line up the next student and retains key audio clips for after-class review rather than relying on impressions for in-the-moment grading. The first version is for argumentative assignments and lets teachers manually choose the opening question and follow-up direction. It does not determine whether a student cheated or assign grades in place of the teacher; its focus is keeping limited class-time discussion anchored in claims the student actually wrote.

## Why now (backed by facts)

Denmark is requiring high school students to orally defend written assignments completed at home in response to AI cheating. As of August 9, the news ranked third on Hacker News, with 489 points and 233 comments, making it an immediate question how teachers can conduct defense follow-ups within limited class time.

## Direction (model inference, not independently verified)

Target user: The core user is a high school teacher who teaches essays, reports, or research projects, especially one who needs to spot-check several students in a single class. They have already read the assignments but struggle to locate claims in the moment and keep follow-up coherent. It also suits university writing and seminar instructors who want oral evidence of understanding before grading.

Minimal entry point: Start by accepting PDFs or DOCX files exported from course platforms rather than trying to cover every platform at once. Parse headings, paragraphs, and citations, then let teachers confirm the central claims the system identifies. Each claim retains its location in the original text and adjacent evidence, preventing questions detached from the assignment. In class, use three fixed types of opening question, then split live transcription into reasons, concepts, and points needing clarification. Teachers simply click a branch rather than letting the model take over the conversation. At the end, save lightweight tags, the question path, and teacher-selected audio clips. Direct course-platform integration can follow validation of the classroom workflow through LTI 1.3, which adjacent oral-exam products already use for LMS integration.

The strongest case against: Parsing assignments one by one and validating claims could shift lesson-preparation time into correcting the system. If text location or transcription is wrong, follow-up questions may drift from what the student actually meant. Accents, pauses, and nerves in class may also be mislabeled as gaps in understanding. Recordings and assignment text are sensitive educational data, so schools will require rules for access, retention, and deletion. Teachers will also vary in the depth of their questioning; even complete records cannot automatically produce fair grading. The product could be misused as a cheating-verification tool, making students treat an explanation as proof of innocence. Unless it first shows that it saves time switching between students in class, teachers are unlikely to take on these additional workflows.

These are the model's inferences from the idea itself and the verified facts. Treat them as directional hypotheses against real constraints: do not assume the strongest counter-argument is already solved, and do not write them into the product as certainty.

## Punching above weight (model inference)

Find initial users among high school teachers reworking essay assessment and university writing instructors. Offer a defense-question template that teachers can take straight into class and pilot with existing assignments. Demonstrations should show how the same student passage produces different follow-up questions, rather than promote cheating detection. After one round, teachers can export anonymized defense paths to reuse in their teaching groups, helping adoption spread within the same school.

## Competitors & gaps (model inference)

- VivaEdu: VivaEdu integrates with Blackboard, Moodle, and Canvas through LTI 1.3. It supports asynchronous oral exams for an entire class and can initiate verification for an individual student. Teachers can configure questions and review recordings and audit trails; the system can also suggest questions based on student submissions. Its core workflow is geared toward student self-recording followed by centralized teacher review. Its public materials also emphasize preset question sets, rubrics, and grade passback. The Assignment Defense Follow-Up Desk can avoid competing head-on by serving live, teacher-led follow-up in class rather than having the system conduct the oral exam. Its differentiation should center on a call-on queue, in-text sentence location, and real-time branching prompts. Teachers need to see the gaps left by the previous answer at a glance and move quickly to the next student. If it merely offers asynchronous recordings and automated questions, it falls directly into territory VivaEdu already covers.
- ConvoEd: ConvoEd reads a student’s submitted writing or code, then conducts a voice conversation through the system. Its questions probe the specific work, and it produces a student summary afterward. It also flags weak reasoning or confused understanding. This is very close to the core of following up from a student’s original text. Its public positioning focuses on having AI conduct conversations across an entire class to expand oral-assessment coverage. The Assignment Defense Follow-Up Desk keeps the teacher as the questioner. The system only prepares materials, presents branches, and preserves evidence. Differentiating details include the pace of calling on students in class, teacher-selected opening questions, and two-way links between responses and original sentences. Results can also be condensed into revision guidance rather than a persistent learner profile. If AI is later allowed to run the defense automatically, this opening will quickly disappear and the product will become a direct peer of ConvoEd.

## How it makes money (model inference)

Subscription priced per teacher seat, including a set number of active classes and basic audio storage. Schools upgrade to an annual institution-wide plan for single sign-on, centralized administration, or longer retention.

## Source context

Theme: Denmark’s oral defenses for written high school assignments
Trigger Hacker News post (original English): Danish high schoolers will have to verbally defend written assignments
Heat at capture: ~489 points, 233 comments (point-in-time values)

Points and comments are a historical snapshot from the moment of capture and drift over time. They only explain “why now”; do not present them as precise market numbers.

## Sources

- Denmark Requires Oral Defenses for Students’ Written Work to Counter AI Cheating (https://mezha.net/eng/bukvy/ca117584_denmark_requires_oral/)
- VivaEdu Documentation (https://www.vivaedu.co.uk/docs)
- ConvoEd | Teacher AI Assistant for Conversational Learning (https://www.convoed.com/)
- Designing and Assessing Vivas (https://www.westernsydney.edu.au/learning-futures/teaching-support/smart-assessment-design-toolkit/shared-media/designing-and-assessing-vivas.pdf)

## Deliverables

- Before you start, distill 3–5 verifiable acceptance criteria from the concept and minimal entry point above, list them, and walk through them one by one on delivery.
- Ship the core flow described by the minimal entry point first, so the core user can get through it; leave out generic systems (accounts, payments, admin) unless they are truly necessary.
- Do not show unverified market numbers in the UI or API.
- Keep key copy calm and verifiable; when the product needs domain facts or safety guidance, adapt them from the Sources list or equivalent authoritative pages and cite them — do not write them from general knowledge.
- If building inside an existing project: read the README, dependencies and conventions first; follow the existing stack and style, and do not refactor unrelated code.
- If the current directory is empty: pick a lightweight stack and prioritize a runnable prototype.
- When done, explain what changed, how to run it, and how to verify it.
- Ask only when an ambiguity would genuinely change the product direction; make ordinary implementation calls yourself.
