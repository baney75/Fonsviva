# Add a cloud provider (personal use only)

> **Status: planned, not released.** Fonsviva has no release yet, so there is nothing to install today. These steps are the target behavior. Each one becomes true only when its test in [TESTING.md](https://github.com/baney75/Fonsviva/blob/main/TESTING.md) passes, and [SUPPORTED.md](https://github.com/baney75/Fonsviva/blob/main/SUPPORTED.md) is the source of truth for what works now. An agent must check SUPPORTED.md first and tell the person plainly if a step isn't supported yet.

Cloud providers live only in Fonsviva. The vetted list is in [providers](../providers.md), and the rules are in [CLOUD](../CLOUD.md).

## Steps

1. Choose a provider from [providers](../providers.md) and create an account and API key on its own site.
2. Run `fonsviva cloud add <provider> --profile personal`, or use **Cloud** in the web app. Fonsviva asks for the key once and stores it encrypted. It never shows it again.
3. Turn it on for the personal profile: `fonsviva cloud enable <provider> --profile personal`.

## Check

- `fonsviva cloud list` shows the provider as `on (personal only)`.
- `fonsviva cloud enable <provider> --profile untocaesar-client` or `--profile unicerebrum` is refused with `blocked: protected workload`.
- A test job shows the cost first and waits for your confirmation.
