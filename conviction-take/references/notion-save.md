# Saving a take to Notion

## The database

The Takes database already exists. Go straight to it, do not search for it.

- Database page: `https://app.notion.com/p/0817404134a24a4a864a6a48bfd65c8c`
- Data source ID for creating pages: `be39fe13-ef24-4998-8d4c-9df28f54f578`
- Location: HOME page, under 💾 OS, below Posting Automation

Fetch the data source before writing if it has been a while, in case Antoine has edited the properties. Property names must match exactly.

## Schema

| Property | Type | What goes in it |
|---|---|---|
| Name | title | Subject plus angle, so the list is scannable unopened |
| Subject | text | Plain name of the company, policy, work or claim |
| Lens | multi-select | venture, politics, history, culture, science |
| Verdict | select | interesting, watch, overhyped, pass, undecided |
| Conviction | select | high, medium, low |
| One line | text | The compressed take from the end of the analysis |
| Source | url | The primary link |
| Date | date | When the take was built |
| Revisit | date | When the earliest tripwire becomes checkable |

Dates use the expanded form: `date:Date:start` and `date:Date:is_datetime` set to 0.

## Writing the entry

- **Name**: "Saronic Port Alpha: a shipyard bet dressed as a drone-boat scale-up" rather than "Saronic". The angle belongs in the title.
- **Verdict** and **Conviction**: your actual assessment. Do not default to "undecided" and "medium" to avoid committing. If the take reached a conclusion, record it. Conviction is about how sure the verdict is, and is a separate judgment from the verdict itself.
- **Revisit**: the date the earliest tripwire becomes checkable, so the entry surfaces when it is testable. If no tripwire has a date, use six months out.
- **Page content**: the full take with headers intact, plus a Sources section at the end. Do not summarise it. Drop the inline glossary parentheticals only if they make the stored version unreadable, otherwise keep them.

## Revisiting a subject

Before building a take on anything, search the Takes data source (`collection://be39fe13-ef24-4998-8d4c-9df28f54f578`) for the subject.

If a prior take exists:

1. Read it.
2. Open the new take by saying what you previously concluded and what has changed since.
3. Check the old tripwires explicitly. Say which fired, which did not, and which are still open. This is the point of the whole system.
4. Append the new take to the existing page under a dated header rather than creating a duplicate row.
5. Update Verdict, Conviction and Revisit on the existing row.

## Existing entries

- Saronic Port Alpha, 28 July 2026, verdict "watch", conviction medium, revisit 31 January 2027.
