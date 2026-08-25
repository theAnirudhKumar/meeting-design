---
name: meeting-design
description: >
  Designs a meeting before it happens so it produces a decision rather than a discussion that has to be repeated. Trigger whenever the user says "plan this meeting", "build an agenda", "agenda for", "run a workshop", "facilitate", "offsite", "kickoff", "planning session", "how should I structure this meeting", "who should be in this meeting", "this meeting keeps going in circles", or names an upcoming meeting and asks what to do with it. Also trigger when they ask whether the meeting is needed at all, or when a recurring meeting has stopped producing anything. It names the decision, picks the decision rule out loud, sizes the room, sequences divergence before convergence, and plans for deadlock before it happens. Ships fill-in agenda templates rather than advice. Use a call-recap or meeting-notes skill for what happens after the meeting; this one is for before.
---

# Meeting Design

Most bad meetings were bad before anyone walked in. The agenda named topics rather than a decision, nobody said how the decision would be made, and the one person who could actually make it was not in the room.

The failure this exists to prevent: **a meeting that ends with "let's take this offline" and reconvenes three weeks later having lost the thread.** That is not a facilitation problem. It is a design problem, and it is fixed before the invite goes out.

---

## What this needs

**Minimum: what the meeting is about and roughly who is coming.** It will produce the agenda, the decision rule and the attendee cut from that, and mark what it had to assume.

**Better with** the decision you are actually trying to reach, the names and roles of attendees, and what happened last time if this is recurring.

**Best with** the pre-read or the document under discussion, so the agenda can be built around what people will have already seen.

---

## Step 0: Decide whether to hold it at all

Run this first. A meeting held out of habit costs more than the hour, because it teaches people that your meetings are optional.

**Do not hold a meeting when:**

- There is no decision and no disagreement. Send the document
- One person has all the information and everyone else is receiving it. Send the document
- The decision-maker cannot attend and the point was to reach them. Move it
- It is a status round-robin where each person speaks to the leader and nobody speaks to each other. Replace it with a written update
- The real blocker is that two people disagree and have not spoken. Set up that conversation instead

**Hold it when** there is genuine disagreement to resolve, a decision that needs several people's input in the same room, work that only happens when people are together, or a relationship that needs the time.

If you cancel, say what replaces it. A cancelled meeting with no substitute is a dropped thread.

---

## Step 1: Write the decision in one sentence

Before anything else, finish this sentence:

> **By the end of this meeting we will have decided \_\_\_\_\_\_\_\_.**

If you cannot finish it, you are not holding a decision meeting, and that is fine as long as you know it. There are three shapes and they are built differently:

| Shape | The sentence it finishes | What the agenda optimises for |
| :--- | :--- | :--- |
| **Decide** | "We will have decided X" | Getting to a call, with the rule named up front |
| **Generate** | "We will have produced X options worth evaluating" | Volume and range before any judgement |
| **Align** | "Everyone will be able to explain X in their own words" | Comprehension checked out loud, not assumed |

Mixing two shapes in one hour is the most common structural error. A generate block and a decide block need different rules, different energy and usually different rooms. If you must run both, put a visible break between them and say which one you are in.

See `references/meeting-shapes.md` for the full agenda skeleton for each.

---

## Step 2: Name the decision rule, out loud, in the invite

This is the highest-value step and almost nobody does it.

When the rule is unnamed, everyone assumes a different one. The person who assumed consensus feels steamrolled. The person who assumed the leader would decide thinks the discussion was theatre. Both are right, because no rule was ever agreed.

The five rules, in one line each:

| Rule | Who decides | Use when |
| :--- | :--- | :--- |
| **Directive** | The leader, and they say so before discussion | Speed matters more than buy-in, or it is genuinely their call |
| **Consult** | The leader, after hearing everyone | The default for most business decisions. Honest and fast |
| **Consent** | The group, unless someone has a reasoned objection | Reversible decisions where you want speed with a safety valve |
| **Consensus** | Everyone has to be able to live with it | Rare. Only where implementation depends on genuine buy-in |
| **Delegate** | One named person, with the group as input | The decision is one person's to own and you are giving them cover |

Say it in the invite, in one line: *"This is a consult decision. I will hear everyone and then decide by Friday."* People argue very differently when they know whether they are voting or advising.

Full selector logic and the failure mode of each rule is in `references/decision-rules.md`.

---

## Step 3: Cut the room

Two lists, not one:

- **Deciders.** Exactly one for the decision named in Step 1. If you have two, you have not named the decision precisely enough
- **Contributors.** People with information or a stake that changes the outcome. Each one should be answerable to "what would we get wrong without them"
- **Everyone else gets the notes.** Being informed is not a reason to attend

**The size rule.** Past roughly eight people, the meeting stops deciding and starts performing. Individuals go quiet, the confident ones fill the space, and the quiet ones write to you afterwards with the thing they did not say. If the list is longer than eight, either the meeting is an Align shape, or you are inviting people for political cover rather than for the decision.

