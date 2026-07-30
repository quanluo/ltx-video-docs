# Troubleshoot LTX-2 CUDA and Memory Errors

Status: source-reviewed diagnostic guide; not independently reproduced.

## 1. Record the environment

Before changing settings, capture:

- LTX repository commit;
- checkpoint filename;
- Python, PyTorch, CUDA, and driver versions;
- GPU model and VRAM;
- system RAM and free storage;
- pipeline or workflow;
- width, height, frames, precision, and offload mode;
- complete error text without tokens or private paths.

## 2. Separate setup failures from out-of-memory failures

An import error, incompatible CUDA extension, missing model, gated-repository
error, and CUDA out-of-memory event require different fixes. Do not reduce
resolution until you know the error is memory-related.

## 3. For a CUDA out-of-memory event

Change one variable at a time:

1. stop other GPU workloads and restart the process;
2. use the distilled pipeline when appropriate;
3. try `--quantization fp8-cast` with a supported setup;
4. try `--offload cpu` with sufficient system RAM;
5. keep `--max-batch-size 1`;
6. reduce resolution or frame count while respecting the CLI constraints;
7. use documented tiling/decoding options for the selected pipeline.

Do not present a successful reduced setting as proof of a universal hardware
minimum.

## 4. For a checkpoint or access error

- confirm the file exists and is not an HTML/error download;
- verify the filename matches the checked-out code and workflow;
- accept gated model terms;
- log into Hugging Face with the intended account and read scope;
- re-download a corrupted or partial file.

## 5. For ComfyUI missing nodes

- confirm `Lightricks/ComfyUI-LTXVideo` is installed;
- restart ComfyUI;
- inspect startup logs;
- update the workflow and extension as a compatible pair;
- avoid replacing missing nodes with similarly named third-party nodes without
  understanding the graph.

## Sources

- [Official pipeline troubleshooting and optimization](https://github.com/Lightricks/LTX-2/tree/main/packages/ltx-pipelines/docs)
- [Official ComfyUI integration](https://github.com/Lightricks/ComfyUI-LTXVideo)
