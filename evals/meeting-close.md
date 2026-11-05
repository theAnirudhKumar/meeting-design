# Evaluation: meeting-close

**Run on:** 5 Nov 2026, Haiku, Sonnet and Opus (run as model subagents), each shown only the verbatim descriptions of all 29 skills (26 in this repository plus the 3 in meeting-design), description snapshot `c4b8a8cfab44`. Judged on the description alone. A cell is the skill that model picked; **bold** means it differs from the expected answer. Cases with a single expected answer: 12. All three models matched on 11; Haiku 11, Sonnet 12, Opus 11. The protect-my-focus description was reworded after this run; see the targeted rerun in `evals/README.md`.

**Method** (from [README.md](README.md)): give a model the verbatim `description` of every skill in this repository, plus the sibling descriptions listed below, and nothing else. Put each message to it, ask for one skill name or `none`, with a confidence and a one-line reason. Repeat on Haiku, Sonnet and Opus. Record the disagreements. Pin the exact description text with the git commit it came from, because a result holds for one wording only.

**Descriptions under test:** snapshot `c4b8a8cfab44`, the 29 descriptions shown together.

**Sibling descriptions to include in a run:** `meeting-design`, `meeting-close`, `meeting-audit`, plus, from [work-design](https://github.com/theAnirudhKumar/work-design), `meeting-or-message`. For the cases marked "other repo" also include a call-recap or meeting-notes skill, such as the `call-recap` skill in common skill sets.

---

## Should fire

| # | Message | Expected | Haiku | Sonnet | Opus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | "Here are my notes from the pricing call. Write up what we decided." | meeting-close | none | none | none |
| 2 | "Draft the follow-up email for the meeting we just had. Notes below." | meeting-close | meeting-close | meeting-close | meeting-close |
| 3 | "What did we actually agree on in this thread? Who owns what?" | meeting-close | meeting-close | meeting-close | meeting-close |
| 4 | "Turn this transcript into a decision log with owners and dates." | meeting-close | meeting-audit | meeting-audit | meeting-audit |
| 5 | "We talked about a lot of things in the planning meeting. Which ones did we actually decide?" | meeting-close | meeting-close | meeting-close | meeting-close |
| 6 | "Here is the recap from our sync. Flag anything we discussed but never settled." | meeting-close | meeting-close | meeting-close | meeting-close |

## Should not fire

Near misses that belong to a sibling or to another repository. The pass condition is that `meeting-close` is not chosen.

| # | Message | Expected | Haiku | Sonnet | Opus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | "Summarise this call so I can read it in two minutes." | none of the three; a call-recap or notes skill (other repo) | meeting-close | meeting-close | meeting-close |
| 2 | "Transcribe this recording." | none (this skill does not record or transcribe) | none | none | none |
| 3 | "Build an agenda for next week's planning meeting." | meeting-design | meeting-design | meeting-design | meeting-design |
| 4 | "Which of my recurring meetings should I cancel?" | meeting-audit | meeting-close | meeting-close | meeting-close |
| 5 | "Prep me for my call with the client tomorrow." | none of the three; a call-prep skill (other repo) | **meeting-design** | none | **meeting-design** |
| 6 | "Pull the action items out of this email chain into a task list." | none, or meeting-close if the thread was a meeting recap. Record which | meeting-close | meeting-close | none |

## Conflicts

No simple pass or fail. Record what each model chose and decide, in writing, whether the split is acceptable.

| # | Message | Expected | Haiku | Sonnet | Opus |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | "Here are my meeting notes. Summarise them and list the action items." | conflict: meeting-close or a call-recap or notes skill. The ask for a summary leans to the other skill, the action items lean to meeting-close. Record what each model does; a split is acceptable | meeting-close | meeting-close | meeting-close |
| 2 | "Here is the agenda and the notes. Did we get to the decision we planned?" | meeting-close. The agenda comparison is a Step 1 input | meeting-close | meeting-close | meeting-close |

---

## Output check, by hand

Run the messy-notes case in [examples/pricing-call-close.md](../examples/pricing-call-close.md) and check the output has:

- [ ] A decision record where a hedged line ("I think we agreed") is marked needs confirming, not firm
- [ ] The decision rule named, or "rule not stated", never guessed
- [ ] Dissent recorded with the reason, or "reason not recorded"
- [ ] Every missing owner or date written in capitals, with a proposed value marked as proposed
- [ ] A separate list of what was discussed but never decided, with a route for each
- [ ] A follow-up message that leads with the decision and is under 150 words
- [ ] No names, reasons or dates that are not in the pasted text
- [ ] No claim to have recorded, joined or transcribed the meeting

---

## Not tested here

- **Whether the description survives the listing budget.** Routing is tested with descriptions shown in full. In a real installation the listing is truncated and a newly installed skill with no invocation history loses its description text first.
- **Output quality.** These cases test which skill fires. The output check above is done by hand on one case per skill.
- **Real sessions.** Every case is a constructed message written by the author of the skill. Nothing here shows the skill firing in the wild.

## Rerun when

A description changes anywhere in the repository, a skill is added or removed, or a model is added to the set.

## Misses and how to read them

| Case | Message | Expected | Haiku | Sonnet | Opus | Reading |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| meeting-close#5.2 | "Prep me for my call with the client tomorrow." | none of the three; a call-prep skill (ot | **meeting-design** | none | **meeting-design** | Stale expectation. "Prep my client call" belongs to meeting-design, which is installed alongside now. |
