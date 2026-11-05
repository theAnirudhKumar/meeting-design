# meeting-design

**Paste in an invite, a set of notes or your recurring calendar. Get back a verdict, a rewritten invite or a decision record you can send.**

Three skills for Claude that cover the whole life of a meeting: [design it before](skills/meeting-design), [close it after](skills/meeting-close), [audit the ones that repeat](skills/meeting-audit). Nothing to set up. They work on text you paste into a chat.

## Before and after

You paste this:

```
Weekly Product Sync
Fridays 10:00-11:00, recurring. 11 attendees.
Weekly sync to go over updates from each team and discuss blockers. Please come prepared to share.
```

You get this back (from [the full example](examples/weekly-status-meeting.md)):

```
Verdict: Shrink. Eleven people take turns reporting to one lead. Updates move
to writing; the call keeps only what is stuck.

Cost: 11 people x 1 hour x 60 = 660 per meeting, about 2,860 a month at weekly.
(Assumption: 60 per hour per person. Replace it with your own.)

Title: Product blockers: who is stuck and what unblocks them
Length: 25 min   Chair: Maya
Decision: By the end every blocked item has an owner and a next step.
How we decide: Delegate. The person who can unblock an item owns it.
If we do not decide: Maya assigns it by end of Monday.
Read first: the status thread. Add your update by Thursday 5pm.
Who: five leads stay. The other six read the thread and join when named.
```

The people, the company and the numbers in that example are invented. [More examples](examples/) cover a 14-person kickoff, a customer review, messy notes after a call and a recurring calendar.

---

## Say this, get that

| Say this | Skill | You get |
| :--- | :--- | :--- |
| "Fix this invite" with the invite pasted. "Build an agenda for X." "Who should be in this meeting?" "Prep my 1:1 / retro / board review / customer call." | [`meeting-design`](skills/meeting-design) | A verdict (cancel and replace with a doc, shrink, or keep and fix), a rewritten invite ready to paste, the attendee cut, the meeting cost |
| "Here are my notes, what did we actually decide?" "Draft the follow-up." "Who owns what from this?" | [`meeting-close`](skills/meeting-close) | A decision record, a follow-up message ready to send, and a list of what was discussed but never decided |
| "Audit my recurring meetings." "Which of these can I cancel?" "What do our standing meetings cost?" | [`meeting-audit`](skills/meeting-audit) | A verdict per meeting, hours a month freed, the cost, a sunset date, and the one message to send |

Many AI meeting tools work after the meeting and summarise it. These three work on the parts a summary cannot fix: the design before it, and the decision and follow-up after it.

---

## Install

**In Claude Code or Cowork, one line (Claude Code 2.1.275 or later):**

```
/plugin install meeting-design --marketplace theAnirudhKumar/meeting-design
```

**On an older version, two lines:**

```
/plugin marketplace add theAnirudhKumar/meeting-design
/plugin install meeting-design@meeting-design-marketplace
```

**Or paste this to an AI tool that can read and write files on your computer:**

```
Install the skills from https://github.com/theAnirudhKumar/meeting-design:
copy every folder in its skills/ directory into ~/.claude/skills/ and tell
me where they landed.
```

**Or in the Claude app, no terminal:** download this repository as a ZIP, zip each folder inside `skills/` on its own, then go to Customize, Skills, Create skill, Upload skill and upload each ZIP. You can install just one.

**Or just read it.** Each skill is plain markdown. The templates in each `assets/` folder can be copied into a calendar invite without Claude involved at all.

---

## What it does not do

- It does not record, join or transcribe meetings. `meeting-close` works on notes or a transcript you paste.
- It does not read your calendar unless you have a calendar connector installed and ask it to. Without one, you paste the list.
- It does not send, cancel or schedule anything. It drafts; you send.
- It is not a meeting summariser. If you want a faithful summary of what was said, use a call-recap or notes tool. These skills answer a different question: what was decided, by whom, by when, and over whose objection.

Nothing here needs a terminal, a workspace, a connector or an API key.

---

## Who this is for

People who chair things without the word "facilitator" in their job title. Ops leads, account managers, project managers, HR partners, agency leads, founders, anyone who called a meeting this week and is not sure it needed to happen, or sat in one that did not.

---

## What each skill does

