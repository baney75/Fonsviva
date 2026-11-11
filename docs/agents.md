# For agents: quickstart

You are an AI agent setting up Fonsviva for a person. Follow these rules and pages in order. Don't guess.

> **Status: planned, not released.** Fonsviva has no release yet, so there is nothing to install today. These steps are the target behavior. Each one becomes true only when its test in [TESTING.md](https://github.com/baney75/Fonsviva/blob/main/TESTING.md) passes, and [SUPPORTED.md](https://github.com/baney75/Fonsviva/blob/main/SUPPORTED.md) is the source of truth for what works now. An agent must check SUPPORTED.md first and tell the person plainly if a step isn't supported yet.

## Rules

- Read [SUPPORTED.md](https://github.com/baney75/Fonsviva/blob/main/SUPPORTED.md) first. Only do steps listed as supported. Otherwise tell the person it's not available yet.
- Ask the person before installing anything, before turning on any cloud provider, and before any step that costs money.
- Never print, log or paste API keys. Fonsviva stores provider keys; the person enters them.
- Never enable cloud for UntoCaesar client or volunteer work or for UniCerebrum. Fonsviva blocks it; don't try to work around the block.
- Run every **Check** and compare with the expected output before moving on. Stop and report if a check fails.

## Steps

1. [Install](https://baney75.github.io/Fonsviva/setup/install)
2. [Connect apps and agents](https://baney75.github.io/Fonsviva/setup/connect-fonsviva)
3. [Select models](https://baney75.github.io/Fonsviva/setup/select-models)
4. [Add a cloud provider](https://baney75.github.io/Fonsviva/setup/add-cloud-provider)
5. [Troubleshoot](https://baney75.github.io/Fonsviva/setup/troubleshoot)

## Shared facts (the same in every repo)

- Fonsviva is the shared local compute layer. Install it once; every app uses it. Repo: [https://github.com/baney75/Fonsviva](https://github.com/baney75/Fonsviva). Docs: [https://baney75.github.io/Fonsviva/](https://baney75.github.io/Fonsviva/).
- Fonsviva runs on its own as a command-line tool (`fonsviva`) plus a web app. Planned default address: `http://127.0.0.1:7341` (web app), `http://127.0.0.1:7341/v1` (OpenAI-compatible API), `http://127.0.0.1:7341` origin (Anthropic-compatible API).
- Users pick models inside each app. Fonsviva downloads, stores and serves them.
- Cloud providers (RunPod and the others in [providers](https://baney75.github.io/Fonsviva/providers)) are added, turned on and off, and linked **only in Fonsviva**. Personal use only. UntoCaesar client or volunteer returns and all UniCerebrum work are hard-blocked from cloud. See [cloud rules](https://baney75.github.io/Fonsviva/CLOUD).
- Apps never store provider keys or call a cloud provider. They show where each job ran.

## Machine-readable index

[llms.txt](https://baney75.github.io/Fonsviva/llms.txt)
