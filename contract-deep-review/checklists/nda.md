# Checklist — NDA / confidentiality agreement

Full deep-review checklist. Apply every item. For each: locate the concept
(any wording), judge presence + adequacy, follow the interactions, assign
status + severity, and draft a redline for anything not ✅.

Context for A&B: NDAs are often mutual and high-volume. The existential risks are
**IP/know-how leaking out** (residuals, feedback, narrow confidentiality) and
**asymmetry** when A&B is the one sharing sensitive quantum information.

---

### 1. Mutual vs one-way
- **Check:** does confidentiality protect both parties, or only the counterparty?
- **Good:** mutual, or one-way in A&B's favour when only A&B discloses.
- **Flag if:** one-way protecting only the counterparty while A&B will also share sensitive info. *Severity: high.*
- **Redline:** convert to mutual, or ensure A&B's disclosures are equally protected.

### 2. Definition of Confidential Information
- **Check:** how broadly is protected information defined?
- **Good:** broad — covers technical + business info, oral and written, **whether or not marked**.
- **Flag if:** limited to "marked confidential", to written-only, or only to the counterparty's information (so A&B's verbal technical input isn't covered). *Severity: medium (high if A&B is the main discloser).*
- **Redline:** broaden to cover information disclosed in any form, and A&B's contributions.
- **Interacts with:** items 6 (residuals) and 7 (feedback) — a narrow definition here makes those far more dangerous.

### 3. Carve-outs / exclusions
- **Check:** the standard exceptions to confidentiality.
- **Good:** the usual four — public domain, already known, independently developed, lawfully received from a third party.
- **Flag if:** exclusions are broader than standard (e.g. "information the Recipient believes is non-confidential"), which guts protection. *Severity: medium.*

### 4. Purpose / permitted use
- **Check:** what the receiving party may use the information for.
- **Good:** narrowly tied to the specific "Purpose" (the evaluation/collaboration at hand).
- **Flag if:** use is permitted for "any business purpose" or is undefined. *Severity: medium.*
- **Redline:** define the Purpose specifically and limit use to it.

### 5. Obligations / standard of care / need-to-know
- **Check:** duty of care and who the recipient may share with.
- **Good:** at least reasonable care (ideally same as own confidential info); disclosure limited to need-to-know recipients bound by equivalent terms.
- **Flag if:** no standard of care, or free sharing with affiliates/advisors without confidentiality obligations. *Severity: medium.*

### 6. Residuals clause
- **Check:** any clause letting the recipient use information "retained in memory" / "unaided memory" / "residuals".
- **Good:** none.
- **Flag if:** present — it quietly strips trade-secret protection by letting the recipient reuse what its people remember. *Severity: high.*
- **Redline:** strike the residuals clause entirely.

### 7. Feedback / improvements clause
- **Check:** any clause assigning feedback/suggestions to the disclosing party.
- **Good:** none, or mutual and limited to high-level feedback on the evaluated product.
- **Flag if:** one-way against A&B in a technical/supplier/co-development context — A&B's engineering guidance could be assigned away. (Low concern in a pure product-evaluation NDA.) *Severity: high in technical context; low otherwise.*
- **Redline:** delete, make mutual, or carve out A&B's pre-existing and independently developed IP.
- **Interacts with:** item 2 — read together.

### 8. IP ownership / no licence granted
- **Check:** does disclosure transfer any ownership or licence in A&B's IP?
- **Good:** explicit statement that no licence or ownership is granted by disclosure; each party keeps its own IP.
- **Flag if:** any assignment or licence of A&B's IP/materials to the recipient. *Severity: critical.*
- **Redline:** add "no rights are granted except the limited right to use Confidential Information for the Purpose."

### 9. Term & survival
- **Check:** how long the agreement lasts **and** how long confidentiality survives.
- **Good:** confidentiality survives 2–5 years for business info, and **indefinitely for trade secrets**.
- **Flag if:** a single short term (e.g. 2 yrs) with no perpetual survival for trade secrets. *Severity: medium (high if core technical IP is disclosed).*
- **Redline:** add perpetual survival for trade secrets.

### 10. Return / destruction of information
- **Check:** obligation to return or destroy on termination/request.
- **Good:** return or certified destruction, with a reasonable archival/backup exception.
- **Flag if:** absent, or lets the recipient keep everything. *Severity: low–medium.*

### 11. Compelled disclosure carve-out
- **Check:** what happens if the recipient is legally compelled to disclose.
- **Good:** allowed only to the extent legally required, with prior notice to A&B where lawful, and efforts to limit/seek protection.
- **Flag if:** unrestricted disclosure "as required" with no notice. *Severity: low–medium.*

### 12. Remedies / injunctive relief
- **Check:** remedy for breach.
- **Good:** acknowledges injunctive relief is available (damages alone are inadequate).
- **Flag if:** liability for breach of confidentiality is capped or limited. *Severity: medium–high.*

### 13. No warranty on accuracy
- **Check:** does A&B warrant the accuracy/completeness of what it discloses?
- **Good:** information provided "as is", no warranty.
- **Flag if:** A&B warrants accuracy — creates unnecessary exposure. *Severity: low.*

### 14. Governing law & jurisdiction
- **Check:** which law and courts apply.
- **Good:** French law / EU courts, or a neutral acceptable forum.
- **Flag if:** a distant/unfavourable jurisdiction or one hostile to injunctive relief. *Severity: low–medium.*

### 15. Assignment
- **Check:** can the counterparty assign the NDA (e.g. on acquisition)?
- **Good:** no assignment without consent, or A&B's confidential info stays protected on any change of control.
- **Flag if:** free assignment, so a competitor could acquire the counterparty and A&B's info. *Severity: medium.*

### 16. Export control (foreign counterparty)
- **Check:** if the counterparty is foreign and technical info will be shared.
- **Good:** an export-compliance clause; both parties comply with applicable export laws.
- **Flag if:** foreign counterparty + controlled/quantum technical disclosure + no export clause. *Severity: escalate.*
- **Action:** route to a human for export-control assessment; do not clear on triage logic alone.

### 17. Personal data / GDPR
- **Check:** does the NDA involve exchanging personal data?
- **Good:** if yes, GDPR obligations acknowledged; a DPA if one party processes for the other.
- **Flag if:** personal data shared with no GDPR/DPA treatment. *Severity: high; escalate if processing on another's behalf with no DPA.*

### 18. Embedded non-solicit / non-compete
- **Check:** NDAs sometimes smuggle in non-solicitation or non-compete terms.
- **Good:** none, or narrow and mutual.
- **Flag if:** a non-solicit of employees or a non-compete restricting A&B's business — often out of place in an NDA. *Severity: medium–high.*
- **Redline:** remove, or narrow and make mutual.
