# LTX-2 GPU and VRAM Guide

Status: source-reviewed; no independent hardware benchmark.

LTX-2 is a large audio-video model. A useful hardware guide must distinguish
official prerequisites, model-file size, system RAM, GPU VRAM, precision,
offload mode, output settings, and pipeline choice.

## What official sources currently say

The official ComfyUI integration README lists a CUDA-compatible GPU with
`32GB+` VRAM and `100GB+` free storage as prerequisites for its documented
workflow environment. Treat this as an upstream prerequisite for that setup,
not a universal guarantee for every graph or pipeline.

The Python pipeline exposes quantization and CPU/disk offload options specifically
to reduce peak GPU memory. Their existence does not establish a single minimum
VRAM number.

## Variables that change memory use

- checkpoint precision and quantization policy;
- single-stage versus two-stage generation;
- output width, height, and frame count;
- full versus distilled pipeline;
- image/video/audio conditioning;
- VAE decoding strategy and tiling;
- LoRAs and additional control models;
- batch size, compilation, and offload mode;
- ComfyUI nodes and cached models.

## How to evaluate your hardware

1. Start with the exact upstream example and default dimensions.
2. Record code commit, checkpoint filename, driver, CUDA, GPU, VRAM, RAM, and
   free storage.
3. Run one generation while monitoring peak allocated and reserved memory.
4. Change one variable at a time.
5. Report failures as observed results, not inferred minimums.

## Avoid misleading comparisons

Do not compare a low-resolution single-stage run with a two-stage upscaled
workflow as if they were equivalent. Do not publish a VRAM number without the
precision, resolution, frame count, model, and offload mode.

## Sources

- [Official ComfyUI-LTXVideo prerequisites](https://github.com/Lightricks/ComfyUI-LTXVideo)
- [Official optimization guide](https://github.com/Lightricks/LTX-2/blob/main/packages/ltx-pipelines/docs/optimization.md)
