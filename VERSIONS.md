# Versions

What changed, and when.

## 1.1.0

**Added the contribution surface.** `validate-skills.py`, a GitHub Actions workflow running it on every pull request, `CONTRIBUTING.md`, issue and pull request templates, and a gitignore. The structural rules were previously enforced only by a hook on the maintainer's own machine, so anyone arriving by fork had nothing to run.

**Fixed two structural defects.** `marketplace.json` declared the plugin but no `skills` array, so nothing connected the plugin entry to the skill on disk. The README mentioned the skill folder twice in prose but never linked it, so a reader had nothing to click.

**Fixed a stale link.** The Elsewhere section pointed at `theAnirudhKumar/skills`, which is now `work-design`. GitHub's redirect meant the link kept working and nothing ever failed, which is exactly how that kind of drift survives.

## 1.0.1

Plugin manifest added for community marketplace submission.

## 1.0.0

First release. `meeting-design`: names the decision, states the decision rule, cuts the room, sequences divergence before convergence, and plans for deadlock in advance. Ships fill-in agenda and pre-read templates.
