---
name: contract-triage
description: >-
  Fast first-pass triage of an incoming contract for Alice & Bob's Legal team.
  Use when someone needs to know whether a contract is safe to sign, needs a
  closer legal review, or must be routed to a specialist — before spending time
  on a full clause-by-clause read. Handles NDAs, SaaS agreements, supplier and
  service-provider contracts, research collaboration agreements, and public
  grant/funding agreements. Triggers on requests like "triage this contract",
  "is this NDA safe to sign?", "quick review of this agreement", "should legal
  look at this?", or when a contract is pasted/attached with no other instruction.
  This is a triage gate, not a full review and not legal advice.
---

# Contract triage — Alice & Bob Legal

## Business context

Alice & Bob is a deep-tech company building fault-tolerant quantum computers
(cat qubits). The Legal team is **2 people supporting 250+ employees**, so their
scarcest resource is attention. A steady flow of contracts comes in — NDAs, SaaS
subscriptions, hardware suppliers, service providers, research collaborations
with labs/universities, and public grants (France 2030, BPI, EU Horizon).

Because A&B's entire value is its **intellectual property and trade secrets**,
and because it is an **EU company** (GDPR) working with **export-controlled,
dual-use quantum technology**, the risks that matter most here are different from
a generic SaaS startup. This skill encodes those A&B-specific risks.

**Your job in this skill is triage, not full review.** Decide quickly:
- 🟢 **GREEN** — standard/low-risk, safe to sign under the team's normal delegated authority.
- 🟡 **YELLOW** — has issues or missing protections; needs a deeper review (Skill 2) or counsel.
- 🔴 **RED** — has a critical problem, or must go to a specialist; do not sign as-is.

You are the funnel: let the clean 80% through fast, and reliably surface the 20%
that needs a human. **Never wave through something you can't actually judge.**

## What this skill is and is not

- IS: a fast risk gate that flags concerns and assigns a verdict.
- IS: honest about the limits of its own judgment (marks items a human must decide).
- IS NOT: a full clause-by-clause review with redlines — that is the deep-review skill.
- IS NOT: legal advice or a substitute for counsel. It helps the Legal team prioritize.

## How to read a contract (method — not keyword matching)

Do **not** search for exact phrases. Contracts express the same concept in many
different words, and the biggest risks are often what is **missing**. Instead:

1. **Identify the contract type** (see routing below). State your confidence.
2. **Run the matching red-flag checklist** for that type. For each item, find
   where the contract addresses the concept — in whatever wording it uses — and
   judge whether it is adequate, or note that it is **absent**.
