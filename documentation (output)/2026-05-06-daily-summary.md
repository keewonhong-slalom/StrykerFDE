# Daily Summary — 2026-05-06

**Sources:**
- `raw/05-06/AI CoE _ FDE Deep Dive Ortho AI Translator .docx` — Deep dive with Ortho team on the AI Translation use case (Kee-Won Hong, Rachel James, Victoria Austin). Covered translation workflow, vendor structure, regulatory proofreading requirement, Azure Translator approach, and pilot scoping.
- `raw/05-06/Stryker FDE Team Daily Meeting.docx` — FDE team daily standup (38 min, full team + Jennifer Kwapis). Recapped the translation deep dive, reviewed the AI Use Case Hub explorer live with Joe, discussed platform team strategy, data confidentiality, and Microsoft's parallel engagement.
- `raw/05-06/Stryker FDE - Mid-Week Touchpoing.docx` — 1-hour mid-week touchpoint with Alfonso Perez and Matthew Abreu (AI CoE build manager). Deep alignment session on the full prioritization process, intake risk framework, SharePoint as source of truth, abnormal order entry POC, and lead time ML model demo.

---

## Key Information & Highlights

- **Ortho AI Translation deep dive completed.** The use case is translating regulatory product documents (Word, PDF, Excel, images) from English to German, French, and Italian — and secondarily, acquired-company languages to English. The business currently uses two vendors: a translation vendor (expensive, general) and a domain-specific proofreader (validates technical accuracy). The goal is to eliminate the translation vendor using AI, while keeping the proofreader in the loop. Victoria confirmed the solution is simply the **Azure Translator API** (an out-of-the-box API call), with no custom agent build required. The reusable component is a **best-practice runbook** on how to configure glossaries, translation memory, and human-in-the-loop evaluation — not a technical artifact. ROI is straightforward: project translation cost eliminated. **Proposed pilot: German-only subset, routed directly to proofreader, skipping translation vendor.** A 30-minute follow-up is scheduled within the week to determine prioritization.

- **Alfonso walked the team through the full AI CoE prioritization process.** Key takeaway: FDE's prototype work is the on-ramp to the formal prioritization gate, not a side track. The gate requires a validated **Rough Order of Magnitude (ROM)** from the build team (Kenneth) and a validated **projected value** from the business — both must be confirmed *before* the prioritization call, not at it. The lesson from Cycle 1: architecture (Steve) was blindsided, causing a rebuild of the entire case. PMCH 2.0 is not yet in the SharePoint list — it cannot enter the prioritization process until it is added.

- **FDE team formally reviewed the AI Use Case Hub explorer with Joe Kennedy.** Key dispositions reached live:
  - **EU Customer Service (Project Air):** In production — skip
  - **Aura AI Orchestration:** Likely the platform MVP they've been building — confirm with Alfonso
  - **Email Order Entry:** Highly similar to GFX (already being built) — potential overlap/connection
  - **Incident Analysis Assistant:** Similar to ECR use case — flag for ECR comparison
  - **ProCare Business Report Card:** Confirmed on hold (Power BI + Copilot self-service strategy)
  - **Translation (multiple):** Aligned to today's deep dive — active
  - **Mako R2:** Interesting but may be product-facing (not internal productivity); DRE team was dissolved and all product-facing AI may now fall under Scott — get guidance from Alfonso
  - **Enterprise Risk & Strategy Analyst:** Very broad; possibly cyber team — investigate before prioritizing
  - **Vocera, Mako, Enterprise Risk:** Andrew flagged as high business impact, but noted these are likely higher effort

- **Abnormal Order Entry (GQO) — Alfonso assigned FDE as POC owner.** This use case involves a machine learning model to detect anomalous customer orders (e.g., a customer accidentally ordering 510,000 units instead of 510). Impact: ~20–30 incidents/year but $5–10M per occurrence. Approach: flag the order before shipping, surface to a human reviewer — no automatic cancellation. Key constraints: data warehouse updates lag by ~1 day; fulfillment cycle is 2–3 days (enough time to intervene on large-value orders). Two model components required: (1) real-time anomaly detection; (2) baseline "what is normal" model (trained per customer over time). Victoria proposed back-testing the POC against historical known errors. Alfonso called this a "foot in the door" for GQO's $7B inventory optimization opportunity.

- **Alfonso showed live demo of the PFEP Lead Time Prediction ML model.** This is an already-running GQO initiative (started ~2 months ago): a machine learning model predicts product lead times (CDC → Holland). In one example, the system recorded 35-day lead time while the model predicted 18 days — triggering a "reduce inventory" recommendation to the supply chain planner. The planner makes the change; no automated ERP updates. Presenting to Stryker leadership in May. This model is the proof point for the GQO inventory optimization strategy: even small improvements against $7B of inventory translate to millions in savings.

