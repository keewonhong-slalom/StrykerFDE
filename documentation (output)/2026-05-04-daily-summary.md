# Daily Summary — 2026-05-04

**Sources:**
- `raw/05-04/Stryker FDE Team Daily Meeting.docx` — Internal FDE team daily standup (Kee-Won Hong, Victoria Austin, Rachel James, Joseph Kennedy, Andrew Stevenson). Covered SharePoint access resolution, pod team structure and delivery model, prototype type framework (A/B/C/D), live demos of the Complaint Intake and Labeling prototypes, and plan for the afternoon Alfonso sync.
- `raw/05-04/Stryker FDE - Weekly Sync.docx` — Weekly sync with Alfonso Perez, Nicole Peterson, Joe Kennedy, Kee-Won Hong, Victoria Austin. Alfonso reviewed the prototype type framework, validated the Labeling diff-checker demo with full approval, discussed POC data strategy (sample data by default), and confirmed sprint priorities for the week.

---

## Key Information & Highlights

- **SharePoint access fully resolved for Kee-Won Hong.** Kee-Won is now inside the Stryker environment and has uploaded the full AI value case backlog (200+ entries) to the repo. Access for Victoria Austin is in progress — Alfonso will send a screenshot of credentials; MFA approval must be triggered by Stryker IT. Rachel James also pending MFA. The access process requires a Stryker internal contact to open the encrypted email and IT to complete MFA over the phone — a two-step process that should be communicated to any future team members being onboarded.

- **Prototype type framework (A/B/C/D) defined and validated by Alfonso.**
  - **Type A:** Scripted UX demo, 24–48 hrs, no live AI — validates experience direction and confirms requirements with the business.
  - **Type B:** Technical spike, 24–48 hrs — proves a single AI/data capability is feasible.
  - **Type C:** Combined UX + AI working demo on synthetic data — validates end-to-end feasibility.
  - **Type D:** MVP-level pilot with real/production data — gated decision, requires group sign-off, generates metrics to inform production investment decision. Typically full sprint(s) of FDE capacity.
  - Alfonso added: prototypes do not have to be custom builds — vendor tools or reusable platform components can serve as the POC vehicle if they address the need.

- **Labeling diff-checker prototype (Type B) demoed live to Alfonso and received full endorsement.** Victoria Austin demonstrated a working prototype using Azure Document Intelligence + OpenAI image understanding + custom Python, running on FDA sample labels. The tool extracts structured fields and symbols from two PDFs and produces a color-coded diff report. Alfonso called it "exactly what they're looking for" and gave his "full blessing" to show the Ortho JR labeling team. He emphasized the high reusability of this PDF-to-JSON extraction approach across many other Stryker use cases (contracts, ECRs, etc.).

- **Complaint intake Type A prototype (Rachel James) demonstrated.** Rachel built a scripted UI prototype showing two complaint intake scenarios: (1) LLM flagging a vague event description ("broke device") and prompting for more detail, and (2) multi-device chunking — detecting that a complaint references two distinct devices and offering to split them. Joe Kennedy described it as "cool" and noted it demonstrates capabilities fast. The framing for Alfonso will be: "Is this the experience you had in mind when you described an intelligent form?"

- **Pod team delivery model clarified by Joe Kennedy.** Two durable pod teams are being built: a small pod and a medium pod. The FDE team's role is to deliver near-shovel-ready use cases to them — validated business case, clear requirements, and a starter prototype or repo. The small pod will share a product owner/solution owner; the medium pod will have its own SO. Stryker employees will be embedded in the pods. FDE is not responsible for discovery within the pod teams — that work should be done before handoff.

- **POC data strategy confirmed by Alfonso.** POCs should use sample/synthetic data by default to avoid delays from data access approvals. Production data access can be pursued in the MVP (pilot) stage. Alfonso warned against two failure modes: POCs built on overly curated data that fail in the real world, and POCs so large they get blocked by approvals.

