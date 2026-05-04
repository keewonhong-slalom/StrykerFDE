# Daily Summary — 2026-05-01

**Sources:**
- `raw/05-01/Stryker FDE Team Daily Meeting.docx` — Internal FDE team daily standup (Kee-Won Hong, Victoria Austin, Rachel James, Andrew Stevenson). Covered debrief from the morning ECR/NC deep-dive, SharePoint access blocker, prototype vs. due diligence framework, use case intake process refinement, and Monday prep for Alfonso/Scott Austin.

---

## Key Information & Highlights

- **Morning deep-dive debrief (ECR/NC use case):** The team debriefed from a morning session on the Engineering Change Request (ECR) / Non-Conformance (NC) use case. Andrew Stevenson provided domain context: NCs are stratified in severity — unchecked, they can escalate to FDA intervention and worst-case a consent decree. The business team noted that ~25% of ECRs result in an NC, largely due to incomplete information in the change request. The team aligned that the root cause is an information completeness problem.

- **Use case disposition — ECR/NC likely not a fit for FDE prototype mandate:** The current solution for the ECR/NC use case is working (a functioning prototype exists); the business team's real need is productionization support and architecture review. The FDE team's mandate is not to harden existing solutions for small internal teams (~150 users) but to identify, validate, and jumpstart high-value net-new use cases. The team agreed this use case should be flagged as "solved — needs productionization" rather than queued for FDE prototyping, unless Alfonso directs otherwise.

- **SharePoint access still blocked:** Both Kee-Won Hong and Victoria Austin remain unable to access the Stryker SharePoint use case list. Alfonso has resent credentials twice (including an encrypted message) but the credentials have not worked. Kee-Won will call Stryker IT support after the standup and loop in Alfonso first to see if there is a faster path.

- **Prototype vs. due diligence framework clarified:** The team crystallized a useful distinction — "due diligence" is always performed as part of use case intake and includes research, stakeholder interviews, and build/buy evaluation. A "prototype" is only warranted when: (a) the team is confident the use case will go to build, (b) there is a specific technical or UX gap that hands-on prototyping can close, and (c) the ROI supports the investment. Building a prototype only to fill a due diligence gap is considered out of scope.

- **Use case intake scoring rubric to be refined for Monday:** The existing scoring rubric broadly aligns with Stryker's AI CoE framework (Alfonso confirmed this on Wednesday) but uses slightly different terminology. Kee-Won will review and adjust the rubric in the 2pm sync so it's ready to present to Alfonso and Scott Austin on Monday.

- **Rachel James built an intake prototype:** Rachel demonstrated a mini-prototype illustrating the AI-assisted form completion concept — specifically, an LLM prompting a user when their input is too sparse (e.g., "device broken") and asking clarifying follow-up questions. This was framed as a communication tool to align the team and stakeholder on the intended functionality, not a production deliverable.

- **FDE team mandate clarified for Andrew Stevenson:** The three pillars of the FDE mandate were articulated: (1) use case prioritization with business case validation, (2) jumpstart prototyping to prove technology and UX viability, and (3) handoff to engineering pods (Slalom or Stryker) for productionization. The FDE team does not own business cases — those belong to the business units — but holds them accountable to their published numbers.

- **RACI/accountability artifact exists:** A responsibility matrix aligning Slalom and Stryker roles was confirmed to exist in one of the kickoff decks. Andrew Stevenson to be added to the FDE Teams channel and provided with daily/use case summaries first; repo access to follow.

- **Clinical research use case still under evaluation:** The team noted the clinical research / Adobe Workfront use case (introduced yesterday) has a weak but conservative business case and a low user base (~2 people mentioned). The team flagged uncertainty and agreed to discuss further in the 2pm sync, potentially planning a follow-up session.

---

## Decisions Made

1. **Decision:** ECR/NC use case to be flagged as "prototype not needed — solution exists, productionization support required" in the use case intake funnel.
   **Rationale:** The business team has a functioning prototype; the gap is productionization, which falls outside the FDE team's core mandate. The larger value (reducing NCs and the 15-hour remediation process they trigger) is noted but requires a different engagement model.
   **Owner / Approver:** Kee-Won Hong; to be validated with Alfonso on Monday.

2. **Decision:** "Prototype" to be reserved for use cases that are (a) approved for build track, (b) have a specific technical/UX gap to close, and (c) have validated ROI. Due diligence is a separate, always-on phase of intake.
   **Rationale:** The team recognized they were conflating due diligence work with prototyping, which risks over-investing in validation of use cases that may never be built.
   **Owner / Approver:** Victoria Austin, Rachel James, Kee-Won Hong (team consensus).

3. **Decision:** Use case intake scoring rubric to be aligned more closely with Stryker AI CoE terminology before the Monday Alfonso/Scott Austin meeting.
   **Rationale:** Minor terminology mismatches (e.g., "effort" vs. "cost") create unnecessary friction in alignment conversations. Alfonso already validates the underlying framework.
   **Owner / Approver:** Kee-Won Hong.

