---
seo_title: "How to Install LTX-2.3 Locally: Complete Setup Guide"
meta_description: "Install LTX-2.3 locally with the official Python repository. Follow the environment, model download, first-run, validation, and troubleshooting steps."
slug: "/install-ltx-video"
canonical: "https://ltx.dev/studio/text-to-video"
primary_keyword: "install LTX Video"
secondary_keywords:
  - "LTX installation guide"
  - "run LTX locally"
  - "LTX-2.3 setup"
  - "LTX Python installation"
search_intent: "How-to / technical"
funnel_stage: "Activation"
content_type: "Technical tutorial"
suggested_schema:
  - "HowTo"
  - "FAQPage"
---

# How to Install LTX-2.3 Locally: Complete Setup Guide

> **About LTX.dev:** [LTX.dev](https://ltx.dev) is an independent multi-model
> AI video platform.

LTX-2.3 can run locally through Lightricks' official Python repository. A local setup gives developers control over model files, workflows, inputs, and deployment, but it requires large downloads and a compatible GPU environment.

This guide follows the current `Lightricks/LTX-2` codebase. Do not use an older `LTX-Video` installation command for LTX-2.3 unless the official documentation specifically directs you to it.

## Before You Install

The official LTX-2.3 Python codebase has been tested with:

- Python 3.12 or newer;
- CUDA newer than 12.7;
- PyTorch around version 2.7;
- the `uv` Python package and environment manager.

You also need:

- a supported NVIDIA GPU for the documented CUDA path;
- enough GPU memory for the selected pipeline;
- substantial system RAM and free storage;
- Git and Git LFS or Hugging Face download tooling;
- acceptance of the licenses for LTX-2.3 and Gemma 3.

See [LTX GPU requirements](https://ltx.dev/studio/text-to-video) before downloading the full checkpoint.

> The requirements above can change. Pin the repository commit used for production and check its README before installation.

## Step 1: Install Prerequisites

Install current NVIDIA drivers, a compatible CUDA environment, Git, and `uv`.

Verify the basic tools:

```bash
nvidia-smi
git --version
uv --version
```

If `nvidia-smi` does not detect the GPU, fix the driver environment before continuing.

## Step 2: Clone the Official LTX-2 Repository

```bash
git clone https://github.com/Lightricks/LTX-2.git
cd LTX-2
```

For a repeatable production build, record the commit:

```bash
git rev-parse HEAD
```

Do not run unreviewed scripts from forks when model credentials or private media are present.

## Step 3: Create the Python Environment

The official quick start uses:

```bash
uv sync --frozen
source .venv/bin/activate
```

The frozen lock file helps install the dependency versions tested by the repository maintainers.

Confirm that PyTorch can see CUDA:

```bash
python -c "import torch; print(torch.__version__); print(torch.cuda.is_available()); print(torch.cuda.get_device_name(0) if torch.cuda.is_available() else 'No CUDA GPU')"
```

Expected result: CUDA availability should be `True` for the documented NVIDIA path.

## Step 4: Download the Required Model Files

The official LTX-2 repository currently points to the LTX-2.3 Hugging Face collection. A standard two-stage pipeline may require:

- one LTX-2.3 checkpoint;
- a spatial upscaler;
- the current distilled LoRA used by the pipeline;
- the Gemma 3 text encoder assets.

Example checkpoint options include:

- `ltx-2.3-22b-dev.safetensors`;
- `ltx-2.3-22b-distilled-1.1.safetensors`.

The full checkpoint file is tens of gigabytes. The complete set of assets requires more space than the checkpoint alone.

Download the files from the official
[LTX-2.3 Hugging Face collection](https://huggingface.co/Lightricks/LTX-2.3)
and pass their local paths to the pipeline command below. The repository accepts
explicit paths, so the files do not need to be placed in an invented fixed
directory.

## Step 5: Choose a Pipeline

The official repository contains multiple pipelines. Its recommended production-quality text/image-to-video path is the two-stage pipeline with upsampling.

Before running a command:

1. open `packages/ltx-pipelines/README.md`;
2. select text-to-video or image-to-video;
3. copy the example command for the pinned commit;
4. update only the model paths, prompt, output path, and documented generation options.

Official two-stage text-to-video command pattern:

```bash
python -m ltx_pipelines.ti2vid_two_stages \
  --checkpoint-path /path/to/ltx-2.3-checkpoint.safetensors \
  --distilled-lora /path/to/distilled-lora.safetensors 0.8 \
  --spatial-upsampler-path /path/to/spatial-upscaler.safetensors \
  --gemma-root /path/to/gemma \
  --prompt "A practical test prompt" \
  --output-path ./outputs/first-ltx-video.mp4
```

## Step 6: Run a Small Validation Job

For the first run:

- use the lowest documented resolution and duration for the selected pipeline;
- close other GPU-heavy applications;
- keep the default scheduler and pipeline settings;
- use a simple prompt with one subject and one action;
- save logs and the exact command.

Example prompt:

> A ceramic cup sits on a wooden table as morning light moves slowly across the surface. The camera makes a gentle dolly-in. Quiet room tone and distant birds.

Confirm that:

- the process completes without an out-of-memory error;
- the file opens and contains both video and expected audio;
- frame dimensions and duration match the request;
- no NaN or missing-model errors appear in logs.

## Step 7: Record a Reproducible Environment

Save:

- Git commit SHA;
- model filenames and hashes;
- Python and PyTorch versions;
- GPU model and driver;
- pipeline name and command;
- prompt and seed;
- output resolution, frame rate, and duration;
- measured peak GPU memory and wall-clock time.

This information turns a one-off demo into a testable deployment.

## Common LTX Installation Problems

### CUDA is not available

Check the NVIDIA driver, CUDA-compatible PyTorch build, and whether the process can access the GPU. A locally installed CUDA toolkit does not guarantee that the active PyTorch build supports it.

### The process runs out of GPU memory

Use a documented lower-memory or quantized path, reduce resolution or duration, enable documented offloading, and close other GPU processes. Do not assume a smaller output makes every stage fit; model weights and text encoders also consume memory.

### A checkpoint cannot be found

Confirm the exact filename and path. LTX-2 and LTX-2.3 assets are not interchangeable by name alone. Verify that the pipeline supports the selected checkpoint.

### Hugging Face returns an access error

Log in, accept any required license terms, and verify the repository name. Some companion assets may have separate access conditions.

### `uv sync --frozen` fails

Check the Python version and platform requirements. Avoid casually upgrading individual packages because the lock file is intended to preserve compatibility.

### Output is slow

First determine whether the run is using the expected GPU and precision. Record model loading separately from generation time. Test a documented distilled or quantized pipeline before changing multiple settings at once.

## A Simpler Alternative: ComfyUI

If your goal is interactive creation rather than Python integration, ComfyUI may be faster to validate. It provides visual workflows and can help download the assets required by a template.

Continue with the [LTX ComfyUI complete tutorial](https://ltx.dev/studio/text-to-video).

## Frequently Asked Questions

### What repository should I use for LTX-2.3?

Use the official `https://github.com/Lightricks/LTX-2` repository for the current Python inference and training packages.

### What Python version does LTX-2.3 require?

The current official model card states Python 3.12 or newer for the tested codebase. Verify the pinned repository because requirements can change.

### How large is the LTX-2.3 download?

The main 22B checkpoint is roughly 46 GB, and a working pipeline may also need an upscaler, LoRA, text encoder, and caches. Reserve substantially more storage than the checkpoint size.

### Can I install LTX-2.3 on Windows?

The documented Python path centers on CUDA tooling. Windows users commonly use
a supported ComfyUI package or WSL2; consult the current upstream compatibility
notes for the selected route.

### Can I run LTX-2.3 on a Mac?

Do not assume the older LTX-Video MPS instructions apply to LTX-2.3. The current official LTX-2.3 Python requirements emphasize CUDA. Use a hosted path unless an official or internally tested MPS workflow is available.

## Next Step

Once the first validation job succeeds, save the environment details and move the workflow into version control.

**CTA:** [Download an approved LTX workflow](https://ltx.dev/ltx-workflows) or [open the LTX ComfyUI tutorial](https://ltx.dev/studio/text-to-video).

## FAQPage JSON-LD

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What repository should I use for LTX-2.3?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Use the official Lightricks/LTX-2 repository for the current Python inference and training packages."
      }
    },
    {
      "@type": "Question",
      "name": "What Python version does LTX-2.3 require?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The current official model card states Python 3.12 or newer for the tested codebase. Verify the pinned repository before installation."
      }
    },
    {
      "@type": "Question",
      "name": "How large is the LTX-2.3 download?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The main 22B checkpoint is roughly 46 GB, and a pipeline may also need an upscaler, LoRA, text encoder, and caches."
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
| LTX ComfyUI tutorial | `/ltx-comfyui-tutorial` |
| open-weight AI video generators | `/open-source-ai-video-generator` |
| LTX workflows | `/ltx-workflows` |

## Visual brief

1. Installation flow: prerequisites → clone → environment → models → pipeline → validation.
2. Screenshot of the pinned official repository and commit.
3. Model-file checklist with sizes captured on publication day.
4. Terminal screenshots must redact usernames, tokens, local paths, and private media.

## Promotion hooks

- GitHub: propose a documentation link through the official repository's accepted contribution process; do not open promotional issues.
- Reddit: publish a tested install log including commit, GPU, VRAM, duration, and failure fixes.
- Stack Overflow: answer only real questions with self-contained solutions; disclose affiliation and avoid link-only answers.
- Discord/ComfyUI: share a minimal reproducible environment, not a generic homepage link.

## Sources and review notes

- https://github.com/Lightricks/LTX-2
- https://huggingface.co/Lightricks/LTX-2.3
- https://docs.ltx.io/open-source-model/getting-started/quick-start
- Pipeline command source:
  https://github.com/Lightricks/LTX-2/tree/main/packages/ltx-pipelines
- Download only from canonical repositories and verify hashes when upstream
  publishes them.