- **Week priorities set.** (1) Follow-up with Ortho JR labeling team to present prototype and gather deeper requirements. (2) Schedule additional deep dives (PMCH already on calendar). (3) Review the 200-entry AI backlog and begin prioritization, aligning to Alfonso's existing scoring framework while raising gaps or misalignments. (4) Begin defining the FDE-to-pod-team handoff process and artifact standard.

---

## Decisions Made

1. **Decision:** Prototype type framework (A/B/C/D) is adopted as the team's shared language for scoping and communicating prototype work.
   **Rationale:** Eliminates ambiguity in sprint planning, client communication, and pod team handoffs. Alfonso validated the framework; Joe Kennedy confirmed it aligns with how the AI review board will think about investment sizing.
   **Owner / Approver:** FDE team (Kee-Won Hong, Victoria Austin, Rachel James); Alfonso validated.

2. **Decision:** POCs to use sample/synthetic data by default; production data only at MVP/pilot stage.
   **Rationale:** Avoids weeks of data access approval delays that have blocked prior Stryker AI projects. Alfonso explicitly directed this approach.
   **Owner / Approver:** Alfonso Perez.

3. **Decision:** Labeling diff-checker prototype (Type B) approved for presentation to the Ortho JR labeling team.
   **Rationale:** Alfonso confirmed it addresses exactly what the labeling team is looking for and validated the extensibility of the PDF-to-JSON extraction approach for multi-use-case reuse.
   **Owner / Approver:** Victoria Austin (prototype owner); Alfonso (approver).

4. **Decision:** Type D prototypes are gated — require group sign-off before FDE team commits full sprint capacity.
   **Rationale:** Level D prototypes consume significant FDE resources (full sprints) and should only be initiated when there is sufficient evidence of value and a clear path to production. Stryker IT involvement is a dependency that has historically caused delays.
   **Owner / Approver:** Kee-Won Hong / Joe Kennedy.

5. **Decision:** FDE team will review and prioritize the 200-entry AI backlog iteratively, aligning with Alfonso's framework while flagging misalignments rather than simply matching Stryker's existing scoring.
   **Rationale:** Alfonso explicitly asked the team to raise gaps or improvements in the current prioritization approach rather than just conforming to it.
   **Owner / Approver:** Kee-Won Hong; Alfonso to review.

---

## Action Items & Tasks

