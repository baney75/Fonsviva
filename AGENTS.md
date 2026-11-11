# AGENTS.md

Instructions for AI coding agents (Claude Code, Codex, Cursor and others) working in Fonsviva.

## What this project is

The shared local compute and model-serving layer for UntoCaesar, Gantrel and UniCerebrum. It discovers and manages local models, downloads new ones matched to the hardware, runs a job queue, pools privately shared compute nodes, and serves everything through OpenAI- and Anthropic-compatible APIs. It is built on Sybil Solutions' Local Studio and Local AI registry; see `docs/ARCHITECTURE.md`.

## Ground rules

- **Build on, don't rebuild.** Use Local Studio, the Local AI registry, harness-bridge and the engines (vLLM, SGLang, llama.cpp) as they are. Contribute fixes upstream where they belong. Only build what Fonsviva adds.
- **Local first.** Every feature works on the user's own hardware with no cloud account.
- **Cloud is personal use only.** Cloud providers (RunPod and others) are off by default, available only on a personal profile, and hard-blocked for UntoCaesar client or volunteer work and for UniCerebrum institutional data. Fonsviva is the only place cloud providers, their keys and costs live; the apps never call a provider directly. Follow `docs/CLOUD.md` exactly. Never weaken this block, and never add a setting that bypasses it.
- **Private and secure by default.** API keys are scoped per app and stored encrypted. Never log, print or send secrets, prompts or outputs.
- **Don't break the apps that depend on it.** API changes stay backward compatible. A breaking change needs a new version path and a migration plan.
- **Easy beats clever.** Every screen has to make sense to a non-technical person.
- **Design comes from DESIGN.md.** Follow it for all UI work. If it is empty or silent on something, ask the designer rather than inventing a style.
- **Prove it works.** Back every change with behavior tests or a recorded real run. Don't claim something works without evidence.
- **Small, reviewable changes.** One concern per pull request, with a clear description.

## Skills

Skills live in `skills/maintainer/` (for building this project) and `skills/runtime/` (used by agents inside the app). All are original and tested; see `skills/README.md`. Load the skill that matches your task before starting, and improve it when you learn something.

## Testing and honesty

Never claim the software can do something without a passing test. Follow `TESTING.md`, keep `SUPPORTED.md` honest, and benchmark models per `BENCHMARKS.md`. Model-specific instructions live in `models/<model>/`.

## Releases

Fonsviva ships on two channels, Stable and Dev (no nightly). See `RELEASES.md`. Never push directly to `stable`.

## Repository layout

- `AGENTS.md`: this file
- `CLAUDE.md`: Claude Code entry point, points here
- `DESIGN.md`: design system and UX rules, owned by the designer
- `RELEASES.md`: Stable and Dev channels
- `CONTRIBUTING.md`: how to contribute, including design work and coauthorship
- `TESTING.md`, `SUPPORTED.md`, `BENCHMARKS.md`: behavior tests, honest scope and model benchmarks
- `docs/ARCHITECTURE.md`: what Fonsviva builds on and what it adds
- `docs/MODELS.md`: the model manager
- `docs/CONNECT.md`: connecting agents and apps
- `docs/CLOUD.md`: cloud providers, personal use only
- `skills/maintainer/`, `skills/runtime/`: original, tested skills
- `models/`: per-model instructions
- `tests/`, `benchmarks/results/`: tests and published results
- `design/`: design exports and notes
