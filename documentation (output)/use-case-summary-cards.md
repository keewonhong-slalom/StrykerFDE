# Stryker FDE — Use Case Summary Cards

**Generated:** 2026-05-04
**Scoring system:** T-shirt sizes (S / M / L / XL)
**Size key:**
- VALUE, REACH, DATA READINESS — larger is better (XL = highest value / broadest reach / data fully ready)
- COST, EFFORT, COST OF PRODUCTION DEPLOY — smaller is better (S = cheapest / easiest)

---

### AI-Enabled Complaint Intake (PMCH Phase 2)

An AI validation layer embedded at the point of complaint submission checks MS Form responses against required TrackWise fields in real time, surfaces data quality issues, and performs early failure-mode pre-classification before the complaint enters the specialist review queue. The solution directly targets the 40–50% of ~40K annual JR & MET complaints requiring manual follow-up due to incomplete or ambiguous intake data — compressing the 90-day closure cycle and reducing regulatory audit exposure. The current flow (MS Forms → Power Automate → SharePoint → manual review → TrackWise) has no automated validation; Phase 2 must preserve a human-in-the-loop review gate, and the UIPath RPA migration replacing Power Automate is still being scoped.

| Bucket | Weight | Size | Descriptor |
|--------|--------|------|------------|
| **VALUE** | 5 | L | Reduces rework, audit risk, and 90-day closure delays across high-volume complaint pipeline |
| **COST** | 2 | M | Moderate; requires AI validation layer, TrackWise API integration, and RPA coordination |
| **EFFORT** | 3 | L | High effort; regulated environment, multi-system integration, and HITL architecture add complexity |
| **REACH** | 4 | XL | JR & MET prototype (40K/yr) is directly scalable to 131K complaints across all Stryker divisions |
| **DATA READINESS** | 3 | M | SharePoint list and MS Form data exists; TrackWise field schema and RPA migration scope still TBD |
| **COST OF PRODUCTION DEPLOY** | 2 | L | Medical device regulatory validation, multi-system integration, and IT ownership handoff add significant production cost |

**Track:** Active — FDE prototype candidate
**Source:** 2026-04-28 Ortho JR PCMH Deep Dive; 2026-05-01 intake form and event summary

---

### UC1: Label Modification & Review

An AI comparison engine ingests the Source of Truth (Excel) and the current label preview (PDF/image), automatically diffs the two representations, and produces a structured compliance report flagging any discrepancy between them. The core pain is the double-review burden — both the Labeling team and Regulatory Affairs independently check every label revision — resulting in documented benchmarks of 1,487 hours for Brexit, 314 hours for CE Removal, and 221 hours for MRI-related label changes. A prototype is immediately achievable in 1–2 weeks using existing structured data sources from Prisym 1.6.

| Bucket | Weight | Size | Descriptor |
|--------|--------|------|------------|
| **VALUE** | 5 | L | 120× speedup (10 min → 5 sec/label); 332 hours saved per 1,000 labels reviewed across Labeling + RA |
| **COST** | 2 | L | Medical device validation overhead and Prisym integration required; not off-the-shelf |
| **EFFORT** | 3 | L | 1–2 week prototype feasible; Prisym access and before/after label examples needed |
| **REACH** | 4 | XL | JR + Trauma + global labeling platform; same engine reused directly for UC2 (Migration QA) |
| **DATA READINESS** | 3 | L | Source of Truth (Excel) and label previews (Prisym 1.6) exist; programmatic Prisym access not yet confirmed |
| **COST OF PRODUCTION DEPLOY** | 2 | L | Tool validation in med device context and onePLM cert integration add production complexity and cost |

**Track:** Active — FDE prototype (top priority)
**Source:** 2026-04-27 Ortho JR Labeling Deep Dive; 2026-04-27 scoring sheet

---

### UC3: New Label Creation & Verification

An AI assistant ingests the Label Content Form (Excel) and a translation file, auto-generates an upload-ready file for Prisym, and validates it against the source — eliminating a 22× slower manual creation process and catching upload file errors before they reach the 9-person approval chain. The annual creation volume is unknown, which limits ROI quantification, but even at conservative volume estimates the time savings on upload file creation (3 hrs → 8 min) and error prevention are material. This use case reuses the UC1 architecture, making it a high-efficiency follow-on build.

