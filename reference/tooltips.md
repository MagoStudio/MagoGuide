# In-App Tooltips

[← Quick reference](/reference/overview)

---

> **⚠️ Not authoritative** — This is a verbatim snapshot of the product's in-app tooltip text. Tooltips may be out of date. **Where this page contradicts the rest of the documentation, trust the documentation.** This page exists for support and agent context only.
>
> Placeholders like `{{ frames }}` and `{{ count }}` are filled in at runtime with plan-specific values.

## Payment / subscriptions

| Element                         | Tooltip text                                                                                                                                                 |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Relaxed mode (plan table)       | Relaxed mode allows for free renders for all Mago models |
| Unlimited mode (plan table)     | Unlimited mode allows for free renders for all Mago models and API models (Seedance, Kling, etc.) |
| Relaxed mode plan (frame limit) | Capped at {{ frames }} frames per render                                                                                                                     |
| Basic monthly plan              | 500 credits ≈ 1 video (5 sec, 720p, 24fps); 500 credits ≈ 3 images                                                                                           |
| Pro monthly plan                | 15000 credits ≈ 25 videos (5 sec, 720p, 24fps); 15000 credits ≈ 90 images                                                                                    |
| Studio monthly plan             | {{ count }} credits included monthly                                                                                                                         |
| Credit mode                     | Uses credits, launch as many simultaneous renders as you want; capped at a {{ frames }} frames limit. Ideal for tight deadlines and final production renders |

> The plan-table tooltips summarise model coverage. The per-model list, including GPT Image 2 in Relaxed mode and the image models in Unlimited mode, is in the [model catalog](/models/overview#availability-by-mode).

## Render preview / action buttons

| Element                           | Tooltip text                                                       |
| --------------------------------- | ------------------------------------------------------------------ |
| One video                         | One video                                                          |
| Split view slider                 | Split view slider                                                  |
| Compare two tracks                | Compare two video tracks                                           |
| Fullscreen viewport               | Open fullscreen viewport                                           |
| Crop toggle                       | Draw a crop to render only that area                               |
| Zoom reset                        | Reset                                                              |
| Download SBS video                | Download side-by-side comparison video                             |
| Download SBS video (disabled)     | Select a single finished render track to download comparison video |
| Download SBS video (cropped)      | Comparison video is not available yet for cropped renders          |
| Toggle settings panel             | Show or hide settings                                              |
| Nav credits                       | Credit Balance, click to add more                                  |
| Like / mark a result              | Mark a result                                                      |
| Add to prompt                     | Paste all description to prompt                                    |
| Use this image                    | Select this image for video generation                             |
| Use this image (disabled)         | You can't use this image directly for the currently selected model |
| Edit this render (disabled)       | This model is no longer available                                  |
| Pin to global preview             | Pin to global preview                                              |
| Pin to global preview (disabled)  | Only finished renders can be pinned                                |
| Re-use settings                   | Re-use settings                                                    |
| Iterate render                    | Edit this render                                                   |
| Download video                    | Download clip                                                      |
| To source                         | Select the source video used to create this render                 |
| To source (deleted)               | Source track has been deleted and is not available anymore         |
| Click to rename                   | Click to rename                                                    |
| Generated img2img preview         | Click to zoom                                                      |
| Create image (img2img)            | Generate a stylized frame (img2img)                                |
| Paste disabled (completed render) | You cannot paste into a completed render                           |

## Debug Info

| Element             | Tooltip text  |
| ------------------- | ------------- |
| Copy app info       | Copy app info |
| Copy section        | Copy section  |
| Copy all debug info | Copy all      |

## Img2Img — common

| Element               | Tooltip text                                                                                                                                                                                                   |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Image style reference | Add an image and include it in the scene using the prompt as a guide                                                                                                                                           |

## Img2Img — Nanobanana / Pro / 2

| Element                   | Tooltip text                                                                                                            |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Prompt                    | Give instructions as if you were talking to an artist. For example: change the weather to rain and remove the character |
| Resolution (Nanobanana 2) | Select the output resolution. Higher resolutions cost more credits                                                      |

## Img2Img — GPT Image 2

| Element    | Tooltip text                                                                                                                                                                          |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Prompt     | Describe the edit you want to apply. You can leave it empty to rely purely on references and mask.                                                                                    |
| Quality    | Result size is 2K. Quality settings will not change output size but will impact the level of detail of the output. Set to High if you need precise details (such as small text, etc.) |
| Mask image | Add your frame with the area you want to edit painted in black. It will be used as the mask reference.                                                                                |

### Drawn Mask (Seedream 5.0 Pro)

The draw-your-own-mask UI is available to all users on **Seedream 5.0 Pro**. GPT Image 2 keeps its separate "Mask image" upload field above.

| Element                       | Text                                                                                                                       |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Prompt tip (with drawn mask)  | Tip: include "in the red area" in your prompt.                                                                             |
| Create / Add mask button      | Add mask                                                                                                                   |
| Edit mask button              | Edit mask                                                                                                                  |
| Editor hint                   | Press and move cursor to start drawing                                                                                     |
| Frame mismatch warning        | The mask was drawn on a different frame. The masked area may not match the current frame. Consider resetting and redrawing. |
| Save gate                     | Save your mask to continue                                                                                                 |

## Img2Img — Qwen Image Edit +

| Element              | Tooltip text                                                                                                                  |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Prompt                | Give direct instructions as if you were talking to an artist. For example: change the weather to rain and remove the character |
| Image style reference | You can use up to nine images to provide more context for the style                                                          |

## Masking

| Element       | Tooltip text                                                                                                                                                                                                                                                               |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mask mode     | Create a mask using a prompt or segments. Use prompts to select all people in a frame. To select a specific person, use Visual Selection or describe them precisely, for example: person on the left in a yellow sweater. If other options don't work, try Prompt + Points |
| Mode switcher | Prompt: describe the area to mask in natural language. Visual selection: click on the frame to place points that mark the area to include or exclude.                                                                                                                      |

## Crop

| Element                            | Text                                                                                                            |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Use this — replaces existing crop  | This shot already has a crop. Using this image will replace it with the crop of the generated image.            |
| Use this — removes existing crop   | This generated image has no crop. Using it will remove the crop currently set on this shot.                     |
| Mask / crop mismatch               | The selected mask was generated with a different crop. Adjust the crop or use a matching mask to continue.      |
| Reference frame / crop mismatch    | The reference frame was generated with a different crop. You need to redo frame.                                |
| Key frame not cropped              | Your reference frame is not cropped, so it will show the full frame instead of just the cropped area.           |

## Inpainting

Field **labels**, plus the tooltips of the mask settings (`invert_mask`, `grow_mask_expand`). Other settings of this model also carry tooltips in the app; they are not listed here.

| Element             | Text                              |
| ------------------- | --------------------------------- |
| Editing prompt      | Editing prompt                    |
| Editing prompt hint | Support your changes with prompt  |
| Mask prompt         | Mask prompt (area to be changed)  |
| Applied mask        | Mask                              |
| Invert              | When enabled, the mask is inverted so the masked area becomes unmasked and vice versa. |
| Expand by           | Expands the mask boundary outward by the specified number of pixels. Increase if the mask is cutting off edges of the detected object. |

---

[← Quick reference](/reference/overview)
