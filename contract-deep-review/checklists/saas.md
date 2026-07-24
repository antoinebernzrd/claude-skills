# Checklist — SaaS / software subscription

Full deep-review checklist. A&B is almost always the **customer** signing the
**vendor's** template, so the posture is defensive. The two dominant risk axes are
**data** (GDPR + IP-in-data) and **commercial** (liability, cost, lock-in).

Apply every item: locate the concept, judge presence + adequacy, follow
interactions, assign status + severity, redline anything not ✅.

---

### 1. Subscription grant & scope
- **Check:** what A&B is licensed to do; usage limits (seats, volume, environments).
- **Good:** scope matches intended use; overage handled reasonably.
- **Flag if:** vague scope or punitive overage/true-up terms. *Severity: low–medium.*

### 2. Fees, payment, auto-renewal, price increases
- **Check:** price, payment terms, renewal, and increase mechanics.
- **Good:** capped annual increases; reasonable non-renewal notice window (≤30–60 days).
- **Flag if:** auto-renewal with a long cancellation window, or **uncapped** price increases. *Severity: low–medium (commercial).*
- **Redline:** cap increases (e.g. ≤ CPI or a fixed %); shorten the notice window.

### 3. Term & termination
- **Check:** duration, termination for cause, termination for convenience, effect of termination.
- **Good:** A&B can terminate for material breach (with cure period); clear off-boarding.
- **Flag if:** no termination-for-cause right for A&B, or vendor can terminate at will while A&B is locked in. *Severity: medium.*

### 4. SLA / uptime / support
- **Check:** uptime commitment, support response, remedies (service credits).
- **Good:** meaningful uptime % with credits, matched to how critical the tool is.
- **Flag if:** no SLA on a production-critical service, or credits are the "sole remedy" for prolonged outages. *Severity: low–medium (high if business-critical, e.g. compute/CI).* 

### 5. Data Processing Agreement / GDPR
- **Check:** if the service processes personal data, is there a DPA with Art. 28 terms?
- **Good:** DPA present — processing only on A&B's instructions, confidentiality, security, sub-processor controls, breach notification, deletion/return.
- **Flag if:** personal data processed with **no DPA**. *Severity: critical → escalate.*
- **Redline:** require the vendor's DPA (or attach A&B's) before signing.

### 6. International data transfer mechanism
- **Check:** where data is hosted/processed; if outside the EEA, the transfer basis.
- **Good:** EU hosting, or valid SCCs / EU-US Data Privacy Framework certification.
- **Flag if:** US/non-EU vendor with no transfer mechanism. *Severity: high.*
- **Redline:** add SCCs / confirm DPF; prefer EU data residency.

### 7. Sub-processors
- **Check:** can the vendor use sub-processors; notice and objection rights.
- **Good:** list available, advance notice of changes, flow-down of obligations.
- **Flag if:** unrestricted sub-processing with no notice. *Severity: medium.*

### 8. Customer data ownership
- **Check:** who owns the data A&B uploads.
- **Good:** A&B retains all ownership; vendor gets only a limited licence to provide the service.
- **Flag if:** any vendor ownership claim over Customer Data. *Severity: high.*

### 9. Vendor use of Customer Data (the A&B-specific trap)
- **Check:** what the vendor may do with A&B's data beyond providing the service.
- **Good:** use strictly limited to delivering the service, on A&B's instructions.
- **Flag if:** vendor may use data to "improve its services", "develop products", or **train models** — even if "aggregated"/"de-identified". *Severity: critical if the tool touches technical data, source code, or research data; high otherwise.*
- **Redline:** restrict to service provision only; explicitly prohibit training/product development on Customer Data.
- **Interacts with:** item 8 — ownership means little if usage rights are broad.

### 10. Security commitments
- **Check:** stated security posture.
- **Good:** recognised standard (SOC 2 / ISO 27001), encryption in transit/at rest, breach-notification timeline.
- **Flag if:** no security standard or vague "industry-standard" language only. *Severity: medium (high given A&B's IP sensitivity).*

### 11. Confidentiality
- **Check:** mutual confidentiality covering A&B's data and configuration.
- **Good:** mutual, standard.
- **Flag if:** one-way, or excludes the data A&B puts into the system. *Severity: medium.*

### 12. IP ownership (product & feedback)
- **Check:** vendor owns its product (fine); watch for a broad feedback-assignment clause.
- **Good:** A&B keeps its IP; feedback assignment is absent or narrow.
- **Flag if:** broad feedback clause assigning A&B's suggestions/technical input. *Severity: medium.*

### 13. Warranties
- **Check:** does the vendor warrant the service?
- **Good:** service will materially conform to docs; non-infringement warranty.
- **Flag if:** "as-is", all warranties disclaimed. *Severity: medium.*

### 14. Limitation of liability
- **Check:** the cap and its carve-outs.
- **Good:** reasonable cap **with carve-outs** (uncapped or super-capped) for data breach, confidentiality breach, and IP infringement.
- **Flag if:** capped at fees paid with **no carve-outs** — meaningless if a breach exposes A&B's IP or personal data. *Severity: high.*
- **Redline:** add carve-outs for data/security breach, confidentiality, IP infringement; raise the general cap.

### 15. Indemnification
- **Check:** does the vendor indemnify A&B if the software infringes third-party IP?
- **Good:** vendor IP-infringement indemnity for A&B.
- **Flag if:** no IP indemnity, or A&B must indemnify the vendor broadly. *Severity: medium.*

### 16. Data return / portability on termination
- **Check:** can A&B extract its data in a usable format on exit; deletion of data by vendor.
- **Good:** export in a standard format within a defined window; certified deletion after.
- **Flag if:** no export path (lock-in), or vendor retains data. *Severity: medium.*

### 17. Suspension rights
- **Check:** when the vendor can suspend the service.
- **Good:** only for material breach/non-payment with notice.
- **Flag if:** broad suspension at vendor's discretion. *Severity: low–medium.*

### 18. Unilateral changes
- **Check:** can the vendor change terms/service/pricing by updating a URL?
- **Good:** material changes require notice; A&B can terminate if adverse.
- **Flag if:** vendor may change terms unilaterally, effective immediately. *Severity: medium.*

### 19. Governing law & dispute resolution
- **Check:** governing law, venue, arbitration.
- **Good:** EU/acceptable law; courts or reasonable arbitration.
- **Flag if:** distant US-state law + mandatory arbitration + class-action waiver. *Severity: low–medium.*

### 20. Publicity
- **Check:** can the vendor use A&B's name/logo as a customer reference?
- **Good:** only with A&B's prior written consent.
- **Flag if:** vendor may publicise the relationship freely. *Severity: low.* (A&B may not want its tooling public.)
