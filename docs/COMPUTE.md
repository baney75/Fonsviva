# Adding compute: easy and secure

Fonsviva has one guided **Add compute** flow, in the web app and as `fonsviva add`, for three kinds of compute.

| Kind | What happens |
|---|---|
| **This or another local machine** | Fonsviva detects GPUs, memory, disk and engines, measures speed, and estimates power cost ([COSTS](COSTS.md)). |
| **A Spark or other node** | The node runs `fonsviva node join`, which shows a short pairing code. Pairing happens over Tailscale, and both sides must confirm the code. The owner sets who may use it, when, and limits. |
| **A cloud provider** | Personal profile only. Pick from [providers](providers.md), paste the key once, set budgets before it can be turned on ([COSTS](COSTS.md)). |

## Security rules

- **Keys never live in plain config.** Provider keys, node credentials and app keys are stored in the OS keychain (macOS Keychain, Windows Credential Manager, Linux Secret Service) or, where none exists, an encrypted store. Config files hold references only.
- **Scoped keys.** Each app, agent and node gets its own key, limited to the profiles, job types, models and nodes it needs, with optional expiry. See [KEYS](KEYS.md).
- **Pairing over Tailscale.** Nodes talk over the private tailnet, never an open port. Pairing needs a code confirmed on both sides.
- **One-step revoke.** `fonsviva revoke <app|agent|node|provider>` or one button removes access at once and stops its running jobs. Cloud revocation also stops that provider's pods.
- **Never shown again.** A key is shown once at creation, never logged, never in errors or exports.
