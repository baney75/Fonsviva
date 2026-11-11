# API keys

Every app, agent, person and node reaches Fonsviva with its own key. Keys are stored in the OS keychain or an encrypted store, never in plain config (see [COMPUTE](COMPUTE.md)).

## Org keys

Orgs and their admins create keys scoped by:

- **App** (UntoCaesar, Gantrel, UniCerebrum, or a named agent)
- **Model**
- **Job type** (see [JOBS](JOBS.md))
- **Node** (which machines it may run on)

Each key can have an **expiry** and **limits**: requests per minute, tokens, spend, concurrent jobs, and allowed cloud use, which is **off by default** and can never be turned on for UntoCaesar client or UniCerebrum profiles ([CLOUD](CLOUD.md)).

Keys can be **rotated** (new secret, same scope, old one stops after a short overlap) and **revoked** in one step. Each key has a **usage log**: when, what job type, which model and node, tokens, cost and result.

## Keys made by agents

- An agent can create a key only **within its own key's permissions**, never wider: same or narrower apps, models, job types, nodes, limits and cloud use.
- Agent-made keys are **short-lived by default** (1 hour unless the person sets longer, up to the creator's own expiry).
- Every agent-made key is **labelled agent-created** and recorded in the audit log with the creating key, the person it acted for and the scope.

## Sharing a key safely

A key is **never shown in chat or in logs**. To get a key to a person or another machine, Fonsviva offers:

- a **one-time link** that shows the key once and then expires,
- a **pairing code** the recipient enters in their own Fonsviva or app, or
- a **handoff** straight into the recipient's OS keychain or secret store.

CLI: `fonsviva keys create`, `fonsviva keys list`, `fonsviva keys show <name>` (scope and usage, never the secret), `fonsviva keys rotate <name>`, `fonsviva revoke <name>`, `fonsviva keys share <name> --link|--code|--keychain`.
