---
title: "FCAJ Sharing Session – Agentic AI Build Week 2026"
date: 2026-07-25
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

## Event information

- **Time:** 09:00–12:00, July 25, 2026
- **Venue:** 26th Floor, Bitexco Financial Tower, Ho Chi Minh City
- **Organizer:** First Cloud AI Journey (FCAJ)
- **My role:** Attendee at the sharing and retrospective session

## Event context

The session was held after Agentic AI Build Week 2026 so four teams from the FCAJ community could review their journeys from problem selection to MVP completion and pitching. Some teams received awards in the Built with AWS track. What interested me most, however, was not only the results but also how each team turned an initial idea into a product that could be demonstrated and validated within a short period.

The presentations showed that buildathon pressure is not purely technical. A team must also understand the need, agree on the business logic, limit scope, divide responsibilities, and prepare a story that helps the audience recognize the product's value.

## Product-development lessons

### Start with a real problem

The most convincing presentations clearly identified the user, the difficulty that user faced, and the outcome the solution needed to produce. Technology mattered only when it supported that business flow. If the business logic remained unclear, adding more AI models or cloud services would not make the product coherent.

Because competition time was limited, each team also needed to choose one core flow and complete it. A small MVP with clear input, useful output, and a stable demonstration was more valuable than many disconnected features that had not been validated.

### Coordinate as a team

An effective team needs members whose skills complement one another and who communicate regularly. Assigning roles is useful only when everyone shares the same objective. During implementation, the team must update progress, detect duplicated or misaligned work, and adjust scope early.

I also learned that listening and reaching agreement are as important as technical expertise. Under time pressure, a team cannot pursue every idea. Members need to explain trade-offs, accept a shared decision, and take collective responsibility for the selected approach.

A team may include business analysts, developers, cloud engineers, UI/UX designers, and members responsible for pitching, so the same problem can be viewed from several perspectives. This diversity helps uncover business requirements, technical risks, user-experience concerns, and time constraints. The team must combine those perspectives into one objective and scope instead of allowing each role to optimize only its own part.

### Communicate value instead of listing technology

A clear pitch should answer four questions: What is the problem? Who experiences it? How does the solution work? What practical impact does it create? Architecture and a working demo provide evidence of feasibility, but the audience still needs to understand why the product should exist.

This lesson changed how I think about presenting a project. Instead of beginning with frameworks and AWS services, I should first explain the context, business flow, and expected outcome, then show how the technology supports those requirements.

## SA Professional AI Native App case study

Among the four presentations, the **SA Professional** idea stood out because it addressed a practical Solution Architect workflow. At the beginning of a project, an architect often has to read SOP, BRD, or PRD documents, extract requirements, identify missing information, draft an architecture, create diagrams, and estimate cost within a short time.

The presentation used a realistic scenario: a customer might call in the evening and expect an initial proposal by the following morning. Within that short window, the Solution Architect still needs to clarify requirements, identify assumptions, outline one or more architecture options, and provide a sufficiently grounded cost estimate for the next discussion. The challenge is not merely working quickly, but avoiding important omissions when the initial information is incomplete.

The team's solution focused on that workflow. A user supplies documents and natural-language descriptions; the system structures the requirements, highlights information gaps, and proposes high-level design options, diagrams, and cost estimates for further review. Each design option describes the main components, data flow, suitable services, and trade-offs involving cost, security, scalability, or delivery time. AI handles the initial preparation, while the architect remains responsible for confirming requirements, comparing alternatives, assessing risk, and approving the final design.

The main lesson was not to copy a particular architecture, but to identify a time-consuming step in an existing process and build a tool whose output can be reviewed and edited. This approach is particularly useful near the end of a capstone project, when a team must reconcile requirements, finalize architecture, find missing sections, and prepare documentation.

## Applying the lessons

I can apply the following principles directly to group projects:

- Agree on the user, problem, and business flow before dividing technical tasks.
- Complete one testable end-to-end flow before expanding scope.
- Assign work through clear outputs and update progress frequently.
- Use architecture diagrams, demonstrations, and evidence to explain decisions.
- Treat AI as a drafting assistant; validate its output against requirements and source code.
- Structure a pitch as problem – solution – operation – impact.

## Participation evidence

{{< report-image src="images/4-EventParticipated/4.2-Event2/image.png" alt="FCAJ Agentic AI Build Week session information" >}}

<p style="text-align: center;"><em>Figure 4.2. FCAJ Agentic AI Build Week session information at Bitexco Financial Tower.</em></p>

{{< report-image src="images/4-EventParticipated/4.2-Event2/image-1.png" alt="Sharing and retrospective session venue" >}}

<p style="text-align: center;"><em>Figure 4.3. Attendees following the FCAJ teams' presentations.</em></p>

## Conclusion

The session showed me that a strong product balances three elements: it solves the right need, can be implemented, and can be explained clearly. In addition to Agentic AI and AWS knowledge, I learned about scope control, team coordination, and evaluating a solution through practical value. These lessons apply to Cloud E-Wallet, my capstone work, and future projects.
