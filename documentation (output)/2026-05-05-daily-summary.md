# Daily Summary — 2026-05-05

**Sources:**
- `raw/05-05/Stryker FDE Team Daily Meeting.docx` — FDE team daily standup (Kee-Won Hong, Rachel James, Victoria Austin, Joseph Kennedy, Andrew Stevenson, Nicole Peterson). Covered PMCH follow-up scheduling, Ortho Labeling deep dive rescheduling, ProCare use case cancellation, use case backlog review plan, ECR scoping, pod team handoff planning, staffing update, and capacity management.
- `raw/05-05/AI COE Use Case Backlog Review Part 1.docx` — Working session where Kee-Won, Rachel, Victoria, and Andrew reviewed the AI Use Case Hub (HTML explorer) to filter and flag high-value use cases from the 200+ entry backlog. Identified Vocera, My Mako, and PO Rating Agent as strong candidates.

---

## Key Information & Highlights

- **ProCare use case officially dropped.** Melissa Sentifante confirmed the ProCare team is self-implementing a Power BI + Copilot solution. FDE will not pursue this use case. The team will redirect effort toward the 26 use cases currently in "Ideation" status in Alfonso's Power BI dashboard — which Rachel clarified is specifically the subset Alfonso references in discussions (not the full 200+ entry list).

- **Ortho Labeling deep dive rescheduled to Wednesday, May 13 at 9:00am ET, extended to one hour.** Victoria Austin wants to use the live prototype demo as a vehicle to probe deeper questions — specifically, *which fields* the labeling team actually needs to compare. DT&D are available; Allison may need to drop. Olga is out. Kee-Won will be out that week, so Rachel and Victoria will lead.

- **PMCH follow-up meeting to be scheduled by Kee-Won.** Priority attendees: Javier, Alessandra, and Niall (identified as the most engaged participants from the original PMCH session). Alfonso and Matt Johnson to be included for visibility/awareness.

- **Use case backlog review session held this afternoon (Part 1).** Team walked through the AI Use Case Hub explorer with filters on ideation phase, urgency, and build type. Three use cases flagged for further investigation: (1) **Vocera** — recent acquisition seeking ROI, technology for hospital communications; (2) **My Mako** — Stryker's orthopedic robot, use case involves AI-powered weekly surgical data summaries; (3) **PO Rating Agent** — matches purchase orders to internal sales orders via field extraction. Andrew noted solving for Mako or Vocera would generate significant downstream goodwill and funding. The Kee-Won also noted that risk scores in the backlog are likely ambiguous (may reflect "risk of not implementing" rather than execution risk).

- **ECR Assistant use case redirected to the platform team.** The ECR team has already built a prototype they are satisfied with; they now need architecture review and productionalization support — not FDE discovery work. Rachel and Victoria agreed this falls outside FDE's scope. Andrew suggested ECR is a good early test case for asserting FDE's discipline around role definition and handoff. Nicole confirmed: redirect to platform team, or potentially the Clever team depending on domain.

- **Intake capacity management raised by Nicole Peterson.** Nicole recommended the team consider pausing new intake for 1–2 weeks to focus on handoff preparation before the pod teams onboard. Kee-Won noted Alfonso's guidance is approximately 2–3 Type A/B use cases per week; capacity for larger Type C/D builds running in parallel is still TBD. Victoria aligned: the immediate hard deadline is having at least one well-scoped, shovel-ready use case ready for the incoming pod team.

- **Handoff process planning initiated.** Kee-Won will schedule a meeting with Travis (overall product owner) and Katie (Account Executive) to define what a formal FDE → pod team handoff should look like. Joe confirmed Katie owns delivery and should lead that planning. Joe also referenced Brian Kulsicki (on the EIM project) who built an agent-based requirements template grounded in Stryker's working style — team agreed to connect with Brian and reuse that template.

- **SO staffing update.** One SO position remains open on the medium pod team. Katie has local SO candidates from the delivery capability. Nicole will connect with Katie to evaluate candidates on merit, with preference for AI-enabled experience. Gavin is confirmed in the platform lead/SOSO role. Travis locked in as program-level product owner.

- **Requirements quality lesson from the Clever project.** Joe flagged that the Clever team is doing a URS requirements review where 20% of requirements are open to interpretation — creating downstream ambiguity about whether user stories satisfy them. Recommendation: FDE should produce requirements that leave minimal room for interpretation, and capture lessons learned before the same pattern affects this program.

- **Portfolio tracking alignment needed.** Andrew and Kee-Won discussed the need to merge FDE's own use case tracking (cases they've personally intaked and are managing) with the Stryker AI COE's 200+ entry list into a single source of truth. Kee-Won suggested adding status fields to the list to indicate routing decisions (e.g., "recommended for platform team," "recommended for data tower," "FDE-active").

---

## Decisions Made

