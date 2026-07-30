# Set Up LTX-2.3 in ComfyUI

Status: source-reviewed against official integration commit `3b9c5cd`; not
independently executed by LTX.dev.

## Install

The official integration recommends Comfy Manager:

1. Open ComfyUI.
2. Open Manager.
3. Select **Install Custom Nodes**.
4. Search for `LTXVideo`.
5. Install the Lightricks package.
6. Restart ComfyUI.

The custom nodes appear under the `LTXVideo` category. Confirm the repository
owner before installing similarly named packages.

## Models

The current official README identifies:

- an LTX-2.3 development or distilled checkpoint;
- Gemma 3 text encoder files;
- spatial upscaler for two-stage graphs;
- temporal upscaler for workflows that use it;
- distilled LoRA for applicable two-stage workflows;
- task-specific IC-LoRAs.

Use the exact current filenames and folder locations from the upstream README.
Do not mix an older workflow with renamed checkpoints without checking its
nodes.

## Start from official workflows

Import one of the versioned files from
`example_workflows/2.3/`. This independent index provides stable links for:

- [single-stage text/image-to-video](https://github.com/quanluo/ltx-comfyui-workflows/tree/main/workflows/01-t2v-i2v-single-stage);
- [two-stage text/image-to-video](https://github.com/quanluo/ltx-comfyui-workflows/tree/main/workflows/02-t2v-i2v-two-stage);
- [two-stage lipdub](https://github.com/quanluo/ltx-comfyui-workflows/tree/main/workflows/03-lipdub-two-stage).

## Import checklist

- Update ComfyUI and the official custom nodes intentionally.
- Resolve missing nodes and model selectors.
- Replace example media with authorized assets.
- Review output paths and dimensions.
- Save an environment-specific copy rather than overwriting the canonical JSON.

## Source

- [Lightricks/ComfyUI-LTXVideo](https://github.com/Lightricks/ComfyUI-LTXVideo)
