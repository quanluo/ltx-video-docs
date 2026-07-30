# Documentation Plan

## Initial editorial queue

| Priority | Guide | Primary intent | Status |
|---:|---|---|---|
| P0 | `getting-started/installation.md` | Install LTX-2 locally | Requires hardware verification |
| P0 | `hardware/gpu-vram-matrix.md` | LTX GPU and VRAM requirements | Requires measured data |
| P0 | `guides/text-to-video.md` | Generate video from text | Requires end-to-end test |
| P0 | `guides/image-to-video.md` | Generate video from an image | Requires end-to-end test |
| P1 | `troubleshooting/cuda-and-memory.md` | Fix CUDA or VRAM errors | Source review required |
| P1 | `prompting/synchronized-audio.md` | Prompt audio-video generation | Output review required |
| P1 | `comfyui/setup.md` | Set up LTX in ComfyUI | Version test required |
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
