---
name: meeting-design
description: >
  Fixes or designs a meeting before it happens. Trigger on "fix this invite", "here is my agenda, tighten it", "review this meeting invite", "build an agenda", "plan this meeting", "who should be in this meeting", "is this meeting necessary", "run a workshop", "kickoff", "offsite", "prep my 1:1 / retro / board review / customer call / interview loop", "this meeting keeps going in circles", or when an invite, agenda or calendar description is pasted. Gives a verdict (cancel and replace with a doc, shrink, or keep and fix), a rewritten invite ready to paste, the attendee cut and the meeting cost. Names the decision, the decision rule and the deadlock plan. Not for writing up a meeting that already happened (meeting-close), a whole list of recurring meetings (meeting-audit), or choosing between email and a meeting for one message.
---

# Meeting Design

Most bad meetings were bad before anyone walked in. The invite named a topic rather than a decision, nobody said how the decision would be made, and the one person who could make it was not in the room.

The failure this exists to prevent: **a meeting that ends with "let's take this offline" and reconvenes three weeks later having lost the thread.** That is a design problem, and it is fixed before the invite goes out.

This is the "before" skill. If `meeting-close` and `meeting-audit` are installed they cover after the meeting and a pile of recurring meetings. Nothing here depends on them.

---

## What this needs

**Minimum: the invite, or two sentences on what the meeting is about and roughly who is coming.** Paste the title, description, length and attendee list as they are. The skill works from that and marks what it had to assume.

**Better with** the decision actually wanted, attendee roles, and what happened last time if it recurs.

**Best with** the pre-read or document under discussion.

Never block on missing detail. Run with assumptions, list them at the end, and ask at most three questions there.

---

## Quick fix: when the user pastes an invite, agenda or calendar entry

Do this whenever the input is an existing invite or agenda, or the user says "fix this". Go to Full design only when the user is planning from scratch.

1. **Extract the facts.** Title, length, recurrence, attendee count and roles, description. Count the names if no count is given. Anything missing becomes an assumption, never a guess presented as fact.
2. **Pick the verdict.** Take the first that applies:
   - **Cancel and replace with a doc.** There is no decision and no disagreement, or one person is informing everyone else. Name the replacement: a one-page doc, a comment thread with a deadline, or a short message.
   - **Shrink.** A real decision or disagreement exists, but the room or the length is bigger than the decision needs. Say the new length and the new attendee list.
   - **Keep and fix.** The size is right and the design is wrong: no decision sentence, no rule, no close. Fix those.
3. **Give the cost line.** See Meeting cost below.
4. **Rewrite the invite** from `assets/invite-template.md`. The title becomes the decision. Put the decision sentence, the decision rule, the pre-read, timed agenda items, the deadlock default and the close in it. Leave a `[bracket]` for any fact the user did not supply. Never fill a bracket with a plausible guess.
5. **Cut the room.** Name the decider, the contributors, and who moves to "informed, gets the notes". Give one clause of reasoning each: what would be got wrong without this person.
6. **If the meeting matches a type** (1:1, standup or status, customer call, retro, interview, board or exec review), read `references/meeting-types.md` and apply its playbook before writing the invite.

Answer in this order, with nothing before the verdict:

1. **Verdict**, one line, and the reason in one sentence
2. **Cost**, one line
3. **Rewritten invite**, in a code block ready to paste
4. **Attendee cut**
5. **What I assumed**, and up to three questions

If the verdict is "cancel and replace", the rewritten invite is the replacement message or doc outline, not a calendar invite.

---

## Meeting cost

Cost = attendees x hours x an hourly rate. Use the rate the user gives. If none, ask once; if still none, show the formula with a placeholder rate and label it: *"Assumption: 60 per hour per person. Replace it with your own."* Never present a placeholder as a measured figure.

Say it as one line: *"11 people x 1 hour x 60 = 660 per meeting, about 2,860 a month at weekly."* Only time in the room is counted, so it is a floor: preparation and the cost of being interrupted are excluded. Do not quote benchmarks about what meetings cost in general.

---

## Full design: when planning from scratch

### 1. Decide whether to hold it

Do not hold it when there is no decision and no disagreement, one person holds all the information and everyone else receives it, the decision-maker cannot attend, it is a status round-robin where each person talks to the leader only, or two people disagree and have not spoken (set up that conversation instead). Hold it for genuine disagreement, a decision needing several people's input at once, or work that only happens together. If cancelling, say what replaces it.

