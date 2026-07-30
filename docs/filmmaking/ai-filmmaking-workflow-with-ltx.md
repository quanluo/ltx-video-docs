---
title: "AI Filmmaking Workflow With LTX"
description: "Plan an AI film as versioned shots with prompts, continuity assets, source records, editing and rights review."
canonical: "https://ltx.dev/ai-filmmaking-workflow"
primary_keyword: "AI filmmaking workflow"
reviewed: "2026-07-30"
---

# AI Filmmaking Workflow With LTX

> **About LTX.dev:** [LTX.dev](https://ltx.dev) is an independent multi-model
> AI video platform.

AI filmmaking is manageable when treated as a sequence of shots rather than one
giant prompt. The durable workflow remains familiar: brief, script, shot list,
generation, continuity review, edit, audio mix and rights record.

## 1. Write a production brief

Define the audience, duration, aspect ratio, visual language, characters,
dialogue, distribution and rights constraints.

## 2. Convert the script into shots

| Shot | Purpose | Framing | Camera | Action | Audio |
|---|---|---|---|---|---|
| 01 | Establish place | Wide | Slow push | Market opens | Room tone |
| 02 | Introduce lead | Medium | Static | Lead looks up | Dialogue |

Ask each generation to complete one continuous action.

## 3. Build continuity assets

Approve reference sheets for characters, wardrobe, props, locations, color,
lighting, camera rules and voice direction.

## 4. Generate and review

Start with low-cost composition tests. For each approved take, record:

- model and version;
- prompt and revision;
- input assets;
- duration and resolution;
- status and rights review.

Review whether the story action is readable, identity is stable, camera motion
is usable, audio is aligned and edit handles are sufficient.

## 5. Repair and edit

Where supported, use a retake operation for a flawed range and extend for a
needed continuation. Assemble approved clips in a nonlinear editor. Perform
timing, transitions, color, captions and final audio there.

## 6. Keep a provenance manifest

```json
{
  "shot_id": "SC02_SH04",
  "model": "LTX-2.3",
  "prompt_version": 4,
  "output_asset": "SC02_SH04_take03.mp4",
  "review_status": "approved",
  "rights_review": "complete"
}
```

## Related resources

- [LTX prompt library](../prompting/ltx-video-prompts-library.md)
- [Create an AI short film](create-ai-short-films-with-ltx.md)
- [Prompt cookbook](https://github.com/quanluo/ltx-video-prompts)
- [Generate on LTX.dev](https://ltx.dev/studio/text-to-video)
