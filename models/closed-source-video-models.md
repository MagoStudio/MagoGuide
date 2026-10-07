# Closed-Source Video Models

[← Mago video models](/models/mago-video-models) · [Model catalog](/models/overview) · [Image models →](/models/image-models)

---

Closed-source models are third-party models integrated into Mago. They share several properties:

- **Easier to use** — fewer settings, faster onboarding.
- **Instruction-based prompts** — tell the model what to do, not what the result should look like. ([Why?](/guide/prompting-guide))
- **More expensive** — higher credit cost per render than Mago models.
- **Not frame-perfect** — frame count, frame rate, character identity, and composition can drift.
- **Stricter moderation** — content filters are tighter; VFX content like blood may be blocked.
- **Availability** — not available in Relaxed mode (Pro); available in Unlimited mode (Studio). Otherwise they consume credits.

**Best fit:** short shots, quick results, simple transformations. Less suited to long-form, precision work, or sequences requiring strict consistency.

| Model | Specialty |
| --- | --- |
| [Kling O1 Pro](#kling-o1-pro) | General-purpose transformation |
| [Kling O3 Pro](#kling-o3-pro) | Improved general-purpose |
| [Kling 2.6 Motion Control Pro](#kling-26-motion-control-pro) | Character replacement, lip sync |
| [Kling 3.0 Motion Control](#kling-30-motion-control) | Character replacement with multi-angle Elements |
| [Seedance 2.0](#seedance-20) | Powerful general transformation, audio |
| [Seedance 2.0 Image-to-Video](#seedance-20-image-to-video) | Generate video from a start image |
| [Seedance 2.5 - vid2vid](#seedance-25---vid2vid) | Video transformation with longer clips |
| [Happy Horse 1.0](#happy-horse-10) | General-purpose transformation |

---

## Kling O1 Pro

General-purpose video transformation from Kuaishou.

- **Prompting:** instruction-based. E.g. _"remove the crowd"_, _"change time of day to midnight"_.
- **Image references:** attach up to two reference images, refer to them in the prompt as `@image1` and `@image2`.
- **Elements:** attach an Element — a fixed pair of angles (main + secondary) of the same character or object, referenced in the prompt as `@Element1` — useful for character continuity.

> **Example prompts**
> _"Replace the couch with the couch from @image1."_
> _"Add the character from @image1 walking through the scene."_
> _"Change the weather to a heavy rainstorm."_

## Kling O3 Pro

Improved version of Kling O1 Pro. Same prompt and reference structure. Generally stronger results.

## Kling 2.6 Motion Control Pro

Character-replacement specialist. Strong at lip sync and facial expression preservation.

- **Character reference:** required. A full-body reference works even for close-ups, though [Modify Frame](/guide/workspaces/modify-frame) preparation gives better results.
- **Prompting:** leave the prompt empty at first. Add one only if specific issues need fixing.

> **⚠️ Prompt warning** — Adding a prompt to Kling 2.6 Motion Control Pro often makes the result *worse* than leaving it empty. Try empty first.

## Kling 3.0 Motion Control

Like Kling 2.6 Motion Control Pro but supports **Elements** — a two-angle reference pair (main + secondary) for the same character. Use when you have two reference views of the same character and want more consistent identity across the shot.

## Seedance 2.0

ByteDance model. Powerful general transformation with strong creative range.

- **Prompting:** instruction-based.
- **Source video reference:** refer to it as `@video1`.
- **Image references:** up to 9, as `@image1`–`@image9`.
- **Audio generation:** optional toggle in Advanced — generates sound for the output.
- **Output resolution:** 720p, 1080p (default), or 4K. 4K renders at 1,875 cr/sec.

> **Example prompts**
> _"Use @image1 as the new character. Replace the person in @video1 with this character."_
> _"Remove all people from @video1."_

## Seedance 2.0 Image-to-Video

ByteDance model. Generates video from a start image — no source video required. It is not in the Render Video model dropdown: open the **Global Timeline**, click **Add** in the timeline, then **Generate with AI**. The window is labelled as a prototype feature and may be unstable. Generations appear in the window's **Generations** list, from which you can use one as the input video for a shot.

- **Start image:** required. Defines the first frame of the output video.
- **End image:** optional. When provided, the clip animates towards it — useful for controlled transitions.
- **Prompt:** required. Describe the motion and action you want to see.
- **Duration:** 4–15 seconds (default 5).
- **FPS:** 1–60 (default 24).
- **Resolution:** default 720p. Each option shows its credits per second.
- **Generate audio:** optional toggle, **on** by default.
- **Prompting:** instruction-based.

**Two quality tiers**, switched with the **Standard / Fast** selector at the top of the settings (an info icon compares the two):

| Tier | Speed | Available resolutions | Credits per second |
| --- | --- | --- | --- |
| Standard | Normal | 480p, 720p, 1080p, 4K | 275 / 617 / 1,389 / 3,174 |
| Fast | Faster | 480p, 720p | 220 / 494 |

> **Example prompts**
> _"The character smiles and looks to the left."_
> _"Zoom out slowly to reveal the full scene."_
> _"Rain begins to fall across the landscape."_

## Seedance 2.5 - vid2vid

ByteDance model. Video transformation with reference images and longer clip support.

- **Prompting:** instruction-based. Refer to the source track as `@video1`.
- **Source video reference:** required — the timeline track is the video reference.
- **Image references:** up to 9, as `@image1`–`@image9`.
- **Audio generation:** optional toggle in Advanced — generates sound for the output. Defaults **off**.
- **Output resolution:** 480p, 720p (default), or 1080p. **4K is not available** on Seedance 2.5.
- **Aspect ratio:** Auto (default), 21:9, 16:9, 4:3, 1:1, 3:4 or 9:16.
- **Duration:** 4–30 seconds. Seedance 2.0 caps at 15 seconds.

| Resolution | Credits/sec |
| --- | --- |
| 480p | 252 |
| 720p | 566 |
| 1080p | 1,274 |

Pricing is based on the integer-rounded clip length, not the raw fraction.

> **Example prompts**
> _"Use @image1 as the new character. Replace the person in @video1 with this character."_
> _"Remove all people from @video1."_

## Happy Horse 1.0

Alibaba model. Similar in approach to Kling O1 / O3 Pro.

- **Prompting:** instruction-based.
- **Image references:** up to 5, as `@image1`–`@image5`.
- **Output resolution:** 720p (default) or 1080p.

> **Example prompts**
> _"Change the weather to summer with sunny skies."_
> _"Replace the background with the cityscape from @image1."_

---

[← Mago video models](/models/mago-video-models) · [Model catalog](/models/overview) · [Image models →](/models/image-models)
