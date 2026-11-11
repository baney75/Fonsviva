# Install Fonsviva

> **Status: planned, not released.** Fonsviva has no release yet, so there is nothing to install today. These steps are the target behavior. Each one becomes true only when its test in [TESTING.md](https://github.com/baney75/Fonsviva/blob/main/TESTING.md) passes, and [SUPPORTED.md](https://github.com/baney75/Fonsviva/blob/main/SUPPORTED.md) is the source of truth for what works now. An agent must check SUPPORTED.md first and tell the person plainly if a step isn't supported yet.

Fonsviva can be set up on its own, before any app. Apps that find it will use it; apps that don't will install it for you (see each app's install page).

## Steps

1. Install Fonsviva from the [latest Stable release](https://github.com/baney75/Fonsviva/releases). (No release yet.)
2. Run `fonsviva setup`. It scans this machine, lists models already installed by Ollama, LM Studio, llama.cpp, vLLM, SGLang and the Hugging Face cache, and recommends a first model that fits.
3. Open the web app at `http://127.0.0.1:7341`.

## Check

Run `fonsviva status`. Expected output:

```
Fonsviva <version> running at http://127.0.0.1:7341
Profile: personal
Nodes: 1 (this machine)
Models: <number found>
Cloud providers: off
```

`fonsviva status --json` returns the same as JSON with `"running": true`. `curl http://127.0.0.1:7341/health` returns `{"status":"ok"}`.

If any check fails, see [troubleshoot](troubleshoot.md).