### 2. Write the decision in one sentence

> **By the end of this meeting we will have decided ______.**

If it cannot be finished, name the shape instead. Mixing shapes in one hour is the commonest structural error.

| Shape | The sentence it finishes | The agenda optimises for |
| :--- | :--- | :--- |
| **Decide** | "We will have decided X" | A call, with the rule named up front |
| **Generate** | "We will have produced X options worth evaluating" | Range before any judgement |
| **Align** | "Everyone can explain X in their own words" | Comprehension checked out loud |

Skeletons for each are in `references/meeting-shapes.md`.

### 3. Name the decision rule in the invite

When the rule is unnamed, everyone assumes a different one. The person who assumed consensus feels steamrolled, and the person who assumed the leader would decide thinks the discussion was theatre.

Pick one of Directive, Consult, Consent, Consensus or Delegate using the selector in `references/decision-rules.md`, and write it as one line: *"This is a consult decision. I will hear everyone and decide by Friday."* State it before discussion, never after a disagreement starts. Say what happens to dissent: it is recorded and the group moves anyway.

### 4. Cut the room

- **Decider:** exactly one. Two means the decision is not precise enough yet.
- **Contributors:** each must answer "what would we get wrong without them".
- **Informed:** gets the notes. Optional attendance is a tell that someone is informed, not a contributor.

Past roughly eight, a meeting performs more than it decides: confident people fill the space and quiet people write to the chair afterwards. If the list is longer, the meeting is an Align shape or people are being invited for cover.

### 5. Move reading and writing out of the discussion

Send the pre-read (`assets/pre-read-template.md`, one page), then spend the first ten minutes reading it in the room. This is Amazon's silent-read practice, and it removes the pretence that everyone prepared. Before opening a question, give two minutes for everyone to write an answer, so the first speaker does not set the frame for the rest.

### 6. Diverge before converging

Frame the question without smuggling in an answer, generate silently, then evaluate against criteria agreed before the options appeared. Criteria chosen afterwards get chosen to fit the option the room already likes.

### 7. Box the time and name the cut item

Put minutes against every item and decide now which item is cut on overrun. Deciding live means the last item always loses, even when it was the one that mattered. Protect the decision block.

### 8. Plan the deadlock

Answer "what if we do not decide?" in the invite. Pick one: a **default takes effect** (strongest, because delay now has a consequence), it **escalates to a named person by a named date**, or the group **reconvenes with a specific missing thing** and a named person fetching it.

### 9. Close in the room

Last five minutes, out loud: the decision in one sentence, the owner (a person, not a team), the date, who tells whom, and any open item with its own owner and date. "Offline" is only acceptable with a name and a date.

---

## Output for a full design

1. The decision sentence and shape
2. The decision rule, phrased for the invite
3. The attendee cut: decider, contributors, informed, and who was removed and why
4. The agenda with minutes and the named cut item, using `assets/agenda-template.md`
5. The pre-read, or what it must contain
6. The deadlock plan and the close checklist
7. The cost line
8. What was assumed

Hand over the filled template, not a description of it.

---

## Failure modes

- **Topics instead of a decision.** Nouns produce a discussion, questions produce answers
- **The unnamed rule.** The commonest reason people leave unhappy with an outcome they agreed to
- **A directive run as a consult.** If the call is made and the meeting exists to explain it, say so. Staging a consultation that is not real costs the room's trust
- **Inviting for cover.** It doubles the room and halves the candour
- **Evaluating during generation.** The first critical comment ends the idea phase
- **Rewriting the invite and inventing the facts.** Placeholders stay in brackets until the user fills them
- **Cutting the customer's people.** In a meeting with an outside party, cut only your own side and say so
- **No close.** Everyone leaves with a different memory of what was agreed

---

## Reference files

- `references/decision-rules.md` - the five rules, the selector, how each fails
- `references/meeting-shapes.md` - agenda skeletons for decide, generate, align, workshops and a recurring meeting you chair
- `references/meeting-types.md` - playbooks for 1:1s, standups and status, customer calls, retros, interviews, board and exec reviews
- `assets/invite-template.md` - the paste-ready invite used by the quick fix
- `assets/agenda-template.md` - fill-in agenda
- `assets/pre-read-template.md` - fill-in pre-read
