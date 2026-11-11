# Connecting agents and apps

Fonsviva serves an OpenAI-compatible API at `http://<host>:<port>/v1` and an Anthropic-compatible API at the same origin. Each agent gets its own API key from the Connect screen, which shows the exact setup to paste for the harness the user picks and confirms the connection with a test request.

| Harness | Where setup goes | Notes |
|---|---|---|
| pi | `~/.pi/agent/models.json` | OpenAI-compatible provider entry. |
| oh-my-pi (OMP) | `~/.omp/agent/models.yml` | OpenAI-compatible provider entry. |
| opencode | `opencode.json`, `provider` section | OpenAI-compatible provider with the model list. |
| Crush | Crush provider config | OpenAI-compatible provider. |
| Goose | Goose provider settings | OpenAI-compatible host and key. |
| Aider | Environment or `.aider.conf.yml` | OpenAI API base and key. |
| Cline, Kilo, Continue | Extension provider settings | "OpenAI compatible" provider with base URL and key. |
| Claude Code | `ANTHROPIC_BASE_URL` and `ANTHROPIC_AUTH_TOKEN` | Base URL is the origin **without** `/v1`. |
| Codex | `~/.codex/config.toml`, `model_providers` | Uses `wire_api = "responses"`. |
| Hermes | Hermes provider settings | OpenAI-compatible endpoint. |

harness-bridge already handles many of these; Fonsviva uses it where it fits and keeps the table above tested (see `TESTING.md`). Every row must have a passing compatibility test before it appears in the app.

The Connect screen also lists every connected app and agent, its last request, its usage and a one-click revoke.
