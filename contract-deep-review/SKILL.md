---
name: contract-deep-review
description: >-
  Deep, clause-by-clause legal review of a single contract for Alice & Bob's
  Legal team, producing per-clause findings, severity, and concrete redlines or
  recommended actions. Trigger automatically and immediately, in the same
  response, right after a contract-triage pass on a complete document concludes
  YELLOW or RED — do not wait for the user to ask separately. Also trigger when
  a thorough review is explicitly requested ("full review", "redline this",
  "review clause by clause"), or automatically for research collaboration and
  grant agreements, which always warrant depth regardless of a triage verdict.
  Covers NDAs, SaaS, supplier/service-provider, research collaboration, and
  public grant/funding agreements. This is a detailed review that supports the
  Legal team's judgment; it is not legal advice and does not replace counsel.
---

# Contract deep review — Alice & Bob Legal

## Business context

Alice & Bob builds fault-tolerant quantum computers (cat qubits). Its Legal team
is **2 people for 250+ employees**, and its core value is **IP and trade secrets**.
It is an **EU company** (GDPR) working with **export-controlled, dual-use quantum
technology**, and it is heavily funded by **public grants** (France 2030, BPI, EU
Horizon). Those four facts — IP, GDPR, export control, public funding — drive what
"risky" means here and are baked into every checklist.

This skill is the **deep review** half of a two-skill system:
- `contract-triage` is the fast gate (safe / risky / route-to-human).
- **This skill** does the slow, thorough read once a contract is worth it.

## When to use this skill

- **Triage just returned 🟡 YELLOW or 🔴 RED on a complete document** → continue
  into this review **immediately, in the same response** — don't stop at the
  triage recommendation and wait to be asked. (Exception: if triage's own output
  was the incomplete-document/unfilled-template case, or an out-of-scope routing,
  there is nothing to deep-review yet — do not trigger.)
- Someone explicitly asks for a full review, redlines, or clause-by-clause analysis.
- The contract is a **research collaboration** or **grant** (always review in depth,
  regardless of what a triage pass would have concluded).

If the contract is a type this skill doesn't have a checklist for, or is
out-of-scope (employment, lease, financing), say so and stop — don't improvise a
deep review you're not equipped for.

## Method

1. **Determine the contract type.** If triage already classified it, reuse that.
   Otherwise classify it now, and state your confidence.
2. **Load the matching checklist file** from `checklists/` and apply **every**
   item in it. Do not review from memory — the checklist is the source of truth:
   | Type | File |
   |------|------|
   | NDA | `checklists/nda.md` |
   | SaaS | `checklists/saas.md` |
   | Supplier / service-provider | `checklists/supplier-service.md` |
   | Research collaboration | `checklists/research-collaboration.md` |
   | Grant / public funding | `checklists/grant.md` |
   | Unknown / other (in-scope but unrecognised) | `checklists/generic-spine.md` |
3. **For each checklist item:** locate where the contract addresses the concept —
   in whatever words it uses — then decide:
   - is it **present**? (if absent, that itself may be the finding)
   - is it **adequate** vs. "what good looks like"?
   - does its meaning change when read **together** with related clauses? (the
     checklist notes these interactions — follow them)
4. **Assign a status and severity** to each item, and for anything not ✅, draft a
   **redline or recommended action** (see redline guidance below).
5. **Separate structure from substance.** You can judge whether a clause is
   *structurally* protective (objective, balanced, has a cure path, etc.). You
   **cannot** judge deal-specific substance (are the technical specs right? is the
   price fair? is this counterparty trustworthy?). Mark those **👤 needs human**
   and say what the human must decide — never fake domain input you don't have.
6. **Roll up** to an overall recommendation and a short summary a busy lawyer can
   read first.

## Output modes

- **Default (NDA, SaaS, supplier/service, research, generic):** clause-by-clause
  findings table + redlines + summary. See format below.
- **Grant / public funding:** these are largely non-negotiable, so do **not**
  produce redlines. Produce an **obligations map** — a plain-English list of what
  A&B is committing to, which obligations conflict with A&B's interests, and which
  need a leadership/strategic decision. The `grant.md` checklist specifies this.

## Output format (default mode)

