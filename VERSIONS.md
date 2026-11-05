# Versions

What changed, and when.

## 2.0.0

**Covers the whole life of a meeting, not just the part before it.** Version 1 designed the meeting and stopped, and said outright that what came after belonged to someone else. That left the decision, the owner and the follow-up, which are the things people most often get wrong, outside the set. Two skills join `meeting-design`: `meeting-close` turns pasted notes into a decision record, a follow-up message and a list of what was discussed but never decided, and `meeting-audit` takes recurring meetings and returns a verdict on each, the hours freed and one message to send. Neither records or transcribes anything; both work from text you paste.

**Added a quick fix to `meeting-design`.** The usual way in is "here is my invite, fix it", and the old skill answered with an eight-step method. It now opens with a path that returns a verdict (cancel and replace with a doc, shrink, or keep and fix), a rewritten invite, the attendee cut and a meeting cost line. The method itself is tighter, with the long essay parts moved into references.

**Added meeting types.** `references/meeting-types.md` covers 1:1s, standups and status meetings, customer calls, retros, interviews, and board or exec reviews. The recurring-meeting advice that sat in `meeting-shapes.md` is now the `meeting-audit` skill, with the short version left behind for a meeting you chair yourself.

**Added meeting cost.** One honest formula: attendees x hours x an hourly rate you give. With no rate, a labelled placeholder. It counts time in the room only and says so.

**Added examples and evals.** Six worked cases with invented organisations, and one eval file per skill. The evals are written but not yet run against any model, and say so at the top of each file.

**Fixed version drift.** `plugin.json` said 1.0.1 while `marketplace.json` and this file said 1.1.0, and nothing noticed. `validate-skills.py` now fails if the three disagree, if a skill has no eval file, or if a relative link in a markdown file does not resolve.

## 1.1.0

**Added the contribution surface.** `validate-skills.py`, a GitHub Actions workflow running it on every pull request, `CONTRIBUTING.md`, issue and pull request templates, and a gitignore. The structural rules were previously enforced only by a hook on the maintainer's own machine, so anyone arriving by fork had nothing to run.

**Fixed two structural defects.** `marketplace.json` declared the plugin but no `skills` array, so nothing connected the plugin entry to the skill on disk. The README mentioned the skill folder twice in prose but never linked it, so a reader had nothing to click.

**Fixed a stale link.** The Elsewhere section pointed at `theAnirudhKumar/skills`, which is now `work-design`. GitHub's redirect meant the link kept working and nothing ever failed, which is exactly how that kind of drift survives.

## 1.0.1

Plugin manifest added for community marketplace submission.

## 1.0.0

First release. `meeting-design`: names the decision, states the decision rule, cuts the room, sequences divergence before convergence, and plans for deadlock in advance. Ships fill-in agenda and pre-read templates.
