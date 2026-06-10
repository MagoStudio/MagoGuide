# Closed-Source Video Models

[← Mago video models](mago-video-models) · [Model catalog](index) · [Image models →](image-models)

---

Closed-source models are third-party models integrated into Mago. They share several properties:

- **Easier to use** — fewer settings, faster onboarding.
- **Instruction-based prompts** — tell the model what to do, not what the result should look like. ([Why?](../guide/prompting-guide))
- **More expensive** — higher credit cost per render than Mago models.
- **Not frame-perfect** — frame count, frame rate, character identity, and composition can drift.
- **Stricter moderation** — content filters are tighter; VFX content like blood may be blocked.
- **Not available in Relaxed mode** — always consume credits.

**Best fit:** short shots, quick results, simple transformations. Less suited to long-form, precision work, or sequences requiring strict consistency.

| Model | Specialty |
| --- | --- |
| [Kling 01 Pro](#kling-01-pro) | General-purpose transformation |
| [Kling 03 Pro](#kling-03-pro) | Improved general-purpose |
| [Kling 2.6 Motion Control](#kling-26-motion-control) | Character replacement, lip sync |
| [Kling 3.0 Motion Control](#kling-30-motion-control) | Character replacement with multi-angle Elements |
| [Seedance 2.0](#seedance-20) | Powerful general transformation, audio |
| [Happy Horse](#happy-horse) | General-purpose transformation |

---

## Kling 01 Pro

General-purpose video transformation from Kuaishou.

- **Prompting:** instruction-based. E.g. _"remove the crowd"_, _"change time of day to midnight"_.
- **Image references:** attach reference images, refer to them in the prompt as `@image1`, `@image2`, etc.
- **Elements:** attach an Element consisting of multiple angles of the same character or object — useful for character continuity.

> **Example prompts**
> _"Replace the couch with the couch from @image1."_
> _"Add the character from @image1 walking through the scene."_
> _"Change the weather to a heavy rainstorm."_

## Kling 03 Pro

Improved version of Kling 01 Pro. Same prompt and reference structure. Generally stronger results.

## Kling 2.6 Motion Control

Character-replacement specialist. Strong at lip sync and facial expression preservation.

- **Character reference:** required. A full-body reference works even for close-ups, though [Modify Frame](../guide/workspaces/modify-frame) preparation gives better results.
- **Prompting:** leave the prompt empty at first. Add one only if specific issues need fixing.

> **⚠️ Prompt warning** — Adding a prompt to Kling 2.6 Motion Control often makes the result *worse* than leaving it empty. Try empty first.

## Kling 3.0 Motion Control

Like 2.6 Motion Control but supports **Elements** with multiple character angles. Use when you have multiple reference views of the same character (front, side, back) and want consistent identity across the shot.

## Seedance 2.0

ByteDance model. Powerful general transformation with strong creative range.

- **Prompting:** instruction-based.
- **Source video reference:** refer to it as `@video1`.
- **Image references:** up to 9, as `@image1`–`@image9`.
- **Audio generation:** optional toggle in Advanced — generates sound for the output.
- **Output resolution:** 720p or 1080p (1080p is significantly more expensive).

> **Example prompts**
> _"Use @image1 as the new character. Replace the person in @video1 with this character."_
> _"Remove all people from @video1."_

## Happy Horse

Alibaba model. Similar in approach to Kling 01/03 Pro.

- **Prompting:** instruction-based.
- **Image references:** up to 5, as `@image1`–`@image5`.
- **Output resolution:** 720p or 1080p.

> **Example prompts**
> _"Change the weather to summer with sunny skies."_
> _"Replace the background with the cityscape from @image1."_

---

[← Mago video models](mago-video-models) · [Model catalog](index) · [Image models →](image-models)
