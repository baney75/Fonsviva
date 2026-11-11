# Testing: honest claims only

Fonsviva must never claim it can do something it can't. Every claim in the README, the docs or the app has a behavior test behind it, and the results are public in this repo.

## Behavior tests

Each test runs the real software against real engines and models and checks what a user or app would see.

### API compatibility, per harness

For every harness in `docs/CONNECT.md` (pi, oh-my-pi, opencode, Crush, Goose, Aider, Cline, Kilo, Continue, Claude Code, Codex, Hermes):

- Apply the setup the Connect screen generates, then run the harness for real.
- It must list models, stream a reply, make a tool call and receive the tool result, through the endpoint that harness uses (Chat Completions, Responses or Anthropic Messages).
- Claude Code must work with the origin as base URL (no `/v1`). Codex must work with `wire_api = "responses"`.
- A harness is listed in `SUPPORTED.md` only after this passes.

### Model manager

- On a test machine with known models installed through Ollama, LM Studio, llama.cpp, vLLM and the Hugging Face cache, the inventory finds every one, with the right size and quantization, and no extras.
- The same model stored twice is flagged as a duplicate.
- Remove asks first, warns when an app depends on the model, and never deletes a file Fonsviva didn't download without confirmation.
- Hardware fit: a model that doesn't fit the device is never marked "recommended."
- An interrupted download resumes and the checksum is verified.

### Cloud block

- With cloud providers on, any job carrying an UntoCaesar client or volunteer profile, or a UniCerebrum profile, is refused before a single byte leaves the machine. Checked by watching network traffic, not just the response.
- No setting, flag, environment variable or API field turns this off.
- A personal job never goes to cloud without its own confirmation, and the cost is shown first.
- Every job record says where it ran.

### Job queue

- Queue jobs, kill the Fonsviva process and the host, restart: every job is still there and finishes or resumes, with none run twice.
- A Spark that drops off the network mid-job: the job is retried on an allowed machine or marked failed with a plain reason.

### Adding compute and keys

- Add a local machine, a Spark and a cloud provider through the guided flow: each ends in a working, listed resource.
- After adding keys, search every config file, log and export on disk: no key appears in plain text. Keys are found only in the OS keychain or the encrypted store.
- A scoped key used outside its scope (another profile, job type or model) is refused.
- Node pairing fails with a wrong or unconfirmed code, and works only over the tailnet.
- `fonsviva revoke` on an app, node or provider cuts access on the next request and stops its running jobs; for a provider, its pods are stopped (checked on the provider's own API).

### Costs

- Power cost for a fixed job matches wattage × hours × rate within the stated tolerance, and changes when the user edits the rate.
- Cloud estimate is shown before launch, and the day and month totals match the provider's billing records for the test account.

### Cloud spend protection

Run against a real provider test account with tiny caps.

- **Caps:** a job that would pass the per-job cap is refused before launch; a running job that reaches the daily or monthly cap is stopped, and new cloud jobs are blocked until the period resets or the user raises the cap.
- **Auto-stop:** a pod idle for 10 minutes (default) is stopped; a job that reaches its max runtime is stopped. Confirmed on the provider's API, not just in Fonsviva.
- **Orphans:** a pod or volume launched by Fonsviva and left without a job (for example after killing Fonsviva) is found and stopped on next start.
- **Storage warning** appears before any paid volume is created.
- **Alerts** fire at 50%, 80% and 100% of budget, once each.
- **Dry run** launches nothing (verified on the provider's API) and shows the same plan and estimate a real run uses.
- **Emergency stop:** `fonsviva cloud stop-all` and the button stop every pod on every provider and turn cloud off.
- **Cheapest safe GPU:** the picker never chooses a GPU without a passing recipe for the model.

### Jobs of every type

For each job type in `docs/JOBS.md` (chat, batch, notebooks, image, video, audio, embeddings, training, renders): submit through the API and the CLI, and the job shows queue position, status, logs, artifacts, cost and where it ran. Restart during each type and the job resumes or fails cleanly, never runs twice.

### Install flow in the apps

- With Fonsviva running, each app connects and lets the user pick and install models in the app.
- With no Fonsviva, each app installs it only after asking, runs its setup inside the app, and the result is a standalone Fonsviva another app can reuse.
- The app's cloud step for UntoCaesar client work or UniCerebrum is absent or blocked.

### Model storage

- Disk use per model, drive and node matches the file system.
- The same weights installed by two engines and the HF cache are stored once after dedupe, and every engine still loads them.
- A moved model still loads in every app that uses it.
- Cleanup lists unused models oldest first with their users; protected models never appear; nothing is deleted without confirmation.
- A download larger than free space or quota is refused before it starts; an interrupted download resumes; a corrupted file fails the checksum and is never loaded.

### Key expiry, limits and scope

- **Expiry:** a key fails on the first request after it expires; an agent-made key with no expiry set expires after 1 hour.
- **Limits:** each limit (rate, tokens, spend, concurrent jobs) is hit exactly at its value: the next request or job is refused with a plain reason, and the usage log records it.
- **Cloud on a key:** off by default; a key without cloud permission can't cause a cloud job even when the profile allows cloud; UntoCaesar client and UniCerebrum keys can never be given cloud.
- **Scope:** a request for a model, job type, app or node outside the key's scope is refused.
- **No widening:** an agent asking to create a key with any scope or limit wider than its own key is refused, field by field; every agent-made key is labelled and in the audit log.
- **Rotate:** after rotation the old secret fails once the overlap ends, and the new one works with the same scope.
- **Sharing:** a one-time link works once and then fails; keys never appear in chat transcripts, logs, errors or exports (searched after the test).

### Agent setup docs

An agent given only the repo or site follows `docs/agents.md` on a clean machine, and every **Check** in `docs/setup/` gives the expected output. Any mismatch is a docs bug that blocks release.

### Updates

- Update from the last Stable release with jobs queued: nothing is lost.
- Roll back: the previous version runs with the same settings, keys, inventory and queue.
- A tampered update is refused.

### Keys and isolation

- One app's key can't see another app's jobs or usage. A revoked key fails at once.
- Secrets never appear in logs, errors or exports.

## Rules

- **No unknown error.** Any output that differs from the expected result fails the test. "Close enough" is a failure.
- **Known limits are declared.** Anything Fonsviva doesn't support yet is listed in `SUPPORTED.md`, and the app tells the user plainly instead of guessing.
- **Real behavior, not mocks.** Tests run real engines, models and harnesses.
- **Regressions block release.** Any failing test blocks promotion from Dev to Stable.

## Layout

- `tests/golden/`: expected outputs and fixtures.
- `tests/skills/<skill-name>/`: tests for each skill.
- `benchmarks/results/`: published results per model and device.
