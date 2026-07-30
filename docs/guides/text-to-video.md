# Generate Text-to-Video with LTX-2.3

Status: source-reviewed; not independently executed by LTX.dev.

Use the official distilled pipeline for a compact starting command. Complete
the [installation guide](../getting-started/installation.md) first.

```bash
uv run python -m ltx_pipelines.distilled \
  --distilled-checkpoint-path models/ltx-2.3/ltx-2.3-22b-distilled-1.1.safetensors \
  --spatial-upsampler-path models/ltx-2.3/ltx-2.3-spatial-upscaler-x2-1.1.safetensors \
  --gemma-root models/gemma-3-12b \
  --seed 42 \
  --prompt "A small ferry leaves a foggy harbor at dawn. The camera watches from the pier as ropes fall, the engine starts, and the vessel moves into gray water. Gulls call above the quiet motor and the harbor bell rings once." \
  --output-path output/text-to-video.mp4
```

## Choose the pipeline deliberately

The official selection guide distinguishes several paths:

- `distilled` for the fastest upstream inference path;
- `ti2vid_two_stages` as the recommended production-quality path;
- `ti2vid_two_stages_hq` for the alternate higher-quality sampler;
- `ti2vid_one_stage` primarily for education and prototyping.

Use `--help` on the selected module. Do not assume flags are identical across
releases or pipelines.

## Write the prompt chronologically

Describe the main action, visible movement, subject appearance, environment,
camera behavior, lighting, then sound/dialogue. A coherent sequence is easier
to interpret than disconnected quality terms.

## Output and claims

The pipeline writes an MP4 to the selected path. Exact duration, dimensions,
runtime, VRAM, visual quality, and audio behavior depend on defaults, model
revision, parameters, and hardware. No independent benchmark is asserted here.

## Related

- [Runnable command reference](https://github.com/quanluo/ltx-video-examples/tree/main/examples/01-text-to-video-cli)
- [Official pipeline selection](https://github.com/Lightricks/LTX-2/blob/main/packages/ltx-pipelines/docs/pipeline-selection.md)