- **GFX (AI Email Order Entry) context provided by Alfonso.** GFX is an existing application that converts customer email POs into SAP orders via EDI. The AI layer (already being built) determines: (1) Is this email an order? (2) Has it already been processed in SAP? (queried via Databricks). A technical issue with Microsoft Graph (email sender masking) caused a process change — the team is switching from email-based extraction to Salesforce ticket-based processing. Alfonso noted this Salesforce integration creates a natural bridge to bring Project Air (EU customer service AI) capabilities to the US market.

- **SharePoint is the single source of truth — all FDE outputs must go there.** Kenneth (AI CoE build side manager) requires all meeting recordings, notes, and deliverables in a specific SharePoint folder. Alfonso reinforced: use the existing **Comments column** for FDE notes, or create a single **"Slalom FDE" column** — do not create multiple new columns. The team committed to transferring all outstanding notes to SharePoint this week. Alfonso emphasized: if it's not in SharePoint, it doesn't exist for the prioritization process.

- **"Lanes" column to be added to the SharePoint use case list.** Alfonso and Matthew Abreu aligned on adding a "lane" column that identifies who owns each use case (Slalom FDE, Slalom Pod Team 1/2/3, internal Stryker team). This will allow FDE to filter their work cleanly from the full 200+ entry list.

- **Data confidentiality directive issued by Joe Kennedy.** The Stryker AI Use Case CSV data pulled into the FDE repo must stay within the private Stryker GitHub repository. It must not be shared broadly within Slalom or used as input to other client work.

- **Matthew Abreu (AI CoE build manager) introduced.** He manages the build-side intake and prioritization process. He explained the three intake paths: (1) formal intake form with risk questionnaire; (2) Plan View record (linked to PowerBI); (3) informal ideas (current gap — no formal capture). He is working on **lightweight ideation-stage intake guidelines** that ask minimal questions upfront, with a heavier risk review deferred to the pre-production stage.

- **Microsoft engagement creating noise.** Microsoft is selling directly to Stryker business units outside of the AICOE process — sometimes proposing use cases that are misaligned. Victoria shared that Microsoft has already selected two use cases: (1) **Clinical Research** (which FDE has already been exploring) and (2) **Quality Verification AI for Contracts** (new — not seen in the current list). Joe and Jennifer noted this needs to be managed; Joe will coordinate with Jennifer on alignment with the Microsoft reps.

---

## Decisions Made

1. **Decision:** Azure Translator API (out-of-the-box) is the translation technology; no custom agent needed.
   **Rationale:** It's a simple API call; the reusable value is a best-practice runbook, not a custom build.
   **Owner / Approver:** Victoria Austin; team concurrence

2. **Decision:** Translation pilot scope: German-only, bypass translation vendor, route directly to domain proofreader.
   **Rationale:** Lower risk, contained scope; proofreader provides feedback on quality before wider rollout.
   **Owner / Approver:** Team; to be confirmed with Ortho team at follow-up

3. **Decision:** ProCare Business Report Card → status changed to Hold.
   **Rationale:** Business intends to use Power BI + Copilot self-service; don't build what Copilot will replace.
   **Owner / Approver:** Alfonso Perez; to coordinate with Gustavo

4. **Decision:** FDE notes to go into SharePoint Comments column or a single "Slalom FDE" column — not separate systems.
   **Rationale:** Alfonso's preference to keep one source of truth; avoid column sprawl.
   **Owner / Approver:** Alfonso Perez

5. **Decision:** Abnormal Order Entry (GQO) — FDE team takes POC ownership.
   **Rationale:** Interesting ML use case with clear high-value potential; foot in the door for GQO inventory optimization.
   **Owner / Approver:** Alfonso Perez

6. **Decision:** Stryker use case data stays in private Stryker GitHub repo only — not shared broadly within Slalom.
   **Rationale:** Data confidentiality; Stryker-specific use cases must not flow into other client engagements.
   **Owner / Approver:** Joseph Kennedy

7. **Decision:** Andrew Stevenson credentials — hold for now.
   **Rationale:** His role is SME/advisory, not hands-on keyboard in the Stryker environment.
   **Owner / Approver:** Joseph Kennedy

---

## Action Items & Tasks

