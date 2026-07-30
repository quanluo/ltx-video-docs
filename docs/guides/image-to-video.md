# Generate Image-to-Video with LTX-2.3

Status: source-reviewed; not independently executed by LTX.dev.

The official CLI accepts image conditioning as:

```text
--image PATH FRAME_INDEX STRENGTH [CRF]
```

After completing installation, place authorized media at
`assets/reference.jpg`, then:

```bash
uv run python -m ltx_pipelines.distilled \
  --distilled-checkpoint-path models/ltx-2.3/ltx-2.3-22b-distilled-1.1.safetensors \
  --spatial-upsampler-path models/ltx-2.3/ltx-2.3-spatial-upscaler-x2-1.1.safetensors \
  --gemma-root models/gemma-3-12b \
  --image assets/reference.jpg 0 0.8 \
  --seed 21 \
  --prompt "The camera slowly approaches the subject. A soft breeze moves loose fabric and nearby leaves while the lighting direction and scene layout remain consistent." \
  --output-path output/image-to-video.mp4
```

Here, frame index `0` conditions the first frame and `0.8` is an example
strength, not a universal optimum.

## Prompt for motion

The image already supplies appearance and composition. Focus the prompt on:

- subject action;
- environmental motion;
- camera movement;
- what should remain stable;
- chronological sound events.

## Rights and privacy

Use images you own or are allowed to process. Obtain consent for identifiable
people, and do not commit private or customer media to a public repository.

## Sources

- [Official conditioning guide](https://github.com/Lightricks/LTX-2/blob/main/packages/ltx-pipelines/docs/conditioning.md)
- [Official CLI argument definitions](https://github.com/Lightricks/LTX-2/blob/main/packages/ltx-pipelines/src/ltx_pipelines/utils/args.py)
