# Image Models (Modify Frame)

[← Closed-source video models](closed-source-video-models) · [Model catalog](README) · [Upscale models →](upscale-models)

---

Image models edit, stylize, or transform a single frame in the [Modify Frame](../guide/workspaces/modify-frame) workspace. **All current image models accept instruction-based prompts.** The most important habit is including preservation directives.

> **💡 Preservation directives** — For most edits, instruct the model to preserve what should *not* change:
> _"Keep the original composition."_ · _"Keep the original outlines."_ · _"Keep the original character intact."_ · _"Do not change the lighting."_ · _"Keep the original framing and proportions."_
> These work with GPT Image 2, Nano Banana 2, and Nano Banana Pro.

---

## GPT Image 2

OpenAI image model. Strong at precise editing; respects original content very well.

- **Output resolution:** 2K.
- **Prompting:** instruction-based.
- **Quality setting:** standard or high. High improves fine detail like small text. Doesn't change output size but increases generation time. Most useful paired with a video model that can preserve that detail.
- **Image style reference:** optional input guiding the visual style.
- **Mask image input:** a painted mask area limiting the edit to a specific region.

> **Use when** — Precision editing of a specific element. Adding/removing objects. Text-sensitive edits (GPT Image 2 handles text better than most models).

## Nano Banana Pro

Strong general-purpose image edit and style transfer model.

- **Output resolution:** up to 2K.
- **Prompting:** instruction-based.
- **Image style reference:** optional.

> **⚠️ Known behavior** — When adding an image reference, Nano Banana Pro may confuse which input is the source and which is the reference. If results are wrong, retry with explicit phrasing: _"use the first image as the reference"_ or _"use the second image as the source"_; if it still fails, invert the images in the prompt.

## Nano Banana 2

- **Output resolution:** 1K, 2K, or 4K.
- **Prompting:** instruction-based.
- **Image style reference:** optional.
- **Best for:** higher-resolution outputs, since it supports 4K natively.

## Legacy & specialized image models

Still available but generally superseded by the models above.

| Model | Notes |
| --- | --- |
| Nano Banana | Lighter, faster predecessor to Nano Banana 2 and Pro. |
| Kontext | Older edit model. CFG range 1.1–15. |
| MAGO (img2img) | Older Mago-internal style transfer model with ControlNet support. |
| Seedream | Original default. Still available for compatibility. |

## Selection guide

| Goal | First choice | Alternative |
| --- | --- | --- |
| Precise edit, one element | GPT Image 2 | Nano Banana Pro |
| Style transfer | GPT Image 2 | Seedream |
| 4K output | Nano Banana 2 | — |
| Mask-based edit | GPT Image 2 (mask input) | Mago Inpaint on video |
| Character preparation for video | GPT Image 2 | Nano Banana 2 |
| Text-sensitive edit | GPT Image 2 | Nano Banana 2 |

---

[← Closed-source video models](closed-source-video-models) · [Model catalog](README) · [Upscale models →](upscale-models)
