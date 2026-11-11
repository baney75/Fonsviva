# Select and get models

> **Status: planned, not released.** Fonsviva has no release yet, so there is nothing to install today. These steps are the target behavior. Each one becomes true only when its test in [TESTING.md](https://github.com/baney75/Fonsviva/blob/main/TESTING.md) passes, and [SUPPORTED.md](https://github.com/baney75/Fonsviva/blob/main/SUPPORTED.md) is the source of truth for what works now. An agent must check SUPPORTED.md first and tell the person plainly if a step isn't supported yet.

People usually pick models inside each app. Fonsviva's own model manager is for seeing and managing everything at once. Details: [MODELS](https://baney75.github.io/Fonsviva/MODELS).

## Steps

1. `fonsviva models list` shows every installed model, its size, quantization, speed on this device and which apps use it.
2. `fonsviva models search <words>` finds registry recipes and Hugging Face models that fit this hardware.
3. `fonsviva models get <id>` downloads one, verifies it, and runs the gates.

## Check

`fonsviva models list` shows the new model with gates `pass`. Models that fail a gate are marked and never offered to an app for that task.
