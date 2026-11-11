# Fonsviva

Fonsviva is an open-source, local compute and model-serving layer. It runs AI models on hardware you own, lets you see and manage every model already on your machines, and serves them to apps and coding agents through one private API. [UntoCaesar](https://github.com/baney75/UntoCaesar), [Gantrel](https://github.com/baney75/Gantrel) and [UniCerebrum](https://github.com/baney75/UniCerebrum) run on it.

The name is Latin for "living fountain," from Jeremiah 2:13: "they have forsaken me, the fountain of living waters, and hewed them out cisterns, broken cisterns, that can hold no water."

## What it does

- **Manage the models you already have.** One list of every model on your devices, from Ollama, LM Studio, llama.cpp, vLLM, SGLang and the Hugging Face cache, with size, quantization, measured speed and which apps use each one. Update, remove or pin any model in one click.
- **Get local models easily.** Browse Hugging Face and tested registry recipes, filtered to what fits your hardware. Each model shows whether it passed the registry's gates on hardware like yours before you download it.
- **Keep working while you're away.** A job queue runs long work in the background and survives restarts.
- **Share compute privately.** Compute nodes ("Sparks") let a family, a team or a campus pool their own machines over a private network.
- **Connect any agent.** OpenAI- and Anthropic-compatible endpoints, with per-app API keys, usage tracking and copy-paste setup for pi, oh-my-pi, opencode, Crush, Goose, Aider, Cline, Kilo, Continue, Claude Code, Codex and Hermes.
- **Cloud for personal use only.** RunPod and other cloud providers can be turned on for a personal profile. They live only in Fonsviva (the apps never call a provider themselves), are off by default, and are never used for client tax returns or institutional data. See [docs/CLOUD.md](docs/CLOUD.md).

## Built on

Fonsviva builds on open work from [Sybil Solutions](https://github.com/sybil-solutions) and [0xSero](https://github.com/0xSero) instead of reinventing it:

- [Local Studio](https://github.com/sybil-solutions/local-studio) (MIT): the controller that discovers vLLM, SGLang, llama.cpp, LM Studio and any `/v1/models` server, serves OpenAI Chat Completions, Completions, Anthropic Messages and Responses APIs, and reaches every machine over Tailscale.
- [Local AI registry](https://github.com/sybil-solutions/local-ai-registry) ([local.sybilsolutions.ai](https://local.sybilsolutions.ai)): tested model recipes per GPU and the six gates every recipe must pass.
- [local-ai-images](https://github.com/sybil-solutions/local-ai-images): attested container images pinned by the registry, so a recipe runs the same everywhere.
- [spark-stack](https://github.com/sybil-solutions/spark-stack): preparing, serving, freeing and reporting on models across DGX Sparks.
- [harness-bridge](https://github.com/0xSero/harness-bridge) and [omarchy-local-ai](https://github.com/0xSero/omarchy-local-ai): pointing coding harnesses at a local endpoint.

Engines: vLLM and SGLang for large GPUs, llama.cpp for Macs, CPUs and small cards. LiteLLM or GPUStack are optional for routing or a standalone cluster, and llm-d is used only where a university already runs Kubernetes. See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for what Fonsviva adds on top.

## Principles

- **Local first.** Your models run on your hardware, and your data stays with you.
- **Easy for anyone.** Someone who has never heard of quantization can still pick the right model.
- **Honest.** Speed, fit and quality claims come from real measurements, never guesses.
- **Stable.** Other apps depend on Fonsviva, so it ships on Stable and Dev channels only.

## Status

Early planning. Contributions and ideas are welcome.

## License

MIT