4. **Decision:** Andrew Stevenson to receive daily/use case summaries first; repo access to be set up separately.
   **Rationale:** Repo access introduces a learning curve; summaries provide faster onboarding value.
   **Owner / Approver:** Kee-Won Hong.

---

## Action Items & Tasks

| # | Task | Owner | Due Date | Priority | Source |
|---|------|-------|----------|----------|--------|
| 1 | Email Alfonso before calling Stryker IT help desk — ask if there is a faster path to SharePoint access | Kee-Won Hong | Today (05-01) | High | Daily Meeting |
| 2 | Call Stryker IT support to resolve SharePoint credentials access | Kee-Won Hong / Victoria Austin | Today (05-01) | High | Daily Meeting |
| 3 | Refine use case intake scoring rubric — align terminology with Stryker AI CoE framework for Monday demo | Kee-Won Hong | 05-01 (2pm sync) | High | Daily Meeting |
| 4 | Prep short summary of the two priority use cases (scope, target outputs) for Monday Alfonso/Scott Austin meeting | Kee-Won Hong | Monday 05-04 | High | Daily Meeting |
| 5 | Define and document prototype goal for each of the two priority use cases before Monday | Victoria Austin / Kee-Won Hong | Monday 05-04 | High | Daily Meeting |
| 6 | Evaluate clinical research use case further — assess user base, ROI, and build/buy options (Adobe Workfront integration) | Victoria Austin / Rachel James | TBD | Medium | Daily Meeting |
| 7 | Share ECR/NC deep-dive transcript and notes with Andrew Stevenson via summary | Kee-Won Hong | ASAP | Medium | Daily Meeting |
| 8 | Add Andrew Stevenson to FDE Teams channel | Kee-Won Hong | ASAP | Medium | Daily Meeting |
| 9 | Set up repo access for Andrew Stevenson | Kee-Won Hong | TBD | Low | Daily Meeting |
| 10 | Flag ECR/NC use case as "productionization track" in use case scoring rubric and document rationale | Kee-Won Hong / Team | Monday 05-04 | Medium | Daily Meeting |

---

## Risks & Blockers

- **Risk/Blocker:** SharePoint use case list still inaccessible despite two credential attempts from Alfonso.
  **Impact:** Cannot re-score all 26 use cases or complete full prioritization alignment before Monday.
  **Mitigation / Owner:** Kee-Won to email Alfonso first, then escalate to Stryker IT help desk. Kee-Won and Victoria Austin both blocked.

- **Risk/Blocker:** Without full access to the 26-use-case list, the team is making prioritization decisions with incomplete information.
  **Impact:** Risk of de-prioritizing or missing use cases that may be high-value.
  **Mitigation / Owner:** Kee-Won Hong to resolve credentials blocker as top priority today.

- **Risk/Blocker:** Clinical research use case has a small user base and unclear ROI justification.
  **Impact:** Risk of investing prototype/due diligence effort in a low-return use case.
  **Mitigation / Owner:** Victoria Austin and Rachel James to evaluate further; decision expected in near-term sync.

- **Risk/Blocker:** FDE team's scoring rubric terminology does not exactly match Stryker AI CoE framework.
  **Impact:** Minor alignment friction with Alfonso and the AI review board; risk of confusion in Monday meeting.
  **Mitigation / Owner:** Kee-Won Hong to align terminology before Monday.

---

## Open Questions & Parking Lot

1. Should the ECR/NC use case be formally removed from the FDE prototype queue, or kept as a conditional item pending Alfonso's input on Monday?
2. What is Alfonso's exact title and organizational role? (Andrew Stevenson noted his backdrop said "Innovation Excellence" — likely IT/technical innovation lead.)
3. How do we structure the handoff artifact from FDE to engineering pods? What is the canonical format — is it the scoring rubric, an epic template, or something else?
4. For the clinical research use case: how many users would actually benefit, and is Adobe Workfront integration technically feasible within Stryker's IT environment?
5. Should the FDE team develop a mini "balanced scorecard" to report progress to Stryker executives, as suggested by Andrew Stevenson? If so, what are the right metrics?
6. What is the right cadence and format for sharing summaries with Andrew Stevenson — daily digest, use-case-specific summaries, or both?

---

## Next Steps & Follow-Ups

- **Today (05-01), immediately after standup:** Kee-Won Hong to email Alfonso re: SharePoint access, then call Stryker IT support.
- **Today (05-01), 2pm sync:** Team to refine scoring rubric terminology, review clinical research use case disposition, and define prototype goals for the two priority use cases.
- **Monday (05-04):** Sprint demo / review with Alfonso and Scott Austin. Kee-Won to present updated use case scoring rubric and short summary of the two priority use case prototypes. Victoria Austin to demo Label Modification prototype.
- **Ongoing:** Andrew Stevenson onboarding — Teams channel access and summary sharing first, repo access to follow.
- **TBD:** Follow-up session on clinical research use case to assess viability before committing to due diligence effort.