```
Contract type: <type> (confidence: high/medium/low)
Overall recommendation: <sign as-is | sign after fixes below | do not sign / escalate>
Summary: <2–3 sentences — the headline risks and what to do>

Findings (clause by clause):

### <Clause / item>
- Status: ✅ ok | ⚠️ negotiate | 🚩 problem | 👤 needs human
- Severity: critical | high | medium | low | —
- What it says: <short paraphrase or quote>
- Why it matters (for A&B): <plain reason>
- Redline / action: <proposed change, or what a human must decide>

... (repeat per finding; lead with 🚩 critical/high, then ⚠️, then note key ✅) ...

Open questions for the team (👤): <bulleted list, or "none">
```

Rules:
- Lead with the worst findings. Don't bury a critical IP flag under formatting.
- Show clean ✅ items briefly (so the team sees what was checked) but don't pad.
- Every 🚩 and ⚠️ must have a concrete redline or action — not just a complaint.
- Every 👤 must say exactly what decision the human needs to make.

## Redline guidance

When proposing a change, be specific and usable:
- Prefer showing **current → proposed** language, or clearly describe the edit.
- Keep proposed wording plain and neutral; A&B can hand it to the counterparty.
- Offer a **fallback** where relevant ("ideal: assign IP to A&B; fallback:
  exclusive, royalty-free, worldwide licence").
- Tie the redline to the reason ("so A&B retains ownership of the results it paid
  for"). Don't propose changes you can't justify from the checklist.

## Few-shot example (abridged) — supplier/service SOW → RED

**Input:** A services agreement engaging a firm to design a control-electronics
sub-assembly. Key terms: *"All deliverables are provided on an as-is basis.
Deliverables are deemed accepted upon delivery."* IP clause: *"Provider retains
all intellectual property in the deliverables and grants Customer a non-exclusive
licence to use them."* Liability capped at the fees paid.

**Output (abridged):**
```
Contract type: Supplier / service-provider (confidence: high)
Overall recommendation: do not sign / escalate — critical IP and acceptance issues.
Summary: A&B would pay to develop a sub-assembly but not own it, accept it with no
testing, and have no meaningful remedy if it's defective. Fix IP, acceptance, and
liability before proceeding.

### IP ownership of deliverables
- Status: 🚩  Severity: critical
- What it says: Provider retains all IP; A&B gets a non-exclusive licence.
- Why it matters: A&B is paying to create IP central to its hardware and would not
  own it — and the provider could reuse it, including with competitors.
- Redline / action: "Provider hereby assigns to Customer all right, title and
  interest in the Deliverables." Fallback: exclusive, worldwide, royalty-free
  licence + no reuse for third parties in the quantum field. Carve out Provider's
  clearly-listed pre-existing IP only.

### Acceptance of deliverables
- Status: 🚩  Severity: high
- What it says: "Deemed accepted upon delivery", deliverables "as-is".
- Why it matters: A&B has no chance to test conformance and no remedy for defects.
- Redline / action: add an acceptance-testing right (e.g. 30 days), conformance to
  the Schedule A specs, a cure-or-refund path, and final payment on acceptance.
- 👤 Needs human: engineering must define the actual acceptance specs (Schedule A).

### Limitation of liability
- Status: 🚩  Severity: high
- What it says: liability capped at fees paid; no carve-outs.
- Why it matters: if a defect damages A&B equipment or IP, the cap is far below the
  real downside.
- Redline / action: add carve-outs (IP infringement, breach of confidentiality,
  personal injury/property damage) and raise the general cap.

Open questions for the team (👤):
- Engineering to define acceptance specs (Schedule A).
- Is Provider's "pre-existing IP" list accurate and acceptably narrow?
```

## Edge case handling

- **Type has no checklist / out of scope** → say so and stop; route to the right
  specialist. Don't improvise.
- **Contract mixes types** (e.g. MSA + embedded DPA) → load and apply each relevant
  checklist; report findings per part.
- **Clause can't be located** → state that the concept appears **absent** and treat
  absence as the finding (often a risk in itself), rather than assuming it's fine.
- **Conflicting clauses** inside the contract → flag the conflict explicitly; it's a
  drafting risk even if each clause alone is acceptable.
- **Partial / truncated document** → review what's present, and clearly list what
  couldn't be assessed. Don't infer missing clauses.
- **Deal-specific substance** (specs, price, counterparty trust) → always 👤; state
  the decision needed.
- **Non-English contract** → review in the original language (French is common at A&B).
- **User wants only redlines / only a summary** → still run the full review
  internally; then give them the view they asked for, but keep the critical flags
  visible.
