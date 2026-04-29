# Daily Summary — 2026-04-29

**Sources:**
- `raw/04-29/Stryker FDE Team Daily Meeting (1).docx` — ~25-minute FDE daily standup (3:30 PM UTC) with Victoria Austin, Kee-Won Hong, Rachel James, and Joseph Kennedy covering the swag scoring slide, Alfonso check-in prep, deep dive scheduling, data team coordination, and repo housekeeping.
- `raw/04-29/Stryker FDE - Mid-Week Touchpoint.docx` — ~45-minute mid-week touchpoint (7:30 PM UTC) between Kee-Won Hong, Rachel James, and Alfonso Perez (Stryker EDT) covering use case prioritization alignment, document intelligence architecture, vendor exploration, POC-to-production operating model, and SharePoint/Power BI access status.

---

## Key Information & Highlights

### Morning Daily Standup (3:30 PM UTC)

- **Swag scoring slide finalized ahead of Alfonso check-in.** Kee-Won ran the use case list through Claude as a first-pass sanity check; the AI output surfaced complaint intake and label modification as top priorities, consistent with the team's own thinking. The slide was updated before the afternoon touchpoint.

- **Scoring methodology simplified to t-shirt sizes.** The team landed on S/M/L/XL sizing across all scoring dimensions (Strategic Priority, Complexity, Financial ROI, Scalability) to avoid implying false precision while still communicating relative weight between use cases.

- **"Hold" recommendation language replaced with "Further Evaluation."** The original label felt too final; the new language reflects that the board is a dynamic prioritization tool, not a gate.

- **Column labels aligned to Alfonso's intake report framework.** The scoring columns were renamed to map directly to Alfonso's existing prioritization report: Strategic Priority, Complexity (was: Effort), Financial ROI, and Scalability (was: Reach). The intent is to signal FDE is building on, not duplicating, his process.

- **Slide talk track agreed: FDE extends Alfonso's framework.** Joe Kennedy emphasized that Alfonso should see FDE's scoring slide as a natural extension of his own intake process — giving him visibility into why specific use cases are being selected for each sprint, not a competing framework.

- **Alfonso's discovery stages identified as potential status column.** Joe found Alfonso's workflow on SharePoint: Start → Add Technical Scoping → Define Use Case → POC Needed → Funding → Execute POC → Close Discovery. The team may align the scoring slide's status entries to these stages.

- **New deep dives scheduled at 30 minutes each.** An hour-long format was not feasible this week given calendar constraints. The team accepts 30 minutes as the working norm, with additional sessions booked freely as needed — this is now standard FDE rhythm.

- **Pre-read questions to be sent before every deep dive.** Proactive question-sharing ensures attendees come prepared with documents and data, maximizing session value.

- **Data team (Data Tower) sync deferred.** Joe flagged that Scott Sacka's data team has AI-specific budget but it is project-scoped, not intended for broad data infrastructure. FDE will revisit the sync next Tuesday once deeper use case evidence exists.

- **Repo housekeeping assigned.** Kee-Won will add Obsidian setup instructions and Victoria's FDE Flywheel notes to the primary FTE repo.

---

### Afternoon Mid-Week Touchpoint with Alfonso Perez (7:30 PM UTC)

- **Full alignment reached on top 2 use cases to advance.** Alfonso confirmed strong agreement on the two priority areas the FDE team surfaced:
  1. **Label Modification Review** — OCR/document intelligence use case with a reusable template-based architecture (PDF → AI processing → JSON output). Alfonso sees this as applicable beyond labeling to contracts, QA, technician checklists, and other form-heavy workflows across the enterprise.
  2. **AI-Powered Complaint Intake Form** — An AI-enriched form/process that validates inputs against back-end data sources at time of entry, reducing downstream errors. Not necessarily a form UI — the concept is an intelligent, guided intake process.

- **New Label Creation = Phase 2; Label Migration = Future phase.** Alfonso and the team agreed New Label Creation is a logical second phase after the modification use case is proven (lower volume, similar pattern). Label Migration has too many unknowns and regulatory complexity (international translations, country-specific standards) and was deferred.