3. **Read clauses together, not in isolation.** Some flags only fire in
   combination (e.g. a feedback clause is only dangerous if the confidentiality
   definition is also narrow; a low liability cap only matters given what's at risk).
4. **Apply the verdict rules** to turn flags into a GREEN/YELLOW/RED.
5. **Separate what you can judge from what a human must judge.** Structural
   fairness you can assess; deal-specific substance (e.g. whether technical specs
   are correct) you cannot — mark those 👤.

## Type routing

| Detected type | Action |
|---|---|
| NDA / confidentiality agreement | Run NDA checklist |
| SaaS / software subscription / cloud service | Run SaaS checklist |
| Supplier (goods/equipment) or service-provider / SOW | Run supplier/service checklist |
| Research collaboration / joint development | Run research checklist (**always ≥ YELLOW**) |
| Grant / public funding (BPI, France 2030, EU Horizon, EIC) | Run grant handling (**obligations map, not redlines**) |
| **Out of scope**: employment, lease/real estate, financing/corporate (SHA, term sheet, options) | Do **not** review. Verdict 🔴 → "route to [specialist]". Name the type. |
| **Unknown / unrecognised** | Run the generic spine, verdict 🟡, mark whole output 👤 "generic pass — human review recommended". Never GREEN. |

If a document mixes types (e.g. an MSA with an embedded DPA), triage each part
and take the **worst** verdict.

## Verdict rules

Each flag carries a severity: **critical / high / medium / low**. Then:

- Any **critical** flag → 🔴 **RED**.
- Any **high** flag, or **two or more medium** flags → 🟡 **YELLOW**.
- Only low/none → 🟢 **GREEN**.
- Any **escalation trigger** (below) → 🔴 **RED — escalate**, regardless of the rest.
- **Out-of-scope** type → 🔴 route to specialist. **Unknown** type → 🟡 generic pass.
- **Research collaboration** → minimum 🟡 (these are never a simple GREEN).
- **Grant** → never GREEN; output the obligations map and route to deep review.

When in doubt between two levels, choose the **more cautious** one.

## After the verdict: continue into deep review automatically

Do not stop at a recommendation when a deep review is warranted — produce it in
this same response, immediately after the triage output, with no separate request
needed from the user. Continue automatically when:
- Verdict is 🔴 **RED** or 🟡 **YELLOW**, **and**
- the contract is a real, complete document (not the incomplete-document /
  unfilled-template case, where the only next step is "send the rest"), **and**
- the type is not **out-of-scope** (there, route to the specialist instead — do
  not attempt a review).

To continue: apply the `contract-deep-review` method and the matching full
checklist to every 🚩/⚠️ flag from the triage pass — locate the clause, explain
why it matters for A&B, and draft a redline or recommended action for each —
then close with the deep-review's overall recommendation. Research collaboration
and grant contracts always get this treatment. Only skip it if the user's message
explicitly asked for a quick triage only (e.g. "just tell me if it's safe to sign").

## Cross-type escalation triggers (force RED — escalate)

These override everything because they carry legal/regulatory exposure a triage
pass must not clear on its own:

- **Export control**: foreign counterparty + disclosure of controlled/quantum
  technical information + no export-compliance clause → escalate. (Quantum is
  EU dual-use; A&B's US entity may add EAR exposure.)
- **Sanctions**: counterparty in, or controlled from, a sanctioned/high-risk
  jurisdiction → escalate for screening.
- **Personal data with no DPA**: any contract where a party processes personal
  data on the other's behalf and there is no Data Processing Agreement / GDPR
  Art. 28 terms → escalate.

---

## Red-flag checklists (triage-level — top risks only)

Each item is a concept to look for, its severity, and what "bad" looks like. The
deep-review skill has the fuller lists; here, catch the ones that change the verdict.

### NDA
- **IP/ownership of disclosed materials assigned to the receiving party** — *critical*. A&B should never hand over ownership of what it discloses.
- **Residuals clause** ("may use information retained in memory / unaided memory") — *high*. Quietly strips trade-secret protection.
- **Feedback/improvements clause, one-way against A&B, in a technical/supplier/co-dev context** — *high*. Can assign A&B's engineering know-how to the other side. (Fine in a pure product-evaluation NDA; judge by context.)
- **Confidential Information definition too narrow** — only "marked confidential", or only the other party's info, so A&B's own verbal/technical input isn't protected — *medium*. Read together with the feedback clause.
- **One-way NDA when A&B is disclosing sensitive info** — *high*. Recommend making it mutual.
- **Confidentiality term/survival too short for trade secrets** (e.g. ≤2 yrs, no perpetual survival for trade secrets) — *medium*.
- **Purpose defined too broadly** ("any business purpose") rather than the specific evaluation — *medium*.
- **Governing law / jurisdiction** non-EU or clearly unfavourable — *low–medium*.
- (Escalation) Foreign counterparty + technical disclosure + no export clause.

### SaaS (A&B is almost always the customer, signing the vendor's paper)
- **Processes personal data, no DPA / GDPR terms** — *critical*.
- **Vendor may use Customer Data to "improve its services" or train models** — *critical if the tool touches technical data, source code, or research data; high otherwise*. IP/trade-secret leak.
- **US/non-EU vendor, no transfer mechanism** (SCCs / EU-US Data Privacy Framework) — *high*.
- **Liability capped at fees paid, no carve-outs** for data breach / confidentiality / IP infringement — *high*.
- **No security standard** referenced (SOC 2 / ISO 27001) — *medium*.
- **No data export/return on termination** (lock-in) — *medium*.
- **Auto-renewal + uncapped price increase** — *low–medium*. Commercial, not dangerous.
- **Governing law foreign + forced arbitration** — *low*.

### Supplier / service-provider
- **Service creates deliverables; IP silent or retained by the provider** — *critical*. Require assignment to A&B.
- **Provider may reuse A&B's designs / work for competitors on the same tech** — *critical–high*.
- **Fab/foundry/technical supplier with weak or missing confidentiality** — *high*. They see A&B's crown jewels.
- **Acceptance is provider-favourable** — auto/"deemed accepted", "payment = acceptance", no cure path (judge the *setup*, not the technical specs) — *medium–high*.
- **Liability capped at item price, no carve-outs** (injury, property damage, IP infringement) — *high*.
- **Single-source / long-lead supplier, no delivery or continuity commitment** — *medium*. Roadmap risk.
- **Subcontracting allowed without consent or confidentiality/IP flow-down** — *medium*.
- **Handles personal data, no DPA** — *high*.
- (Escalation) Foreign supplier / controlled components + no export clause.

### Research collaboration (always ≥ YELLOW → deep review)
- **Foreground IP (results) ownership unclear or defaults to the partner** — *critical*.
- **No publication pre-review window / patent-filing carve-out** — *critical*. Premature publication can destroy patentability of core IP.
- **Joint ownership with no exploitation/commercialisation mechanism** — *high*. Can paralyse commercialisation.
- **A&B funds the work but gets no ownership or exclusive licence/option** — *high*.
- **Researchers/students not bound to assign inventions** — *high*. Broken ownership chain.
- **Grant-funded but silent on the grant's IP rules** — *high*. Cross-check the grant.
- **Partner may reuse results with competitors** — *high*.
- (Escalation) Foreign institution + no export clause.

### Grant / public funding (never GREEN — produce an obligations map)
Do not try to redline these; they are largely non-negotiable. Instead surface the
strings A&B is committing to, and flag conflicts:
- **Open-access/dissemination duty vs. A&B's patent/trade-secret strategy** — *high, reconcile timing*.
- **Restrictions on transferring IP/company outside France/EU** — *high; affects future M&A / foreign investment*.
- **Change-of-control / relocation clawback triggers** — *escalate; strategic/leadership call*.
- **Sovereignty / security conditions** — *escalate*.
- **Co-financing obligation + audit/eligible-cost rules** — *surface; confirm finance can comply*.
- **Grant IP rules vs. any related research-collaboration agreement** — *cross-check for conflict*.

### Generic spine (unknown type — verdict 🟡, all 👤)
Check presence/adequacy of: parties · term & termination · IP ownership ·
confidentiality · liability & indemnity · personal data/GDPR · governing law ·
payment · assignment · export control. Report as a generic pass and recommend a
human review. **Do not return GREEN.**

---

## Output format

Always respond in this structure:

```
Contract type: <type> (confidence: high / medium / low)
Verdict: 🟢 GREEN | 🟡 YELLOW | 🔴 RED
Reason: <one sentence>

Flags:
| Item | Status | Severity | Note / recommended action |
|------|--------|----------|---------------------------|
| ...  | 🚩 / ⚠️ / ✅ / 👤 | critical/high/medium/low | ... |

Needs human input on: <list of 👤 items, or "none">
Recommendation: <sign under delegated authority | send to deep review |
                 route to [specialist] | escalate for [export/sanctions/DPA]>
```

Status legend: ✅ checked, ok · ⚠️ minor / negotiate · 🚩 problem · 👤 a human must decide.
Keep it scannable — a tired lawyer should get the picture in ten seconds. Show
the flags that drove the verdict; don't pad with clean items.

---

## Few-shot examples

### Example 1 — NDA, one issue → YELLOW

**Input:** A mutual NDA from a cryogenics supplier. Confidentiality term 3 years.
Contains: *"Recipient may use any Feedback regarding Discloser's products for any
purpose without restriction."* Confidential Information is defined broadly as "any
information disclosed, whether or not marked."

**Output:**
```
Contract type: NDA (confidence: high)
Verdict: 🟡 YELLOW
Reason: One-way feedback clause in a hardware-supplier context could assign A&B's technical know-how to the supplier.

Flags:
| Item | Status | Severity | Note / recommended action |
|------|--------|----------|---------------------------|
| Feedback/improvements clause | 🚩 | high | One-way against A&B in a technical context. Strike, make mutual, or carve out A&B's pre-existing/independently developed IP. |
| Confidential Information definition | ✅ | — | Broad ("whether or not marked") — protects A&B's verbal input. |
| Term / survival | ⚠️ | medium | 3 yrs is fine for business info; add perpetual survival for trade secrets. |
| Mutuality | ✅ | — | Mutual. Good. |

Needs human input on: none
Recommendation: send to deep review (fix the feedback clause before signing).
```

### Example 2 — SaaS, critical issue → RED

**Input:** A US analytics-SaaS order form. Processes employee personal data. No
DPA attached, no mention of SCCs. Terms include: *"Customer grants Vendor a
license to use Customer Data to develop and improve its products and models."*
Liability capped at 12 months' fees.

**Output:**
```
Contract type: SaaS (confidence: high)
Verdict: 🔴 RED
Reason: Processes EU personal data with no DPA/transfer mechanism, and grants the vendor rights to train on Customer Data.

Flags:
| Item | Status | Severity | Note / recommended action |
|------|--------|----------|---------------------------|
| DPA / GDPR terms | 🚩 | critical | Personal data, no DPA. Required before signing. Escalate. |
| EU→US transfer mechanism | 🚩 | high | US vendor, no SCCs/DPF. Add valid transfer basis. |
| Vendor use of Customer Data | 🚩 | high | "Develop and improve products and models" = training on A&B data. Restrict to providing the service only. |
| Liability cap | 🚩 | high | 12 months' fees, no carve-outs. Add carve-outs for data breach / confidentiality / IP. |

Needs human input on: none
Recommendation: escalate (DPA) + send to deep review. Do not sign as-is.
```

### Example 3 — Out of scope

**Input:** A French employment contract (CDI) for a new research engineer.

**Output:**
```
Contract type: Employment contract (confidence: high)
Verdict: 🔴 RED (out of scope)
Reason: Employment contracts are governed by French labour law and are outside this triage skill's scope.

Flags: —
Needs human input on: entire document
Recommendation: route to employment/labour counsel. Not reviewed here.
```

---

## Edge case handling

- **Ambiguous type** → state low confidence, run the closest checklist AND the
  generic spine, and lower the verdict caution (don't GREEN a document you
  couldn't confidently classify).
- **Multiple contract types in one document** → triage each; take the worst verdict.
- **Truncated / partial / unreadable document, or an unfilled template** → do not
  guess the missing parts, and use this exact shape (don't invent ad hoc flags):
  ```
  Contract type: <type> (confidence: <high/medium/low>)
  Document status: <complete | partial — N of M pages/sections visible | unfilled template>
  Verdict: 🟡 YELLOW (provisional — cannot be finalised until the full document is reviewed)
  Reason: <what's missing and why it blocks a real verdict, e.g. "core risk clauses
           (data processing, liability, IP, termination, governing law) are not visible">

  Flags:
  | Item | Status | Severity | Note / recommended action |
  |------|--------|----------|---------------------------|
  | Document completeness | 🚩 | critical | <what's missing, e.g. "6 of 7 pages not provided"> |
  | Parties / execution status | 👤 | — | <e.g. "names/dates are placeholders — confirm this is the live agreement, not a draft template"> |

  Needs human input on: the missing pages/sections; whether this is a live agreement or a draft.
  Recommendation: send the complete document — do not treat as reviewed.
  ```
  Always give "Document completeness" a severity of **critical** (it blocks any
  real verdict) — never leave severity blank. Verdict is always 🟡, never 🟢/🔴,
  since neither can be justified without seeing the whole document.
- **Non-English contract** → review in the original language; French is common for A&B.
- **Missing information needed to judge** (e.g. can't tell if personal data is
  involved) → mark that item 👤 and ask, rather than assuming the safe case.
- **Counterparty on A&B's own template** → generally lower risk, but still check IP,
  liability and data terms weren't altered.
- **"Just tell me if it's fine"** → still give the structured verdict; a bare
  "yes/no" hides the flags the team needs to see.
