# Daily Summary — 2026-04-30

**Sources:**
- `raw/04-30/AI CoE _ FDE Deep Dive - Ortho JR PCMH Phase 2.docx` — Meeting transcript of the AI CoE / FDE deep-dive session with the Ortho JR PCMH Phase 2 team (Niall Murphy, Alessandra Chavez, Javier Diaz, Dmytro Turchak, Rachel James, Victoria Austin, Kee-Won Hong). Focused on the current complaint intake process, RPA architecture, TrackWise integration, and the vision for an AI-enabled intake solution.
- `raw/04-30/Stryker FDE Team Daily Meeting.docx` — Internal Slalom FDE team daily standup (Victoria Austin, Rachel James, Kee-Won Hong, Joseph Kennedy, Nicole Peterson, Andrew Stevenson). Covered debrief from the morning deep-dive, use case prioritization update, ROI governance, new team member introduction, and prototype planning.

---

## Key Information & Highlights

- **RPA architecture clarified:** The existing RPA toolset performs three core functions for the Ortho JR complaint intake flow — (1) reading SharePoint form data, (2) sending confirmation/follow-up emails via Outlook, and (3) populating fields in TrackWise. Multiple RPAs exist for different downstream process stages beyond intake.
- **TrackWise as system of record:** TrackWise is the quality management system of record, but the UI is fragmented across many tabs and considered burdensome. The team builds workarounds (SharePoint + RPA) to avoid direct entry. A future AI solution could bypass the SharePoint intermediary and write directly to TrackWise, provided a human review step is preserved before customer-facing communications go out.
- **AI-enabled intake vision aligned:** The JR team and Slalom aligned on a future state where an AI agent guides complaint submitters through an intelligent, branching intake form — pre-populating known fields from event narratives, skipping irrelevant questions, and surfacing inconsistencies. The goal is to have a complete, high-quality record at the end of intake with minimal or no back-and-forth.
- **Multi-device chunking idea raised (Javier Diaz):** For complaints involving multiple devices, AI should chunk the event narrative on a per-device basis to facilitate cleaner downstream processing and classification.
- **Confidence-threshold review model proposed:** The team discussed a model where high-confidence, straightforward complaints can flow through automatically, while lower-confidence cases are flagged for specialist review before TrackWise submission and customer contact.
- **New team member onboarded:** Andrew Stevenson (Global HCLS, Med Tech & Services) joined the FDE team. Deep med-tech industry background across McKesson, pharma, and medical devices. Will serve as an embedded SME for healthcare domain context.
- **Use case prioritization confirmed with Alfonso:** Kee-Won confirmed that the two top-priority use cases (Label Modification & Review; AI-Enabled Complaint Intake) were validated by Alfonso. Full re-scoring of all 26 use cases in the Stryker SharePoint list is pending access (credentials outstanding as of end of day).
- **ROI governance escalating:** Joe Kennedy flagged that use case ROI will be reported up to an AI Review Board and ultimately to the Stryker board. Claire Gilbert (DSL, returning from leave in ~2 weeks) will own ROI coordination. The contract total is approximately $40M over 3 years with a $6M/year flex capacity.
- **Label Modification prototype target: Monday.** Victoria Austin committed to having a scrappy Label Modification prototype (PDF upload → JSON extraction UI) ready to demo to Alfonso and Scott Austin on Monday.
- **Build vs. buy check to be integrated into intake scoring:** Alfonso asked the team to evaluate whether existing market tools (e.g., JotForm, Red Cube) could solve use cases before building. This will be added to the scoring/intake criteria.

---

## Decisions Made

1. **Decision:** Focus prototype development on Label Modification & Review and AI-Enabled Complaint Intake as the two top-priority use cases.
   **Rationale:** Validated by Alfonso; both have clear value and are technically feasible for near-term prototyping.
   **Owner / Approver:** Kee-Won Hong (team lead); Alfonso (Stryker sponsor)

2. **Decision:** Label Modification prototype to be demo-ready by Monday for internal alignment with Alfonso and Scott Austin.
   **Rationale:** Joe Kennedy noted that showing tangible output early builds credibility and executive excitement.
   **Owner / Approver:** Victoria Austin

3. **Decision:** Future AI intake solution should preserve a human review step prior to customer contact (CC1) and TrackWise submission, with an automated fast-track for high-confidence cases above a defined threshold.
   **Rationale:** Specialists must retain control over outbound customer communications and quality system entries. TrackWise failures (e.g., system updates) also require a recovery mechanism.
   **Owner / Approver:** Agreed by Niall Murphy, Alessandra Chavez, Javier Diaz, Rachel James, Victoria Austin

4. **Decision:** Add a "build vs. buy" check to the use case intake and scoring process.
   **Rationale:** Alfonso directed the team to evaluate existing market solutions (e.g., JotForm, Red Cube) before committing to custom development.
   **Owner / Approver:** Victoria Austin / Rachel James (to integrate into scoring template)

5. **Decision:** Claire Gilbert will own ROI coordination across use cases when she returns from leave (~2 weeks).
   **Rationale:** Contract scale ($40M / 3 years) and board reporting require tight, bottom-up ROI tracking. Claire has prior Stryker AI intake experience and familiarity with the AI Value Platform.
   **Owner / Approver:** Joseph Kennedy

---

## Action Items & Tasks

