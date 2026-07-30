---
article_id: 06
status: publish-ready
last_reviewed: 2026-07-30
seo_title: "LTX Workflows: ComfyUI Templates for AI Video"
meta_description: "Download practical LTX‑2.3 ComfyUI workflows for text-to-video, image-to-video, keyframes, audio-led video, retakes, and controlled generation."
slug: "/ltx-workflows"
canonical: "https://ltx.dev/ltx-workflows"
primary_keyword: "LTX workflow"
secondary_keywords:
  - "LTX ComfyUI workflow"
  - "LTX workflow download"
  - "ComfyUI video workflow"
  - "AI video workflow"
  - "LTX-2.3 workflow"
search_intent: "Resource / tutorial"
recommended_length: "2,200–3,000 words plus downloadable assets"
---

# LTX Workflows: ComfyUI Templates and Multi-Model AI Video Paths

> **About LTX.dev:** [LTX.dev](https://ltx.dev) is an independent multi-model
> AI video platform.

LTX workflows turn a repeatable generation process into a file you can inspect, modify, and share. This library organizes practical LTX‑2.3 workflows by task, from a first text-to-video test to multi-stage generation, keyframe control, audio-led video, and selective retakes.

Creators who do not want to manage local nodes and checkpoints can use the
[LTX.dev text-to-video workspace](https://ltx.dev/studio/text-to-video), which
offers a unified interface for several video models. Local ComfyUI workflows and
the hosted multi-model workspace serve different needs and can be used together.

> **Version note:** These workflows target LTX‑2.3. Model files, nodes, and workflow formats can change. Check the version label and dependency list before downloading.

## Quick start

1. Install or update ComfyUI.
2. Open **Templates** and search for **LTX‑2.3**.
3. Start with the official text/image-to-video distilled two-stage template.
4. Use **Download all** to fetch required models.
5. Restart ComfyUI, load a workflow, update the prompt, and run it.

For manual setup and troubleshooting, follow the [LTX ComfyUI tutorial](/ltx-comfyui-tutorial).

## Choose an LTX workflow

| Workflow | Best for | Input | Output | Difficulty | Download |
|---|---|---|---|---|---|
| Text to video, distilled two-stage | First successful generation | Text | Video + synchronized audio | Beginner | [Official 2.3 workflow directory](https://github.com/Lightricks/ComfyUI-LTXVideo/tree/master/example_workflows/2.3) |
| Image to video | Animating a still image | Image + text | Video + synchronized audio | Beginner | [Official 2.3 workflow directory](https://github.com/Lightricks/ComfyUI-LTXVideo/tree/master/example_workflows/2.3) |
| Keyframe interpolation | Moving between designed frames | 2+ images + text | Controlled transition | Intermediate | [Official 2.3 workflow directory](https://github.com/Lightricks/ComfyUI-LTXVideo/tree/master/example_workflows/2.3) |
| Audio to video | Voice- or music-led scenes | Audio + prompt | Video conditioned on audio | Intermediate | [Official 2.3 workflow directory](https://github.com/Lightricks/ComfyUI-LTXVideo/tree/master/example_workflows/2.3) |
| Retake | Regenerating part of a clip | Video + time range + prompt | Revised segment | Advanced | [Official LTX‑2 pipelines](https://github.com/Lightricks/LTX-2) |
| IC-LoRA control | Pose, depth, motion, or guided transformation | Control input + prompt | Controlled video | Advanced | [Official LTX‑2 pipelines](https://github.com/Lightricks/LTX-2) |

## 1. Text-to-video workflow

Use this workflow when you have a scene description and want LTX‑2.3 to generate the visual sequence and synchronized sound together.

### Recommended prompt structure

```text
[Subject and action]. [Location and time].
Camera: [shot size, lens feel, movement].
Lighting: [quality, direction, color].
Audio: [dialogue, ambience, music, sound effects].
Timing: [what happens first, next, and last].
```

### What to customize

- Prompt and negative constraints.
- Duration or frame count.
- Aspect ratio and output resolution.
- Seed for repeatability.
- Fast/distilled versus higher-quality pipeline.
- Upscaling stage and final encoding settings.

### Quality check

- The main action is visible and occurs in the intended order.
- Audio does not contradict the scene.
- The subject remains recognizable across the clip.
- Camera motion is physically plausible.
- No unexpected text, logos, or artifacts appear.

## 2. Image-to-video workflow

Use image-to-video when composition, character design, or product appearance must begin from a controlled still frame.

### Input-image checklist

- Use a clean, sufficiently large source image.
- Avoid ambiguous limbs, reflections, and cropped faces.
- Keep the requested motion compatible with the initial pose.
- Describe motion and timing instead of repeating every visible detail.

### Example motion prompt

```text
The cyclist leans forward and begins pedaling. Grass moves in a light crosswind.
The camera tracks alongside at a steady speed. Natural road ambience and soft tire noise.
```

## 3. Keyframe interpolation workflow

Keyframes provide stronger composition control than a text-only prompt. Use them for product turns, scene transitions, planned camera moves, and transformations.

### Production notes

- Keep lighting and subject identity compatible across keyframes.
- Use fewer, clearer transitions before adding complexity.
- Test at lower cost or faster settings, then rerun the approved setup at target quality.
- Save the seed, workflow JSON, model checksum, and prompt with each approved output.

## 4. Audio-to-video workflow

LTX‑2.3 can condition video on an audio input. This is useful for dialogue, music, podcasts, and sound-driven timing.

### Use cases

- A presenter or character speaking supplied dialogue.
- Music-led edits in which motion follows beats.
- Visualizing an existing voice track.
- Rebuilding a shot while preserving audio timing.

### Review points

- Lip and gesture timing.
- Speaker identity and framing.
- Whether the generated scene respects pauses and emphasis.
- Rights and consent for uploaded voices or music.

## 5. Retake workflow

Retake regenerates a selected time range instead of discarding the whole clip. Use it when the overall generation works but one moment needs correction.

### Retake checklist

1. Define the smallest useful time region.
2. Preserve surrounding context.
3. Describe the desired change precisely.
4. Compare the edit boundary frame by frame.
5. Confirm audio continuity.

## 6. Controlled generation with IC-LoRAs

LTX provides control paths for tasks such as pose, depth, motion tracking, HDR, detail enhancement, camera control, and lip dubbing. Availability and model compatibility vary by release.

> Verify that each LoRA or IC-LoRA explicitly supports LTX‑2.3 before publishing a workflow. LoRAs trained for an earlier latent space may need retraining.

## How the two-stage workflow fits together

```text
Prompt / image / audio
        ↓
Text and conditioning encoders
        ↓
Stage 1 latent generation
        ↓
Spatial upscaler
        ↓
Stage 2 refinement
        ↓
Video + synchronized audio
```

## Installation requirements

The official ComfyUI guide currently recommends:

- ComfyUI.
- Python 3.10 or newer.
- A CUDA-compatible GPU.
- 32 GB or more VRAM for the documented setup.
- 100 GB or more free disk space for models and cache.

Lower-memory methods may exist, but they should be labeled as community or experimental unless verified by LTX. See [LTX GPU requirements](/ltx-gpu-requirements) for tested configurations.

## Troubleshooting

### LTX nodes do not appear

Restart ComfyUI, inspect the console for dependency errors, and confirm that the node package is installed under the expected `custom_nodes` directory.

### Models are missing

Open the workflow dependency panel and verify filenames and folders. Avoid silently renaming checkpoint files because workflow references may break.

### Out-of-memory errors

Use an approved low-VRAM loader, reserve VRAM for the host system, reduce resolution or duration, and close other GPU workloads.

### A workflow opens with red nodes

The workflow may depend on missing custom nodes or a newer package version. Record the workflow version and install only trusted dependencies.

## Download and contribute

- **Primary CTA:** [Download official LTX‑2.3 workflows](https://github.com/Lightricks/ComfyUI-LTXVideo/tree/master/example_workflows/2.3)
- **Secondary CTA:** [Read the LTX ComfyUI tutorial](../comfyui/ltx-comfyui-tutorial.md)
- **Contributor CTA:** Submit a tested workflow with preview, version, hardware, dependencies, seed, and license.

## Continue in LTX.dev

- [Generate video from text](https://ltx.dev/studio/text-to-video)
- [Animate an image](https://ltx.dev/studio/image-to-video)
- [Create video from audio](https://ltx.dev/studio/audio-to-video)
- [Transform an existing video](https://ltx.dev/studio/video-to-video)
- [Browse the independent GitHub workflow index](https://github.com/quanluo/ltx-comfyui-workflows)

## Frequently asked questions

### What is an LTX workflow?

An LTX workflow is a reusable generation pipeline—commonly a ComfyUI JSON graph—that records model loaders, conditioning, sampling, upscaling, decoding, and output steps.

### Does LTX‑2.3 work with ComfyUI?

Yes. LTX maintains ComfyUI integration, custom nodes, templates, and example workflows for LTX‑2.3.

### Where can I download official LTX workflows?

Use the Lightricks `ComfyUI-LTXVideo` repository and the LTX documentation. Prefer version-pinned official files over unverified mirrors.

### How much VRAM does an LTX‑2.3 ComfyUI workflow need?

The official ComfyUI setup guide currently lists a CUDA GPU with 32 GB or more VRAM. Actual usage depends on the checkpoint, quantization, duration, resolution, and offloading.

### Can I use an older LTX workflow with LTX‑2.3?

Not automatically. Nodes, checkpoints, upscalers, and LoRAs may be version-specific. Use a migration guide or rebuild the workflow with LTX‑2.3-compatible assets.

## FAQ schema

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is an LTX workflow?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "An LTX workflow is a reusable generation pipeline, commonly a ComfyUI JSON graph, that records model loading, conditioning, sampling, upscaling, decoding, and output steps."
      }
    },
    {
      "@type": "Question",
      "name": "Does LTX-2.3 work with ComfyUI?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Yes. LTX maintains ComfyUI integration, custom nodes, templates, and example workflows for LTX-2.3."
      }
    },
    {
      "@type": "Question",
      "name": "Where can I download official LTX workflows?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Use the official Lightricks ComfyUI-LTXVideo repository and LTX documentation, and prefer version-pinned files over unverified mirrors."
      }
    },
    {
      "@type": "Question",
      "name": "How much VRAM does an LTX-2.3 ComfyUI workflow need?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The official ComfyUI setup guide currently lists a CUDA GPU with 32 GB or more VRAM. Actual usage depends on checkpoint, quantization, duration, resolution, and offloading."
      }
    },
    {
      "@type": "Question",
      "name": "Can I use an older LTX workflow with LTX-2.3?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Not automatically. Nodes, checkpoints, upscalers, and LoRAs may be version-specific, so use a migration guide or rebuild the workflow with compatible assets."
      }
    }
  ]
}
</script>
```

## Internal links

| Anchor text | Target | Placement |
|---|---|---|
| LTX ComfyUI tutorial | [`../comfyui/ltx-comfyui-tutorial.md`](../comfyui/ltx-comfyui-tutorial.md) | Quick start and troubleshooting |
| install LTX locally | [`../getting-started/install-ltx-video-locally.md`](../getting-started/install-ltx-video-locally.md) | Installation requirements |
| LTX GPU requirements | [`../hardware/ltx-video-gpu-requirements.md`](../hardware/ltx-video-gpu-requirements.md) | VRAM section |
| LTX video prompts | [Prompt cookbook](https://github.com/quanluo/ltx-video-prompts) | Text-to-video workflow |
| LTX ecosystem hub | [Ecosystem](https://github.com/quanluo/ltx-dev-ecosystem) | Contribution section |
| open-source AI video models | [`../comparisons/open-source-ai-video-models.md`](../comparisons/open-source-ai-video-models.md) | Conclusion |

## Image and video requirements

1. Hero: workflow gallery grid, 1600×900, WebP, no baked-in body text.
2. Annotated ComfyUI screenshot showing loader → conditioning → sampler → upscaler → output.
3. One preview loop for each downloadable workflow, compressed MP4/WebM with poster image.
4. Dependency badge graphic: LTX version, ComfyUI version, VRAM tested, last tested date.
5. Alt text must describe the task and visible nodes, not repeat the keyword mechanically.

## Promotion points

### GitHub

- Add this page to the official workflow repository README under “Guides”.
- Require contributor metadata: workflow version, model checksum, hardware, runtime, dependencies, sample output, and license.
- Suggested repository description: `Versioned LTX-2.3 ComfyUI workflows for text-to-video, image-to-video, keyframes, audio-led video, and controlled generation.`

### Reddit

Suggested title: `I organized the official LTX-2.3 ComfyUI workflows by task, dependencies, and VRAM`

Post angle: explain what was tested, disclose affiliation, include two useful screenshots, link to the GitHub repository first, and place the guide link only where subreddit rules permit.

### Community

- ComfyUI Discord: share one tested workflow and invite reproducible bug reports.
- LTX Discord: request maintainers to verify version labels.
- Hugging Face model discussions: link only when answering a relevant setup question.

## Editorial sources

- [Using ComfyUI with LTX](https://docs.ltx.video/open-source-model/integration-tools/comfy-ui)
- [LTX‑2 official repository](https://github.com/Lightricks/LTX-2)
- [ComfyUI-LTXVideo official repository](https://github.com/Lightricks/ComfyUI-LTXVideo)
- [LTX‑2.3 model overview](https://ltx.io/model/ltx-2-3)