1. **Decision:** Drop ProCare use case from FDE's active pipeline.
   **Rationale:** Business team self-selected a Power BI + Copilot solution and will not require FDE-led prototyping.
   **Owner / Approver:** Joseph Kennedy (relayed from Melissa Sentifante)

2. **Decision:** Move Ortho Labeling deep dive from May 11 to May 13, expanding to 1 hour.
   **Rationale:** Victoria needs more time to demo the prototype and surface deeper field-level questions from the labeling team.
   **Owner / Approver:** Joseph Kennedy (scheduling)

3. **Decision:** ECR Assistant use case is not FDE work; redirect to the platform team.
   **Rationale:** The team has a working prototype; they need infrastructure and productionalization support, not business-problem-to-AI-solution discovery.
   **Owner / Approver:** Victoria Austin / Nicole Peterson (concurred)

4. **Decision:** Focus remaining intake on 1–2 additional use cases from the 26 in "Ideation" before pausing for pod team onboarding.
   **Rationale:** Capacity needs to be preserved for handoff prep; the hardest near-term deadline is having shovel-ready work for the incoming pod team.
   **Owner / Approver:** Team alignment; Nicole Peterson (guidance)

5. **Decision:** Use the 26 "Ideation" use cases from Alfonso's Power BI as the primary candidate pool for next intake.
   **Rationale:** These have already passed some vetting; reviewing all 200+ is not feasible given current capacity.
   **Owner / Approver:** Kee-Won Hong

---

## Action Items & Tasks

| # | Task | Owner | Due Date | Priority | Source |
|---|------|-------|----------|----------|--------|
| 1 | Schedule PMCH follow-up meeting; prioritize Javier, Alessandra, Niall | Kee-Won Hong | This week | High | Daily standup |
| 2 | Book Ortho Labeling deep dive for May 13, 9am ET, 1 hour | Joseph Kennedy | Today | High | Daily standup |
| 3 | Continue AI use case backlog review (Part 2) to identify 1–2 final intake candidates | Kee-Won, Rachel, Victoria, Andrew | This week | High | Both meetings |
| 4 | Add flagged use cases (Vocera, My Mako, PO Rating Agent) to notes in Hub explorer | Kee-Won Hong | Today | Medium | Backlog review |
| 5 | Schedule handoff planning meeting with Travis and Katie | Kee-Won Hong | This week | High | Daily standup |
| 6 | Connect with Brian Kulsicki to obtain/review his requirements agent template | Kee-Won Hong / Nicole Peterson | This week | Medium | Daily standup |
| 7 | Katie to reach out to Nicole about local SO candidates for medium pod | Katie (AE) | TBD | Medium | Daily standup |
| 8 | Add routing status fields to AI Use Case Hub tracking (platform team, data tower, FDE-active) | Kee-Won Hong | This week | Medium | Daily standup |
| 9 | Raise production approval gate question with Alfonso and Scott on Wednesday | Team | Wednesday | High | Daily standup |
| 10 | ECR use case: notify the ECR team that FDE is routing their use case to the platform team | Victoria Austin / Nicole Peterson | TBD | Medium | Daily standup |

---

## Risks & Blockers

- **Risk:** Victoria Austin still pending Stryker help desk callback for system access.
  **Impact:** May limit Victoria's ability to work directly with Stryker systems and SharePoint.
  **Mitigation / Owner:** Victoria to call again; Stryker IT process requires internal contact to open encrypted email + MFA call. Victoria Austin / Stryker IT.

- **Risk:** Intake volume may outpace capacity before pod team onboarding.
  **Impact:** FDE team may not have a well-scoped, shovel-ready work product ready for the incoming pod team.
  **Mitigation / Owner:** Team agreed to cap additional intake at 1–2 more cases; Nicole Peterson to help set expectations with Alfonso/Scott.

- **Risk:** Requirements ambiguity as demonstrated by the Clever project URS review.
  **Impact:** 20% of requirements are open to interpretation — creates downstream confusion for pod teams implementing from FDE handoff docs.
  **Mitigation / Owner:** Apply lessons learned; ensure FDE-authored requirements are specific and verifiable. Joseph Kennedy (tracking this).

- **Risk:** ECR team may be left in limbo if not clearly told who will support them.
  **Impact:** Relationship and expectation management; team may continue coming to FDE.
  **Mitigation / Owner:** Victoria / Nicole to communicate ECR routing clearly to the team.

- **Risk:** Risk scores in the AI CoE backlog are ambiguous (likely "risk of not implementing" rather than execution risk).
  **Impact:** Cannot rely on risk field as a filter for prioritization without manual verification.
  **Mitigation / Owner:** Team to evaluate use cases manually when in doubt; do not use risk score as sole filter. Kee-Won Hong.

---

## Open Questions & Parking Lot

