---
title: "LTX API Guide: Text, Image and Audio to Video"
description: "An independent guide to Lightricks' LTX API, including synchronous and asynchronous generation, job polling and production integration."
canonical: "https://ltx.dev/ltx-api-guide"
primary_keyword: "LTX API"
reviewed: "2026-07-30"
---

# LTX API Guide

> **About LTX.dev:** [LTX.dev](https://ltx.dev) is an independent multi-model
> AI video platform.

The public LTX API documentation describes text-to-video, image-to-video and
audio-to-video generation with synchronized audio, plus Retake and Extend
operations. It offers a synchronous route for simple experiments and an
asynchronous route for production jobs.

## Choose sync or async

Use synchronous generation for a short proof of concept. Use asynchronous
generation when an application needs job state, retries, controlled timeouts
and background processing.

The production flow is:

```text
client → application backend → LTX async job
  ↑              ↓                 ↓
  └── status/result ← storage ← poller
```

## Keep authentication on the server

Create a key in the provider console and store it in a server-side secret
manager. Never expose it in browser JavaScript, mobile binaries, screenshots or
public repositories.

## Submit and track a job

Copy endpoint names, model identifiers and request fields from the
[live API reference](https://docs.ltx.io/). A robust application should:

1. validate the user, prompt and input assets;
2. create an internal generation record;
3. submit the provider job;
4. save the provider job ID;
5. poll with backoff until completion or failure;
6. import the result into controlled storage;
7. return a signed application URL.

Do not depend indefinitely on a provider output URL. Save the result according
to your own retention and user-deletion policy.

## Production controls

- idempotency for repeated user actions;
- per-user duration, resolution and spending limits;
- a maximum polling deadline;
- structured errors without secrets;
- a reconciliation worker for interrupted jobs;
- moderation, consent and acceptable-use enforcement;
- input URL validation to prevent server-side request forgery.

## Use LTX.dev or integrate directly

Use [LTX.dev](https://ltx.dev/studio/text-to-video/ltx) when the goal is to
create with supported models in one hosted workspace. Integrate the provider API
directly when building a separate application that needs programmatic control.

## Related resources

- [Build an AI video application](build-ai-video-app-with-ltx-api.md)
- [AI video generators for developers](../comparisons/ai-video-generators-for-developers.md)
- [LTX model developer guide](ltx-developer-guide.md)
- [Independent examples](https://github.com/quanluo/ltx-video-examples)

## Sources

- [LTX API documentation](https://docs.ltx.io/)
- [LTX API pricing](https://docs.ltx.io/pricing)
- [LTX.dev LTX model workspace](https://ltx.dev/studio/text-to-video/ltx)
