---
use_case: AI-Enabled Complaint Intake
source: 4/28/2026 Ortho JR PCMH Deep Dive (raw/4282026 Ortho JR PCMH Deep Dive.pdf, reference/PMCH_Phase_2.pptx); TrackWise PI Required Fields Appendix; Event Summary Report PR 4316035 (5/1/2026); Intake Form (4/30/2026)
date_generated: 2026-04-28
date_updated: 2026-05-01
---

---

### AI-Enabled Complaint Intake

An AI layer embedded at the point of complaint submission validates field rep MS Form responses against required TrackWise fields, surfaces data quality issues in real time, and performs early failure mode pre-classification before the complaint enters the specialist review queue. The solution directly targets the 40–50% of ~40K annual JR & MET complaints that require manual follow-up due to incomplete or ambiguous intake data, reducing rework, compressing the 90-day closure cycle, and lowering regulatory audit exposure. The current flow—MS Forms → Power Automate → SharePoint list → manual specialist review → TrackWise—contains no automated validation; any Phase 2 solution must preserve a human-in-the-loop review gate, and the UIPath RPA migration replacing Power Automate is still being scoped.

| Bucket | Weight | Score (1–5) | Descriptor |
|--------|--------|-------------|------------|
| **VALUE** | 5 | 4 | Reduces rework, audit risk, and 90-day closure delays across high-volume complaint pipeline |
| **COST** | 2 | 3 | Moderate cost; requires AI validation layer, TrackWise API integration, and RPA coordination |
| **EFFORT** | 3 | 2 | High effort; regulated environment, multi-system integration, and HITL architecture add complexity |
| **REACH** | 4 | 5 | Intake process is universal; JR & MET prototype (40K/yr) is scalable to 131K complaints across all Stryker divisions |

> **Composite Score: 52 / 70**

---

## Scoring Assumptions & Flags

- **VALUE (4)**: Scored conservatively vs. 5 because Phase 1 already addressed failure mode classification for straightforward cases; Phase 2 is incremental improvement on an established foundation.
- **COST (3)**: Architecture for RPA replacement (UIPath) is undefined; if the intake application is net-new rather than a forms enhancement, cost pressures up toward 2. *Revisit after architecture session.*
- **EFFORT (2)**: Low score reflects the regulated medical device context (TrackWise validation, 21 CFR Part 820 traceability requirements), multi-system touchpoints, and the dependency on IT to own the automation long-term.
- **REACH (5)**: Stryker explicitly noted complaint intake "applies across Stryker" — the 40K JR & MET volume is the prototype; 131K enterprise-wide is the ceiling.

---

## Key Details from Deep Dive (4/28/2026)

**Problem framing**
- Front-end intake is fragmented: MS Forms → Power Automate email → SharePoint list → manual review → TrackWise
- No automated data validation; specialists manually vet form content for typos and missing fields before TrackWise entry
- 40K complaints/year (JR & MET); 131K across all Stryker divisions
- Metric: close within 90 days; current delays create poor customer experience and regulatory audit risk
- 40–50 FTE working on complaints today

**Phase 1 context**
- Built in-house AI to classify failure mode against the Master File
- Runs on a scheduled basis (Mon/Fri); AI handles straightforward cases, team reviews and provides feedback
- Categorization happens at the complaint (child) level, not the PI (parent) level

**Phase 2 focus**
- Make the intake "front door" smarter, cleaner, faster, and more compliant
- Standardize intake channel (MS Forms or equivalent; eliminate phone/email intake)
- Add failure mode pre-classification earlier — at the point of form submission
- Key goal: **completeness and data quality at intake**
- Replacing Power Automate with UIPath (rationale and scope TBD — follow-up needed)

**Architecture constraints**
- A new solution cannot go directly from user submission to TrackWise — a manual review gate must remain
- Expectation that automation will move to IT ownership, not remain in the business
- Language of record in TrackWise is English; high US volume means English-first is appropriate