| # | Task | Owner | Due Date | Priority | Source |
|---|------|-------|----------|----------|--------|
| 1 | Build Label Modification prototype (PDF upload → JSON extraction UI, Stryker branding) for Alfonso/Scott Austin demo | Victoria Austin | Monday, 2026-05-04 | High | Team Daily Meeting |
| 2 | Gain access to Stryker SharePoint use case list (credentials from Alfonso outstanding) | Kee-Won Hong | ASAP | High | Team Daily Meeting |
| 3 | Re-score all 26 use cases in Stryker SharePoint list using FDE prioritization framework (value/cost/effort/reach) | Kee-Won Hong / Team | After SharePoint access | High | Team Daily Meeting |
| 4 | Add "build vs. buy" check to use case intake scoring template | Victoria Austin / Rachel James | TBD | Medium | Team Daily Meeting |
| 5 | Create a running notes page in the repo to capture intake questions, scoring criteria, and flywheel observations | Kee-Won Hong | TBD | Medium | Team Daily Meeting |
| 6 | Run the AI Value Platform ROI calculator internally for top use cases; compare against Stryker's submitted numbers | Team (Nicole to advise) | Before next Alfonso sync | Medium | Team Daily Meeting |
| 7 | Define what "prototype" means for each use case (scope, deliverable, goal) to avoid open-ended dependencies | Kee-Won Hong / Victoria Austin | TBD | Medium | Team Daily Meeting |
| 8 | Schedule follow-up deep-dive with Ortho JR team; prepare pre-read with targeted questions and data-sharing agenda (TrackWise schema, intake form) | Victoria Austin | TBD | High | AI CoE Deep Dive |
| 9 | Obtain current intake form and TrackWise field schema from Ortho JR team for AI intake design | Victoria Austin / Rachel James | Next JR call | High | AI CoE Deep Dive |
| 10 | Evaluate JotForm and other off-the-shelf tools as potential alternatives for complaint intake | Team | TBD | Medium | Team Daily Meeting |
| 11 | Brief Claire Gilbert on FDE project status and ROI tracking needs when she returns from leave | Joseph Kennedy / Nicole Peterson | ~2026-05-11 | High | Team Daily Meeting |
| 12 | Confirm access to AI Value Platform for full team | Nicole Peterson (confirmed done) | Completed | Low | Team Daily Meeting |

---

## Risks & Blockers

- **Risk/Blocker:** Kee-Won Hong does not yet have access to the Stryker SharePoint use case list despite Alfonso sending credentials.
  **Impact:** Delays full use case re-scoring and prioritization alignment.
  **Mitigation / Owner:** Kee-Won to follow up with Alfonso; resolve ASAP.

- **Risk/Blocker:** Stryker's existing ROI calculations for use cases are of questionable rigor (Alfonso acknowledged a prior POC produced incorrect value estimates).
  **Impact:** Risk of committing to use cases whose business case does not hold under scrutiny; downstream accountability to AI Review Board and board of directors.
  **Mitigation / Owner:** Claire Gilbert to re-interrogate ROI with business teams upon return; team to run AI Value Platform analysis in parallel.

- **Risk/Blocker:** TrackWise system instability (platform updates, outages) could cause silent failures if AI writes directly to it without a confirmation/reporting layer.
  **Impact:** Quality records could be lost or mis-populated with no visibility for specialists.
  **Mitigation / Owner:** Alessandra Chavez flagged; proposed solution is a completion/error report out to specialists after each batch run.

- **Risk/Blocker:** Intake AI must handle highly variable event narratives — from one-word descriptions ("device broken") to multi-paragraph accounts — and multi-device complaints.
  **Impact:** Complicates NLU logic and branching; intake completeness cannot be guaranteed without robust edge-case handling.
  **Mitigation / Owner:** Javier Diaz proposed per-device chunking; Victoria Austin confirmed feasibility; to be scoped during prototype phase.

- **Risk/Blocker:** Some Stryker teams may be labeling projects as "AI" to gain higher internal priority, without genuine AI applicability.
  **Impact:** FDE team could be pulled into low-value work; budget and resources diluted.
  **Mitigation / Owner:** Kee-Won Hong flagged; team to vet all use cases for genuine AI fit. Nicole and Joe endorsed vetting approach.

---

## Open Questions & Parking Lot

1. Should the future AI intake solution write directly to TrackWise (bypassing SharePoint), or should SharePoint remain as an intermediary for auditability and error recovery?
2. What is the exact TrackWise field schema for complaint records? (Required to drive AI intake branching and completeness logic.)
3. Where does the expert intake knowledge currently live — in people's heads, SOPs, or documented questionnaires? Who should be interviewed to extract it?
4. Is JotForm or another off-the-shelf tool a viable replacement for the custom intake form? (Alfonso's question; Red Cube raised for clinical research use case.)
5. What is Alfonso's/Scott Austin's approval criteria for moving a prototype to a funded production build? (Nicole suggested asking this directly.)
6. How should the AI handle product-specific intake differences (e.g., Mako robot vs. implants vs. instruments)? Master file classification seems key here — Dmytro Turchak flagged this; Javier Diaz to elaborate.
7. What is the right feedback loop mechanism to allow the intake AI to learn and improve from specialist corrections over time?

---

## Next Steps & Follow-Ups

- **Monday, 2026-05-04:** Internal sprint demo / retro with Alfonso and Scott Austin. Victoria Austin to present Label Modification prototype.
- **Upcoming:** Follow-up deep-dive session with Ortho JR PCMH Phase 2 team. Victoria Austin to send pre-read with targeted questions. Agenda to include: data sharing, TrackWise schema walkthrough, intake form review, and failure mode classification detail.
- **~2026-05-11:** Claire Gilbert returns from leave and takes ownership of ROI coordination across use cases.
- **Ongoing:** FDE team to continue parallel use case intake and scoring as access to the full 26-case SharePoint list is secured.
- **Clinical Research Deep Dive:** Separate deep-dive session with the clinical research team noted as occurring today (April 30) — Red Cube repository and AI assistant tooling to be evaluated as part of that session.
