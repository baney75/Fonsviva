# Skills

Skills are the instructions that make agents build Fonsviva and help users run it well. They must be standardized and powerfully good: a weak or vague skill is a bug.

## Two sets

- `skills/maintainer/`: skills for agents that build and maintain Fonsviva itself (adding engine support, harness compatibility, running releases, updating benchmarks).
- `skills/runtime/`: skills the assistant inside Fonsviva uses while helping a user (picking a model for their hardware, fixing a broken connection, explaining a job that failed).

## Originality

Every skill here is original work written for Fonsviva. We study strong skills we already have or find, learn what makes them good, and then write our own. We don't copy them in. Credit sources that taught us something in the skill's Sources section.

## The standard

Every skill is a folder with a `SKILL.md`. Copy `_template/` in the right set to start one. Each `SKILL.md` has:

1. **Frontmatter:** `name` (kebab-case, same as the folder) and `description` (one line saying exactly when to use it).
2. **Goal:** what a finished, correct result looks like.
3. **Inputs:** what the skill needs before it starts.
4. **Steps:** the exact procedure, in order.
5. **Rules and checks:** hard constraints and how to verify the output before returning it.
6. **Sources:** references the skill relies on, with links.

## Every skill is tested

A skill is not merged without tests in `tests/skills/<skill-name>/` showing it produces correct results on real cases, and a benchmark run showing which models can follow it (see `BENCHMARKS.md`). If a model needs different wording to follow a skill, that goes in `models/<model>/`, not in a fork of the skill.