| Bucket | Weight | Size | Descriptor |
|--------|--------|------|------------|
| **VALUE** | 5 | L | 22× upload creation speedup; prevents 9-approver chain from reviewing preventable upload errors |
| **COST** | 2 | M | Reuses UC1 infrastructure; all inputs are structured Excel — lower marginal cost than UC1 |
| **EFFORT** | 3 | L | 1–2 week prototype feasible; end-to-end sample data not yet secured |
| **REACH** | 4 | L | Reuses UC1 infrastructure; applicable to Trauma labeling translations; narrower ceiling than UC1 |
| **DATA READINESS** | 3 | L | Label Content Form and upload files exist in structured Excel; end-to-end examples to be secured |
| **COST OF PRODUCTION DEPLOY** | 2 | M | Lower than UC1; no Prisym image rendering needed; same validation overhead applies |

**Track:** Active — FDE prototype (secondary, to follow UC1)
**Source:** 2026-04-27 Ortho JR Labeling Deep Dive; 2026-04-27 scoring sheet

---

### UC2: Label System Migration QA

An AI bulk-comparison engine ingests the full label catalog from Prisym 1.6 (legacy) and Prisym 360 (target), pairs records across systems using a shared identifier, and produces a structured QA report — replacing what would otherwise be 3,000 hours of manual review and directly competing against the $247,560 Falcon Tool. This is the highest raw-value use case in the labeling portfolio, but it is hard-blocked: Prisym 360 does not yet exist, and prototyping against real data is not currently possible. The UC1 prototype directly de-risks this use case and provides the comparison engine it will require.

| Bucket | Weight | Size | Descriptor |
|--------|--------|------|------------|
| **VALUE** | 5 | XL | 3,000 hrs → 16 hrs (187× speedup); directly displaces $247K Falcon Tool cost at migration |
| **COST** | 2 | XL | Very high; bulk Prisym export infrastructure from two systems (one nonexistent) required |
| **EFFORT** | 3 | XL | Very high; Prisym 360 does not exist — prototype against real data is not possible today |
| **REACH** | 4 | XL | If Prisym 360 rolls out globally, all Stryker labeling divisions benefit at migration |
| **DATA READINESS** | 3 | S | Prisym 360 label data does not exist; Prisym 1.6 access not yet confirmed |
| **COST OF PRODUCTION DEPLOY** | 2 | XL | Two-system bulk export pipeline, label pairing mechanism, and full tool validation required |

**Track:** Deferred — blocked until Prisym 360 data is accessible (~2027). UC1 prototype de-risks this use case.
**Source:** 2026-04-27 Ortho JR Labeling Deep Dive; 2026-04-27 scoring sheet

---

### UC4: International Compliance Assurance

An AI monitoring agent tracks changes to international labeling standards (via Accuris) and automatically assesses their impact against Stryker's current label portfolio and corporate SOPs — replacing a reactive, manual process in which the Regulatory Affairs team learns of global standard changes after the fact. The strategic ceiling is high (applicable to all global labeling divisions) but the use case is currently un-prototypable: Accuris data is downloaded in encrypted form with an undefined integration path, and the tool itself — which assesses regulatory compliance — would require formal validation in a recursive and complex regulatory context.

| Bucket | Weight | Size | Descriptor |
|--------|--------|------|------------|
| **VALUE** | 5 | L | Proactive compliance monitoring reduces risk of non-compliant labels remaining in market |
| **COST** | 2 | XL | Very high; Accuris encryption, undefined pipeline, and recursive tool validation are all hard blockers |
| **EFFORT** | 3 | XL | No prototypable path today; Accuris integration architecture completely undefined |
| **REACH** | 4 | XL | Applicable to all global Stryker labeling divisions if Accuris integration is resolved |
| **DATA READINESS** | 3 | S | Accuris data encrypted on download; integration path undefined; cannot assess volume or quality |
| **COST OF PRODUCTION DEPLOY** | 2 | XL | Highest production cost in portfolio — AI tool validating regulatory compliance must itself be validated |

