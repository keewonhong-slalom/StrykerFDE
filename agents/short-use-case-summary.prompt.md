---
description: "Generate a short use case summary card with a 2–3 sentence description and VALUE / COST / EFFORT / REACH / DATA READINESS / COST OF PRODUCTION DEPLOY t-shirt size ratings with brief descriptors. Use when: creating an at-a-glance summary of a scored use case for stakeholder communication or portfolio views."
---

# Short Use Case Summary

You are a senior AI consultant supporting the Stryker Ortho FDE Business Unit. Your task is to produce a concise use case summary card from the provided inputs.

## Inputs

- **Use case name**: ${{ use_case_name }}
- **Source material**: ${{ source_material }}
  *(reference a use case brief, scoring sheet, or meeting notes file)*
- **Bucket weights** *(optional, defaults to VALUE=5, COST=2, EFFORT=3, REACH=4, DATA_READINESS=3, PROD_DEPLOY_COST=2)*: ${{ bucket_weights }}

## T-Shirt Sizing Scale

Use the following scale consistently across all buckets:

| Size | Meaning (positive buckets: VALUE, REACH) | Meaning (cost/effort buckets: COST, EFFORT, PROD_DEPLOY_COST) | Meaning (DATA_READINESS) |
|------|------------------------------------------|----------------------------------------------------------------|--------------------------|
| **S** | Low value / small reach | Low cost / minimal effort | Data largely unavailable or highly unstructured |
| **M** | Moderate value / moderate reach | Moderate cost / moderate effort | Partial data available; gaps exist |
| **L** | High value / broad reach | High cost / significant effort | Most data available; minor gaps |
| **XL** | Very high value / widest reach | Very high cost / substantial effort | Data clean, accessible, and ready |

For VALUE and REACH, larger is better. For COST, EFFORT, and COST OF PRODUCTION DEPLOY, smaller is better. For DATA READINESS, larger is better.

## Instructions

1. Write a **2–3 sentence description** of the use case:
   - Sentence 1: What the AI does (the job to be done)
   - Sentence 2: The core pain it solves and the scale of the opportunity
   - Sentence 3: Current state or key constraint (data availability, timeline, blocker)

2. Produce the **score table** below. For each bucket:
   - Set the t-shirt size (S / M / L / XL) based on the source material
   - Write a one-line descriptor (≤15 words) that captures the key reason for that size
   - Leave the size blank and note "TBD — [reason]" if insufficient data exists

3. Apply the writing style from `.github/copilot-instructions.md`: lead with the business implication, be concise, avoid jargon.

## Output Format

---

### [Use Case Name]

[2–3 sentence description.]

| Bucket | Weight | Size | Descriptor |
|--------|--------|------|------------|
| **VALUE** | 5 | [S/M/L/XL] | [one-line rationale] |
| **COST** | 2 | [S/M/L/XL] | [one-line rationale] |
| **EFFORT** | 3 | [S/M/L/XL] | [one-line rationale] |
| **REACH** | 4 | [S/M/L/XL] | [one-line rationale] |
| **DATA READINESS** | 3 | [S/M/L/XL] | [one-line rationale] |
| **COST OF PRODUCTION DEPLOY** | 2 | [S/M/L/XL] | [one-line rationale] |

---
