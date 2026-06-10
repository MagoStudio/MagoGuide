# Glossary

[← Quick reference](README.md)

---

| Term | Meaning |
| --- | --- |
| **Project** | A body of work containing multiple shots. A project exists as long as it has at least one Shot — deleting the last Shot also deletes the project. |
| **Shot** | A single editable video segment within a project. The unit of rendering. Displayed as one entry in the shots panel and one row in the project timeline. |
| **Render** | An output produced from a source video inside a shot. Appears as a render track. |
| **Track** | A layer attached to a Shot. Two kinds: **Image Track** (the source video) and **Render Track** (a generated output). |
| **Image Track** | The original uploaded video. Always present, one per Shot. Also called "source track". |
| **Render track** | A generated output, stacked below the source in the shot editor. A render track can be **pinned**. |
| **Iterated track** | A render produced using *Edit this Render* on a previous track. |
| **Pin** | Marking a render track as the representative render for a shot, shown in the Project Timeline. Only finished render tracks can be pinned. |
| **Edit this Render** | Action that uses a render as the input video for the next operation. |
| **Reuse Settings** | Action that loads a track's settings into the Settings panel. |
| **Project Timeline** | The full sequence of all shots in a project, shown as a horizontal timeline with a playhead, ruler, and zoom controls. Each slot shows the pinned render (or source video if none is pinned). Also called "Global Timeline" in parts of the UI. |
| **Video Model** | An AI model that generates video (e.g. MagoV3, MagoV4, MagoV5, Seedance, Kling, GPT Image 2, Upscaler). |
| **Credits mode** | Pay-per-render mode. Each render consumes credits based on frame count, resolution, and the selected model. |
| **Relaxed mode** | A per-model frame-range cap that unlocks at Pro/Studio tier, allowing renders longer than Basic's limit. Mago models only. Not the same as "unmetered". |
| **ControlNet** | A conditioning signal (depth, pose, SoftEdge, Canny) that constrains the model's output. |
| **Context size** | Frames per chunk in long renders. |
| **Context overlap** | Frames that overlap between adjacent chunks during chunked rendering. |
| **Dynamic reference** | Setting that regenerates the reference image between chunks. |
| **Start frame buffer** | Warm-up frames added at the start of a render to prevent flickering. |
| **Auto Prompt** | Mago-generated prompt based on video and reference descriptions. |
| **Descriptive prompt** | A description of the desired result. Required by Mago models. |
| **Instruction prompt** | A directive to the model. Used by closed-source and image models. |
| **Frame-perfect** | Property of Mago models: N input frames produce N output frames, each corresponding to a specific source frame. |
| **Img2Img (Image-to-Image)** | The class of AI models used in the **Modify Frame** tab. Takes a source frame + prompt + settings and outputs an edited frame. Distinct from video-to-video rendering. Examples: GPT Image 2, Nano Banana Pro, Seedream — the full selectable list lives in the [Tooltips reference](tooltips.md). |
| **Modify Frame** | The UI tab where users apply Img2Img models to individual frames. "Modify Frame" is the product name; "Img2Img" is the technical model category. |
| **Masking** | A workflow that produces a black-and-white mask video using the SAM3 Mask model, to feed into Inpainting. |
| **Inpainting** | A video model (product label: **Mago Inpaint**) that edits only the region defined by a mask video. |
| **Element / Element Pair** | A reference object used by the element-swap Kling models (Kling O1 Pro, Kling 3.0 Motion Control, Kling O3 Pro). Supports two angles: a main reference image and an optional frontal image. |
| **Drawn Mask** *(coming soon)* | A red mask painted by hand with a brush on a single video frame inside **Modify Frame**, telling **GPT Image 2** which region to edit. Distinct from **Masking** (the SAM3 mask *video* used by Inpainting). Until this feature is available, use the "Mask image" upload field instead. |
| **Reference Frame** | An image input that acts as a style or content reference for a render. Order-independent — multiple reference frames can be added. |
| **Key Frame** | An image input anchored to a specific frame index in the output, guiding the model at that exact point. |
| **Preset** | Quick-start configuration that sets a model and baseline settings. |
| **EXR** | OpenEXR image format. Used in professional VFX pipelines for high dynamic range and lossless compositing. |
| **Denoise (Creative Upscaler)** | Strength of reconstruction during upscale. Higher means more model freedom and more added detail. |

---

[← Quick reference](README.md)
