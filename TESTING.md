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