- **Vendor-first approach mandated for both use cases.** Alfonso explicitly directed the team to investigate existing market solutions before building. For the document intelligence use case, he noted the market likely has mature OCR-to-JSON tools. For the intake form, he called out **JotForm** specifically — a form-with-chatbot product that Stryker's AI Council has already pre-approved, which simplifies licensing. If a vendor solution meets requirements, FDE should leverage it rather than reinventing the wheel.

- **Preferred architecture for document intelligence.** Alfonso outlined his recommended pattern: PDFs are stored in Azure **Blob Storage** (not SharePoint directly). An Azure-based processing pipeline (Foundry + chosen LLM) picks up files, processes them, and routes outputs back to a SharePoint list or folder — transparent to end users who only see the familiar SharePoint UI. A pending/in-process/complete state machine governs the workflow.

- **Stryker context: why SharePoint is the de facto standard.** Alfonso provided important background: Stryker has grown almost entirely through acquisitions, leaving fragmented ERPs and systems. The **Accelerate** ERP standardization program (currently on Release 7) works to consolidate acquired companies, but new acquisitions continuously outpace it. Data analytics as a team is only ~2 years old. In this environment, Microsoft Forms → SharePoint → Power BI is the practical standard the business relies on — not because it is optimal, but because IT/EDT is perpetually behind business needs.

- **POC-to-production gap is a known, structural risk.** Alfonso shared context on EDT's operating model, which does not natively contemplate iterative product development. The process is designed around: project defined → built once → delivered → enhancements only via formal change requests. This creates a real gap between a quick POC and a production-ready system. Alfonso's recommended bridge is an **MVP/pilot phase** with real data flows and edge case handling before committing to the full EDT project process. He cautioned the team to expect this complexity when working with other Slalom pods as well.

- **POC timeline calibration: 1–3 weeks with real sample data.** Alfonso acknowledged the team's goal of rapid 2–3 day POCs but noted Stryker's environment makes sub-week POCs difficult. He is comfortable with 1–3 week POCs. He also confirmed that Dianette is providing real label sample files for testing; the Stryker–Slalom MSA covers the NDA, so no additional sign-off is required.

- **AI as scope-creep vector — a pattern to manage.** Alfonso flagged a recurring pattern across Stryker: business stakeholders are labeling process problems as "AI use cases" to get prioritization and funding. True AI value is often confined to a specific processing box within a larger deterministic workflow. FDE should probe whether a stated use case genuinely requires AI or whether automation alone would suffice.

- **Access update: Kee-Won confirmed; Rachel pending.** Kee-Won's system username is ready. Rachel's account hit a duplicate-name conflict (there is another Rachel James in the system) and is being resolved — Alfonso or Michael Bajestero will send her credentials once confirmed.

- **Alfonso to attempt attendance at tomorrow's Ortho Phase 2 call.** He has conflicts but will try to join at least the start of the session. He also noted his focus for that project will be scoping down version 2 of the Ortho process to a straight-line deliverable.

---

## Decisions Made

1. **Switch swag scoring to t-shirt sizes (S/M/L/XL) across all dimensions.**
   - **Rationale:** Numeric scores imply precision the team does not yet have. T-shirt sizes communicate estimates more honestly.
   - **Owner:** Kee-Won Hong.

2. **Replace "Hold" with "Further Evaluation" in the recommendation column.**
   - **Rationale:** "Hold" implies a use case is dropped. The intent is relative prioritization only.
   - **Owner:** Kee-Won Hong.

3. **Rename scoring columns to align with Alfonso's intake report (Strategic Priority, Complexity, Financial ROI, Scalability).**
   - **Rationale:** Signals FDE is building on Alfonso's existing framework rather than duplicating it.
   - **Owner:** Kee-Won Hong.

4. **Top 2 use cases confirmed for near-term prototype focus: Label Modification Review and AI Complaint Intake Form.**
   - **Rationale:** Strong team and stakeholder alignment; both cases are reusable patterns with broad enterprise applicability.
   - **Owner / Approver:** Alfonso Perez (Stryker EDT) + FDE team.

