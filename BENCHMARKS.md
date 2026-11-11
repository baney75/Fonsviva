# Benchmarking local models

Fonsviva must know which models actually run well on which device. Guessing is not allowed.

## Built on the Local AI registry

Model launches come from Sybil Solutions' [Local AI registry](https://github.com/sybil-solutions/local-ai-registry) ([local.sybilsolutions.ai](https://local.sybilsolutions.ai)). Each registry recipe is a validated way to run a model on a specific GPU that passed six gates: it loads, chats, reasons, calls tools, holds context and decodes at 15 tok/s or more.

Fonsviva runs the same gates on **any** device, including Macs, CPUs and small cards the registry doesn't cover yet, so a user can see for themselves whether a model works on their own machine.

## Fonsviva gates

On top of the registry gates, Fonsviva measures:

- **Time to first token and sustained speed** at short and long context.
- **Memory headroom:** peak memory while serving, with the device's other work running.
- **Concurrency:** speed with two and four requests at once, for shared Sparks.
- **API fidelity:** tool calls and streaming come back correctly through both the OpenAI and Anthropic endpoints.

Each dependent app (UntoCaesar, Gantrel, Corunis) adds its own task gates in its own repo. A model is offered to an app only where it passed that app's gates on that hardware.

## How a run works

1. Pick a registry recipe for the hardware, or a Hugging Face model the user chose.
2. Run the gates in `tests/` against it on the device.
3. Save the result to `benchmarks/results/<model>/<device>.json` with the recipe ID, engine and version, date, hardware, result per gate and a log hash.
4. Offer the run to the registry upstream when it covers new hardware.

## Per-model instructions

Each model that passes gets a folder in `models/<model>/` (copy `models/_template/`) with the engine settings, chat template, tool-call format and known issues that model needs.
