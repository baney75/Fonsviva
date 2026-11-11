# Jobs

Agents and apps send work to Fonsviva through the API and the CLI (`fonsviva jobs submit`). Every job, of any type, has a queue position, status, logs, artifacts, a cost (power or cloud) and a record of where it ran. Jobs survive restarts.

| Type | Examples |
|---|---|
| Chat and completions | OpenAI and Anthropic compatible requests |
| Batch | Many prompts or files in one job |
| Jupyter notebooks | Run a notebook on a chosen machine and return the executed notebook |
| Image generation | Text to image, image editing |
| Video generation | Text or image to video |
| Audio | Speech to text, text to speech |
| Embeddings | Documents to vectors |
| Fine-tunes and training | LoRA and full fine-tunes, with checkpoints |
| Renders | 3D renders, for example from Gantrel |

Statuses: `queued`, `running`, `paused`, `done`, `failed` (with a plain reason), `blocked` (profile not allowed on any available machine), `stopped` (budget cap, auto-stop or user).

CLI: `fonsviva jobs list`, `fonsviva jobs show <id>`, `fonsviva jobs logs <id>`, `fonsviva jobs artifacts <id>`, `fonsviva jobs cancel <id>`. Every submit accepts `--dry-run`.