**Open questions (from session)**
- Inputs & outputs for the current failure mode classification model
- Full architecture of the Phase 1 solution
- Rationale for the current Power Platform–only build (skillset gap vs. deliberate choice)
- What the "master file" is and how it's maintained
- Where exactly the human review step fits in a redesigned flow
- What a prototype application would look like and own

---

## TrackWise PI Required Fields (Source of Truth for Intake Completeness)

The following field groups are **mandatory to open a Product Inquiry (PI)** in TrackWise. These define the minimum intake completeness target the AI layer must validate against.

**PI Record Header (System-Enforced)**
- Record Type, Division, CIC, Originator, Business Unit, Owner
- Awareness Date / Event Date, Date Received / Date Opened
- Source of Inquiry / Intake Source

**Product Identification (at least one required)**
- Product Name, Product Code / Catalog Number, Product Lot/Serial #, Product Family
- *As Reported* (free text — used when device/catalog is unknown)

**Inquiry Description & Event Metadata**
- Event Description, Event Date, Country of Event, Reporter Type, How Was Issue Noticed
- Procedure Completed Successfully, Patient Involvement, Medical Intervention
- Surgical Delay, Surgical Delay Length
- Adverse Consequences, Adverse Consequences Details
- Injury, Death, Serious Public Health Threat, Counterfeit Product

**Contact Information**
- Initial Reporter Name (First/Last), Address, City, State/Prov (2-digit if US), Postal Code, Country
- Email, Phone, Reporter Type, Health Professional Occupation, Sales Rep

> **Key intake principle:** A PI is an information-gathering and assessment record. Regulatory conclusions, severity, and investigation outcomes are **not** required at intake — scope AI validation accordingly.

**Downstream required fields (triggered post-intake — not in scope for intake AI)**

| Stage | Trigger | Newly Required |
|-------|---------|----------------|
| Regulatory Review | Regulatory Tab active | Decision, Rationale, Product Grid fields |
| Complaint Creation | Complaint Required = Yes | Complaint intake fields |
| Investigation | Investigation Required | Root cause, evaluation |
| Regulatory Reporting | Reportable = Yes | MDR / MIR details |
| Closure | Status = Closed | All closure controls |

---

## Concrete Example: PR 4316035 (Event Summary Report, 5/1/2026)

This record illustrates a **low-risk, non-reportable PI** flowing through the current manual intake process. It is a useful prototype benchmark for AI intake validation.

**Event**
- **Product:** Handpiece MICS — ROB3173 TKA 2.1 (Mako 4 Robot ONLY), Catalog 209063, Lot 42030823/4220806
- **Issue:** Handle will not stay in the locked position
- **Case type:** TKA (Mako 4 Robot); device to be decontaminated prior to return
- **How noticed:** Pre-Op
- **Procedure completed successfully:** Yes
- **Patient involvement:** No — No Impact
- **Medical intervention / Surgical delay / Adverse consequences:** No

**Intake & routing**
- Opened: 08 Apr 26 via Email; CIC: Joint Replacement; CMC: Joint Replacement-Robotics
- Reporter: Brook Bowman (Company Rep), Grace Surgical Hospital, Lubbock TX
- Physician: David Shephard; Anatomy: Knee

**Regulatory outcome**
- MDR: Not reportable — highest potential severity S2, occurrence O3; no serious injury/death in 4-year complaint history for this device family
- MIR: N/A — Event outside EU
- Final state: No Report Required Approval

**Communication log (illustrates manual follow-up burden)**
- Contact 1: 08 Apr 26 (Email) — Confirmation + first request for additional info
- Contact 2: 15 Apr 26 (Email) — Second request for additional info
- Contact 3: 21 Apr 26 (Email) — Third request for additional info
- Status: Information Obtained / Attempts Completed

> **AI opportunity:** This record required 3 follow-up contacts over 13 days to obtain information that could have been captured at intake. An AI-assisted intake layer validating completeness at submission would eliminate this cycle for cases like PR 4316035. Estimated impact: reduce follow-up rate on low-risk PIs and accelerate time-to-regulatory-decision from ~13+ days toward same-day.

---
