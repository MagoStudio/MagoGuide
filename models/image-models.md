# Image Models (Modify Frame)

[← Closed-source video models](/models/closed-source-video-models) · [Model catalog](/models/overview) · [Upscale models →](/models/upscale-models)

---

Image models edit, stylize, or transform a single frame in the [Modify Frame](/guide/workspaces/modify-frame) workspace. Models accept a source frame plus an instruction-based prompt. Separately, script projects have a **Reference image model** dropdown that generates reference images from a prompt alone (see [Script project reference images](#script-project-reference-images)).

> **💡 Preservation directives** — For most edits, instruct the model to preserve what should _not_ change:
> _"Keep the original composition."_ · _"Keep the original outlines."_ · _"Keep the original character intact."_ · _"Do not change the lighting."_ · _"Keep the original framing and proportions."
> These work with GPT Image 2, Nano Banana 2, Nano Banana Pro, and Seedream 5.0 Pro.

---

## GPT Image 2

OpenAI image model. Strong at precise editing; respects original content very well.

- **Output resolution:** 2K.
- **Prompting:** instruction-based.
- **Quality setting:** medium (default) or high. High improves fine detail like small text. Doesn't change output size but increases generation time. Most useful paired with a video model that can preserve that detail.
- **Image style reference:** optional input guiding the visual style (up to 9 images).
- **Mask image input:** add your frame with the area you want to edit painted in black; it is used as the mask reference.
- **Availability:** Relaxed and Unlimited modes.

> **Use when** — Precision editing of a specific element. Adding/removing objects. Text-sensitive edits (GPT Image 2 handles text better than most models).

## Nano Banana Pro

Strong general-purpose image edit and style transfer model.

- **Prompting:** instruction-based.
- **Image style reference:** optional (up to 9 images).
- **Availability:** Unlimited mode only — not available in Relaxed mode.

> **⚠️ Known behavior** — When adding an image reference, Nano Banana Pro may confuse which input is the source and which is the reference. If results are wrong, retry with explicit phrasing: _"use the first image as the reference"_ or _"use the second image as the source"_; if it still fails, invert the images in the prompt.

## Nano Banana 2

- **Output resolution:** 0.5K, 1K, 2K (default), or 4K. Higher resolutions cost more credits.
- **Prompting:** instruction-based.
- **Image style reference:** optional (up to 9 images).
- **Best for:** higher-resolution outputs, since it supports 4K natively.
- **Availability:** Unlimited mode only — not available in Relaxed mode.

## Seedream 5.0 Pro

ByteDance image editing model. Strong at stylization and instruction-based transforms.

- **Cost:** 120 credits per image.
- **Reference images:** up to 9 reference images accepted as style or content guidance.
- **Availability:** Unlimited mode only — not available in Relaxed mode.
- **Drawn mask:** paint a red mask by hand on the frame (from a video source) to limit the edit to a specific region. Tip: include "in the red area" in your prompt.

> **Use when** — Style transfer or visual transformation where you want a different aesthetic look while preserving overall composition.

## Qwen Image Edit +

Alibaba image editing model.

- **Prompting:** instruction-based.
- **Reference images:** up to 9, providing style/content context.
- **Availability:** Unlimited mode only — not available in Relaxed mode.

> **Use when** — General instruction-based edits or stylization, similar territory to Seedream 5.0 Pro.

---

## Script project reference images

Script projects have a **Reference image model** dropdown that generates reference images from a prompt alone — no source frame needed. It is separate from the Modify Frame model list.

| Option | Notes |
| --- | --- |
| Seedream 5 Pro | Default. |
| GPT Image 2 | |
| Nano Banana 2 | |

Reference images generated from the script project always use Credits mode.

> **Use when** — You need a generated reference image from scratch — a character design, background, or scene that doesn't yet exist in your project.

---

## Selection guide

| Goal                            | First choice                         | Alternative                                   |
| ------------------------------- | ------------------------------------ | --------------------------------------------- |
| Precise edit, one element       | GPT Image 2                          | Nano Banana Pro                               |
| Style transfer                  | GPT Image 2                          | Seedream 5.0 Pro                              |
| 4K output                       | Nano Banana 2                        | —                                             |
| Mask-based edit                 | GPT Image 2 (mask input)             | Mago Inpaint on video                         |
| Character preparation for video | GPT Image 2                          | Nano Banana 2                                 |
| Text-sensitive edit             | GPT Image 2                          | Nano Banana 2                                 |

---

[← Closed-source video models](/models/closed-source-video-models) · [Model catalog](/models/overview) · [Upscale models →](/models/upscale-models)
