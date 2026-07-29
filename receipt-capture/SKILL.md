---
name: receipt-capture
description: Capture a receipt or expense into Antoine's 🧾 Receipt Inbox Notion database, to be reconciled monthly against his bank export. Trigger whenever Antoine sends a photo of a receipt, ticket de caisse, or card slip — even with no text — or says things like "add this expense", "capture this receipt", "reçu", "ticket", "j'ai payé 20 chez X", "40€ resto hier", "paid 15 for lunch, work". A bare amount+merchant message counts. Also for cash expenses ("paid cash"). NOT for importing bank exports, categorizing the Excel log, or answering finance questions — those run in Claude Code on the Mac.
---

# /receipt-capture — Receipt Inbox

One job: turn a receipt (photo or words) into one well-formed row in the
**🧾 Receipt Inbox** Notion database, status **Pending**, with a 10-second
interview. A monthly job on his Mac matches pending rows against the Crédit
Mutuel bank export and writes his answers into the Financial Statement
workbook — **what he answers here beats every auto-rule there**, so capture
faithfully and compactly.

The database: search Notion for the "Receipt Inbox" database under the
*Finance Automation* page (data source `collection://b8614648-b2a7-4faa-83b6-8ae4310d499b`).

## Step 1 — Extract

From the photo (or message): **merchant** (title), **date** of purchase
(default: today; "hier" = yesterday), **total amount** (final total, tip
included), **currency**.

- `Amount` is **signed like the bank: negative for expenses**, positive only
  for money coming in (refunds, reimbursements).
- Non-EUR receipt: `Original amount` = the foreign total, `Currency` = its
  currency, `Amount` = your best EUR estimate (say "≈" in the reply).
- Cash ("en liquide"): `Status` = **Cash** (it will never hit the bank export).
  Everything else: `Status` = **Pending**.

## Step 2 — The interview (always, ONE compact message)

Never guess silently: after extracting, ask ONE short message covering only
what his caption didn't already answer, then wait:

> 🧾 Doctolib −60,00 € · 15/01
> 1. Catégorie : **Health / Doctor appointment** — ok ?
> 2. Actual ou **ghost** (avancé pour quelqu'un) ? Si ghost : pour qui —
>    Parents / Debts / Others ?
> 3. Un commentaire ?

Rules of the interview:
- His caption pre-answers: "resto, ghost parents, dîner avec papa" answers
  everything → skip the questions, file directly, confirm in one line.
- Propose your best category guess in question 1 — he confirms with "ok"/"oui"
  or corrects.
- Account is automatic (Compte_Courant_CM at reconciliation) — only ask if he
  hints he paid with another card or account.
- One receipt = one interview message max. Several receipts in one message →
  one merged interview, numbered.

## Ghost expenses (his exact convention)

Ghost = "I paid, but someone else ultimately bears it (or owes me)".
In the row: `Ghost` = true, `From` = **Me**, `To` = whoever bears it
(**Parents** / Debts / Others). Keep the real expense category in
Category/Subcategory (a doctor stays Health even when parents reimburse).
The reverse flow (a reimbursement arriving) is a positive Amount with
`From` = them, `To` = Me, category Secondaries/Reimbursement.

## Step 3 — Parents-ghost → WhatsApp handoff

When the answer is **ghost → To = Parents**, after filing the row:

1. Compose a short French note, e.g.:
   `Coucou, j'ai avancé 60,00 € chez Doctolib le 15/01 — reçu en photo. Antoine`
   (adapt merchant/amount/date; one sentence, no flourish).
2. Reply with a tap-to-send link so he can forward it with the photo from his
   phone: `https://wa.me/<number>?text=<URL-encoded note>` — the number is on
   the private **Finance Automation** page in Notion (parent of the Receipt
   Inbox), line "Parents WhatsApp:". Fetch it from there; if absent, ask
   Antoine once and add it to that page. Remind him: *"tape le lien, ajoute la
   photo (dernière du rouleau), envoie"*. Sending in WhatsApp is his
   confirmation — never claim the message was sent.
3. Append "receipt forwarded to parents" to the row's `Comment`.

## Step 4 — Write the row

Create the page in the data source with: Merchant, `date:Date:start`
(YYYY-MM-DD), Amount, Currency, Original amount (if FX), Category, Subcategory,
Ghost (`__YES__`/`__NO__`), From, To, Comment, Status. Attach the photo if the
surface supports it; skip silently if not. **Dedupe first**: same amount +
same date already Pending → ask before creating a second row (double-sent
photo vs. two real coffees).

## Categories (exact select options)

- **Groceries**: Bulk groceries · Small groceries · Little extras
- **Outside_Consumption**: Intentional eating out · No choice eating out · Drinks · Dinner at friend's · Work/Uni consumption · Coffee
- **Activities**: Party · Sports · Cultural · Trip
- **Transportations**: Public transportation · Private transportation · Personal transportation · Travel transportation
- **Subscriptions**: Mobile plan · Xbox · Sports membership · Wifi · AI
- **Housing**: Rent · House insurance · Mortgage · Energy · Deposit · Temporary Stays
- **Bank**: Account fees · Overdraft fees · Loan fees · Loan insurance
- **Material**: Clothes/ Accessories · Tech · Newspaper/books · Art piece · Home objects · Bricolage
- **Health**: Doctor appointment · Meds · Cosmetics · Hairdresser
- **Education**: Tuitions · Extras · University Sports
- **Household_Necessities**: Laundry · Miscelleanous
- **Gifts** (no subcategory)
- **Transfer**: Interbank transfer · Interbank transfer fees
- Income — **Primaries**: Main Job · Allowance · CAF / **Secondaries**: Ad hoc Missions · Side Hustle · Funds Disbursement · Reimbursement · Gift · Reselling · Interbank transfer · Intrabank transfer

Shorthand: "resto" → Outside_Consumption/Intentional eating out · "courses" →
Groceries/Small groceries · "verres" → Drinks · "taf" → Work/Uni consumption ·
"essence"/"péage" → Transportations/Travel transportation · "métro" → Public
transportation · "pharma" → Health/Meds · "sport" → Activities/Sports.

## Reply (after the interview)

One line: `🧾 Doctolib −60,00 € → Health/Doctor appointment · ghost → Parents · pending reconciliation`
plus the WhatsApp link line when applicable. No essays.
