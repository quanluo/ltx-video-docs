# LTX Video Documentation and Multi-Model Learning Hub

> **Independent platform notice:** Maintained by
> [LTX.dev](https://ltx.dev), an independent multi-model AI video platform.
> Not affiliated with or endorsed by Lightricks or any other model provider.
> Model names and trademarks belong to their respective owners.

Practical guides for multi-model AI video creation, LTX open-model workflows,
hardware, prompting, comparisons, and production decisions.

[Explore LTX.dev](https://ltx.dev) ·
[Compare video models](https://ltx.dev/studio/text-to-video) ·
[Ecosystem hub](https://github.com/quanluo/ltx-dev-ecosystem) ·
[Workflows](https://github.com/quanluo/ltx-comfyui-workflows) ·
[Examples](https://github.com/quanluo/ltx-video-examples) ·
[Prompts](https://github.com/quanluo/ltx-video-prompts)

## Published guides

| # | Guide | Continue on LTX.dev |
|---:|---|---|
| 1 | [Best open-weight AI video generators in 2026](docs/guides/open-source-ai-video-generators-2026.md) | [Open the model workspace](https://ltx.dev/studio/text-to-video) |
| 2 | [What is LTX Video?](docs/getting-started/what-is-ltx-video.md) | [Generate with LTX 2.3](https://ltx.dev/studio/text-to-video/ltx) |
| 3 | [Install LTX‑2.3 locally](docs/getting-started/install-ltx-video-locally.md) | [Use hosted generation](https://ltx.dev/studio/text-to-video/ltx) |
| 4 | [LTX‑2.3 GPU and VRAM requirements](docs/hardware/ltx-video-gpu-requirements.md) | [Use hosted generation](https://ltx.dev/studio/text-to-video/ltx) |
| 5 | [LTX‑2.3 ComfyUI tutorial](docs/comfyui/ltx-comfyui-tutorial.md) | [Open the workflow platform](https://ltx.dev/studio/text-to-video) |
| 6 | [LTX workflow library and multi-model paths](docs/workflows/ltx-workflow-library.md) | [Choose a video task](https://ltx.dev/studio/text-to-video) |
| 7 | [AI video model benchmark: published specs](docs/benchmarks/ai-video-model-benchmark.md) | [Compare available models](https://ltx.dev/studio/text-to-video) |
| 8 | [LTX.dev vs Runway](docs/comparisons/ltx-dev-vs-runway.md) | [Try the multi-model workspace](https://ltx.dev/studio/text-to-video) |
| 9 | [LTX.dev vs Kling AI](docs/comparisons/ltx-dev-vs-kling.md) | [Generate with Kling 3.0](https://ltx.dev/studio/text-to-video/kling) |
| 10 | [Open-source and open-weight video models](docs/comparisons/open-source-ai-video-models.md) | [Generate with LTX 2.3](https://ltx.dev/studio/text-to-video/ltx) |
| 11 | [Generate AI video locally with LTX](docs/guides/local-ai-video-generation.md) | [Use hosted LTX 2.3](https://ltx.dev/studio/text-to-video/ltx) |
| 12 | [Open-weight Sora alternatives in 2026](docs/comparisons/open-source-sora-alternatives-2026.md) | [Compare hosted models](https://ltx.dev/studio/text-to-video) |
| 13 | [Independent LTX API guide](docs/developers/ltx-api-guide.md) | [Create with LTX 2.3](https://ltx.dev/studio/text-to-video/ltx) |
| 14 | [Build an AI video generator app](docs/developers/build-ai-video-app-with-ltx-api.md) | [Open the model workspace](https://ltx.dev/studio/text-to-video) |
| 15 | [Practical LTX video prompt library](docs/prompting/ltx-video-prompts-library.md) | [Browse prompts](https://ltx.dev/prompts) |
| 16 | [Cinematic AI video prompts](docs/prompting/cinematic-ai-video-prompts.md) | [Try a prompt](https://ltx.dev/prompts) |
| 17 | [AI filmmaking workflow](docs/filmmaking/ai-filmmaking-workflow-with-ltx.md) | [Create a video](https://ltx.dev/studio/text-to-video) |
| 18 | [Create an AI short film](docs/filmmaking/create-ai-short-films-with-ltx.md) | [Open text to video](https://ltx.dev/studio/text-to-video) |
| 19 | [AI video generators for developers](docs/comparisons/ai-video-generators-for-developers.md) | [Compare models](https://ltx.dev/studio/text-to-video) |
| 20 | [LTX model developer guide for LTX.dev users](docs/developers/ltx-developer-guide.md) | [Generate with LTX 2.3](https://ltx.dev/studio/text-to-video/ltx) |

## Documentation map

```text
docs/
├── getting-started/
├── hardware/
├── guides/
├── workflows/
├── benchmarks/
├── comparisons/
├── prompting/
├── comfyui/
├── developers/
├── filmmaking/
├── training/
├── troubleshooting/
└── migration/
```

## Use the ecosystem

```text
LTX.dev model workspace
        ↕
Documentation and comparisons
        ↕
Workflows ↔ Examples ↔ Prompt cookbook
        ↕
Canonical upstream model sources
```

- Start with the [model comparison](docs/benchmarks/ai-video-model-benchmark.md).
- Choose a [text](https://ltx.dev/studio/text-to-video),
  [image](https://ltx.dev/studio/image-to-video),
  [audio](https://ltx.dev/studio/audio-to-video), or
  [video](https://ltx.dev/studio/video-to-video) task.
- Use the [workflow index](https://github.com/quanluo/ltx-comfyui-workflows)
  for local ComfyUI paths.
- Adapt a recipe from the
  [prompt cookbook](https://github.com/quanluo/ltx-video-prompts).
- Reproduce local integrations with
  [video examples](https://github.com/quanluo/ltx-video-examples).

## Editorial standard

Every guide distinguishes LTX.dev platform behavior from third-party model
behavior. Version, pricing, duration, resolution, license, and provider claims
are dated and linked to their sources. Source-based comparisons do not invent
visual-quality scores.

## License

Original repository documentation is available under the [MIT License](LICENSE).
Linked models, projects, trademarks, and media retain their own terms.
