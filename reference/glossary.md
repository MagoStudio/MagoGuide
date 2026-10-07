# Glossary

[← Quick reference](/reference/overview)

---

| Term | Meaning |
| --- | --- |
| **Project** | A body of work containing multiple shots. A project exists as long as it has at least one Shot — deleting the last Shot also deletes the project. |
| **Automatic Project Naming** | New projects start named `Untitled` (or `Untitled_NN` when taken). The first video uploaded into a still-default, empty project auto-renames it to the first 10 characters of the video's filename with the extension stripped — e.g. `Project_summer_ep01.mp4` → `Project_su`. Never overrides a user-chosen name, never re-triggers once the project has content, and is skipped during onboarding. |
| **Shot** | A single editable video segment within a project. The unit of rendering. Displayed as one entry in the shots panel and one row in the project timeline. |
| **Render** | An output produced from a source video inside a shot. Appears as a render track. |
| **Track** | A layer attached to a Shot. Two kinds: **Image Track** (the source video) and **Render Track** (a generated output). |
| **Image Track** | The original uploaded video. Always present, one per Shot. Also called "source track". |
| **Render track** | A generated output, stacked below the source in the shot editor. A render track can be **pinned**. |
| **Iterated track** | A render produced using _Edit this Render_ on a previous track. |
| **Pin** | Marking a render track as the representative render for a shot, shown in the Project Timeline. Only finished render tracks can be pinned. |
| **Edit this Render** | Action that uses a render as the input video for the next operation. |
| **Render Crop** | A rectangular region drawn on the video preview that restricts what gets rendered — only the selected area is processed and output. Available on Mago-native models (Transform, Style Transfer, Inpaint, Character, Clean Plate, SDR-to-HDR, the mask engine, and upscalers). Not available on Kling, Seedance, or Happy Horse. |
| **Reuse Settings** | Action that loads a track's settings into the Settings panel. |
| **Project Timeline** | The full sequence of all shots in a project, shown as a horizontal timeline with a playhead, ruler, and zoom controls. Each slot shows the pinned render (or source video if none is pinned). Also called "Global Timeline" in parts of the UI. |
| **Video Model** | An AI model that generates video (e.g. Mago Transform, Mago Style Transfer, Seedance, Kling, Upscaler). |
| **Credits mode** | Pay-per-render mode. Each render consumes credits based on frame count, resolution, and the selected model, with unlimited concurrent renders. The alternative to **Relaxed mode** and **Unlimited mode**. |
| **Relaxed mode** | The Pro plan's rate-limited mode that doesn't spend credits. Covers the Mago video and upscale models and the GPT Image 2 image model; other models are not available in it. Concurrent renders and maximum number of frames are capped unlike in credits mode. |
| **Unlimited mode** | The Studio plan's equivalent of **Relaxed mode**, covering every model (including Seedance, Kling and the other image models) with higher usage limits. |
| **ControlNet** | A conditioning signal (depth, pose, SoftEdge, normal map) that constrains the model's output. |
| **Context size** | Frames per chunk in long renders. |
| **Context overlap** | Frames that overlap between adjacent chunks during chunked rendering. |
| **Dynamic reference** | Setting that regenerates the reference image between chunks. |
| **Auto Prompt** | Mago-generated prompt based on video and reference descriptions. |
| **Descriptive prompt** | A description of the desired result. Required by Mago models. |
| **Instruction prompt** | A directive to the model. Used by closed-source and image models. |
| **Frame-perfect** | Property of Mago models: N input frames produce N output frames, each corresponding to a specific source frame. |
| **Img2Img (Image-to-Image)** | The class of AI models used in the **Modify Frame** tab. Takes a source frame + prompt + settings and outputs an edited frame. Distinct from video-to-video rendering. Examples: GPT Image 2, Nano Banana Pro, Seedream 5.0 Pro — the full selectable list lives in the [Image models catalog](/models/image-models). |
| **Modify Frame** | The UI tab where users apply Img2Img models to individual frames. "Modify Frame" is the product name; "Img2Img" is the technical model category. |
| **Masking** | A workflow that produces a black-and-white mask video to feed into Inpainting. |
| **Inpainting** | A video model (product label: **Mago Inpaint**) that edits only the region defined by a mask video. |
| **Element / Element Pair** | A reference object used by the element-swap Kling models (Kling O1 Pro, Kling 3.0 Motion Control, Kling O3 Pro). Supports two angles: a main reference image and an optional frontal image. |
| **Drawn Mask** | A red mask painted by hand with a brush on a single video frame inside **Modify Frame**, telling **Seedream 5.0 Pro** which region to edit. Available to all users on Seedream 5.0 Pro. Distinct from **Masking** (the mask _video_ used by Inpainting). GPT Image 2 keeps its separate "Mask image" upload field. |
| **Reference Frame** | An image input that acts as a style or content reference for a render. Order-independent — multiple reference frames can be added. |
| **Key Frame** | An image input anchored to a specific frame index in the output, guiding the model at that exact point. |
| **Preset** | Quick-start configuration that sets a model and baseline settings. |
| **Crop** | A rectangular area drawn on a Shot so a render covers only that region of the input video instead of the whole frame. A crop that covers the full frame changes nothing about the output. |
| **EXR** | OpenEXR image format. Used in professional VFX pipelines for high dynamic range and lossless compositing. |
| **Detail enhancement (Creative Upscaler)** | Strength of reconstruction during upscale (formerly "Denoise"). Higher means more model freedom and more added detail. |

---

[← Quick reference](/reference/overview)