**Track:** Deprioritized — hard-blocked on Accuris access. Revisit when integration path is defined.
**Source:** 2026-04-27 Ortho JR Labeling Deep Dive; 2026-04-27 scoring sheet

---

### ECR Description Assistant

An AI agent guides change owners (CA2s) through a 15-question structured input form and generates a compliant, comprehensive ECR description for copy/paste into onePLM — reducing write time from 15–20 minutes to 5 minutes and targeting the root cause of 25% of all non-conformities (NCs) in the T&E division, each of which triggers 15–20 hours of resolution effort. The solution is already built and piloted on Power Apps + Power Automate + Copilot Studio with positive NPS; what the team needs now is solution architecture review, proper Power Platform environment setup, and productionization hardening to safely scale from a scrappy sandbox build to 3–10 additional Stryker divisions.

| Bucket | Weight | Size | Descriptor |
|--------|--------|------|------------|
| **VALUE** | 5 | XL | Targets 25% NC root cause; each NC avoided saves 15–20 hrs remediation; ~100 hrs/yr description time saved |
| **COST** | 2 | M | Working prototype exists; productionization requires env setup, service accounts, and co-build process — not a net-new build |
| **EFFORT** | 3 | S | Core AI build is complete and piloted; FDE effort is architecture review and environment hardening, not prototyping |
| **REACH** | 4 | XL | 15 DPO questions appear generic across all divisions; 3–10 additional divisions already expressed interest |
| **DATA READINESS** | 3 | L | SharePoint KB and historical ECRs available; AI Builder training data exists but pipeline not yet implemented |
| **COST OF PRODUCTION DEPLOY** | 2 | L | Requires Power Platform environment provisioning, dev/QA/prod pipeline via Stryker IT co-build, and service account migration |

**Track:** Productionization — solution exists and works; FDE role is architecture review and hardening, not prototyping. Escalate to Alfonso for direction on resourcing model.
**Source:** 2026-05-01 Ortho ECR Assistant Deep Dive; 2026-05-01 use case brief

---

### UC1 (Clinical Research): Claim Verification & Evidence Grounding

An AI agent ingests a collateral document and its full reference set, automatically identifies all citation-relevant claims (distinguishing them from general knowledge statements), resolves garbled PDF filenames using metadata matching, maps each claim to its supporting reference(s), and produces a structured Reviewer Summary Table with a support classification, rationale, and AI confidence level per claim. This directly targets a process where 3 independent reviewer groups (Clinical, Regulatory, Legal) each spend up to 5 hours on the same review — approximately 15 hours of combined effort per collateral package — and a 65% time reduction is projected at MVP. Prior internal work on a similar claim verification use case exists (contact: Jada Berenguer, AI excellence team) and must be reviewed before new scoping begins.

| Bucket | Weight | Size | Descriptor |
|--------|--------|------|------------|
| **VALUE** | 5 | L | 65% review time reduction projected; 3 independent reviewer groups each spend 5 hrs on the same review |
| **COST** | 2 | M | MVP (no ReadCube integration) is a constrained and well-scoped build; Phase 2 adds API complexity |
| **EFFORT** | 3 | M | PDF parsing, claim identification NLU, and reference resolution are tractable; prior internal work reduces unknowns |
| **REACH** | 4 | M | Small user base (~2–5 SME reviewers); value add per user is high but total headcount impact is limited |
| **DATA READINESS** | 3 | M | PDFs and Word docs are on hand; ReadCube API ToS and non-licensed access to be confirmed; no formal accuracy rubric documented |
| **COST OF PRODUCTION DEPLOY** | 2 | M | Adobe Workfront integration and Chrome plugin / desktop automation path both under evaluation; production complexity is moderate |

**Track:** Under evaluation — conservative but promising business case; due diligence in progress. Confirm Jada Berenguer's prior work before proceeding. Decision expected at next team sync.
**Source:** 2026-04-30 Ortho Clinical Research Deep Dive; 2026-04-30 use case brief
