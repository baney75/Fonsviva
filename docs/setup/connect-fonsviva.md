# Connect apps and agents to Fonsviva

> **Status: planned, not released.** Fonsviva has no release yet, so there is nothing to install today. These steps are the target behavior. Each one becomes true only when its test in [TESTING.md](https://github.com/baney75/Fonsviva/blob/main/TESTING.md) passes, and [SUPPORTED.md](https://github.com/baney75/Fonsviva/blob/main/SUPPORTED.md) is the source of truth for what works now. An agent must check SUPPORTED.md first and tell the person plainly if a step isn't supported yet.

## Apps (UntoCaesar, Gantrel, UniCerebrum)

Apps connect themselves: when an app finds Fonsviva it sends a connection request. Approve it in the web app under **Connect**, or run `fonsviva keys approve <app>`. Each app gets its own key and profile.

Check: `fonsviva keys list` shows the app with status `active` and its profile (`personal`, `untocaesar-client` or `unicerebrum`).

## Coding agents

Create a key with `fonsviva keys create --app <name>`, then use the setup for your harness in [CONNECT](https://baney75.github.io/Fonsviva/CONNECT). Check: the Connect screen's **Test** button, or `fonsviva keys test <name>`, returns `ok` with a model list.
