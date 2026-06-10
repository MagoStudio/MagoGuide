# In-App Tooltips

[← Quick reference](README.md)

---

> **⚠️ Not authoritative** — This is a verbatim snapshot of the product's in-app tooltip text. Tooltips may be out of date. **Where this page contradicts the rest of the documentation, trust the documentation.** This page exists for support and agent context only.
>
> Placeholders like `{{ frames }}` and `{{ count }}` are filled in at runtime with plan-specific values.

## Payment / subscriptions

| Element                         | Tooltip text                                                                                                                                                 |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Relaxed mode                    | Relaxed rendering, does not require credits, one or two renders at a time. Perfect for experimentation and non-urgent projects                               |
| Relaxed mode plan (frame limit) | Capped at {{ frames }} frames per render                                                                                                                     |
| Pro monthly plan                | 15000 credits ≈ 25 videos (5 sec, 720p, 24fps); 15000 credits ≈ 90 images                                                                                    |
| Studio monthly plan             | {{ count }} credits included monthly                                                                                                                         |
| Credit mode                     | Uses credits, launch as many simultaneous renders as you want; capped at a {{ frames }} frames limit. Ideal for tight deadlines and final production renders |

## Render preview / action buttons

| Element                           | Tooltip text                                                       |
| --------------------------------- | ------------------------------------------------------------------ |
| One video                         | One video                                                          |
| Split view slider                 | Split view slider                                                  |
| Compare two tracks                | Compare two video tracks                                           |
| Compare four tracks               | Compare four video tracks                                          |
| Download frame                    | Download a frame from the video so you can stylize it elsewhere    |
| Fullscreen viewport               | Open fullscreen viewport                                           |
| Download SBS video                | Download side-by-side comparison video                             |
| Download SBS video (disabled)     | Select a single finished render track to download comparison video |
| Toggle settings panel             | Show or hide settings                                              |
| Nav credits                       | Credit Balance, click to add more                                  |
| Like / mark a result              | Mark a result                                                      |
| Add to prompt                     | Paste all description to prompt                                    |
| Use this image                    | Select this image for video generation                             |
| Use this image (disabled)         | You can't use this image directly for the currently selected model |
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
| Prompt                | Describe the transformation you want to apply to the image                                                                                                                                                     |
| Negative prompt       | Describe what you do not want to see in the output. It can be specific elements that appear in your results and that you wish to remove, or general concepts related to quality (low resolution, bad anatomy). |
| Image style reference | Add an image and include it in the scene using the prompt as a guide                                                                                                                                           |

## Img2Img — Kontext

| Element | Tooltip text                                                                                          |
| ------- | ----------------------------------------------------------------------------------------------------- |
| CFG     | Controls how strongly the prompt influences the result. Higher values mean stronger prompt adherence. |
| Seed    | Set a specific seed for reproducibility. Leave empty for random seed.                                 |

## Img2Img — Mago

