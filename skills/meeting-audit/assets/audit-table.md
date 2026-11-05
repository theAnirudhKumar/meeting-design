# Audit Table

One row per recurring meeting. Fill the first five columns from what the user gave, work out the rest. Mark rough numbers with a tilde.

**Hourly rate:** [rate]  *(assumption if the user did not give one: replace it with your own)*

**Occurrences per month:** daily on weekdays 21.7, weekly 4.33, every two weeks 2.17, monthly 1, quarterly 0.33.

---

| Meeting | Cadence | Length | People | Owner | Person-hours / month | Cost / month | Verdict | New shape | Hours freed / month |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
|  |  |  |  | mine / theirs |  |  | Keep / Shrink / Async / Kill |  |  |
|  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |

**Person-hours per month** = occurrences x length in hours x people.
**Cost per month** = person-hours x hourly rate.

**Freed**
- Kill: all person-hours
- Shrink: old person-hours minus (new length x new people x same occurrences)
- Async: two thirds of the old person-hours. *Assumption: reading and replying costs a third of the meeting length per person.*
- Keep: none

---

## Totals

- **Audited:** [hours per month], [cost per month]
- **Freed:** [hours per month], [cost per month], [share of audited]

## Start here

1. [meeting], frees [hours] a month
2. [meeting]
3. [meeting]

## Sunset lines for what stays

| Meeting | Runs until | Continues only if |
| :--- | :--- | :--- |
|  | [date] | It has produced a decision in the last month |

## The one message

> [four sentences: what changes and from when, why, what replaces it, the review date and an invitation to object]

## Assumptions

- [rate]
- [rough attendee counts]
- [who owns what]
