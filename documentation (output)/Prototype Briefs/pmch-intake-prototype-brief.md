# Prototype Brief — AI-Enabled Complaint Intake (PMCH Phase 2)

**Date:** May 5, 2026
**Use Case:** AI-Enabled Complaint Intake — Ortho JR PCMH Phase 2
**Division / Team:** Joint Replacement (Ortho) — Post-Market Complaints Handling
**Prepared By:** AI Consulting Team (FDE)
**Sources:**
- `documentation (output)/Use Cases/Use Case - PMCH Intake/use-case-summary.md` — Primary use case summary with scoring, deep-dive findings, TrackWise field schema, and concrete example (PR 4316035)
- `documentation (output)/2026-04-28-daily-summary.md` — Post-deep-dive team debrief; aligned prototype scope to intake form; surfaced key unknowns
- `documentation (output)/2026-04-30-daily-summary.md` — Phase 2 deep-dive with PCMH team; RPA architecture clarified; AI intake vision aligned; multi-device chunking and confidence-threshold review model discussed
- `documentation (output)/2026-05-04-daily-summary.md` — Type A prototype (scripted intake UI) demonstrated by Rachel James; Alfonso validated prototype type framework and POC data strategy
- `raw/AI Use Case Hub.csv` — JR Post Market Complaint Handling entry; Phase 1 already in production; savings data (729 hrs/yr JR; 2,083 hrs/yr cross-divisional)
- `reference/process/FDE Flywheel.md` — Prototype taxonomy (Ulna/Radius/Metacarpal/Brachium) and goals of prototyping

---

## Executive Summary

*(Stakeholder-facing)*

Stryker's Ortho JR complaint handling team processes approximately 40,000 complaints per year, and 40–50% require time-consuming manual follow-up because the intake form captures incomplete or ambiguous information at submission. Phase 1 AI (deployed internally for failure mode classification) has already demonstrated the team's willingness and capacity to adopt AI tooling — the opportunity for Phase 2 is to push intelligence to the earliest possible moment: the intake form itself. A prototype in this space would validate whether an AI-guided intake experience can meaningfully reduce follow-up rates, confirm stakeholder alignment on the future-state vision, and provide the technical evidence needed to scope a production investment. Given that a scripted Type A prototype has already been built and demonstrated, the next logical step is a Type B technical spike to prove the core AI feasibility (real-time field validation and failure mode pre-classification from unstructured narrative), followed by a Type C working demo if the spike succeeds. Success means the JR team confirms the AI-guided experience reflects their vision and that the core AI task is feasible on synthetic data.

---

## Use Case Context

*(Reference — for full detail see: `documentation (output)/Use Cases/Use Case - PMCH Intake/use-case-summary.md`)*

**Problem Statement:**
The JR complaint intake process is fragmented across MS Forms, Power Automate / RPA, SharePoint, and TrackWise. No automated validation exists at the point of submission, so specialists must manually vet every incoming form before entering records into TrackWise — consuming significant FTE time and introducing delays that risk the 90-day closure target and create regulatory audit exposure under 21 CFR Part 820.

**Current State:**
- Flow: MS Forms → Power Automate / RPA → SharePoint → manual specialist review → TrackWise
- ~40,000 complaints/year (JR & MET); 131,000 enterprise-wide
- 40–50 FTE working complaints today
- 40–50% of submissions require at least one manual follow-up contact due to incomplete data
- Concrete example: PR 4316035 required 3 follow-up contacts over 13 days to obtain information that should have been captured at intake
- Phase 1 AI (failure mode classification against the Master File) already in production, running on a Mon/Fri schedule; handles straightforward cases with human review
- UIPath RPA migration (replacing Power Automate) is in progress; scope is undefined

**Proposed Future State:**
An AI agent operates at the intake form itself — guiding complaint submitters (typically field reps) through a branching, intelligent form that pre-populates known fields from event narratives, skips irrelevant questions, surfaces inconsistencies, detects multi-device submissions and offers to chunk them, and performs failure mode pre-classification at submission time. High-confidence, complete records are fast-tracked; lower-confidence or incomplete records are flagged for specialist review before TrackWise entry and customer contact. No submission goes directly to TrackWise without a human review gate.

