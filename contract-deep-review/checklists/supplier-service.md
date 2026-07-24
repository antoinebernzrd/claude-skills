# Checklist — supplier / service-provider

Full deep-review checklist. This covers **two sub-types** — decide which applies
(some items apply to both):
- **Supplier (goods/equipment):** buying hardware (cryogenics, control
  electronics, components). Focus: delivery, warranties, defect liability, continuity.
- **Service provider (services/SOW):** work done for A&B (fabrication, R&D
  subcontracting, engineering, IT). Focus: **IP ownership of deliverables**,
  confidentiality, subcontracting.

The marquee A&B risk here is **IP ownership of what the provider creates**. Apply
every relevant item; locate the concept, judge presence + adequacy, redline anything not ✅.

Sub-type tags: **[G]** goods, **[S]** services, **[G/S]** both.

---

### 1. Scope / statement of work / specifications [G/S]
- **Check:** are deliverables, specs, and quantities precisely defined?
- **Good:** clear SOW/spec schedule; measurable outputs.
- **Flag if:** vague scope, "as directed", or specs missing. *Severity: medium.*
- **👤 Needs human:** whether the technical specs themselves are correct — engineering decides.

### 2. IP ownership of deliverables [S]
- **Check:** who owns what the provider creates for A&B.
- **Good:** **assigned to A&B** ("Provider assigns all right, title and interest in the Deliverables to Customer").
- **Flag if:** silent (default may leave ownership with the provider), or provider retains ownership and grants a mere licence. *Severity: critical.*
- **Redline:** full assignment to A&B. Fallback: exclusive, worldwide, royalty-free licence + no third-party reuse in the quantum field.
- **Interacts with:** item 4 (background IP).

### 3. Provider reuse / competitor restriction [S]
- **Check:** may the provider reuse A&B's designs or apply learnings for competitors?
- **Good:** no reuse of A&B's materials; ideally no work for named competitors on the same tech during/after.
- **Flag if:** provider may reuse deliverables or A&B's confidential designs. *Severity: critical–high.*
- **Redline:** prohibit reuse of A&B materials; add a targeted non-reuse/field restriction.

### 4. Background / pre-existing IP [S]
- **Check:** how pre-existing IP is defined and carved out of any assignment.
- **Good:** each party keeps clearly-identified pre-existing IP; provider grants A&B a licence to any of its background IP needed to use the deliverables.
- **Flag if:** "background IP" is broad/undefined so it swallows the deliverables, or A&B gets no licence to background IP embedded in what it bought. *Severity: high.*

### 5. Confidentiality [G/S]
- **Check:** protection of A&B's designs/information the provider will see.
- **Good:** strong confidentiality; for fab/foundry/technical suppliers, ideally + no-reuse.
- **Flag if:** weak, one-way, or missing — especially for a technical supplier handling A&B's crown jewels. *Severity: high.*

### 6. Acceptance / testing [S]
- **Check:** how deliverables are accepted (judge the **setup**, not the specs).
- **Good:** A&B tests against the spec, defined review window, rejection → cure → refund/terminate path, final payment on acceptance.
- **Flag if:** auto/"deemed accepted", "payment = acceptance", "use = acceptance", provider self-certifies, or no cure path. *Severity: medium–high.*
- **Redline:** add an objective, A&B-controlled acceptance regime tied to the spec.
- **👤 Needs human:** the actual pass/fail criteria — engineering defines.

### 7. Delivery / lead time / continuity [G]
- **Check:** delivery dates, remedies for delay, supply/spares continuity.
- **Good:** firm dates, delay remedies (credits), continuity/spares commitment — important for **single-source, long-lead** hardware.
- **Flag if:** no firm delivery or continuity commitment on critical equipment. *Severity: medium (roadmap risk).* 

### 8. Warranties [G/S]
- **Check:** quality guarantees.
- **Good:** goods conform to spec and are free from defects for a defined period; services performed in a professional/workmanlike manner.
- **Flag if:** "as-is" / all warranties disclaimed. *Severity: medium.*

### 9. Defect remedy [G]
- **Check:** remedy for defective goods.
- **Good:** repair/replace/refund within a warranty period; provider bears return costs.
- **Flag if:** no remedy, or remedy at provider's sole discretion. *Severity: medium.*

### 10. Limitation of liability [G/S]
- **Check:** the cap and carve-outs.
- **Good:** reasonable cap **with carve-outs** for personal injury, property damage, IP infringement, and confidentiality breach.
- **Flag if:** capped at the item/fee price with no carve-outs — inadequate if a defect damages A&B equipment or a run. *Severity: high.*
- **Redline:** add carve-outs (injury, property, IP, confidentiality); raise the cap.

### 11. Indemnification [G/S]
- **Check:** does the provider indemnify A&B for third-party IP infringement and for injury/property damage caused by its goods/staff?
- **Good:** provider IP-infringement + injury/property indemnity.
- **Flag if:** no indemnity, or A&B indemnifies the provider broadly. *Severity: medium–high.*

### 12. Subcontracting / assignment [G/S]
- **Check:** may the provider subcontract or assign; flow-down of terms.
- **Good:** not without A&B's consent; confidentiality + IP obligations flow down to subcontractors.
- **Flag if:** free subcontracting/assignment with no flow-down — sensitive work could be delegated. *Severity: medium.*

### 13. Payment / milestones / change orders [G/S]
- **Check:** payment schedule, milestone linkage, change-control process.
- **Good:** payment tied to milestones/acceptance; a defined change-order process.
- **Flag if:** full upfront payment regardless of performance, or open-ended change costs. *Severity: low–medium.*

### 14. Term & termination [G/S]
- **Check:** duration, termination for cause/convenience, effect on deliverables/IP.
- **Good:** A&B can terminate for breach; on termination A&B keeps rights to paid-for deliverables and IP.
- **Flag if:** A&B loses IP/deliverables on termination, or can't exit for cause. *Severity: medium.*

### 15. Maintenance / spares / support [G]
- **Check:** post-delivery support, spare-parts availability, maintenance terms.
- **Good:** defined support and spares availability period.
- **Flag if:** none, on critical long-life equipment. *Severity: low–medium.*

### 16. Insurance [G/S]
- **Check:** provider's insurance, especially for on-site work or expensive equipment.
- **Good:** adequate liability/professional-indemnity cover evidenced.
- **Flag if:** none required for on-site services or high-value hardware. *Severity: low–medium.*

### 17. Export control [G/S]
- **Check:** foreign supplier, controlled components, or A&B sharing controlled designs (e.g. with an overseas fab).
- **Good:** export-compliance clause; provider warrants components' export status.
- **Flag if:** foreign supplier/controlled items + no export clause. *Severity: escalate.*
- **Action:** route to a human for export-control assessment.

### 18. Personal data / DPA [G/S]
- **Check:** does the service involve personal data (IT, payroll, recruiting, managed services)?
- **Good:** DPA with GDPR Art. 28 terms.
- **Flag if:** personal data processed with no DPA. *Severity: high → escalate.*

### 19. Title & risk of loss [G]
- **Check:** when title and risk pass to A&B.
- **Good:** risk passes on delivery/acceptance; title on payment/delivery.
- **Flag if:** risk passes before A&B receives/accepts the goods. *Severity: low–medium.*

### 20. Regulatory / safety compliance [G]
- **Check:** compliance with applicable standards (CE, RoHS/REACH, safety).
- **Good:** provider warrants compliance.
- **Flag if:** no compliance warranty on regulated equipment. *Severity: low–medium.*
