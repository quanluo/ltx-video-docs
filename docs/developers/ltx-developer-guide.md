---
title: "LTX Model Developer Guide for LTX.dev Users"
description: "Navigate hosted LTX generation, third-party API integration, local LTX-2.3 pipelines, ComfyUI, training and independent ecosystem resources."
canonical: "https://ltx.dev/developer-guide"
primary_keyword: "LTX developer guide"
reviewed: "2026-07-30"
---

# LTX Model Developer Guide for LTX.dev Users

> **About LTX.dev:** [LTX.dev](https://ltx.dev) is an independent multi-model
> AI video platform.

Choose a path based on the result you need:

| Goal | Start here |
|---|---|
| Generate with LTX in a hosted multi-model workspace | [LTX.dev](https://ltx.dev/studio/text-to-video/ltx) |
| Integrate LTX programmatically | [Independent API guide](ltx-api-guide.md) |
| Run LTX-2.3 locally | [Local generation guide](../guides/local-ai-video-generation.md) |
| Use ComfyUI | [Workflow index](https://github.com/quanluo/ltx-comfyui-workflows) |
| Reuse prompts | [Prompt cookbook](https://github.com/quanluo/ltx-video-prompts) |
| Reproduce examples | [Examples](https://github.com/quanluo/ltx-video-examples) |

## Hosted generation on LTX.dev

LTX.dev provides text-, image-, audio- and video-oriented creation paths and
supports multiple third-party models. Use this route when model comparison and
fast hosted creation matter more than local pipeline control.

## Direct API integration

The provider documentation describes synchronous and asynchronous LTX API
routes. Production applications should keep keys server-side, use internal job
records, poll with backoff and import completed outputs into controlled storage.

## Local LTX-2.3 development

The current LTX-2 monorepo contains core model code, high-level pipelines and
training tools. The documented pipeline set includes text/image-to-video,
distilled inference, keyframe interpolation, audio-to-video and specialized
editing or transformation paths.

The older LTX-Video repository is a legacy route. Pin working deployments and
migrate with reproducibility checks instead of mixing old commands with current
checkpoints.

## Independent ecosystem map

```text
LTX.dev creation workspace
        ↕
Independent guides and comparisons
        ↕
Workflows ↔ Examples ↔ Prompt cookbook
        ↕
Canonical model-provider sources
```

The [LTX.dev ecosystem hub](https://github.com/quanluo/ltx-dev-ecosystem)
connects these resources. Every repository discloses its independent status and
links to canonical provider documentation for model claims.

## Developer reading list

- [Generate locally](../guides/local-ai-video-generation.md)
- [Open-weight Sora alternatives](../comparisons/open-source-sora-alternatives-2026.md)
- [LTX API guide](ltx-api-guide.md)
- [Build an AI video app](build-ai-video-app-with-ltx-api.md)
- [Prompt library](../prompting/ltx-video-prompts-library.md)
- [Cinematic prompts](../prompting/cinematic-ai-video-prompts.md)
- [AI filmmaking workflow](../filmmaking/ai-filmmaking-workflow-with-ltx.md)
- [Create an AI short film](../filmmaking/create-ai-short-films-with-ltx.md)
- [AI video generators for developers](../comparisons/ai-video-generators-for-developers.md)

## Sources

- [LTX.dev](https://ltx.dev)
- [LTX API documentation](https://docs.ltx.io/)
- [LTX-2 official repository](https://github.com/Lightricks/LTX-2)
- [LTX-2.3 model repository](https://huggingface.co/Lightricks/LTX-2.3)
- [Official ComfyUI integration](https://github.com/Lightricks/ComfyUI-LTXVideo)
