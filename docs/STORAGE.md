# Model storage

Models are large. Fonsviva makes their disk use visible and easy to manage.

- **Disk use** per model, per drive and per node, with free space shown next to it.
- **Dedupe:** one copy of shared weights across engines (Ollama, LM Studio, llama.cpp, vLLM, SGLang) and the Hugging Face cache, using links where the engine allows it. Shows the space saved.
- **Move** a model to another drive or node; apps that use it keep working.
- **Cleanup suggestions:** unused models listed oldest first, each with what still uses it, its size and when it was last used. Nothing is deleted without the user confirming that model.
- **Quotas** per drive or node, and a warning **before** a download that won't fit.
- **Downloads** resume after interruption and are checksum-verified before use.
- **Pin and protect:** pinned models stay loaded; protected models are never suggested for cleanup and can't be removed without unprotecting first.
