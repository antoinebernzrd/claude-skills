# Alice & Bob — Legal Standard Positions ("the playbook")

> Shared reference for the `triage-contract` and `review-contract` skills.
> This file encodes Alice & Bob's default risk appetite so the skills don't
> fall back to generic commercial standards. **Update this file, not the
> skills, when positions change.**

## Company context

- **Alice & Bob** — ~250 employees. In-house legal team of **2 people**.
- We are based in the **EU**. Default governing-law preference: an EU member
  state; **French law acceptable and preferred** where we have leverage.
- Most contracts we review are **inbound**: a counterparty sends us their
  paper. **Our default posture is the RECIPIENT** — customer/buyer (SaaS,
  suppliers, services) or receiving party (NDAs). Positions below are written
  from that posture. Flag explicitly if we are the drafter/discloser instead.
- Personal data is in scope for most SaaS and many supplier deals → **GDPR/DPA
  is a first-class, always-checked axis**, not an afterthought.
- Contracts may be **in French or English** — review in the original language;
  do not force a translation.

## Routing model (this is the whole point)

Our alternative to in-house review is **expensive outside counsel**. So the
traffic light is a **cost-and-bandwidth routing decision**, not a corporate
escalation ladder. There is no senior counsel or GC — only three rungs:

| Light | Meaning | Routes to | Target time |
|---|---|---|---|
| 🟢 **GREEN** | Matches our standard positions; routine | **Self-serve** — business owner proceeds under standard delegation; legal not required | Same day |
| 🟡 **YELLOW** | Deviates but within a range we can handle in-house | **The 2-person legal team** — run `review-contract` for redlines | 1–3 days |
| 🔴 **RED** | Outside our range, or specialist/high-exposure | **Worth paying outside counsel** — legal team scopes and engages | As needed |

Design rule: **push work down the ladder.** The default question is always
"can this be GREEN and self-served?" We only spend the 2 lawyers' time on
YELLOW, and only spend money on RED.

---

## Standard positions — common clauses

Format: **GREEN** = accept as-is · **YELLOW** = negotiate in-house · **RED** = outside counsel / do not sign as-is.

### Limitation of liability
- **GREEN:** Cap ≥ 12 months' fees; mutual; consequential damages excluded mutually; standard carveouts (IP infringement, breach of confidentiality, data breach) uncapped or super-capped.
- **YELLOW:** Cap 3–12 months' fees; asymmetric but negotiable; carveouts missing one standard item.
- **RED:** **Uncapped liability for us**, or no limitation clause, or cap < 3 months' fees on a material deal, or liability caps that are one-sided against us on their breaches.

### Indemnification
- **GREEN:** Mutual; vendor indemnifies us for IP infringement of their product and for their data breaches.
- **YELLOW:** Unilateral in our favour missing; scope narrower than preferred.
- **RED:** We indemnify them broadly / "for any breach"; uncapped indemnity flowing from us; no IP-infringement indemnity from a SaaS vendor.

### Data protection (GDPR) — always check
- **GREEN:** DPA present; vendor = processor; sub-processor notification + objection right; breach notice ≤ 72h; SCCs or adequacy for any non-EU transfer; deletion/return on exit; data hosted in EU/EEA.
- **YELLOW:** DPA present but missing one element (e.g. no explicit sub-processor objection); data in an adequacy country (UK, etc.); breach notice "without undue delay" but no fixed hours.
- **RED:** **No DPA where personal data is processed**; transfers to a non-adequate country with no SCCs; vendor claims to be an independent controller of our users' data; no deletion on exit.

### IP / ownership
- **GREEN:** Each party keeps pre-existing IP; deliverables/work product assigned to us (services); no grab of our data or feedback.
- **YELLOW:** Broad but negotiable feedback licence; deliverable ownership unclear.
- **RED:** Assignment of *our* pre-existing IP; vendor claims ownership of our data or derived data; perpetual irrevocable licence to our confidential materials.

### Term & termination
- **GREEN:** Termination for convenience with ≤ 90-day notice **or** term ≤ 12 months; auto-renewal with ≥ 60-day opt-out window; data export on exit.
- **YELLOW:** Multi-year lock-in but with exit rights; auto-renewal with 30-day window; early-termination fee.
- **RED:** No termination for cause; multi-year lock-in with no exit and punitive early-termination; auto-renewal with < 30-day / silent window on a material spend.

### Confidentiality (inside commercial contracts)
- **GREEN:** Mutual; 2–5 year survival; standard carveouts.
- **YELLOW:** One-sided but reasonable; survival slightly long.
- **RED:** Perpetual (non-trade-secret); no carveouts; captures publicly available info.

### Governing law & disputes
- **GREEN:** EU member-state law; litigation in a reasonable EU venue.
- **YELLOW:** Non-preferred but acceptable EU/adequacy jurisdiction; institutional arbitration in a neutral seat.
- **RED:** Remote/unfavourable jurisdiction; mandatory arbitration with counterparty-favourable rules; US law + US venue on a material deal.

---

## Type-specific checklists (layer on top of the common clauses)

### NDA
Use `triage-nda` logic. Key A&B positions: mutual by default; term 2–3y (survival ≤5y); standard carveouts (public, prior possession, independent development, third-party, legal compulsion) all present; **no non-solicit / non-compete / exclusivity / IP grant hidden inside**; no liquidated damages. Missing *independent development* carveout or an embedded non-solicit → at least YELLOW, usually RED.

### SaaS agreement
- **SLA / uptime:** ≥ 99.5% with service credits → GREEN; no SLA on a business-critical tool → YELLOW/RED.
- **Data location & sub-processors:** EU hosting + published sub-processor list → GREEN.
- **Auto-renewal & price escalation:** capped uplift (e.g. ≤ CPI or ≤ 5%) → GREEN; uncapped renewal price hikes → YELLOW.
- **Exit / portability:** data export in a usable format on termination → required for GREEN.
- **Security:** ISO 27001 / SOC 2 evidence → supports GREEN.

### Supplier / service-provider contract
- **Deliverables & acceptance:** clear acceptance criteria and rejection right → GREEN.
- **Warranties:** fitness-for-purpose + defect remedy → GREEN; "as is" on a paid service → YELLOW.
- **Subcontracting:** notice/consent for subcontractors → GREEN.
- **IP in deliverables:** assigned to us or licensed for our purpose → required.
- **Payment:** net 30–60, no penalty interest above statutory → GREEN.

---

## Always-RED tripwires (any contract type)

Route straight to outside counsel regardless of everything else:

- Uncapped liability or uncapped indemnity flowing **from** Alice & Bob.
- Personal data processed with **no DPA** and no willingness to add one.
- International data transfer to a non-adequate country with no safeguards.
- Assignment or exclusive licence of Alice & Bob's **pre-existing IP**.
- Non-compete / exclusivity binding Alice & Bob.
- Change-of-control clause letting the counterparty terminate or reprice on our M&A.
- Document is **mislabelled** (an "NDA" that contains substantive commercial obligations).
- Regulated/novel domain (antitrust, financial-services licensing, employment litigation) — outside a 2-person generalist team's scope.

---

## Disclaimer (must appear in every skill's output)

This is a workflow aid, not legal advice. Output must be reviewed by a
qualified member of the Alice & Bob legal team before signature or reliance.
