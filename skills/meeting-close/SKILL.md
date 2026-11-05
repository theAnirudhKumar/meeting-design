---
name: meeting-close
description: >
  Turns messy notes from a meeting that already happened into a decision record and a follow-up message. Trigger on "write up what we decided", "here are my notes, what was decided", "draft the follow-up", "send-around after the meeting", "decision log", "what did we actually agree", "who owns what from this", "turn this transcript into actions", or when the user pastes notes, a transcript or a recap and wants decisions, owners and dates. Outputs the decision, the rule used, owner, date, recorded dissent, open items, a ready-to-send message, and a flag for anything discussed but never decided. Works only on text the user pastes; it does not record or transcribe. Not a summary tool: for a faithful summary of what was said use a call-recap or notes skill. Not for planning a meeting (meeting-design) or auditing recurring ones (meeting-audit).
---

# Meeting Close

A summary records what was said. A decision record records what was decided, by whom, by when, over whose objection, and what was left open. Most notes are the first and people need the second.

The failure this exists to prevent: **everyone leaves with a different memory of what was agreed, and the notes settle it a week later in whichever direction the note-taker remembered.**

This skill works on text the user pastes: notes, a transcript, a chat recap, a voice-memo dump. It does not record, join or transcribe meetings, and it never sends anything.

---

## What this needs

**Minimum: whatever was written down.** Messy bullet points are enough. Run on them and mark what could not be determined.

**Better with** the original invite or agenda, so the decision that was meant to be made can be compared with what was recorded.

**Best with** the attendee list and who chaired, so owners and the decision rule can be checked against real names.

If a calendar or notes connector is available and the user asks, it may be used to fetch the notes or the attendee list. Never require it; if the notes are not pasted and no connector exists, ask the user to paste them.

---

## Step 1: Read everything, then sort every item

Read the full text first. For a transcript, read all of it, not the opening. Then place every substantive item in exactly one bucket:

| Bucket | The test |
| :--- | :--- |
| **Decided** | A specific choice was stated and someone with authority made or accepted it. "Let's go with 15%" qualifies. "We should probably look at 15%" does not |
| **Action** | Someone is to do something. It needs a named person and a date to count as complete |
| **Discussed, not decided** | Positions were exchanged and the notes show no choice. This is the bucket most notes bury |
| **Dissent** | Someone objected or preferred otherwise, and it is stated in the notes |
| **Context** | Background that explains a decision. Keep only what the decision needs |

Mark each Decided item with a confidence: **firm** (clear wording and a clear decider) or **needs confirming** (hedged wording such as "I think we agreed", or no decider named). Quote the hedge so the user can see why.

Never promote a hedged item to firm. Never invent an owner, a date, a reason or a name that is not in the text.

## Step 2: Find the decision rule that was used

State how it was decided: Directive, Consult, Consent, Consensus or Delegate, taken from the evidence in the notes ("Dana made the call after hearing everyone" is Consult). If the notes do not show it, write **rule not stated** and add one line saying why that matters: without a stated rule, the people who disagreed cannot tell whether the decision was final.

## Step 3: Record dissent honestly

Write who disagreed and the reason, using only what the notes say. If the notes say "Dana was not thrilled" with no reason, record exactly that and mark the reason as missing. Recorded dissent is what lets the dissenter commit to the outcome, as in disagree-and-commit, so a record that leaves it out fails the person it is for.

## Step 4: Surface what was never decided

List every item in the Discussed, not decided bucket. For each, suggest one of three routes and say which fits: decide asynchronously by a stated date, put it on a named future meeting, or drop it explicitly. A topic without a route will be rediscovered in the next meeting.

## Step 5: Fill the owners and dates, and make the gaps visible

Every action and open item gets an owner and a date. Where the notes lack one, write **NO OWNER** or **NO DATE** in capitals and add a proposed value marked *(proposed)*. A visible gap gets fixed; a plausible filled-in value gets believed.

## Step 6: Draft the follow-up message

Fill `assets/follow-up-message.md`. Rules:

- Lead with the decision, in one sentence, before any background
- Under 150 words for a normal meeting
- List actions as "name, what, by when"
- State anything needing confirmation and ask for a reply by a stated date: *"Reply by Thursday if this is wrong."* Silence then counts as agreement, which is a consent test, so say so
- Include the dissent line if there was dissent, worded neutrally
- Match the tone of the notes. Do not make a casual team formal

## Output

In this order:

1. **Decision record**, using `assets/decision-record.md`, one per decision
2. **Not decided**, the list from Step 4 with a suggested route each
3. **Follow-up message**, ready to send, in a code block
4. **What I could not determine**, including every needs-confirming item and missing owner or date

If no decision was made, say so as the first line and do not write a decision record. Produce the Not decided list and a follow-up message that states where things stand.

## What this skill is not

A faithful summary of everything said is a different job. If the user wants one, say this skill will not give it, and that a call-recap or notes tool does. If a user wants this skill to remember a meeting it was not given, say it cannot; it works from pasted text only.

## Failure modes

- **Calling a hedge a decision.** "I think we agreed" is a question to confirm, not a fact to broadcast
- **Burying the undecided.** The item discussed for twenty minutes with no outcome is the one most likely to return
- **Inventing owners to make the table look complete.** A blank that is visible is safer than a name that is wrong
- **Sanitising dissent.** Softening an objection into nothing loses the person who raised it
- **Summary dressed as a record.** If the output could be read without learning what was decided, it is a summary
- **Private content leaking.** Notes may include remarks not meant for the follow-up. Before drafting, check for personal or sensitive remarks and leave them out of the message; mention in the assumptions that you did

## Reference files

- `assets/decision-record.md` - the record, one per decision
- `assets/follow-up-message.md` - the message to send
