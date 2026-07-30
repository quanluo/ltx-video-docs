# Documentation Plan

## Published SEO guides

| Guide | GitHub source | LTX.dev destination |
|---|---|---|
| Open-weight AI video generators | [`guides/open-source-ai-video-generators-2026.md`](guides/open-source-ai-video-generators-2026.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |
| What is LTX Video? | [`getting-started/what-is-ltx-video.md`](getting-started/what-is-ltx-video.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |
| Install LTX-2.3 locally | [`getting-started/install-ltx-video-locally.md`](getting-started/install-ltx-video-locally.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |
| GPU and VRAM requirements | [`hardware/ltx-video-gpu-requirements.md`](hardware/ltx-video-gpu-requirements.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |
| ComfyUI tutorial | [`comfyui/ltx-comfyui-tutorial.md`](comfyui/ltx-comfyui-tutorial.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |

Continue through the
[LTX.dev ecosystem hub](https://github.com/quanluo/ltx-dev-ecosystem),
[runnable examples](https://github.com/quanluo/ltx-video-examples),
[ComfyUI workflows](https://github.com/quanluo/ltx-comfyui-workflows), and
[prompt cookbook](https://github.com/quanluo/ltx-video-prompts).

## Initial editorial queue

| Priority | Guide | Primary intent | Status |
|---:|---|---|---|
| P0 | [`getting-started/installation.md`](getting-started/installation.md) | Install LTX-2 locally | Source-reviewed |
| P0 | [`hardware/gpu-vram-guide.md`](hardware/gpu-vram-guide.md) | Understand GPU and VRAM requirements | Source-reviewed |
| P0 | [`guides/text-to-video.md`](guides/text-to-video.md) | Generate video from text | Source-reviewed |
| P0 | [`guides/image-to-video.md`](guides/image-to-video.md) | Generate video from an image | Source-reviewed |
| P1 | [`hardware/low-vram-options.md`](hardware/low-vram-options.md) | Reduce peak GPU memory | Source-reviewed |
| P1 | [`troubleshooting/cuda-and-memory.md`](troubleshooting/cuda-and-memory.md) | Diagnose CUDA or VRAM errors | Source-reviewed |
| P1 | [`prompting/synchronized-audio.md`](prompting/synchronized-audio.md) | Prompt audio-video generation | Editorial guide |
| P1 | [`comfyui/setup.md`](comfyui/setup.md) | Set up LTX in ComfyUI | Source-reviewed |
| P1 | `training/lora-quickstart.md` | Train an LTX LoRA | Training test required |
| P1 | `migration/ltx-video-to-ltx-2.md` | Migrate to LTX-2 | Upstream review required |

## Page contract

Each guide contains:

1. outcome and supported version;
2. prerequisites;
3. verified steps;
4. expected result;
5. common failures and fixes;
6. related examples and workflows;
7. canonical upstream references;
8. author, reviewer, and last-reviewed date.

Do not convert planned filenames into published claims until the required
verification is complete.

All eight initial guides were reviewed against official sources but were not
independently executed by LTX.dev. They intentionally omit benchmark results.
