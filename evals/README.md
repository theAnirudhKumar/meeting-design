# Evaluations

One file per skill. Each records which prompts should make the skill fire, which near misses should not, and which cases two skills could both claim. The format follows [work-design's evals](https://github.com/theAnirudhKumar/work-design/tree/main/evals).

A skill that never fires is indistinguishable from a skill that was never written. `validate-skills.py` checks structure and a person reads the diff for judgement. Neither can tell you whether a description does its one job, which is what these cases are for.

**Current status: none of these have been run.** The cases and the expected routing are written. No model has been put to them, so every results column says "not yet run". When a run happens, record the date, the models, the exact description text (the git commit is enough) and every disagreement, including the ones that look bad.

| File | Skill | Cases |
| :--- | :--- | :--- |
| [meeting-design.md](meeting-design.md) | before the meeting | 8 should fire, 6 should not, 3 conflicts |
| [meeting-close.md](meeting-close.md) | after the meeting | 6 should fire, 6 should not, 2 conflicts |
| [meeting-audit.md](meeting-audit.md) | recurring meetings | 6 should fire, 5 should not, 2 conflicts |

---

## How to run a pass

1. Collect the `description` field of every skill in this repository, verbatim, and the descriptions named at the top of the skill's eval file from other repositories.
2. Give a model those descriptions and nothing else. Routing happens on the description alone, because the body is not loaded until the skill is chosen.
3. Put each case to it and ask for one skill name or `none`, with a confidence and a one-line reason.
4. Repeat on Haiku, Sonnet and Opus. What works for a larger model can need more detail for a smaller one.
5. Record the results in the skill's file, including disagreements.

## What a pass looks like

- **Should fire:** all three models pick the skill. Two out of three is a finding, not a pass.
- **Should not fire:** no model picks the skill. Which skill they pick instead matters only if it is also wrong.
- **Conflict:** no pass or fail. Record what each model did and decide in writing whether the split is acceptable.
- **Output check:** the skill produces the artefact it promises, filled in, not advice. Checked by hand on one case per skill.

## What these cannot tell you

- **Whether the description survives a real installation.** Listings are truncated to a character budget, and a newly installed skill loses its text first.
- **Whether anything fires in the wild.** Every case is a constructed message written by the skill's author.
- **Anything stable across rewordings.** A result holds for one wording of the descriptions.

## When to rerun

When any description changes, a skill is added or removed, or a model is added. Routing is competitive: a change to one skill can move a case belonging to another.