**Stakeholders:**
| Name | Role |
|------|------|
| Niall Murphy | JR Complaints — primary SME |
| Alessandra Chavez | JR Complaints — process and architecture |
| Javier Diaz | JR Complaints — proposed multi-device chunking |
| Dmytro Turchak | JR Complaints — Master File / product specifics |
| Rachel James | FDE — primary prototype owner (PMCH Intake) |
| Victoria Austin | FDE — technical support |
| Kee-Won Hong | FDE — team lead |

---

## What the Prototype Should Prove

The following hypotheses are ordered by risk level. The prototype program should de-risk the highest-priority items first.

**1. Requirements validation**
> *Does the AI-guided intake experience actually reflect what the JR team has in mind when they describe an "intelligent form"?*
The Type A prototype (scripted) already frames this question for Alfonso. The next step is to confirm the same with the JR business team (Niall, Alessandra, Javier) — do they see themselves and their users in the demo? Would field reps actually use this over the current MS Form?

**2. Technical feasibility — real-time field validation**
> *Can an LLM reliably detect incomplete or ambiguous TrackWise-required fields in a free-text event description, in real time, at the point of submission?*
This is the highest-priority technical unknown. The TrackWise PI Required Fields schema is documented (see use case summary) — validating that an AI layer can meaningfully assess completeness against this schema, on sample/synthetic data, would be the core output of a Type B spike.

**3. Technical feasibility — failure mode pre-classification**
> *Can the AI deliver a plausible failure mode pre-classification at intake, reducing or replacing the current post-submission batch process (Phase 1)?*
Phase 1 classification runs on a scheduled basis and requires a human review loop. Moving this to intake requires the classifier to work on partial data (the narrative as submitted, before specialist enrichment). Feasibility and accuracy delta between the current model and an intake-time model is unknown.

**4. Technical feasibility — multi-device chunking**
> *Can the AI detect that a single narrative references multiple distinct devices and offer a structured split before submission?*
This was raised by Javier Diaz and is already partially demonstrated in the Type A prototype. A Type B spike could validate this on real-style event narratives.

**5. Expected impact**
> *Does the prototype generate enough signal to estimate: (a) reduction in follow-up contacts, (b) specialist time saved per complaint, and (c) uplift in intake data quality?*
The benchmark is concrete: PR 4316035 required 3 follow-up contacts over 13 days. Even a synthetic prototype should be run against a representative set of complaint narratives to estimate how many would be flagged vs. passed at intake.

**6. Stakeholder alignment**
> *Does the JR team confirm this is the right experience, and would they endorse moving to a production investment?*
This is the ultimate gate. The framing established for Alfonso — "Is this the experience you had in mind when you described an intelligent form?" — should be extended to the JR SME team.

---

## Prototype Scope

### In Scope

- **AI-powered intake form UX** — a web or chat-style interface presenting an intelligent, branching complaint intake flow to a simulated field rep user
- **Real-time field validation** — LLM assesses submitted event narrative against TrackWise PI Required Fields; flags missing or ambiguous required fields with specific, actionable prompts
- **Multi-device chunking** — AI detects multiple-device scenarios from the narrative and offers to separate them into distinct records
- **Failure mode pre-classification** — AI suggests a failure mode classification at intake time, surfaced to the submitter (and optionally to the specialist reviewer)
- **Confidence-threshold routing** — UI distinguishes between high-confidence complete records (green / fast-track) and flagged records (yellow/red flag for specialist review)
- **Synthetic / sample data only** — per Alfonso's direction, no production TrackWise data required for the prototype; use fabricated or anonymized sample complaints
- **Demonstration of 2–3 representative complaint scenarios** — at minimum: (1) vague narrative triggering validation prompts; (2) multi-device narrative triggering chunking; (3) straightforward submission passing through cleanly

### Out of Scope (First Prototype)

