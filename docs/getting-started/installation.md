# Install LTX-2.3 Locally

Status: source-reviewed against official LTX-2 commit `9377758`; not
independently executed by LTX.dev.

This guide installs the official Python monorepo and downloads the current
distilled checkpoint, spatial upscaler, and Gemma text encoder used by the
upstream quick start.

## Before you begin

- Review the [LTX-2 Community License](https://github.com/Lightricks/LTX-2/blob/main/LICENSE).
- Confirm your organization is permitted to use the model under those terms.
- Install Git, a compatible NVIDIA/CUDA environment, and
  [`uv`](https://docs.astral.sh/uv/).
- Create enough local space for checkpoints, the text encoder, caches, and
  generated media.

## Clone and install

```bash
git clone https://github.com/Lightricks/LTX-2.git
cd LTX-2
uv sync --frozen
```

`uv sync --frozen` uses the repository lockfile. If you intentionally check out
a different release or commit, keep the code, lockfile, and model versions
aligned.

## Authenticate and download

Accept the model terms on Hugging Face, create a read token with gated-repository
access when required, then:

```bash
hf auth login
hf download Lightricks/LTX-2.3 \
  ltx-2.3-22b-distilled-1.1.safetensors \
  ltx-2.3-spatial-upscaler-x2-1.1.safetensors \
  --local-dir models/ltx-2.3
hf download google/gemma-3-12b-it-qat-q4_0-unquantized \
  --local-dir models/gemma-3-12b
```

## Check the CLI

```bash
uv run python -m ltx_pipelines.distilled --help
```

The help command reads the current pipeline interface without starting a
generation. If imports fail, resolve installation and CUDA issues before
downloading additional optional models.

## Common access error

A Hugging Face `401` or `403` commonly means the model terms were not accepted,
the active token lacks gated-repository read access, or the CLI is logged into a
different account.

## Sources

- [Official LTX-2 repository](https://github.com/Lightricks/LTX-2)
- [Official installation guide](https://github.com/Lightricks/LTX-2/blob/main/packages/ltx-pipelines/docs/installation.md)