| # | Task | Owner | Due Date | Priority | Source |
|---|------|-------|----------|----------|--------|
| 1 | Schedule follow-up with Ortho JR labeling team to present Labeling prototype and gather requirements | Kee-Won Hong | This week | High | Weekly Sync |
| 2 | Present Labeling diff-checker prototype (Type B) to Ortho JR labeling team | Victoria Austin | This week | High | Weekly Sync |
| 3 | Reschedule Alfonso recurring sync to a time that works for Rachel James | Kee-Won Hong | ASAP | High | Daily Meeting |
| 4 | Complete Victoria Austin's Stryker access (Alfonso to send credentials screenshot; IT to set up MFA) | Alfonso Perez / Victoria Austin | ASAP | High | Weekly Sync |
| 5 | Complete Rachel James's Stryker access (credentials sent; MFA pending IT call) | Alfonso Perez / Rachel James | ASAP | High | Weekly Sync |
| 6 | Begin reviewing 200-entry AI backlog and scoring for prioritization alignment with Alfonso's framework | Kee-Won Hong / Team | This week | High | Daily Meeting + Weekly Sync |
| 7 | Define and document the FDE-to-pod-team handoff process and artifact standard | Kee-Won Hong / Team | This week | High | Daily Meeting |
| 8 | Refine Complaint Intake Type A prototype (Rachel James) and prepare framing for Alfonso demo | Rachel James | TBD | Medium | Daily Meeting |
| 9 | Add "prototype type" framing to use case scoring and sprint capacity deck for Alfonso | Kee-Won Hong | Before next Alfonso sync | Medium | Daily Meeting |
| 10 | Add "reusability / extensibility" dimension to prototype scoping framework per Alfonso's feedback | Kee-Won Hong / Victoria Austin | TBD | Medium | Weekly Sync |
| 11 | Plan path to run prototype in Stryker environment once access is available; coordinate with Stryker IT | Victoria Austin | TBD | Medium | Daily Meeting |
| 12 | Add build-time estimates (small pod / medium pod, # weeks) to use case scoring for backlog review | Kee-Won Hong / Team | Before next Alfonso sync | Medium | Daily Meeting |
| 13 | Document Stryker access onboarding two-step process for future pod team members | Kee-Won Hong | TBD | Low | Daily Meeting |

---

## Risks & Blockers

- **Risk/Blocker:** Victoria Austin and Rachel James still do not have Stryker system access; Victoria is blocked on the same credential/MFA process Kee-Won resolved today.
  **Impact:** Both team members cannot access Stryker tools, backlog, or data. Affects ability to run prototypes in Stryker's environment.
  **Mitigation / Owner:** Alfonso to send credentials screenshot for Victoria; Stryker IT to initiate MFA call for both Rachel and Victoria.

- **Risk/Blocker:** Prototype demos create implicit client expectation of immediate enterprise delivery ("Can I download it tomorrow?").
  **Impact:** Risk of business stakeholders misunderstanding prototype scope as production-ready delivery.
  **Mitigation / Owner:** Joe Kennedy flagged; Victoria Austin and Kee-Won Hong to include clear prototype type labeling in all presentations. Alfonso acknowledged and is aligned.

- **Risk/Blocker:** 200-entry AI backlog contains likely stale or low-quality entries that have not been triaged.
  **Impact:** Risk of prioritizing use cases based on volume rather than merit; FDE team could spend time on non-viable items.
  **Mitigation / Owner:** Kee-Won Hong to lead backlog review and triage this week; apply FDE scoring rubric.

- **Risk/Blocker:** Type D prototypes require Stryker IT involvement, which has historically caused delays on prior projects (Andrew Stevenson noted this pattern).
  **Impact:** Full-sprint prototypes requiring Stryker environment access may be blocked.
  **Mitigation / Owner:** Type D prototypes gated; team to coordinate early with Stryker IT when a Type D is approved.

---

## Open Questions & Parking Lot

1. What is the right internal name / metaphor for the prototype types? (Bones of the arm was proposed — ulna, radius, metacarpal — but not finalized. "Type A/B/C/D" is the working label for now.)
2. Will Stryker pod team members be AI-enabled (trained on tooling)? Kee-Won's assumption is yes — how does that change the handoff artifact standard?
3. For the AI backlog (200 entries): what is Alfonso's current scoring methodology, and how does it compare to FDE's rubric? Where should the team flag misalignments?
4. What does the "starter repo" handed off to pod teams look like as a standard artifact? (Kee-Won mentioned giving them a pre-loaded repo — needs definition.)
5. Should a "reusability / extensibility" dimension be formally added to the use case scoring rubric per Alfonso's feedback?

---

## Next Steps & Follow-Ups

- **This week:** Follow-up session with Ortho JR labeling team — Victoria to present diff-checker prototype and gather deeper requirements.
- **This week:** Begin AI backlog review and prioritization (200 entries, align to Alfonso's framework).
- **This week:** Define FDE-to-pod handoff process and artifact standard.
- **ASAP:** Resolve Stryker system access for Victoria Austin and Rachel James.
- **Before next Alfonso sync:** Update use case scoring deck with build-time estimates (pod size + duration) and prototype type framework.
- **Upcoming:** PMCH deep-dive follow-up already on calendar; additional deep dives to be scheduled as backlog review progresses.
- **~3 weeks:** Platform pod team and use case pod teams expected to land — FDE team must have clear backlog prioritization and handoff artifacts ready.
