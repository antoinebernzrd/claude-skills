---
name: receipt-capture
description: Capture a receipt or expense into Antoine's 🧾 Receipt Inbox Notion database, to be reconciled monthly against his bank export. Trigger whenever Antoine sends a photo of a receipt, ticket de caisse, or card slip — even with no text — or says things like "add this expense", "capture this receipt", "reçu", "ticket", "j'ai payé 20 chez X", "40€ resto hier", "paid 15 for lunch, work". A bare amount+merchant message counts. Also for cash expenses ("paid cash"). NOT for importing bank exports, categorizing the Excel log, or answering finance questions — those run in Claude Code on the Mac.
---

# /receipt-capture — Receipt Inbox

One job: turn a receipt (photo or words) into one well-formed row in the
**🧾 Receipt Inbox** Notion database, status **Pending**, in under 10 seconds of
Antoine's attention. A monthly job on his Mac matches pending rows against the
Crédit Mutuel bank export and writes his categories into the Financial
Statement workbook — **his category stated here beats every auto-rule there**,
so capture faithfully and compactly.

The database: search Notion for the "Receipt Inbox" database under the
*Finance Automation* page (data source `collection://b8614648-b2a7-4faa-83b6-8ae4310d499b`).

## Extract

From the photo (or message): **merchant** (title), **date** of purchase
(default: today if absent; "hier" = yesterday), **total amount** (the final
total, tip included), **currency**.

- `Amount` is **signed like the bank: negative for expenses**, positive only
  for money coming in (refunds, reimbursements).
- Non-EUR receipt: `Original amount` = the foreign total, `Currency` = its
  currency, `Amount` = your best EUR estimate (state "≈" in the reply). The
  matcher tolerates ~5% FX drift.
- Cash payment ("en liquide", "cash"): `Status` = **Cash** (it will never appear
  in the bank export). Everything else: `Status` = **Pending**.

## Categorize

Use exactly these Category → Subcategory pairs (select options in the DB):

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

Shorthand he'll use: "resto" → Outside_Consumption/Intentional eating out ·
"courses" → Groceries/Small groceries · "verres"/"drinks" → Drinks · "taf"/
"work lunch" → Work/Uni consumption · "essence"/"péage"/"train (trip)" →
Transportations/Travel transportation · "métro" → Public transportation ·
"pharma" → Health/Meds · "sport" → Activities/Sports.

If he gives no category: **guess from the merchant, save the guess, and say so**
— never block capture on a question. If genuinely unguessable, save without
category (the Mac-side review will catch it).

## Ghost expenses

"paid for Max", "maman me rembourse", "avancé pour la coloc" → `Ghost` = true,
`From` = who paid (usually Me), `To` = who ultimately bears/owes it
(Parents / Debts / Others). The rest of his phrasing goes to `Comment`
("paid for Max, he owes me half").

## Write the row

Create the page in the data source with: Merchant, `date:Date:start`
(YYYY-MM-DD), Amount, Currency, Original amount (if FX), Category, Subcategory,
Ghost (`__YES__`/`__NO__`), From, To, Comment, Status. Attach the photo to the
page if the surface supports it; skip silently if not — the data is what
matters. Several receipts in one message → one row each.

**Dedupe first**: if a Pending row with the same amount and date already
exists, ask before creating a second one (he may have double-sent the photo —
but two coffees at the same place the same day are also real).

## Reply

One line, no essay:
`🧾 Rituals −35.90 € → Health/Cosmetics · pending reconciliation`
Add a second line only for something he must know (guessed category, FX
estimate, possible duplicate).
