# meeting-design

**Design the meeting before you run it.**

Most bad meetings were bad before anyone walked in. The agenda named topics rather than a decision, nobody said how the decision would get made, and the one person who could actually make it was not in the room.

This is a skill for Claude that fixes that at the design stage. You describe the meeting, it gives you back a ready-to-send agenda with the decision named, the decision rule stated, the attendee list cut, and a plan for what happens if the room deadlocks.

It ships fill-in templates rather than advice, because advice does not survive contact with a calendar invite.

---

## What it actually does

| Step | What you get |
| :--- | :--- |
| Should this be a meeting | A straight answer, and what replaces it if not |
| The decision sentence | One line you can finish, or the honest admission that this is not a decision meeting |
| The decision rule | Directive, consult, consent, consensus or delegate, phrased for the invite |
| The room | Deciders, contributors, and everyone you can safely leave off |
| The agenda | Minutes per item, and which item gets cut if you overrun |
| The deadlock plan | What happens if you do not decide, agreed before you need it |
| The close | Decision, owner, date, who gets told, filled in while people are still in the room |

---

## Who this is for

People who chair things without the word "facilitator" anywhere in their job title. Ops leads, account managers, project managers, HR partners, agency leads, founders, community organisers, anyone who called a meeting this week and is not sure it needed to happen.

You do not need to be technical. Nothing here needs a terminal, a workspace, a connector or an API key. It works from what you type into a chat window.

---

## Install

**In the Claude app (no terminal needed)**

1. Download this repository as a ZIP, or clone it
2. Zip the `skills/meeting-design` folder on its own
3. In Claude, go to Customize, then Skills, then Create skill, then Upload skill
4. Upload the ZIP

**As a plugin, in Claude Code or Cowork**

```
/plugin marketplace add theAnirudhKumar/meeting-design
/plugin install meeting-design@meeting-design-marketplace
```

**Or just read it.** The skill is plain markdown. `skills/meeting-design/SKILL.md` is the method, and the two files in `assets/` are templates you can copy into a calendar invite without Claude involved at all.

---

## Where this comes from

The method is assembled from practice that is already well established, and it is worth naming rather than presenting as original:

- **Silent reading at the top of the meeting** is Amazon's narrative memo practice, replacing presentations with a document everyone reads in the room
- **Consent as distinct from consensus**, where the test is a reasoned objection rather than a preference, comes from sociocracy
- **Divergence before convergence** is the core of the Double Diamond, from the British Design Council
- **The pre-mortem**, imagining the failure before it happens, is Gary Klein's, published in Harvard Business Review in 2007
- **Recording the dissent and moving anyway** is Amazon's "disagree and commit"

What this skill adds is the sequencing and the templates, not the ideas.

---

## The two rules behind everything published here

**Nothing may be a prerequisite.** A skill that errors because you lack a file, a connector or a workspace gets uninstalled. This one states the least you can give it and still get something useful.

**Every skill names the failure it exists to prevent.** If it cannot say what goes wrong without it, it is a template rather than a skill. This one prevents the meeting that ends in "let's take this offline" and reconvenes three weeks later having lost the thread.

---

## Contribute

If you run meetings for a living and something here is wrong, that is the most useful thing you can tell me. Open an issue with what happens in reality and what the skill assumed instead.

---

## Elsewhere

- **[Hustlyst](https://hustlyst.com?ref=github)** - twice a week on AI and automation tools for people who don't code
- **[CS Pulse](https://cspulse.com?ref=github)** - community and newsletter for customer success practitioners
- **[More skills](https://github.com/theAnirudhKumar/skills)** - the general-purpose ones

MIT licensed. Fork it, change it, ship it.
