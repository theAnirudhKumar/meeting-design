---
name: meeting-audit
description: >
  Audits recurring meetings or a week of calendar and says which to keep, shrink, convert to async, or kill. Trigger on "audit my meetings", "my calendar is full of meetings", "which meetings can I cancel", "meeting overload", "too many recurring meetings", "how much do our meetings cost", "clean up my calendar", "should we still have this weekly", "kill this standing meeting", or when the user pastes a list of recurring meetings or a calendar export. Outputs a verdict per meeting, hours per month freed, the cost in money, a sunset date for what stays, and one message to cancel or change a meeting without drama. Works from pasted text; a calendar connector may read events if present but is never required. Not for designing one upcoming meeting (meeting-design) or writing up a finished one (meeting-close).
---

# Meeting Audit

A recurring meeting is almost never cancelled, because nobody owns cancelling it and the person who suggests it becomes the person who killed it. So it outlives the problem it was set up to solve.

The failure this exists to prevent: **a calendar full of standing meetings that each made sense once, with nobody able to say which still earn their hours.**

This skill takes the list and does the arithmetic and the judgement, so the user only has to send the messages.

---

## What this needs

**Minimum: a list of recurring meetings** with name, how often, length and roughly how many people. Pasted from a calendar, typed from memory, or a screenshot's text are all fine. A rough number is better than none; mark it as rough.

**Better with** who owns each meeting (the user, or someone else) and, for each, the last decision it produced.

**Best with** an hourly rate. If none is given, ask once; if still none, use a placeholder and label it as an assumption.

If a calendar connector is available and the user asks for it, events may be read to build the list. Never require it, and never edit, cancel or send anything through it. The output is a plan and drafted messages.

---

## Step 1: Build the table

Put every meeting in `assets/audit-table.md`. For each, work out the person-hours per month:

- Occurrences per month: daily (weekdays) 21.7, weekly 4.33, every two weeks 2.17, monthly 1, quarterly 0.33
- Person-hours per month = occurrences x length in hours x attendees
- Cost = person-hours x hourly rate

State these conversions in the output so the user can check them. Only time in the room is counted, so every number is a floor. Do not quote industry benchmarks.

## Step 2: Ask each meeting the same four questions

1. **What decision does it exist to make?** If the user or the invite cannot name one, the answer is "none".
2. **Did it produce one in the last month?** Unknown counts as no.
3. **Is information flowing one way?** One person talking to many is a document.
4. **Is every attendee needed for the decision?** If a third of the room never speaks, they are informed.

## Step 3: Give each meeting one verdict

- **Kill.** No decision named and none produced. Say what, if anything, replaces it: a shared board, a channel, nothing
- **Convert to async.** Information flows one way, or the content is status. It becomes a written update with a reply deadline. Keep a short call for items someone flags as stuck
- **Shrink.** A real decision exists, but the length or the attendee list is more than it needs. State the new length and the new list
- **Keep.** It makes decisions or serves a relationship that needs the live time (1:1s, retros that produce changes). Say why in one clause, and leave it alone

Do not make everything a Kill. If most meetings are worth keeping, say so. A verdict of Keep is a result.

**Ownership changes the move.** If the user owns the meeting, the move is cancelling or changing it. If someone else owns it, the move is a message to the owner proposing the change, or declining the user's own seat with a reason. Never advise the user to unilaterally cancel a meeting that is not theirs.

## Step 4: Count what is freed

Per meeting, from the verdict:

- **Kill:** all of the person-hours
- **Shrink:** old person-hours minus the new person-hours (new length x new attendees x same frequency)
- **Convert to async:** two thirds of the old person-hours. This assumes reading and replying costs a third of the meeting length per person. It is an assumption, so label it and let the user change it
- **Keep:** none

Then total: hours per month freed, the money value at the stated rate, and the share of the audited total. Freed hours are capacity, not output, and say so in one clause if the user treats them as saved.

## Step 5: Set a sunset date for whatever stays

Every Keep and Shrink gets a review date, six weeks out or after the next six occurrences, whichever is earlier. Write it into the invite: *"This meeting runs until [date]. It continues only if it has produced a decision in the last month."* A pre-agreed date means nobody has to be the person who suggested cancelling.

## Step 6: Write the one message

Write a single message the user can send to cancel or change the highest-saving meeting. Keep it to four sentences:

1. What is changing and from when
2. Why, as a fact about time or output, not blame
3. What replaces it
4. The review date, and an invitation to object

Tone: plain and warm. No apology for existing, no accusation. If the user owns several meetings to change, draft the message for the top one and tell them to adapt it. Advise starting with the top one to three by hours freed rather than changing everything at once, because a calendar changed all at once gets noticed as an event, not as an improvement.

## Output

In this order:

1. **The table**, filled from `assets/audit-table.md`, with the conversions stated
2. **Totals**: hours per month freed, cost freed at the stated rate, share of total
3. **Start here**: the top one to three by hours freed
4. **Sunset line** for what stays
5. **The one message**, in a code block
6. **Assumptions**: rate, rough attendee counts, ownership, anything unknown

## Failure modes

- **Auditing by feeling.** "This one is a waste" is not a verdict. Every Kill needs the answer to the four questions
- **Killing the relationship meeting.** 1:1s and customer calls carry things a decision test misses. Default them to Keep
- **Unilateral cancellation of someone else's meeting.** It costs trust. Propose to the owner
- **False precision.** A rate that was assumed and attendee counts that were rough produce an order of magnitude, not an invoice. Say so
- **Counting freed time as output.** It is capacity until something uses it
- **Everything at once.** Change the top few, then look again at the sunset dates

## Reference files

- `assets/audit-table.md` - the table, the conversions and the verdict key