| Element          | Tooltip text                                                                                                                                                                                                                                                                                                          |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Prompt           | Describe the output result you want in descriptive terms: a group of people standing, oil painting style, etc.                                                                                                                                                                                                        |
| Output size      | Size of the longest side of your target output resolution. If your output is 1920x1080, max size is 1920. Note that the output will automatically respect the aspect ratio of your input video.                                                                                                                       |
| Steps            | Total diffusion steps: more steps result in sharper and more detailed results but slower processing. Lower steps can help achieving less refined styles. Keep the values between 3 and 10.                                                                                                                            |
| Image weight     | Controls how strongly the reference image influences the final output. A higher weight means the generation will more closely match the reference image's style and characteristics, while a lower weight creates a more subtle influence and gives more importance to the prompt.                                    |
| CFG              | The higher the CFG (prompt strength), the more impactful will be the prompt on the stylization process. Make sure to decrease the image weight first to ensure the prompt is taken into account, and try to stay within 2 to 3 for most results.                                                                      |
| Denoise          | Denoise (or diffusion strength) indicates how different the output frame will be from the input frame. A value of 1 means the style is fully applied with no influence from the original image. A value of 0 means no style is applied and you retain the original image. It affects both image and prompt influence. |
| Seed             | Random number that will be the starting point of the generation. Try different values for slight variations.                                                                                                                                                                                                          |
| Depth            | Depth detection in order to determine the distance to each pixel in the frame. Helps in breaking down the frame between background, foreground and specific elements.                                                                                                                                                 |
| Depth strength   | Controls the strength of depth-based control. Higher values apply stronger depth guidance to the generation.                                                                                                                                                                                                          |
| Depth range      | Defines the depth range and start/end points for depth processing. Format: range,start,end                                                                                                                                                                                                                            |
| Depth resolution | Resolution used for controlnet maps. Higher resolutions include more details.                                                                                                                                                                                                                                         |
| Tile             | Breaks down the frame in small tiles and checks if details within the tile are coherent and in line with the prompt. Helps in getting rid of bad details and refine good details.                                                                                                                                     |
| Tile start       | Determines when the ControlNet information is used in the generation process — 0 to 1 means it is active for the whole generation, 0 to 0.8 means that the last 20% will be generated free of the ControlNet's influence.                                                                                             |
| Canny            | A method to detect the edges in an image, turning it into a black—and—white outline. So you can redesign objects while keeping the same outline.                                                                                                                                                                      |
| Canny weight     | Edge detection (i.e. outlines) in order to preserve the shapes and general details of the input video. The weight determines how strong is the influence of the outlines information.                                                                                                                                 |

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

### Drawn Mask (team-only)

The draw-your-own-mask UI is visible to Mago team members only; public users see the "Mask image" upload field above instead.

| Element                       | Text                                                                                                                       |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Prompt tip (with drawn mask)  | Tip: include "in the red area" in your prompt.                                                                             |
| Create / Add mask button      | Add mask                                                                                                                   |
| Edit mask button              | Edit mask                                                                                                                  |
| Editor hint                   | Press and move cursor to start drawing                                                                                     |
| Frame mismatch warning        | The mask was drawn on a different frame. The masked area may not match the current frame. Consider resetting and redrawing. |
| Save gate                     | Save your mask to continue                                                                                                 |

## Img2Img — Qwen / Qwen CR

| Element                                 | Tooltip text                                                                                                                                                                                        |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Prompt (qwen)                           | Give direct instructions as if you were talking to an artist. For example: change the weather to rain and remove the character                                                                      |
| Character image (qwen CR)               | Upload the character you want to use for pose transfer                                                                                                                                              |
| Segment character mask prompt (qwen CR) | Most of the times "character" works well. If it's not the case, you will need to describe more precisely the new character you want to insert, including their accessories.                         |
| Grow mask — segment character           | Increase the mask size used to isolate the new character from its source image. This helps include accessories or elements that extend beyond the main shape, like weapons, unique hairstyles, etc. |
| Erase character mask prompt (qwen CR)   | Most of the times "character" works well. If it's not the case, you will need to describe more precisely the existing person you want to replace, including their accessories.                      |
| Grow mask — erase source                | Increase the mask size used to isolate the person from the video frame. This helps include accessories or elements that extend beyond the main shape, like weapons, unique hairstyles, etc.         |

## Img2Img — Seedream

| Element | Tooltip text                                                                                                            |
| ------- | ----------------------------------------------------------------------------------------------------------------------- |
| Prompt  | Give instructions as if you were talking to an artist. For example: change the weather to rain and remove the character |

## Masking

| Element       | Tooltip text                                                                                                                                                                                                                                                               |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mask mode     | Create a mask using a prompt or segments. Use prompts to select all people in a frame. To select a specific person, use Visual Selection or describe them precisely, for example: person on the left in a yellow sweater. If other options don't work, try Prompt + Points |
| Mode switcher | Prompt: describe the area to mask in natural language. Visual selection: click on the frame to place points that mark the area to include or exclude.                                                                                                                      |

## Inpainting

| Element | Tooltip text                                                             |
| ------- | ------------------------------------------------------------------------ |
| Prompt  | Describe the changes you want the model to apply inside the masked area. |

---

[← Quick reference](README.md)
