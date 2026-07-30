# Documentation Plan

## Published SEO guides

| Guide | GitHub source | LTX.dev destination |
|---|---|---|
| Open-weight AI video generators | [`guides/open-source-ai-video-generators-2026.md`](guides/open-source-ai-video-generators-2026.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |
| What is LTX Video? | [`getting-started/what-is-ltx-video.md`](getting-started/what-is-ltx-video.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |
| Install LTX-2.3 locally | [`getting-started/install-ltx-video-locally.md`](getting-started/install-ltx-video-locally.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |
| GPU and VRAM requirements | [`hardware/ltx-video-gpu-requirements.md`](hardware/ltx-video-gpu-requirements.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |
| ComfyUI tutorial | [`comfyui/ltx-comfyui-tutorial.md`](comfyui/ltx-comfyui-tutorial.md) | [LTX.dev creation workspace](https://ltx.dev/studio/text-to-video) |
| Local AI video generation | [`guides/local-ai-video-generation.md`](guides/local-ai-video-generation.md) | [Hosted LTX 2.3](https://ltx.dev/studio/text-to-video/ltx) |
| Open-weight Sora alternatives | [`comparisons/open-source-sora-alternatives-2026.md`](comparisons/open-source-sora-alternatives-2026.md) | [Model workspace](https://ltx.dev/studio/text-to-video) |
| LTX API guide | [`developers/ltx-api-guide.md`](developers/ltx-api-guide.md) | [Hosted LTX 2.3](https://ltx.dev/studio/text-to-video/ltx) |
| Build an AI video app | [`developers/build-ai-video-app-with-ltx-api.md`](developers/build-ai-video-app-with-ltx-api.md) | [Model workspace](https://ltx.dev/studio/text-to-video) |
| LTX prompt library | [`prompting/ltx-video-prompts-library.md`](prompting/ltx-video-prompts-library.md) | [LTX.dev prompts](https://ltx.dev/prompts) |
| Cinematic prompts | [`prompting/cinematic-ai-video-prompts.md`](prompting/cinematic-ai-video-prompts.md) | [LTX.dev prompts](https://ltx.dev/prompts) |
| AI filmmaking workflow | [`filmmaking/ai-filmmaking-workflow-with-ltx.md`](filmmaking/ai-filmmaking-workflow-with-ltx.md) | [Video workspace](https://ltx.dev/studio/text-to-video) |
| Create an AI short film | [`filmmaking/create-ai-short-films-with-ltx.md`](filmmaking/create-ai-short-films-with-ltx.md) | [Video workspace](https://ltx.dev/studio/text-to-video) |
| AI video generators for developers | [`comparisons/ai-video-generators-for-developers.md`](comparisons/ai-video-generators-for-developers.md) | [Compare models](https://ltx.dev/studio/text-to-video) |
| LTX developer guide | [`developers/ltx-developer-guide.md`](developers/ltx-developer-guide.md) | [Hosted LTX 2.3](https://ltx.dev/studio/text-to-video/ltx) |

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

The technical guides are reviewed against public provider sources but are not
presented as independently executed LTX.dev environment tests. They
intentionally omit unsupported benchmark results.
