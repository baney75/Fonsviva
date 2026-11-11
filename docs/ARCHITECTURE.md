# Architecture: what Fonsviva builds on and what it adds

## The base (not rebuilt)

| Layer | Project | What it gives us |
|---|---|---|
| Controller | [Local Studio](https://github.com/sybil-solutions/local-studio) | Finds vLLM, SGLang, llama.cpp, LM Studio and any server that answers `/v1/models`. Serves OpenAI Chat Completions, Completions, Anthropic Messages and Responses. Reaches models on other machines over Tailscale. |
| Recipes | [Local AI registry](https://github.com/sybil-solutions/local-ai-registry) | One tested launch recipe per model and GPU, each with evidence that it passed six gates: load, chat, reasoning, tools, context, and 15 tok/s or more. |
| Images | [local-ai-images](https://github.com/sybil-solutions/local-ai-images) | Attested container images the registry pins. No license yet: reference only until one is added. |
| Spark serving | [spark-stack](https://github.com/sybil-solutions/spark-stack) | Preparing, serving and freeing models on DGX Sparks. No license yet: reference only until one is added. |
| Harness setup | [harness-bridge](https://github.com/0xSero/harness-bridge), [omarchy-local-ai](https://github.com/0xSero/omarchy-local-ai) | Pointing coding harnesses at a local endpoint without editing their configs by hand. |

Engines: vLLM and SGLang on large GPUs; llama.cpp on Macs, CPUs and small cards. Optional: LiteLLM or GPUStack for routing or a standalone cluster; llm-d only where a university already runs Kubernetes. We don't use TGI (archived) and don't treat exo as a building block.

## What Fonsviva adds

v0 runs on top of the Local Studio controller instead of replacing it, and ships part of item 1 (the installed-model list), item 5 (keys) and item 6 (connect). The rest comes after v0.

1. **Model manager and storage.** One inventory of installed models across every engine and device, a guided way to get new ones, and storage management. See [MODELS.md](MODELS.md) and [STORAGE](STORAGE.md).
2. **Job queue.** Long jobs keep running while the user is away, survive restarts, and report where and how they ran.
3. **Sparks (compute nodes).** Machines that people choose to share privately with a family, team or campus. Owners set who can use them, when, and how much.
4. **Hugging Face connector.** Search, download and verify models, with token handling for gated models.
5. **Keys and usage.** Org keys scoped by app, model, job type and node, with expiry, limits, rotation, revoke and a usage log; agents can make narrower, short-lived keys. See [KEYS](KEYS.md).
6. **Connect your agents.** Copy-paste setup for every supported harness. See [CONNECT.md](CONNECT.md).
7. **Workload profiles and the cloud block.** Every API key is bound to one profile (personal, UntoCaesar, Corunis, Gantrel) when it is created. A request can't pick its own profile, and one whose profile field doesn't match its key is refused. Cloud providers can serve only personal work. See [CLOUD.md](CLOUD.md).
8. **Jobs of every type.** Chat, batch, notebooks, images, video, audio, embeddings, training and renders. See [JOBS](JOBS.md).
9. **Costs and spend protection.** See [COSTS](COSTS.md).
10. **Device benchmarks.** Measure any device with the registry's gates plus each app's task gates. See [BENCHMARKS.md](../BENCHMARKS.md).

## Who owns what

- **Fonsviva runs on its own.** It installs and works without any app, as a CLI (`fonsviva`) plus a web app, and is then shared by every app on the machine or network.
- **Apps own model choice.** People pick models inside UntoCaesar, Gantrel and Corunis. Fonsviva downloads, stores and serves them.
- **Fonsviva owns compute and cloud.** Adding machines and nodes, linking cloud accounts, turning providers on or off, keys, costs and budgets happen only in Fonsviva. See [COMPUTE](COMPUTE.md), [COSTS](COSTS.md), [providers](providers.md).
- **Install flow in every app.** If an app finds Fonsviva, it connects and lets the person pick or install models in the app. If not, the app installs Fonsviva (after asking) and runs its setup inside the app's onboarding, including the optional cloud step with the same personal-use-only rule and blocks.

## How the apps use it

UntoCaesar, Gantrel and Corunis call Fonsviva's API with their own keys and profiles. Fonsviva picks a model and machine that passed the app's task gates on that hardware, and refuses rather than falls back to a place the profile doesn't allow.