- **TrackWise integration** — no live read/write to TrackWise; data flow to TrackWise is mocked or omitted. Reason: integration requires Stryker IT involvement and is not needed to validate the AI experience or feasibility
- **RPA / UIPath interaction** — the prototype does not touch the existing RPA architecture. Reason: RPA migration scope is undefined and represents a separate workstream
- **SharePoint integration** — no live connection to the existing SharePoint intermediate store
- **Production security / SSO / Stryker environment** — prototype runs outside the Stryker environment on synthetic data. Reason: access and security approvals are blockers that should not constrain Type A/B/C work
- **Phase 1 model integration** — the existing failure mode classifier (Phase 1) is not directly integrated; the prototype implements its own classification logic or mocks it. Reason: Phase 1 architecture details are unknown; integration can be scoped once feasibility is confirmed
- **Multi-division rollout** — scope is JR only; enterprise expansion to 131K complaints is a production-stage decision
- **Full end-to-end workflow** — the prototype covers the intake moment only (submission → validation → routing decision); specialist review UI and TrackWise population are out of scope

### Prototype Type Options

*(Reference: FDE Flywheel — `reference/process/FDE Flywheel.md`)*

The Type A scripted prototype has already been built and demonstrated. The question is what comes next.

| Type | Timebox | What It Proves | Fits This Use Case If... |
|------|---------|----------------|--------------------------|
| **Ulna (A)** | 24–48 hrs | Single user story, scripted, no live AI | *(Already done — Rachel James, demonstrated 2026-05-04)* |
| **Radius (B)** | 24–48 hrs | Single AI/data task — technical spike, minimal UI | The primary remaining risk is **technical feasibility** of real-time field validation and/or failure mode classification from unstructured narrative |
| **Metacarpal (C)** | 48–72 hrs | Multi-skillset (AI + CX), live AI interaction, single user story | Type B has confirmed the AI task is feasible; team is ready to show a working, interactive demo to the JR business team |
| **Brachium (D)** | 1–3 weeks | Multi requirements, Stryker system integration, pilot-ready, generates metrics | IT readiness confirmed, leadership sign-off obtained, and the team needs production-quality performance data to justify the productionization investment |

> **Suggested progression:** The Type A prototype has already validated the experience direction with Alfonso. The recommended next step is a **Type B spike** on real-time field validation (24–48 hrs, Rachel James), followed by a **Type C demo** combining the UX (from Type A) with live AI (from the spike) for presentation to the JR SME team. Type D would be the gate for a production pilot and should not be entered until the JR team has seen and endorsed the Type C output.

---

## Required Data & Integrations

| Component | Type | Source / System | Availability | Notes |
|-----------|------|-----------------|--------------|-------|
| TrackWise PI Required Fields schema | Reference / validation logic | Documented in use case summary | **Available** — documented in `use-case-summary.md` | Use as the completeness target for AI validation |
| Sample complaint event narratives | Synthetic / anonymized test data | Fabricated or drawn from PR 4316035 (in use case summary) | **Available (synthetic)** | Do not use production complaint records; Alfonso directed synthetic-first |
| Product catalog / failure mode taxonomy (Master File) | Classification reference | Stryker internal — TrackWise | **Unknown** — Dmytro Turchak flagged this; not yet shared | Required for failure mode pre-classification; may need to be mocked for prototype |
| Phase 1 failure mode classifier (inputs/outputs/API) | Integration reference | Stryker internal AI system | **Unknown** — architecture not yet shared | Needed to assess integration path for Phase 2; not required for Type B spike |
| Current intake form (MS Form) | UX reference | Stryker SharePoint | **Pending** — action item from 04-30 deep dive | Required to ensure the prototype intake flow covers all current form fields |
| TrackWise field schema (full) | Integration spec | Stryker — TrackWise | **Pending** — action item from 04-30 deep dive | Full schema needed to design AI branching logic; PI Required Fields are documented but full schema not yet obtained |
| Complaint records (anonymized) for benchmarking | Evaluation dataset | TrackWise historical data | **Unknown** — 10 years of historical data exist per AI Use Case Hub | Useful for measuring classification accuracy; not needed for Type B/C |

**Dependencies requiring Stryker IT / data governance:**
- Access to the Master File / failure mode taxonomy for prototype testing (even a sample or mock version)
- Full TrackWise field schema (can be requested from Niall Murphy / Alessandra Chavez; does not require IT)
- Phase 1 classifier architecture details (Dmytro Turchak / internal AI team)

---

## Build Plan