5. **New Label Creation = Phase 2; Label Migration = Future phase.**
   - **Rationale:** Label creation is a natural extension of modification work (lower volume, one-shot). Migration has too many unknowns and international regulatory complexity.
   - **Owner / Approver:** Alfonso Perez.

6. **Vendor-first approach for both priority use cases.**
   - **Rationale:** Avoid reinventing the wheel; mature market solutions likely exist. JotForm (AI Council pre-approved) identified as a candidate for the intake form use case.
   - **Owner:** FDE team to lead research; Alfonso to validate.

7. **Preferred pipeline architecture: Azure Blob Storage → Foundry/LLM → SharePoint output (transparent to users).**
   - **Rationale:** Industry-grade processing back-end with familiar SharePoint UX for end users. Avoids putting raw PDFs directly in SharePoint for processing.
   - **Owner / Approver:** Alfonso Perez.

8. **Pre-read questions to be sent to deep dive attendees before each session.**
   - **Rationale:** Maximizes value of 30-minute sessions.
   - **Owner:** FDE team (Victoria leading for labeling; team-wide norm).

9. **Data team (Data Tower) sync deferred; revisit Tuesday, May 5.**
   - **Rationale:** Not enough concrete use case data yet to make the conversation productive.
   - **Owner:** Kee-Won Hong.

---

## Action Items & Tasks

| # | Task | Owner | Due Date | Priority | Source |
|---|------|-------|----------|----------|--------|
| 1 | ~~Update swag scoring slide (t-shirt sizes, column names, "further evaluation")~~ *(completed before touchpoint)* | Kee-Won Hong | ✅ Done | High | Daily Standup |
| 2 | Research vendor solutions for document intelligence / OCR-to-JSON (market scan; JotForm, Azure Document Intelligence, others) | FDE Team | This week | High | Mid-Week Touchpoint |
| 3 | Evaluate JotForm for AI Complaint Intake Form use case (validate AI Council pre-approval, test against Stryker requirements) | FDE Team | This week | High | Mid-Week Touchpoint |
| 4 | Send labeling pre-read questions + diagramming output to team chat (Victoria) | Victoria Austin | Today | High | Daily Standup |
| 5 | Add PMCH/EMCH pre-read questions to follow-up meeting invite | Victoria Austin / Rachel James | Before EMCH follow-up | High | Daily Standup |
| 6 | Follow up on Rachel James system access (duplicate name issue — expect email from Alfonso or Michael Bajestero) | Rachel James / Alfonso | TBD (in progress) | High | Mid-Week Touchpoint |
| 7 | Once SharePoint/Power BI access is granted, import all 26 use cases and apply FDE scoring framework | Kee-Won Hong / Team | Upon access confirmation | Medium | Mid-Week Touchpoint |
| 8 | Revisit data team (Data Tower) sync readiness | Kee-Won Hong | Tuesday, May 5 | Medium | Daily Standup |
| 9 | Add Obsidian setup instructions to primary FTE repo | Kee-Won Hong | TBD | Low | Daily Standup |
| 10 | Add Victoria's FDE Flywheel notes to primary FTE repo | Kee-Won Hong | TBD | Low | Daily Standup |
| 11 | Coordinate with Dianette on delivery of real label sample files for POC testing | FDE Team / Alfonso | TBD | Medium | Mid-Week Touchpoint |
| 12 | Define the MVP/bridge framework between POC and production (in collaboration with Alfonso and Kenneth) | FDE Team + Alfonso | TBD | Medium | Mid-Week Touchpoint |

---

## Risks & Blockers

- **Rachel James system access blocked by duplicate-name conflict.** A second Rachel James exists in Stryker's system, causing a credential provisioning issue.
  - **Impact:** Rachel cannot access the SharePoint list or Power BI report needed to support prioritization work.
  - **Mitigation / Owner:** Alfonso's team (Michael Bajestero) is resolving; Rachel to watch for an email with credentials.

