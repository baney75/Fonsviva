# Troubleshoot

> **Status: planned, not released.** Fonsviva has no release yet, so there is nothing to install today. These steps are the target behavior. Each one becomes true only when its test in [TESTING.md](https://github.com/baney75/Fonsviva/blob/main/TESTING.md) passes, and [SUPPORTED.md](https://github.com/baney75/Fonsviva/blob/main/SUPPORTED.md) is the source of truth for what works now. An agent must check SUPPORTED.md first and tell the person plainly if a step isn't supported yet.

Start with `fonsviva doctor`. It checks the service, engines, models, keys and network, and prints one line per check with `ok` or a plain fix.

| Problem | Check | Fix |
|---|---|---|
| Fonsviva not found | `curl http://127.0.0.1:7341/health` | Start it with `fonsviva start`, or install it ([install](https://baney75.github.io/Fonsviva/setup/install)). |
| App not connected | `fonsviva keys list` | Approve the app: `fonsviva keys approve <app>`. |
| Model won't load | `fonsviva models test <id>` | Pick a smaller model or quantization that fits; the output says how much memory it needs. |
| Slow replies | `fonsviva models list` speed column | Use a recipe that passed the speed gate on this hardware. |
| Job waiting | `fonsviva jobs list` | Protected jobs wait for owned machines and never fall back to cloud. Free a machine or add a Spark. |
| Cloud job refused | `fonsviva cloud list` | Expected for UntoCaesar client work and Corunis. Cloud is personal use only. |

If a check isn't in SUPPORTED.md yet, tell the person it's not supported yet instead of guessing. Report bugs at [https://github.com/baney75/Fonsviva/issues](https://github.com/baney75/Fonsviva/issues).
