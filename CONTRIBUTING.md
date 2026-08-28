# Contributing

The most useful thing you can send is not a new skill. It is a meeting this got wrong.

This was written from a particular vantage point: someone who chairs things without the word facilitator in their job title. If the decision rules do not map to how your organisation actually decides, or the agenda shapes break down in a room you sit in every week, that is a defect and worth an issue.

---

## The three things worth contributing

**1. Something here is wrong.** Open an issue saying what happens in reality and what the skill assumed instead. Specific beats general. "The decision rules are off" is hard to act on. "Consent decision-making does not work in a regulated environment where one person is legally accountable for the call, and the skill offers it anyway" is a fix.

**2. A meeting shape is missing.** The skill covers decide, generate and align. If you run one that fits none of those, describe the shape, how often it recurs, and what a good agenda for it looks like.

**3. You have written something.** Open a pull request. Read the rest of this first.

---

## The two rules

**Nothing may be a prerequisite.** A skill that fails because you lack a connector, a file or a terminal gets uninstalled. This one states the least it can run on, which is what the meeting is about and roughly who is coming, then says what each extra input would add.

**Every skill names the failure it exists to prevent.** One sentence, near the top. Here it is the meeting that ends with "let's take this offline" and reconvenes three weeks later having lost the thread.

---

## Writing or editing a skill

### Structure

```
skills/<skill-name>/
  SKILL.md              the method
  references/           detail the method points at, one level deep only
  assets/               templates the skill fills in and hands over
```

### SKILL.md

- **Under 500 lines.** Detail moves into `references/`
- **Frontmatter carries `name` and `description`.** The `name` matches the folder exactly, and so does the H1
- **The description goes under 1,024 characters and leads with literal trigger phrases.** Assistants truncate the tail of a description when the listing grows, so the words someone would actually type go first and the explanation goes last
- **References are one level deep.** A reference pointing at another reference gets partially read
- **Third person throughout.** "The user", not "you", and never a named person

### Ship an asset, not just advice

The difference between a skill people install and one they do not is whether it hands something over. This one ships a fill-in agenda and a pre-read template, because advice does not survive contact with a calendar invite.

### Name the mechanism

Say why something is true, not that it is. "When the decision rule is unnamed, everyone assumes a different one, so the person who assumed consensus feels steamrolled and the person who assumed the leader would decide thinks the discussion was theatre" is useful. "Agree how you will decide" is not.

---

## House style

- **No em dashes.** A comma, a colon, a spaced hyphen or a full stop
- **Name your sources.** This skill draws on Amazon's narrative memo practice, sociocracy's consent decision-making, the Double Diamond and Klein's pre-mortem, and says so. Anything added should be able to say where it comes from
- **No real customer, employer or personal names**, in worked examples too. Where an example needs an organisation, invent one and make it obviously invented
- **No statistics you cannot source.** A great deal of circulated meeting research traces back to vendor marketing with no study behind it. Build on mechanisms rather than numbers

---

## Before you open a pull request

Run the validator. It catches everything structural, so review can be about judgement instead.

```
python3 validate-skills.py
```

Then check what a script cannot see:

- [ ] The skill states the least it needs to run, and nothing is a prerequisite
- [ ] The failure it prevents is named
- [ ] It ships an asset, or there is a reason it does not
- [ ] Any worked example uses an invented organisation
- [ ] Claims about how meetings work name where they come from
- [ ] No real customer, employer or personal names anywhere
- [ ] The README is updated if this adds or removes a skill

---

## What happens next

Pull requests get read as a diff before merging, because that is where a stray name or a broken claim actually shows up. Expect questions on anything stating a fact about how meetings work without saying where that came from. That standard applies to the maintainer as much as to anyone else.