- **SharePoint / Power BI access not yet fully granted.** Without access, the team cannot load all 26 use cases into the scoring framework or validate column alignment with Alfonso's prioritization report.
  - **Impact:** Prioritization process is stalled on a full data set until access is confirmed.
  - **Mitigation:** Being actively resolved; Kee-Won to flag at next contact with Alfonso if not received soon.

- **POC-to-production gap in EDT operating model.** Stryker's EDT project process is designed for big-bang delivery, not iterative product development. Moving from a POC to production requires a full formal project, URS documentation, test case creation, infrastructure validation, and multiple review phases.
  - **Impact:** Risk of scope explosion and timeline slippage when transitioning promising POCs into production systems.
  - **Mitigation / Owner:** Alfonso recommends a defined MVP/pilot phase as a bridge. FDE and Alfonso to align with Kenneth (build team manager) on what this looks like in practice.

- **Data team (Data Tower) budget is project-scoped, not infrastructure-scoped.** Scott Sacka's AI budget supports specific AI projects, not the broad data infrastructure FDE use cases may require.
  - **Impact:** Potential chicken-and-egg dependency — use cases need clean data, but data team funding follows individual project approvals.
  - **Mitigation:** Maintain awareness and avoid premature commitments. Joe Kennedy will flag as project scope clarifies.

- **AI scope-creep from business stakeholders.** Business units are labeling process improvement requests as AI use cases to gain prioritization attention and funding. Genuine AI value may be confined to a small box within a larger automation workflow.
  - **Impact:** Risk of overbuilding AI components where simpler automation would suffice; or underdelivering relative to inflated stakeholder expectations.
  - **Mitigation / Owner:** FDE team to probe true AI need in every deep dive; Alfonso to assist in resetting expectations at the Stryker level.

- **30-minute deep dives may leave gaps.** Calendar constraints are forcing a shorter-than-ideal format for some use case sessions.
  - **Impact:** Key questions or documentation may not surface in a single session.
  - **Mitigation:** Pre-read questions sent in advance; additional sessions booked freely as normal FDE operating rhythm.

---

## Open Questions & Parking Lot

1. What does Alfonso's full Power BI report structure look like? Do the updated FDE scoring column names (Strategic Priority, Complexity, Financial ROI, Scalability) map cleanly once access is confirmed?
2. Should the FDE scoring slide adopt Alfonso's discovery stage labels (Define Use Case, POC Needed, Funding, Execute POC, etc.) as the status column entries?
3. What is the agreed definition and scope of the MVP/pilot phase between POC and EDT production deployment? Who owns this process definition — FDE, Alfonso, or Kenneth's build team?
4. For use cases that don't need a prototype to validate feasibility, what is FDE's alternate recommendation pathway — directly to design/architecture?
5. Which specific vendor solutions exist for template-based OCR-to-JSON document processing? What does the competitive landscape look like and who are the industry leaders?
6. Does JotForm genuinely meet Stryker's SharePoint integration and data security requirements beyond the AI Council pre-approval? What testing is needed to confirm?
7. What does Victoria's FDE Flywheel diagram look like, and does it align with Alfonso's discovery workflow?

---

## Next Steps & Follow-Ups

- **Tomorrow, 4/30 — Ortho Phase 2 deep dive:** Alfonso will attempt to attend. His framing: push for a reduced-scope, straight-line deliverable for version 2 of the Ortho process.
- **This week — EMCH follow-up deep dive:** Victoria and Rachel to finalize and send pre-read questions before the session.
- **This week — Ortho Labeling follow-up:** Victoria to share diagramming output and additional questions in Teams chat today.
- **This week — Vendor research begins:** Team to begin market scan for document intelligence tools (prioritizing Azure Document Intelligence, JotForm, and any AI-Council-approved options).
- **Upon access — Full use case import:** Once SharePoint/Power BI access is confirmed for the full team, FDE will load all 26 use cases into the scoring framework and run the prioritization exercise.
- **Tuesday, May 5 — Data Tower sync reassessment:** Kee-Won to evaluate whether FDE has enough concrete evidence to make that conversation productive.
- **TBD — MVP/pilot framework definition:** FDE team to align with Alfonso and Kenneth on how the POC-to-production bridge is defined and executed within Stryker's EDT model.