### Phase 1 — Setup & Alignment *(~1–2 days)*
- [ ] Present Type A prototype to JR SME team (Niall, Alessandra, Javier) — confirm vision alignment and gather feedback
- [ ] Obtain current MS Form intake form from JR team (Victoria Austin / Rachel James)
- [ ] Obtain TrackWise full field schema from JR team (Victoria Austin)
- [ ] Request sample/mock version of Master File / failure mode taxonomy from Dmytro Turchak
- [ ] Define 3–5 representative complaint scenarios for prototype testing (fabricated narratives covering: vague, multi-device, product-specific, and clean/complete)
- [ ] Confirm build assignments: Rachel James (AI layer + intake logic), Victoria Austin (UX support if needed for Type C)

### Phase 2 — Type B Spike: AI Field Validation *(24–48 hrs)*
- [ ] Implement LLM-based field completeness check against TrackWise PI Required Fields, given an unstructured event narrative input
- [ ] Test against 3–5 fabricated complaint narratives representing the target scenario range
- [ ] Implement multi-device chunking detection (LLM identifies multiple product references and prompts for separation)
- [ ] Implement failure mode pre-classification mock — LLM assigns candidate failure mode from a simplified or mocked taxonomy
- [ ] Document outputs: accuracy/plausibility of validation flags, chunking quality, classification quality, latency
- [ ] **Go/no-go decision:** Is AI field validation sufficiently reliable to proceed to Type C?

### Phase 3 — Type C Working Demo: AI + UX Integration *(48–72 hrs)*
*(Proceed only if Type B spike confirms feasibility)*
- [ ] Integrate live AI layer into the scripted UI from Type A prototype
- [ ] Implement confidence-threshold routing UI (green / yellow-red flag distinction)
- [ ] Prepare 3 scripted demo scenarios (vague narrative, multi-device, clean submission)
- [ ] Run internal review with FDE team before presenting to JR team
- [ ] Present to JR SME team (Niall, Alessandra, Javier, Dmytro); collect structured feedback

### Phase 4 — Demo & Stage Gate *(~1 day)*
- [ ] Run demo session with JR business team and collect structured feedback
- [ ] Document: which scenarios resonated, what was missing, what would block adoption
- [ ] Record explicit answer to: "Is this the experience you had in mind?"
- [ ] Update prototype brief with outcomes
- [ ] Stage gate decision: proceed to scoping Type D / production investment, run another iteration, or pivot

---

## Team Composition

| Role | Responsibility | Notes |
|------|----------------|-------|
| AI Engineer / Prototype Owner | LLM prompt design, field validation logic, classification, multi-device chunking | **Rachel James** (primary — already owns Type A prototype) |
| CX / UX | UI integration for Type C; intake form UX design | **Victoria Austin** (support for Type C; not needed for Type B spike) |
| FDE Lead | Scope management, stakeholder communication, this brief | **Kee-Won Hong** |
| Stryker SME — Process | Intake flow, TrackWise requirements, feedback during demo | **Niall Murphy, Alessandra Chavez** |
| Stryker SME — AI / Data | Master File, failure mode taxonomy, Phase 1 architecture | **Dmytro Turchak** |
| Stryker SME — Technical | Multi-device / product-specific intake logic | **Javier Diaz** |
| IT / Platform | *Not required for Type B/C.* Required for Type D (Stryker environment, SSO) | Flag early if Type D becomes the next stage |

---

## Success Criteria

| Criterion | How Measured | Threshold for Success |
|-----------|-------------|----------------------|
| JR team confirms the AI-guided intake experience reflects their vision | Demo session feedback — explicit "yes" to "Is this the experience you had in mind?" | At least Niall Murphy and Alessandra Chavez confirm alignment |
| LLM field validation correctly identifies incomplete records | Type B spike — AI output vs. TrackWise PI Required Fields on 5 synthetic narratives | ≥ 4 of 5 narratives produce accurate, actionable validation flags with no significant false negatives on mandatory fields |
| Multi-device chunking works on representative narratives | Type B spike — AI correctly detects 2-device narratives and proposes split | Detection rate ≥ 3 of 3 multi-device test cases |
| Failure mode pre-classification produces a plausible candidate | Type B spike — AI classification vs. expected category on synthetic data | Plausible classification (top-1 or top-3) on ≥ 3 of 5 test narratives; exact match not required at this stage |
| Confidence-threshold routing is intuitive to JR team | Demo session observation — do specialists understand the green/yellow/red routing? | No significant confusion from at least 2 JR SMEs during demo walkthrough |
| Prototype runs without Stryker environment dependencies | Build verification | Prototype executes end-to-end on synthetic data with no Stryker system access required |

