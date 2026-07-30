---
seo_title: "LTX-2.3 ComfyUI Tutorial: Text and Image to Video"
meta_description: "Set up LTX-2.3 in ComfyUI, load official text-to-video and image-to-video workflows, install models, write prompts, generate, and troubleshoot."
slug: "/ltx-comfyui-tutorial"
canonical: "https://ltx.dev/ltx-comfyui-tutorial"
primary_keyword: "LTX ComfyUI tutorial"
secondary_keywords:
  - "LTX ComfyUI workflow"
  - "ComfyUI LTX-2.3"
  - "ComfyUI text to video"
  - "ComfyUI image to video"
  - "LTX workflow download"
search_intent: "How-to / resource"
funnel_stage: "Activation"
content_type: "Technical tutorial"
suggested_schema:
  - "HowTo"
  - "FAQPage"
---

# LTX-2.3 ComfyUI Tutorial: Generate Video and Audio Step by Step

> **Independent resource:** This guide is published by
> [LTX.dev](https://ltx.dev), an independent multi-model AI video platform. It
> is not affiliated with or endorsed by Lightricks or ComfyUI.

ComfyUI is one of the most accessible ways to run an editable LTX-2.3 workflow. It represents generation as a graph of connected nodes, so you can inspect the model, prompt, latent setup, sampler, decoder, audio path, and output.

LTX-2.3 can generate synchronized audio and video. Official workflows cover text-to-video, image-to-video, controls, and advanced audio-video tasks. This tutorial starts with an official template instead of building a graph from scratch.

## What You Need

- an updated ComfyUI installation or supported ComfyUI Desktop/Cloud environment;
- a compatible GPU and enough storage for model assets;
- access to the LTX-2.3 Hugging Face files;
- the current LTX workflow template;
- permission to use the model and input media.

Read the [LTX GPU requirements guide](https://ltx.dev/ltx-gpu-requirements) before downloading large files.

## Native Nodes or the LTX Custom Node Package?

Current ComfyUI documentation describes native LTX support, while LTX's own advanced 2.3 workflows may use the `ComfyUI-LTXVideo` package.

Use this rule:

- start with the current built-in ComfyUI template when it supports your target workflow;
- use the official `Lightricks/ComfyUI-LTXVideo` workflows when the LTX documentation specifies custom nodes or advanced features;
- never mix workflow files, checkpoints, and nodes from different LTX versions without checking compatibility.

## Step 1: Update ComfyUI

Update ComfyUI before loading the workflow. If a template or core node is missing, your stable/Desktop build may not yet include the latest release.

For self-managed installations, use the official update method for your installation type. For Desktop or Cloud, check the current release channel.

Open ComfyUI and confirm that the Workflow Template browser is available.

## Step 2: Load an Official LTX Workflow

### Option A: Built-in template

1. Open **Workflow**.
2. Select **Browse Workflow Templates**.
3. Open **Video**.
4. Choose an LTX-2 or LTX-2.3 text-to-video or image-to-video template.
5. Follow the model-download prompt.

### Option B: Official LTX workflow JSON

1. Open the official `Lightricks/ComfyUI-LTXVideo` repository.
2. Select a workflow from the `example_workflows/2.3` directory.
3. Download the JSON.
4. Drag the JSON file onto the ComfyUI canvas.
5. Open the workflow overview and identify missing nodes or models.

Do not download workflow JSON files from an unknown source without inspection.

## Step 3: Install Missing Nodes

If the workflow uses official LTX custom nodes:

1. open ComfyUI Manager;
2. search for the official LTX node package;
3. verify the publisher and repository URL;
4. install it;
5. restart ComfyUI;
6. reload the workflow and check for missing nodes.

The canonical custom-node repository is
[`Lightricks/ComfyUI-LTXVideo`](https://github.com/Lightricks/ComfyUI-LTXVideo).

## Step 4: Download LTX-2.3 Model Files

A standard LTX-2.3 workflow may request:

| File | Typical ComfyUI folder |
|---|---|
| `ltx-2.3-22b-dev.safetensors` or distilled checkpoint | `ComfyUI/models/checkpoints/` |
| `ltx-2.3-22b-distilled-lora-384-1.1.safetensors` | `ComfyUI/models/loras/` |
| `comfy_gemma_3_12B_it.safetensors` | `ComfyUI/models/text_encoders/` |
| LTX spatial upscaler | folder specified by the workflow/docs |

The exact list changes by workflow. Use ComfyUI's model prompt or the official LTX guide instead of copying files into guessed directories.

Restart or refresh model lists after downloading.

## Step 5: Understand the Core Workflow

A basic text-to-video graph usually contains these logical stages:

### Model and text encoder loading

Nodes load the LTX checkpoint, companion LoRA if used, and Gemma text encoder.

### Prompt encoding

The positive prompt describes the scene and sound. A negative prompt may be present depending on the workflow.

### Empty audio-video latent

The workflow defines frame count, dimensions, and frame rate. These settings determine duration and affect memory use.

### Sampling

The sampler denoises the latent using settings matched to the checkpoint. Distilled workflows may use a small number of steps and CFG around 1; do not copy those values to a non-distilled workflow without documentation.

### Decoding and output

Video and audio are decoded and combined into the final media file.

## Step 6: Write an LTX Prompt

Official guidance favors a detailed, chronological paragraph. Include:

1. the main action;
2. specific movement and gestures;
3. subject appearance;
4. environment;
5. camera position and movement;
6. lighting and color;
7. dialogue, music, ambience, or sound effects;
8. changes over time.

Example:

> A baker places a warm loaf on a wooden counter and brushes flour from her hands. Steam rises into soft morning light as the camera slowly moves from a medium shot to a close-up of the crust. A quiet café hum fills the room, with ceramic cups clinking in the background.

Keep the sequence coherent. One shot with clear timing is a better first test than several locations and cuts.

## Step 7: Set Duration, Resolution, and Seed

Start with the defaults in the official template.

- **Frames and FPS** determine duration.
- **Width and height** affect composition and memory.
- **Seed** helps reproduce a generation.
- **Steps and CFG** must match the workflow and checkpoint.

Save the workflow before changing settings. Increase duration or resolution only after the default run succeeds.

## Step 8: Generate the First Video

1. Verify that every model loader resolves to an installed file.
2. Check for red or missing nodes.
3. enter the prompt;
4. click **Queue Prompt** or the current run control;
5. watch the console for memory or model-loading errors;
6. preview the final video and audio;
7. save the workflow JSON and output metadata.

Record the ComfyUI version, workflow source, node versions, checkpoint, seed, and hardware.

## Image-to-Video Workflow

For image-to-video:

1. load an image-to-video template;
2. upload a rights-cleared reference image;
3. describe motion and sound rather than repeating every static detail;
4. keep the first test short;
5. review identity preservation, unwanted camera movement, and edge artifacts.

Example motion prompt:

> The subject looks toward the window and smiles slightly as a breeze moves the curtains. The camera remains steady. Soft city ambience and distant traffic.

## Troubleshooting

### The workflow has missing nodes

Update ComfyUI. Confirm whether the template expects native nodes or the official LTX package. Restart after installation.

### A model filename is red or unavailable

Check the model version, exact filename, and folder. Refresh the model list. Do not rename files unless the documentation permits it.

### CUDA out-of-memory error

Close other GPU tasks, use an official lower-memory path, reduce duration or resolution, and enable documented offloading. See the [GPU guide](https://ltx.dev/ltx-gpu-requirements).

### The result has no audio

Confirm that the selected workflow is an audio-video workflow, not video-only. Check audio VAE and output nodes and verify that your media player supports the output codec.

### The video does not follow the prompt

Simplify the shot, make actions chronological, remove conflicting instructions, and specify camera and sound directly.

### Generation is unexpectedly slow

Confirm that nodes are running on the intended GPU, model files are not reloading for every run, and the chosen workflow is not a full-quality pipeline when a distilled preview path was intended.

## Save and Share a Reproducible Workflow

Before sharing:

- remove private file paths and API keys;
- include a preview, prompt, seed, model filenames, node versions, and license;
- credit the original workflow;
- state the required VRAM based on measurement;
- link to the official model and node repositories;
- provide a changelog when updating the JSON.

## Frequently Asked Questions

### Does LTX-2.3 work with ComfyUI?

Yes. ComfyUI offers LTX support, and Lightricks publishes LTX-2.3 workflows and nodes for supported use cases.

### Where can I download LTX ComfyUI workflows?

Use the ComfyUI template library or the official `Lightricks/ComfyUI-LTXVideo` repository. Match the workflow directory to LTX-2.3.

### Which LTX-2.3 checkpoint should I use?

Use the checkpoint named by the selected official workflow. Full and distilled checkpoints have different behavior and sampler settings.

### How do I add audio to an LTX video?

Choose an LTX-2.3 audio-video workflow. The model can generate synchronized audio and video jointly; a video-only template will not add audio automatically.

### Why are LTX nodes missing?

Your ComfyUI build may be outdated, the workflow may require the official LTX custom node package, or some nodes may have failed to import.

## Start with an Official Workflow

Begin with a default text-to-video template, make one successful generation, and save a reproducible copy before customizing the graph.

**CTA:** [Browse LTX workflows](https://ltx.dev/ltx-workflows) or [learn what LTX-2.3 can do](https://ltx.dev/ltx-video-guide).

## FAQPage JSON-LD

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Does LTX-2.3 work with ComfyUI?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Yes. ComfyUI offers LTX support, and Lightricks publishes LTX-2.3 workflows and nodes for supported use cases."
      }
    },
    {
      "@type": "Question",
      "name": "Where can I download LTX ComfyUI workflows?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Use the ComfyUI template library or the official Lightricks/ComfyUI-LTXVideo repository, matching the workflow to LTX-2.3."
      }
    },
    {
      "@type": "Question",
      "name": "Why are LTX nodes missing?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The ComfyUI build may be outdated, the workflow may require the official LTX custom node package, or nodes may have failed to import."
      }
    }
  ]
}
```

## Internal links

| Anchor | Target |
|---|---|
| What is LTX Video? | `/ltx-video-guide` |
| LTX GPU requirements | `/ltx-gpu-requirements` |
| install LTX locally with Python | `/install-ltx-video` |
| LTX workflow library | `/ltx-workflows` |
| open-weight AI video generators | `/open-source-ai-video-generator` |

## Visual brief

1. Full workflow screenshot with numbered callouts.
2. Model placement table rendered as a simple directory graphic.
3. Prompt anatomy diagram.
4. Before/after image-to-video example with permission and disclosure.
5. Troubleshooting decision tree: missing node vs missing model vs OOM vs no audio.

## Promotion hooks

- r/ComfyUI: share the workflow JSON, preview, exact versions, measured VRAM, and a concise lesson learned.
- GitHub: publish the workflow with a versioned README and license; submit to curated lists only where contributions are welcome.
- LTX Discord: ask for technical review before broad promotion.
- YouTube: record the first successful run in real time, with chapter links and exact versions in the description.

## Sources and review notes

- https://docs.comfy.org/tutorials/video/ltx/ltx-2-3
- https://docs.ltx.io/open-source-model/integration-tools/comfy-ui
- https://github.com/Lightricks/ComfyUI-LTXVideo
- https://huggingface.co/Lightricks/LTX-2.3
- Workflow and node behavior is sourced from the current official ComfyUI and
  LTX documentation linked above.
