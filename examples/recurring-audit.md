# Example: a team lead's recurring calendar

*Illustrative. Invented meetings and numbers.* Skill: `meeting-audit`.

## What was pasted

Eight recurring meetings, with cadence, length, people and who owns them. The rate was not given, so the skill used a placeholder: *Assumption: 60 per hour per person. Replace it with your own.*

## What the skill returned

Occurrences per month: daily on weekdays 21.7, weekly 4.33, every two weeks 2.17, monthly 1.

| Meeting | Cadence | Length | People | Owner | Person-hours / month | Cost / month | Verdict | New shape | Freed / month |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Weekly team sync | weekly | 60 min | 9 | mine | 39.0 | 2,340 | Async | Written update; call only for flagged items | 26.0 |
| Daily product standup | daily | 15 min | 8 | mine | 43.3 | 2,600 | Async | Written thread; 15-minute call only if someone is blocked | 28.9 |
| Leadership staff meeting | weekly | 90 min | 7 | theirs | 45.5 | 2,730 | Shrink | 60 min, same seven, agenda sent ahead | 15.2 |
| Roadmap review | every 2 weeks | 60 min | 12 | theirs | 26.0 | 1,560 | Shrink | 45 min, six decision-makers; the rest get the notes | 16.2 |
| 1:1 with manager | weekly | 30 min | 2 | theirs | 4.3 | 260 | Keep | Relationship and feedback carry it | 0 |
| Team retro | every 2 weeks | 60 min | 8 | mine | 17.3 | 1,040 | Keep | It produces changes, if actions from last time are reviewed | 0 |
| Cross-team dependency sync | weekly | 30 min | 10 | theirs | 21.7 | 1,300 | Kill | Replace with a shared dependency board | 21.7 |
| Monthly all-hands | monthly | 60 min | 40 | theirs | 40.0 | 2,400 | Keep | Out of scope for this lead to change | 0 |

**Totals.** Audited: 237 person-hours a month, about 14,230. Freed: 108 person-hours a month, about 6,480, which is 46% of what was audited. Async rows assume reading and replying costs a third of the meeting length per person, and that is an assumption. Freed hours are capacity, not output.

**Start here**

1. Daily product standup, about 29 hours freed. The user owns it.
2. Weekly team sync, about 26 hours freed. The user owns it.
3. Cross-team dependency sync, about 22 hours freed. The user does not own it, so the move is a message to the owner proposing the board, not a cancellation.

**Sunset lines.** Every meeting that stays in some form (the two async changes, the two shrinks, the retro): *"This meeting runs until 17 Dec. It continues only if it has produced a decision in the last month."*

**The one message** (for the standup, which the user owns)

```
From Monday we are moving the daily standup to a thread. Post what you did, what you are doing next and anything blocked by 9:30. If someone is blocked, tag the person who can help and we will do a quick call at 10:00 for those items only.

The reason is time: the standup is 15 minutes for eight of us every weekday, and most mornings nobody is blocked. We will look at how it is going on 17 Dec, and if it is not working we will put the call back. Tell me before then if it is not working for you.
```

**Assumptions:** the rate; attendee counts as given; the user owns the standup, team sync and retro and none of the others; the all-hands is out of scope.
