# Vetted cloud providers

Cloud providers are **personal use only**, live only in Fonsviva, and are off by default. See [CLOUD](CLOUD.md) for the rules and [COSTS](COSTS.md) for spend protection.

## How this list is made

This is a starting list, not a security review. Before any provider can be turned on, check its published terms: data processing agreement, SOC 2 or ISO 27001 report, data region and deletion policy. Add what you find to its row.

Fonsviva builds on the work of Sherif ([0xSero](https://github.com/0xSero), [Sybil Solutions](https://github.com/sybil-solutions)). A provider is listed only if Sherif has publicly used it, or mentioned it neutrally or positively, and has never spoken badly of it. Each entry links the source. Providers he never mentioned are left out, even good ones. Checked 2026-11-11 against the sybil-solutions and 0xSero GitHub repos, local.sybilsolutions.ai, localstudio.ai, sybilsolutions.ai and his posts on X.

None of these providers publishes FERPA or IRS Section 7216 terms, and none is listed here as confidential (TEE) compute. Listing means "trusted enough for personal experiments," nothing more.

## Listed

| Provider | Kind | Evidence |
|---|---|---|
| [RunPod](https://www.runpod.io) | GPU pods and serverless | The Local AI registry rents test machines on RunPod ([README](https://github.com/sybil-solutions/local-ai-registry#readme), [docs/data.md](https://github.com/sybil-solutions/local-ai-registry/blob/main/docs/data.md)); he names it among the clouds he rents from ([post](https://x.com/0xSero/status/2111211840155824322)) and recommends it to beginners ([post](https://x.com/0xSero/status/2092007207147614246)). |
| [Vast.ai](https://vast.ai) | GPU marketplace | The registry's default rental target for recipe tests ([README](https://github.com/sybil-solutions/local-ai-registry#readme)); he rents from it ([post](https://x.com/0xSero/status/2111211840155824322)). |
| [Prime Intellect](https://www.primeintellect.ai) | GPU cloud | His most-used cloud: "The UX is phenomenal" ([post](https://x.com/0xSero/status/2053720116135673949)); sponsor and frequent recommendation ([post](https://x.com/0xSero/status/2055503924338053537)). |
| [Lambda](https://lambda.ai) | GPU cloud | Sponsor he thanks repeatedly and uses ([post](https://x.com/0xSero/status/2067728294775079214), [post](https://x.com/0xSero/status/2063036402640564342)). He notes high-end GPUs can be hard to get ([post](https://x.com/0xSero/status/2067294476221993418)), an availability note, not a complaint. |
| [Hot Aisle](https://hotaisle.xyz) | AMD GPU cloud | Sponsor; "really pleasantly surprised" and used it for AMD support in his tools ([post](https://x.com/0xSero/status/2024376485469982891), [post](https://x.com/0xSero/status/2020237835912315081)). |
| [NVIDIA Brev](https://developer.nvidia.com/brev) | GPU cloud | Lists Brev credits from NVIDIA among his grants ([post](https://x.com/0xSero/status/2054615204302860334)). |
| [Akash](https://akash.network) | Decentralized GPU cloud | Thanked as a donor for hardware he gave a university ([post](https://x.com/0xSero/status/2110010247981260824), [post](https://x.com/0xSero/status/2107466678262989305)). No record of him running jobs on it, so it is listed last. |

## Not listed

Phala, Tinfoil, Together AI, Nebius, Hyperbolic, Chutes, Venice, NEAR AI and Redpill. None was criticized; they're left out because the check found no clear mention by Sherif. (Chutes appears once in a 2025 reply about a config file, which is too thin to count.) A provider can be added later by pull request with a source link that meets the rule above.