---

## Open Questions & Dependencies

1. **What exactly does the current MS Form ask?** Full field list needed to ensure prototype intake flow covers all current inputs. — Owner: Rachel James / Victoria Austin (request from JR team) | Urgency: **High** (blocks Type C UX design)

2. **What is the TrackWise full field schema?** PI Required Fields are documented; the full schema including branching triggers (e.g., when "Complaint Required = Yes" enables additional fields) is needed to design the AI branching logic. — Owner: Victoria Austin (request from Alessandra Chavez) | Urgency: **High**

3. **What is the Master File / failure mode taxonomy structure?** Needed to implement or mock failure mode pre-classification. Even a simplified version (top-level categories) would unblock the spike. — Owner: Rachel James (request from Dmytro Turchak) | Urgency: **High** (blocks Type B classification task)

4. **What are the inputs and outputs of the Phase 1 classifier?** Understanding the Phase 1 architecture is critical to assessing whether Phase 2 can build on it or must replace it. — Owner: Kee-Won Hong (follow-up with Dmytro / internal AI team) | Urgency: **Medium** (not blocking Type B, but shapes Phase 2 architecture)

5. **Is the UIPath/RPA migration already in flight, and who owns it?** If RPA is being replaced, the production path for a Phase 2 intake AI changes. The prototype is decoupled from this, but it affects the productionization plan. — Owner: Kee-Won Hong (follow-up with Alessandra) | Urgency: **Medium**

6. **Should JotForm or another off-the-shelf tool be evaluated as an alternative to a custom intake solution?** Alfonso directed a build-vs-buy check. This should be completed before committing to a custom build plan. — Owner: Victoria Austin / Rachel James | Urgency: **Medium** (does not block Type B spike, but should be resolved before investing in Type C)

7. **What is the right feedback loop mechanism for the intake AI to improve over time from specialist corrections?** Relevant to production design; not blocking prototype work. — Owner: TBD | Urgency: **Low**

8. **How should the AI handle product-specific intake differences (Mako robot vs. implants vs. instruments)?** Flagged by Dmytro Turchak. Master File classification may drive this. — Owner: Dmytro Turchak to elaborate | Urgency: **Medium** (relevant to classification accuracy; can be scoped post-spike)

---

## Stage Gate Decision Criteria

At the conclusion of the Type C demo session, the team must answer:

| Question | Yes → | No → |
|----------|-------|------|
| Did the JR team confirm the AI intake experience reflects their vision? | Proceed to scoping Type D / production investment | Return for another iteration; identify what was missing |
| Is real-time field validation technically feasible on synthetic data? | Proceed to Type C with confidence | Pivot approach — consider alternative validation logic or descoped AI task |
| Is failure mode pre-classification at intake feasible and useful? | Include as a production requirement | Defer to post-intake step; keep Phase 1 architecture as-is |
| Is multi-device chunking working reliably? | Include as a production requirement | Descope for initial production; revisit as enhancement |
| Has the build-vs-buy check been completed? | Confirm custom build is the right path | Evaluate JotForm / alternative tool before committing sprint capacity |
| Is Stryker IT readiness sufficient for Type D? | Enter Type D gate process | Hold at Type C; allow IT to catch up before committing |

---

## Related Artifacts

- `documentation (output)/Use Cases/Use Case - PMCH Intake/use-case-summary.md` — Full use case summary with scoring, TrackWise schema, and PR 4316035 example
- `documentation (output)/2026-04-28-daily-summary.md` — Initial prototype scope decision (intake form focus)
- `documentation (output)/2026-04-30-daily-summary.md` — Phase 2 deep dive; RPA architecture; AI intake vision alignment
- `documentation (output)/2026-05-04-daily-summary.md` — Type A prototype demo; Alfonso's POC data strategy; prototype type framework validation
- `raw/AI Use Case Hub.csv` — "JR Post Market Complaint Handling" entry (row 32); Phase 1 status and savings data
- `reference/process/FDE Flywheel.md` — Prototype taxonomy and intake process framework