| # | Task | Owner | Due Date | Priority | Source |
|---|------|-------|----------|----------|--------|
| 1 | Transfer all FDE meeting notes and summaries to Kenneth's SharePoint folder | Kee-Won Hong | This week | High | Mid-week touchpoint |
| 2 | Schedule 30-min follow-up with Ortho AI Translation team to finalize prioritization | Kee-Won Hong | This week | High | Deep dive |
| 3 | Schedule 30-min follow-up with Alfonso to review remaining ideation use cases | Kee-Won Hong | End of week | High | Daily standup |
| 4 | Begin Abnormal Order Entry POC scoping (GQO ownership) | FDE team | TBD | High | Mid-week touchpoint |
| 5 | Update ProCare status to "Hold" in SharePoint; coordinate with Gustavo | Alfonso Perez | TBD | Medium | Mid-week touchpoint |
| 6 | Add "Lanes" column to SharePoint use case list | Alfonso Perez / Matt Abreu | TBD | Medium | Mid-week touchpoint |
| 7 | Research Azure Translator customization options (glossary, translation memory) | Victoria Austin | This week | Medium | Deep dive / Daily standup |
| 8 | Get clarification from Alfonso/Scott on Mako R2 scope (product vs. internal productivity) | FDE team | This week | Medium | Daily standup |
| 9 | Ensure Stryker AI Use Case CSV/data remains in private repo; lock down access | Kee-Won Hong | Immediate | High | Daily standup |
| 10 | Add Matthew Abreu's intake process context to shared notes/SharePoint | Kee-Won Hong | This week | Medium | Mid-week touchpoint |
| 11 | Develop lightweight ideation-stage intake guidelines (minimal upfront questions) | Matthew Abreu | TBD | Medium | Mid-week touchpoint |
| 12 | Coordinate with Jennifer Kwapis on Microsoft engagement alignment | Joseph Kennedy | TBD | Medium | Daily standup |
| 13 | Get context on Microsoft-selected "Quality Verification AI for Contracts" use case | Victoria Austin / FDE team | TBD | Low | Daily standup |
| 14 | Confirm Aura AI Orchestration use case = platform MVP with Alfonso | FDE team | Next Alfonso sync | Low | Daily standup |

---

## Risks & Blockers

- **Risk:** Victoria Austin pending Azure environment access (subscription, resource group).
  **Impact:** Cannot begin hands-on POC work in the Stryker AI environment.
  **Mitigation / Owner:** Alfonso coordinating with Steve; Victoria to be pulled in when ready.

- **Risk:** PMCH 2.0 not in the SharePoint AI Use Case list.
  **Impact:** Cannot enter the formal prioritization gate until it is formally submitted and listed.
  **Mitigation / Owner:** Kee-Won to ensure PMCH 2.0 is added to the SharePoint list. Alfonso needs to loop in the team.

- **Risk:** Microsoft is selling directly to Stryker business units outside of AICOE process.
  **Impact:** Creates misaligned use case expectations, duplicated work, and friction with AlfonsoÅs intake process.
  **Mitigation / Owner:** Joseph Kennedy and Jennifer Kwapis to coordinate with Microsoft reps.

- **Risk:** Abnormal Order Entry POC faces 1-day data warehouse lag vs. 2–3 day fulfillment window.
  **Impact:** Very tight window for real-time flagging; may require ERP-level integration that is significantly more complex.
  **Mitigation / Owner:** POC should validate data latency feasibility; Alfonso suggests targeting only high-value orders ($100K+) to reduce volume.

- **Risk:** GFX email masking issue (sender identity lost when AI touches email via Microsoft Graph).
  **Impact:** Slowed the GFX initiative since October/November; switching to Salesforce ticket processing.
  **Mitigation / Owner:** Alfonso / GFX build team (in progress).

- **Risk:** Building solutions that will be superseded by Microsoft Copilot native features.
  **Impact:** Wasted FDE effort; ProCare is the explicit example.
  **Mitigation / Owner:** Alfonso's standing directive: don't build what Copilot will do natively. Apply this filter to all use case evaluations.

---

## Open Questions & Parking Lot

1. Is Mako R2 internal productivity or a product feature? This determines whether it falls under Scott's scope.
2. How is Microsoft's engagement structured — advisory only, or are they building things directly?
3. When will Victoria's Azure subscription/resource group be set up?
4. Where does Clinical Research fit in the FDE pipeline given Microsoft has already selected it?
5. What exactly is the "Quality Verification AI for Contracts" use case Microsoft selected?
6. Does the GFX → Salesforce switch create a concrete bridge to Project Air US expansion?
7. What historical dataset exists for Abnormal Order Entry back-testing (to validate the POC design)?
8. What are the specific terminology/glossary needs for the Ortho labeling translation use case?
9. Is the Incident Analysis Assistant use case meaningfully different from ECR given it uses ServiceNow?
10. What is the Enterprise Risk and Strategy Analyst use case — is it from the cyber team?