**Optional attendance is a tell.** If someone is genuinely optional, they are informed, not a contributor. Mark them informed and let them read the notes.

---

## Step 4: Move the reading out of the discussion

"Did everyone get a chance to read it" is answered honestly by nobody.

Two mechanics fix most of this:

**Silent reading at the top.** Send the pre-read, then give the first ten minutes of the meeting to reading it in the room. People arrive unprepared for reasons that are usually real, and this removes the pretence without shaming anyone.

**Silent writing before discussion.** Before opening any question to the room, give two minutes for everyone to write their own answer. This is the cheapest anchoring fix that exists. Without it, whoever speaks first sets the frame and everyone after them argues inside it, including the people who arrived with a better frame.

The pre-read itself goes in `assets/pre-read-template.md`. Keep it to a page. A pre-read nobody finishes is worse than none, because you will build the agenda assuming they did.

---

## Step 5: Diverge before you converge

Generating options and judging options are different activities, and running them at once kills the first one. The moment someone evaluates, everyone else stops producing.

Sequence it explicitly:

1. **Frame the question** so it does not smuggle in an answer. "How do we make onboarding faster" already assumes speed is the problem
2. **Generate silently first**, then round-robin, then build on each other
3. **Only then evaluate**, against criteria you agreed before seeing the options

That last clause matters more than it looks. Criteria chosen after the options are on the table get chosen to fit whichever option the room already likes.

---

## Step 6: Box the time and say what gets cut

Put minutes against each agenda item, and decide in advance which item gets cut if you overrun. Making that call live, under time pressure, means the last item always loses regardless of whether it was the important one.

A rough default for a decision hour: ten minutes reading, ten framing and questions, twenty on the substance, ten to the decision, ten on owners and next steps.

Protect the decision block. It is the one that gets eaten, and it is the reason for the meeting.

---

## Step 7: Pre-mortem the deadlock

Answer this before the meeting: **what happens if we do not reach a decision?**

Three legitimate answers. Pick one and say it in the room:

- **A default takes effect.** "If we do not agree, we ship the current version." This is the strongest option because it makes delay a choice with a consequence
- **It escalates to a named person by a named date.** Not "we escalate", which happens to nobody
- **We reconvene with something specific that was missing.** Name the missing thing, and who is getting it

Without this, a deadlocked meeting produces a vague commitment to continue, and the decision quietly ages out.

---

## Step 8: Close in the room, not afterwards

The last five minutes, out loud, while everyone is still there:

- **The decision**, stated back, in one sentence
- **The owner**, a named person, not a team
- **The date**
- **Who gets told**, and by whom
- **Any open item**, with an owner and a date of its own

"Let's take it offline" is only acceptable with a name and a date attached. Without those it is the polite way to drop something.

---

## Output

A ready-to-send meeting design:

1. **The decision sentence** from Step 1, and the shape
2. **The decision rule**, phrased for the invite
3. **The attendee cut**, split into decider, contributors and informed, with anyone removed and why
4. **The agenda**, with minutes per item and the named cut item
5. **The pre-read**, or what it needs to contain
6. **The deadlock plan**
7. **The close checklist**
8. **What you had to assume**, stated plainly

Fill-in versions are in `assets/agenda-template.md`. Give the user the filled template, not a description of it.

---

## Failure modes

- **Topics instead of a decision.** An agenda of nouns produces a discussion. An agenda of questions produces answers
- **The unnamed rule.** Covered above, and it is the single most common cause of a meeting people leave unhappy with an outcome they agreed to
- **Inviting for cover.** People added so nobody can say they were not consulted. It doubles the room and halves the candour
- **Evaluating during generation.** The first critical comment ends the idea phase, whatever the agenda says
- **The recurring meeting nobody can cancel.** If it has no decision sentence and has not had one for a month, it is a status update wearing a calendar hold
- **The decision that was already made.** If the call is made and the meeting exists to socialise it, say that. Running it as a consult decision when it is directive is the fastest way to lose a room's trust
- **Running over into the decision block**, so the meeting ends with the discussion and not the call
- **No close.** Everyone leaves with a different memory of what was agreed, and the notes settle it a week later in whichever direction the note-taker remembered

---

## What good looks like

- Someone who missed it can read the notes and know what was decided and why
- The decision rule was stated before the discussion, not after the disagreement
- The quietest person in the room said something, because the format made room for it
- The options were generated before any of them were judged
- The meeting ended early because it was done, not because time ran out
- Nothing needs a follow-up meeting to decide the same thing again

---

## Reference files

- `references/decision-rules.md` - the five rules, how to pick one, and how each fails
- `references/meeting-shapes.md` - agenda skeletons for decide, generate and align, plus recurring formats
- `assets/agenda-template.md` - fill-in agenda
- `assets/pre-read-template.md` - fill-in pre-read
