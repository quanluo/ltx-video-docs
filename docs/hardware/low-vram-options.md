# LTX-2 Low-VRAM Options

Status: source-reviewed; not independently benchmarked.

The official Python CLI provides several controls that can lower peak GPU
memory. They usually trade speed, system RAM, storage traffic, or complexity.

## FP8 cast

```text
--quantization fp8-cast
```

The official CLI describes this as downcasting a BF16 checkpoint during
inference. Hardware and software support still matter.

## FP8 scaled matrix multiplication

```text
--quantization fp8-scaled-mm
```

This is a separate path intended for an FP8 checkpoint and native FP8 support.
Do not use it as a drop-in replacement for `fp8-cast`.

## CPU offload

```text
--offload cpu
```

This keeps transformer weights in system RAM and streams layers to the GPU.
Ensure the machine has enough RAM; expect transfer overhead.

## Disk offload

```text
--offload disk
```

This streams weights from storage when system RAM is also constrained. Storage
capacity and throughput become important and execution may be substantially
slower.

## Control batching

```text
--max-batch-size 1
```

The upstream CLI explains that higher values can reduce transfer overhead but
increase peak memory. Start with `1` when memory is the primary constraint.

## ComfyUI

The official integration documents low-VRAM loader nodes and the ComfyUI
`--reserve-vram` option. Use the current upstream README because node behavior
and supported graphs can change.

## Source-reviewed command

See the independent
[FP8 and CPU-offload example](https://github.com/quanluo/ltx-video-examples/tree/main/examples/02-low-vram-text-to-video).

## Sources

- [Official CLI flags](https://github.com/Lightricks/LTX-2/blob/main/packages/ltx-pipelines/docs/installation.md)
- [Official optimization guide](https://github.com/Lightricks/LTX-2/blob/main/packages/ltx-pipelines/docs/optimization.md)
