# Architecture: what Fonsviva builds on and what it adds

## The base (not rebuilt)

| Layer | Project | What it gives us |
|---|---|---|
| Controller | [Local Studio](https://github.com/sybil-solutions/local-studio) | Finds vLLM, SGLang, llama.cpp, LM Studio and any server that answers `/v1/models`. Serves OpenAI Chat Completions, Completions, Anthropic Messages and Responses. Reaches models on other machines over Tailscale. |
| Recipes | [Local AI registry](https://github.com/sybil-solutions/local-ai-registry) | One tested launch recipe per model and GPU, each with evidence that it passed six gates: load, chat, reasoning, tools, context, and 15 tok/s or more. |
| Images | [local-ai-images](https://github.com/sybil-solutions/local-ai-images) | Attested container images the registry pins. |
| Spark serving | [spark-stack](https://github.com/sybil-solutions/spark-stack) | Preparing, serving and freeing models on DGX Sparks. |
| Harness setup | [harness-bridge](https://github.com/0xSero/harness-bridge), [omarchy-local-ai](https://github.com/0xSero/omarchy-local-ai) | Pointing coding harnesses at a local endpoint without editing their configs by hand. |

Engines: vLLM and SGLang on large GPUs; llama.cpp on Macs, CPUs and small cards. Optional: LiteLLM or GPUStack for routing or a standalone cluster; llm-d only where a university already runs Kubernetes. We don't use TGI (archived) and don't treat exo as a building block.

## What Fonsviva adds

1. **Model manager.** One inventory of installed models across every engine and device, plus a guided way to get new ones. See [MODELS.md](MODELS.md).
2. **Job queue.** Long jobs keep running while the user is away, survive restarts, and report where and how they ran.
3. **Sparks (compute nodes).** Machines that people choose to share privately with a family, team or campus. Owners set who can use them, when, and how much.
4. **Hugging Face connector.** Search, download and verify models, with token handling for gated models.
5. **Per-app API keys and usage.** Each app or agent gets its own key, limits and usage history, and can be revoked alone.
6. **Connect your agents.** Copy-paste setup for every supported harness. See [CONNECT.md](CONNECT.md).
7. **Workload profiles and the cloud block.** Every request carries a profile (personal, UntoCaesar, UniCerebrum, Gantrel). Cloud providers can serve only personal work. See [CLOUD.md](CLOUD.md).
8. **Device benchmarks.** Measure any device with the registry's gates plus each app's task gates. See [BENCHMARKS.md](../BENCHMARKS.md).

## How the apps use it

UntoCaesar, Gantrel and UniCerebrum call Fonsviva's API with their own keys and profiles. Fonsviva picks a model and machine that passed the app's task gates on that hardware, and refuses rather than falls back to a place the profile doesn't allow.
