# The model manager

Managing local models should be as easy as managing apps on a phone.

## Installed models

Fonsviva scans each device and shows one list, whatever tool put the model there:

- Ollama, LM Studio, llama.cpp (GGUF files), vLLM and SGLang servers, and the Hugging Face cache.
- For each model: name, family, size on disk, quantization, context length, measured speed on this device, last used, and which apps and agents use it.
- Duplicates (the same model stored twice by different tools) are flagged, with the space that could be freed.

Actions: **Update** (newer revision or better recipe available), **Remove** (asks first and warns if an app depends on it), **Pin** (keep loaded, never auto-removed), and **Test** (run the gates on this device now).

Fonsviva never deletes a file it did not download unless the user confirms that specific file.

## Get local models

- **Recommended for this device.** Fonsviva reads the hardware (GPU, VRAM, unified memory, CPU, disk) and shows models that fit, with a plain-words reason: "fits in memory, about 40 words a second."
- **Registry recipes first.** Models with a passing Local AI registry recipe for matching hardware show their gate results (load, chat, reasoning, tools, context, speed) as pass or fail before download.
- **Any Hugging Face model.** Search Hugging Face directly. Models without a recipe are marked "untested here" until the user runs the gates.
- **Safe downloads.** Show size and time first, resume interrupted downloads, verify checksums, and use the user's Hugging Face token only for gated models they have access to.

## Trusted models

Each app keeps a list of models that passed its task gates. The manager shows which installed models qualify for which app, so a user never has to guess.