1. What is the formal approval gate for greenlighting a use case to go into production? Is it Scott and Alfonso's budget alone, or do business units have to co-fund bespoke builds? *(Raise Wednesday)*
2. What ROI threshold or timeframe does Alfonso/Scott require before committing to a production build?
3. What does the formal FDE → pod team handoff artifact standard look like? What does "shovel ready" require?
4. How should the team route use cases that require data readiness work before FDE can prototype? To the data tower organization?
5. What specific fields should the Ortho Labeling diff-checker compare? *(To be answered in the May 13 deep dive)*
6. Is the My Mako app an existing tool they want to *improve* or a net-new capability they want to *build*?
7. For the Vocera use case — what specifically is the AI opportunity (triage, routing, summarization)?
8. How will FDE's custom tracking be merged with the Stryker 200+ entry list?
9. Should FDE be advising business unit teams that could self-serve agents, or is there a separate enablement/learning team for that?

---

## Next Steps & Follow-Ups

- **Wednesday, May 13 at 9:00am ET:** Ortho Labeling deep dive (Victoria Austin and Rachel James present); 1 hour; live prototype demo + deep requirements conversation.
- **This week:** Kee-Won schedules PMCH follow-up with Javier, Alessandra, Niall.
- **This week:** Kee-Won schedules handoff planning meeting with Travis and Katie.
- **Part 2 of baacklog review** to be completed to finalize the 1–2 additional intake candidates from the 26 ideation use cases.
- **Wednesday (upcoming Alfonso/Scott sync):** Raise production approval gate question, ROI expectations, and intake pause discussion.
- **Ongoing:** Pod team onboarding is the near-term horizon — all work should orient toward having at least one shovel-ready use case and a defined handoff process before that milestone.

---

## Teams Channel Message

**FDE Team Update — May 5, 2026**

Good update from today's meetings — a couple of directional shifts and good momentum on use case prioritization.

**Key Highlights**
- **ProCare dropped** — their team is self-implementing a Power BI + Copilot solution; we'll redirect energy to the 26 use cases currently in Alfonso's "Ideation" bucket
- **Ortho Labeling deep dive rescheduled** to Wednesday, May 13 (9am ET, 1 hr) — Victoria will demo the prototype live to probe deeper requirements
- **ECR Assistant being routed to the platform team** — they have a working prototype and just need productionalization support; that's not FDE-scope work
- **Backlog review session completed (Part 1)** — flagged Vocera, My Mako, and PO Rating Agent as strong candidates for next intake; will finalize 1–2 picks this week
- **Capacity reality check** — Nicole flagged we may need to pause new intake for 1–2 weeks to focus on pod team handoff prep

**Key Decisions**
- Focus next intake on 1–2 max from the 26 Ideation use cases before pod team onboards
- Handoff planning meeting to be scheduled with Travis + Katie this week
- Connect with Brian Kulsicki to reuse his Stryker requirements agent template

**Coming Up / Next Steps**
- Kee-Won scheduling PMCH follow-up (Javier, Alessandra, Niall)
- Handoff process meeting with Travis + Katie this week
- Wednesday sync with Alfonso/Scott — raise production approval gate and ROI gating questions
- May 13: Ortho Labeling deep dive with the business team

---

## Action Items Teams Message

```
**FDE Action Items — May 5, 2026**

**Kee-Won Hong**
- Schedule PMCH follow-up meeting (prioritize Javier, Alessandra, Niall) *Due: This week* [High]
- Schedule handoff planning meeting with Travis and Katie *Due: This week* [High]
- Continue AI use case backlog review (Part 2) — finalize 1–2 intake candidates from the 26 Ideation use cases *Due: This week* [High]
- Add flagged use cases (Vocera, My Mako, PO Rating Agent) to notes in Hub explorer *Due: Today* [Medium]
- Add routing status fields to AI Use Case Hub tracking (platform team, data tower, FDE-active) *Due: This week* [Medium]
- Connect with Brian Kulsicki to review his Stryker requirements agent template *Due: This week* [Medium]

**Joseph Kennedy**
- Book Ortho Labeling deep dive for May 13, 9am ET, 1 hour *Due: Today* [High]

**Rachel James / Victoria Austin / Andrew Stevenson**
- Continue AI use case backlog review (Part 2) alongside Kee-Won *Due: This week* [High]

**Victoria Austin / Nicole Peterson**
- Notify ECR team that their use case is being routed to the platform team *Due: TBD* [Medium]

**Nicole Peterson / Kee-Won Hong**
- Connect with Brian Kulsicki to obtain/review his requirements agent template *Due: This week* [Medium]

**Katie (AE)**
- Reach out to Nicole about local SO candidates for the medium pod team *Due: TBD* [Medium]

**Team**
- Raise production approval gate and ROI gating questions with Alfonso and Scott on Wednesday *Due: Wednesday* [High]

**Total action items: 10**
```
