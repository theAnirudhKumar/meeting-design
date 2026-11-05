# Evaluation: meeting-audit

**Status: written, not yet run.** Nothing in this file is a model result. The Haiku, Sonnet and Opus columns say "not yet run" because no model was run against these cases when they were written. The Expected column is the routing the author intends, not an observation. Do not read a filled-in Expected column as evidence that the skill fires.

**Method** (from [README.md](README.md)): give a model the verbatim `description` of every skill in this repository, plus the sibling descriptions listed below, and nothing else. Put each message to it, ask for one skill name or `none`, with a confidence and a one-line reason. Repeat on Haiku, Sonnet and Opus. Record the disagreements. Pin the exact description text with the git commit it came from, because a result holds for one wording only.

**Descriptions under test:** as at v2.0.0 of this repository.

**Sibling descriptions to include in a run:** `meeting-design`, `meeting-close`, `meeting-audit`, plus, from [work-design](https://github.com/theAnirudhKumar/work-design), `pick-the-medium`. For the cases marked "other repo" also include a call-recap or meeting-notes skill, such as the `call-recap` skill in common skill sets.

---

## Should fire

| # | Message | Expected | Haiku | Sonnet | Opus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | "My calendar is wall to wall. Here are my recurring meetings. Which can go?" | meeting-audit | not yet run | not yet run | not yet run |
| 2 | "How much are our standing meetings costing us? List below." | meeting-audit | not yet run | not yet run | not yet run |
| 3 | "Audit my week: [pasted calendar export]" | meeting-audit | not yet run | not yet run | not yet run |
| 4 | "We have a weekly sync that nobody likes. Should we still have it?" | meeting-audit | not yet run | not yet run | not yet run |
| 5 | "Help me clean up my calendar before the new quarter." | meeting-audit | not yet run | not yet run | not yet run |
| 6 | "Draft a message to cancel our Monday meeting without annoying anyone." | meeting-audit | not yet run | not yet run | not yet run |

## Should not fire

Near misses that belong to a sibling or to another repository. The pass condition is that `meeting-audit` is not chosen.

| # | Message | Expected | Haiku | Sonnet | Opus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | "Fix the invite for next Tuesday's one-off planning meeting." | meeting-design | not yet run | not yet run | not yet run |
| 2 | "Write up what we decided in this morning's meeting." | meeting-close | not yet run | not yet run | not yet run |
| 3 | "Block out focus time on my calendar every afternoon." | none (calendar editing, not an audit) | not yet run | not yet run | not yet run |
| 4 | "Find a time that works for six people next week." | none (scheduling) | not yet run | not yet run | not yet run |
| 5 | "Should I send a Slack message or set up a meeting?" | pick-the-medium (other repo) | not yet run | not yet run | not yet run |

## Conflicts

No simple pass or fail. Record what each model chose and decide, in writing, whether the split is acceptable.

| # | Message | Expected | Haiku | Sonnet | Opus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | "Is this weekly meeting still worth having? Details: Fridays, 60 minutes, 9 people, status updates." | conflict: meeting-audit or meeting-design quick fix. Same case as in the meeting-design file; the two files should record the same result | not yet run | not yet run | not yet run |
| 2 | "Redesign my team's standing standup so it is useful." | conflict: meeting-design (standup playbook) or meeting-audit. Redesigning one meeting leans to meeting-design; record what each model does | not yet run | not yet run | not yet run |

---

## Output check, by hand

Run the eight-meeting case in [examples/recurring-audit.md](../examples/recurring-audit.md) and check the output has:

- [ ] A row per meeting, with the occurrences-per-month conversions stated
- [ ] Person-hours and cost worked from attendees x length x occurrences, and the arithmetic checks by hand
- [ ] The rate labelled as an assumption if the user gave none
- [ ] A verdict for every meeting, and at least one Keep where the facts support it (not everything killed)
- [ ] The convert-to-async assumption (a third of the meeting length per person) labelled as an assumption
- [ ] A different move for meetings the user does not own: a message to the owner, not a cancellation
- [ ] A sunset date for what stays, and one message of about four sentences
- [ ] No benchmark statistics, and no calendar changes made

---

## Not tested here

- **Whether the description survives the listing budget.** Routing is tested with descriptions shown in full. In a real installation the listing is truncated and a newly installed skill with no invocation history loses its description text first.
- **Output quality.** These cases test which skill fires. The output check above is done by hand on one case per skill.
- **Real sessions.** Every case is a constructed message written by the author of the skill. Nothing here shows the skill firing in the wild.

## Rerun when

A description changes anywhere in the repository, a skill is added or removed, or a model is added to the set.