---

## Next Steps & Follow-Ups

- **This week:** Kee-Won transfers all outstanding FDE notes to Kenneth's SharePoint folder.
- **This week:** 30-min follow-up with Ortho translation team to determine prioritization.
- **By end of week:** Additional 30-min session with Alfonso to review remaining ideation use cases.
- **Ongoing:** FDE team begins Abnormal Order Entry POC scoping (GQO, Alfonso-assigned).
- **Upcoming (Alfonso/Scott sync):** Raise PMCH 2.0 list status, Mako R2 scope question, Microsoft alignment.
- **TBD:** Matthew Abreu developing lightweight ideation-stage intake guidelines — FDE to track and incorporate into process.
- **Near-term:** Pod team onboarding horizon — continue pushing for top-10 backlog and shovel-ready handoff format. Joe's target: tangible outcomes in first 60–90 days.

---

## Teams Channel Message

**FDE Team Update — May 6, 2026**

Big day — a deep dive, a full backlog review with Joe, and a 1-hour alignment session with Alfonso. Lots of clarity on process, priorities, and new use cases.

**Key Highlights**
- **Ortho AI Translation deep dive completed** — solution is Azure Translator API (not a custom build); ROI is clear (replace translation vendor); pilot will target German-only to start, routed to proofreader for validation
- **Alfonso walked us through the full AI CoE prioritization process** — FDE prototypes are the on-ramp to the formal gate; ROM (from build team) + projected value (from business) must be validated *before* the prioritization call, not at it
- **Abnormal Order Entry (GQO) assigned to FDE team** — ML use case to detect anomalous customer orders (20-30/year but $5-10M impact); foot in the door for GQO's $7B inventory optimization opportunity
- **SharePoint = single source of truth** — all notes, recordings, and deliverables must go into Kenneth's SharePoint folder; FDE to use Comments column or a dedicated "Slalom FDE" column (not separate lists)
- **Data confidentiality directive** — Stryker AI use case data stays in private Stryker repo only, not shared within Slalom broadly

**Key Decisions**
- Azure Translator API is the translation solution; reusable component is a best-practice runbook, not a custom agent
- ProCare → Hold (Copilot for Power BI will handle this natively when enabled)
- Abnormal Order Entry POC → FDE takes ownership

**Coming Up / Next Steps**
- Kee-Won transferring all FDE notes to Kenneth's SharePoint folder this week
- 30-min follow-up with Ortho translation team to finalize prioritization
- End-of-week session with Alfonso to review remaining ideation use cases
- POC scoping begins for Abnormal Order Entry (GQO)

---

## Action Items Teams Message

**FDE Action Items — May 6, 2026**

**Kee-Won Hong**
- Transfer all FDE meeting notes and summaries to Kenneth's SharePoint folder *Due: This week* [High]
- Schedule 30-min follow-up with Ortho AI Translation team *Due: This week* [High]
- Schedule 30-min follow-up with Alfonso to review remaining ideation use cases *Due: End of week* [High]
- Ensure Stryker AI Use Case CSV data stays in private repo — lock down access *Due: Immediate* [High]
- Add Matthew Abreu's intake process context to shared notes/SharePoint *Due: This week* [Medium]
- Confirm Aura AI Orchestration = platform MVP with Alfonso at next sync *Due: Next Alfonso sync* [Low]

**FDE Team (Kee-Won / Victoria / Rachel)**
- Begin Abnormal Order Entry POC scoping (GQO) *Due: TBD* [High]
- Get clarification on Mako R2 scope from Alfonso/Scott *Due: This week* [Medium]
- Get context on Microsoft-selected "Quality Verification AI for Contracts" use case *Due: TBD* [Low]

**Victoria Austin**
- Research Azure Translator customization (glossary, translation memory) *Due: This week* [Medium]

**Alfonso Perez**
- Update ProCare status to "Hold" in SharePoint; coordinate with Gustavo *Due: TBD* [Medium]
- Add "Lanes" column to SharePoint use case list *Due: TBD* [Medium]
- Set up Victoria's Azure environment credentials (subscription, resource group) *Due: TBD* [High]

**Matthew Abreu**
- Develop lightweight ideation-stage intake guidelines (minimal upfront questions) *Due: TBD* [Medium]

**Joseph Kennedy**
- Coordinate with Jennifer Kwapis on Microsoft engagement alignment *Due: TBD* [Medium]

**Total action items: 14**
