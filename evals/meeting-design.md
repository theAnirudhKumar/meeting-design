# Evaluation: meeting-design

**Run on:** 5 Nov 2026, second run with the 4.2.0 descriptions, Haiku, Sonnet and Opus (run as model subagents), each shown only the verbatim descriptions of all 29 skills (26 in this repository plus the 3 in meeting-design), description snapshot `731601fe12b6`. Judged on the description alone. A cell is the skill that model picked; **bold** means it differs from the expected answer. Cases with a single expected answer: 15. All three models matched on 15; Haiku 15, Sonnet 15, Opus 15.

**Method** (from [README.md](README.md)): give a model the verbatim `description` of every skill in this repository, plus the sibling descriptions listed below, and nothing else. Put each message to it, ask for one skill name or `none`, with a confidence and a one-line reason. Repeat on Haiku, Sonnet and Opus. Record the disagreements. Pin the exact description text with the git commit it came from, because a result holds for one wording only.

**Descriptions under test:** snapshot `c4b8a8cfab44`, the 29 descriptions shown together.

**Sibling descriptions to include in a run:** `meeting-design`, `meeting-close`, `meeting-audit`, plus, from [work-design](https://github.com/theAnirudhKumar/work-design), `meeting-or-message`. For the cases marked "other repo" also include a call-recap or meeting-notes skill, such as the `call-recap` skill in common skill sets.

---

## Should fire

| # | Message | Expected | Haiku | Sonnet | Opus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | "Here is the invite for Thursday's alignment session with 12 people. Can you fix it?" | meeting-design | meeting-design | meeting-design | meeting-design |
| 2 | "Build me an agenda for a pricing decision meeting with sales and finance." | meeting-design | meeting-design | meeting-design | meeting-design |
| 3 | "Who should actually be in this meeting? Invite list pasted below." | meeting-design | meeting-design | meeting-design | meeting-design |
| 4 | "I have a board review on Monday. How should I structure it?" | meeting-design | meeting-design | meeting-design | meeting-design |
| 5 | "My 1:1s keep turning into status reports. How should I run them?" | meeting-design | meeting-design | meeting-design | meeting-design |
| 6 | "Our sprint retro has gone stale and nothing changes after it. Help me redesign it." | meeting-design | meeting-design | meeting-design | meeting-design |
| 7 | "Is my kickoff meeting necessary? Here is the description: [pasted]." | meeting-design | meeting-design | meeting-design | meeting-design |
| 8 | "Plan a two-day offsite for 10 people so we leave with decisions, not just a good conversation." | meeting-design | meeting-design | meeting-design | meeting-design |

## Should not fire

Near misses that belong to a sibling or to another repository. The pass condition is that `meeting-design` is not chosen.

| # | Message | Expected | Haiku | Sonnet | Opus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | "Here are my notes from the call. What did we actually decide?" | meeting-close | meeting-close | meeting-close | meeting-close |
| 2 | "Audit my recurring meetings and tell me which to cancel." | meeting-audit | meeting-audit | meeting-audit | meeting-audit |
| 3 | "Should I send an email or hop on a call to tell the team about the deadline change?" | meeting-or-message (other repo) | meeting-or-message | meeting-or-message | meeting-or-message |
| 4 | "Summarise this call transcript for me." | none of the three; a call-recap or notes skill (other repo) | none | none | none |
| 5 | "Find a time for me and Sam to meet on Tuesday." | none (scheduling is not this skill) | none | none | none |
| 6 | "Write the follow-up email to the attendees of yesterday's meeting." | meeting-close | meeting-close | meeting-close | meeting-close |

## Conflicts

No simple pass or fail. Record what each model chose and decide, in writing, whether the split is acceptable.

| # | Message | Expected | Haiku | Sonnet | Opus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | "Is this weekly meeting still worth having? Details: Fridays, 60 minutes, 9 people, status updates." | conflict: meeting-design quick fix or meeting-audit. Both give a verdict. Record what each model does and decide in writing; a split is acceptable if both land on a verdict and a cost line | meeting-audit | meeting-audit | meeting-audit |
| 2 | "Should this be a meeting or can I just send a message?" | meeting-or-message (other repo). meeting-design starts once a meeting exists or is planned | meeting-or-message | meeting-or-message | meeting-or-message |
| 3 | "I need to run a meeting and then write it up. Can you help with both?" | conflict: meeting-design first, meeting-close later. Record whether the model names both | meeting-design | meeting-design | meeting-design |

---

## Output check, by hand

Run one case, the pasted-invite one, and check the output has:

- [ ] A verdict on the first line, one of cancel and replace, shrink, or keep and fix
- [ ] A cost line showing attendees x hours x rate, with a placeholder rate labelled as an assumption if none was given
- [ ] A rewritten invite in a code block, with the title as the decision
- [ ] The decision rule stated in one line, and a deadlock default
- [ ] An attendee cut that names who moved to informed
- [ ] Brackets left empty for any fact the user did not supply, and no invented names, dates or links
- [ ] No statistics about what meetings cost or how effective they are

---

## Not tested here

- **Whether the description survives the listing budget.** Routing is tested with descriptions shown in full. In a real installation the listing is truncated and a newly installed skill with no invocation history loses its description text first.
- **Output quality.** These cases test which skill fires. The output check above is done by hand on one case per skill.
- **Real sessions.** Every case is a constructed message written by the author of the skill. Nothing here shows the skill firing in the wild.

## Rerun when

A description changes anywhere in the repository, a skill is added or removed, or a model is added to the set.

## Misses and how to read them

No misses on cases with a single expected answer.