**[`meeting-design`](skills/meeting-design)** has two paths. Paste an invite and it takes the quick fix: verdict, cost, rewritten invite, attendee cut. Plan from scratch and it runs the full method: the decision in one sentence, the decision rule, who is in the room, silent reading, divergence before convergence, the time box, the deadlock plan, the close. It carries playbooks for 1:1s, standups and status meetings, customer calls, retros, interviews, and board or exec reviews.

**[`meeting-close`](skills/meeting-close)** sorts pasted notes into decided, action, discussed but not decided, and dissent. A hedged "I think we agreed" is marked as needing confirmation, not passed off as a decision. Missing owners and dates are flagged in capitals instead of filled with plausible names.

**[`meeting-audit`](skills/meeting-audit)** takes a list of recurring meetings and does the arithmetic: person-hours a month, cost, hours freed by each verdict. It will say Keep when Keep is the answer.

**Meeting cost.** All three use one formula: attendees x hours x an hourly rate you give. If you give none, it shows the formula with a placeholder rate labelled as an assumption. It counts time in the room only, so it is a floor. It does not quote benchmarks.

---

## Where this comes from

The method is assembled from practice that is already well established, and it is worth naming rather than presenting as original:

- **Silent reading at the top of the meeting** is Amazon's narrative memo practice, replacing presentations with a document everyone reads in the room
- **Consent as distinct from consensus**, where the test is a reasoned objection rather than a preference, comes from sociocracy
- **Divergence before convergence** is the core of the Double Diamond, from the British Design Council
- **The pre-mortem**, imagining the failure before it happens, is Gary Klein's, published in Harvard Business Review in 2007
- **Recording the dissent and moving anyway** is Amazon's "disagree and commit"
- **The 1:1 as the report's meeting, not the manager's,** is Andy Grove's, in *High Output Management*
- **The five-phase retro** (set the stage, gather data, generate insights, decide what to do, close) is from Esther Derby and Diana Larsen's *Agile Retrospectives*, building on Norm Kerth's *Project Retrospectives*
- **The decision record** is a relative of the architecture decision record Michael Nygard described in 2011

What these skills add is the sequencing, the quick-fix path from a pasted invite, the close, the audit and the templates, not the ideas.

---

## The two rules behind everything published here

**Nothing may be a prerequisite.** A skill that errors because you lack a file, a connector or a workspace gets uninstalled. Each skill here states the least you can give it and still get something useful.

**Every skill names the failure it exists to prevent.** If it cannot say what goes wrong without it, it is a template rather than a skill.

- `meeting-design` prevents the meeting that ends in "let's take this offline" and reconvenes three weeks later having lost the thread
- `meeting-close` prevents everyone leaving with a different memory of what was agreed
- `meeting-audit` prevents a calendar of standing meetings that each made sense once, with nobody able to say which still earn their hours

---

## Data and privacy

These skills are plain markdown instructions. They contain no code, make no network calls, collect nothing and have no telemetry. They work on text you paste into a chat and see only that, plus whatever your AI tool already has in context. `meeting-audit` can use a calendar connector if your tool has one and you allow it, read-only, but it works fine from pasted text. Nothing is written, sent or saved unless you approve it. Anything you paste is handled by your AI tool under that tool's own terms.

## Contribute

If you run meetings for a living and something here is wrong, that is the most useful thing you can tell me. Open an issue with what happens in reality and what the skill assumed instead.

The evals in [`evals/`](evals) were run once on Haiku, Sonnet and Opus, with one sample per case, and each file records the results and a reading of every miss. A rerun after any change to a skill description is a welcome contribution.

[CONTRIBUTING.md](CONTRIBUTING.md) has the standard this repository holds itself to. Before opening a pull request, run `python3 validate-skills.py`. The same script runs on every pull request.

---

## Elsewhere

- **[Hustlyst](https://hustlyst.com?ref=github)** - AI and automation tools for people who don't code
- **[CS Pulse](https://cspulse.com?ref=github)** - community and newsletter for customer success practitioners
- **[work-design](https://github.com/theAnirudhKumar/work-design)** - the rest of the set: vetting a tool before you sign up, carrying context between sessions, catching an expensive request, and choosing a meeting or a message before you book one

MIT licensed. Fork it, change it, ship it.
