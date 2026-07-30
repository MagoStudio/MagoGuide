# Mago Video Models

[← Model catalog](/models/overview) · [Closed-source video models →](/models/closed-source-video-models)

---

Mago video models are built on Mago's own architecture, leveraging open-source foundations. They run on Mago infrastructure and can be deployed in specific territories or in a client's own environment under Enterprise terms.

**All Mago video models share these properties:**

- **Frame-perfect** — N input frames produce N output frames, each corresponding to a specific source frame.
- **Descriptive prompts** — describe the desired result; do not write instructions. ([Why?](/guide/prompting-guide))
- **Settings-rich** — more controls than closed-source alternatives. Harder to learn, more powerful once learned.
- **Available in Relaxed mode** — unmetered usage subject to [plan limits](/guide/credits-plans-modes#relaxed-mode).
- **Confidential** — not used to train models. Project data stays private.

| Model | Type | Use it when… |
| --- | --- | --- |
| [Mago Transform](#mago-transform) | Full transformation | You want to substantially change a scene |
| [Mago Style Transfer](#mago-style-transfer) | Conforming stylization | You must preserve performance / lip sync while restyling |
| [Mago Character](#mago-character) | Character replacement | You're swapping the character in a shot |
| [Mago Inpaint](#mago-inpaint) | Localized edits | You're editing one masked region |

---

## Mago Transform

**Type: full transformation.** Use when the goal is to substantially change a scene — turn a city into a forest, day into night with new geography, an actor into a creature. Driven mostly by an initial keyframe or reference frame, with the prompt playing a major role.

### ControlNets for Mago Transform

ControlNets are conditioning signals that constrain how far the model can deviate from the source. They're one of the most important Mago Transform settings.

| ControlNet | Use when |
| --- | --- |
| **Depth** | You want to preserve the original composition and volumes as closely as possible. Hardest to transform under — the model is locked to the original 3D structure. |
| **SoftEdge** | You want more interpretive freedom, especially for scenes with movement. The model can reshape outlines. |
| **Pose** | You want to track a humanoid character's pose closely. For human-centric shots. |
| **Depth + Pose** | You want both character tracking and environmental fidelity. Most controlled, hardest to transform under. |

> **💡 ControlNet decision** — Start with **Depth** if the camera is static and structure matters. Switch to **SoftEdge** for creative freedom or significant camera movement. Use **Pose** for character-focused shots.

### Settings

| Setting | Tooltip | Default | Range |
| --- | --- | --- | --- |
| Output size | Size of the longest side of your target output resolution. Lower resolutions will give faster and cheaper results, at the expense of quality. | 1280 | 512–1620 |
| Steps | Total number of diffusion steps. More steps give sharper, more detailed results, but take longer to render; very high values can over-sharpen the image or push colors too far. | 4 | 4–10 |
| Interpolation | Renders every other frame and fills in the rest. Cuts render time and allows larger context size, at the cost of quality in some cases. | Off | On/Off |
| Image sequence export | Output format for the render as an image sequence. | PNG | PNG / EXR 16-bit |
| Context size | When doing long renders, the render is split in smaller parts and attached together. The Context size is the number of frames of those parts. | 120 | 24–160 |
| Context overlap | Number of frames where a render part overlaps with the next one. Small values work best for high movement while higher value is better for more static/slow movement. | 4 | 0–24 |
| Dynamic reference | When enabled, a new reference image is generated between render parts, which allows for better transitions for high movement videos. For static/slow movement videos, disabling it ensures better consistency. | Off | On/Off |
| Prompt strength | Higher values will enforce more strongly the prompt instructions. A value too high might result in visual artifacts. | 1 | 0.5–6 |
| Color consistency | Help the render to follow the color palette of the stylized frame reference. Increase the value if the render color is too different from the frame reference and/or if there is some color drifting. Decrease the value when you work on dynamic scenes. | 1 | 0–1 |
| Shift | Higher values favor overall composition and large shapes; lower values favor fine detail such as detailed textures. | 2 | 1–10 |
| Accelerator | Higher values accelerate render times for faster renders. Might reduce detail and color fidelity at high values. | 1 | 0–1 |
| Seed | Random number that will be the starting point of the generation. Try different values for slight variations. | 42 | — |

### ControlNet settings

| Setting | Tooltip | Default | Range |
| --- | --- | --- | --- |
| Control map selection | Determines what information is extracted from the input video and used to guide the render. Pose follows body movement; Depth captures 3D space; Normal Map captures surface detail; SoftEdge preserves contours. Combined modes apply two maps at once for stronger control, at the cost of longer preprocessing. | Depth | Depth / Normal Map (beta) / Pose / SoftEdge (beta) / Pose+Depth |
| ControlNet resolution | Resolution used for controlnet maps. Higher resolutions include more details. | 1280 | 512–1280 (Normal Map 512–768) |
| ControlNet strength | How strongly the control map guides the generation. Lower values give the model more creative freedom; higher values keep the output closer to the input control map information. | 1 | 0.1–1.5 |
| Pose strength (Pose+Depth only) | Controls the strength of video attention consistency enforcement. Higher values provide more temporal consistency. | 0.5 | 0.1–1.5 |
| Facemesh | Enables higher fidelity of face expressions and lip-sync. | Off | On/Off |
| Input video is a control map | Enable this option if the video you uploaded is a control map. It will then be used directly as the source control map for the generation. | Off | On/Off |

### Prompting

Mago Transform expects **descriptive** prompts. Describe what the output looks like, not what to do.

> **Example**
> ❌ _"Turn this scene into a wooden castle."_
> ✅ _"A medieval wooden castle at dusk with overcast sky, rough-hewn timber walls, slate roof, torches mounted on the gatehouse."_

---

## Mago Style Transfer

**Type: stylization that closely conforms to the source.** Excels at preserving micro-expressions, lip sync, and fine motion while changing visual style. The strongest fit for AI rendering of acted footage where performance must survive the restyle. Also good for relighting and transformations that stay close to the original geometry.

### Settings

| Setting | Tooltip | Default | Range |
| --- | --- | --- | --- |
| Output size | Size of the longest side of your target output resolution. Lower resolutions will give faster and cheaper results, at the expense of quality. | 1280 | 512–1920 |
| Steps | Total number of diffusion steps. More steps give sharper, more detailed results, but take longer to render; very high values can over-sharpen the image or push colors too far. | 4 | 4–20 |
| Level of detail | Controls the level of detail of the generation. A higher number will help render finer details and textures. | 40 | 20–80 |
| Video input strength | The higher the value, the higher the fidelity to the original input video will be (shape, facial expressions, lip-sync, outlines, etc.). | 0.5 | 0.3–1 |
| Interpolation | Renders every other frame and fills in the rest. Cuts render time and allows larger context size, at the cost of quality in some cases. | Off | On/Off |
| Image sequence export | Output format for the render as an image sequence. | PNG | PNG / EXR 16-bit |
| Context size | When doing long renders, the render is split in smaller parts and attached together. The Context size is the number of frames of those parts. | 150 | 24–300 |
| Context overlap | Number of frames where a render part overlaps with the next one. Small values work best for high movement while higher value is better for more static/slow movement. | 10 | 0–24 |
| Dynamic reference | When enabled, a new reference image is generated between render parts, which allows for better transitions for high movement videos. For static/slow movement videos, disabling it ensures better consistency. | On | On/Off |
| Prompt strength | Higher values will enforce more strongly the prompt instructions. A value too high might result in visual artifacts. | 1 | 0.5–6 |
| Color consistency | Help the render to follow the color palette of the stylized frame reference. Increase the value if the render color is too different from the frame reference and/or if there is some color drifting. Decrease the value when you work on dynamic scenes. | 0 | 0–1 |
| Shift | Higher values favor overall composition and large shapes; lower values favor fine detail such as detailed textures. | 8 | 1–10 |
| Accelerator | Higher values accelerate render times for faster renders. Might reduce detail and color fidelity at high values. | 1 | 0–1 |
| Seed | Random number that will be the starting point of the generation. Try different values for slight variations. | 42 | — |

### Use cases

- **AI character rendering** — preserve actor performance while replacing the visual treatment.
- **Animation restyling** — re-render an existing animation in a different style.
- **Relighting** — change lighting without changing composition.
- **Look development** — explore visual treatments quickly without rebuilding motion.

### Troubleshooting

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| Flicker at render start | Weak stylized first frame | Use a cleaner, higher-contrast stylized first frame; keep Dynamic reference on. |
| Output too close to source | Video input strength too high | Lower it below 0.5, especially for long shots. |
| Lip sync drifts on long shots | Chunking issue | Reduce context overlap; ensure Dynamic reference is on. |
| Style doesn't apply strongly | Reference too generic / input strength too high | Use a more distinctive reference; lower video input strength. |

More: [Troubleshooting](/guide/troubleshooting).

---

## Mago Character

**Type: character replacement.** Replaces the character in any scene with a character from a reference image, with or without the reference's background. The reference doesn't need to match the source framing — a full-body reference can replace a close-up character.

> **🧪 Recommended pre-step** — Go through [Modify Frame](/guide/workspaces/modify-frame) first. Generate a reference closely matching the source pose using GPT Image 2 or Nano Banana Pro, then use that frame as the Mago Character reference. Dramatically more controllable than a generic reference.

Two modes, switched by the **Use image background** toggle: **off** = replace the character while keeping the original background (v4.0); **on** = also bring in the reference image's background (v4.1). The **masking settings** below appear only in replacement mode (Use image background off).

### Settings

| Setting | Tooltip | Default | Range |
| --- | --- | --- | --- |
| Use image background | When enabled, the background of the image reference will be used for the render. | Off | On/Off |
| Output size | Size of the longest side of your target output resolution. Lower resolutions will give faster and cheaper results, at the expense of quality. | 1280 | 512–1620 |
| Steps | Total number of diffusion steps. More steps give sharper, more detailed results, but take longer to render; very high values can over-sharpen the image or push colors too far. | 5 | 4–30 |
| Interpolation | Renders every other frame and fills in the rest. Cuts render time and allows larger context size, at the cost of quality in some cases. | Off | On/Off |
| Image sequence export | Output format for the render as an image sequence. | PNG | PNG / EXR 16-bit |
| Pose strength | Defines how strongly the original character pose is used in the final output. A value too high might create artefacts. | 1 | 0.5–1.5 |
| Face strength | Defines how strongly the original character facial expressions are used in the final output. A value too high might generate a stiffer face. | 1 | 0.5–1.5 |
| Grow face mask | Margin around the face area added to the face detection to include potentially overlapping facial features of the input video character (big eyebrows, long chin, etc.). | 50 | 0–200 |
| Masking threshold (replacement mode) | Sensitivity level of the mask. The lower the threshold, the more "inclusive" the mask: good to replace complex characters, but can lead to the inclusion of unwanted elements. | 0.3 | 0.1–0.9 |
| Masking prompt (replacement mode) | Text description of the character you want to replace. Being more precise helps selecting the right character in multi-character scenes. | character | free text |
| Grow Mask (replacement mode) | Number of pixels added to the mask borders. Increase this value to include elements that are sticking out of the main shape of the original character (pointy hair, accessories, etc.). | 10 | 0–50 |
| Prompt strength | Higher values will enforce more strongly the prompt instructions. A value too high might result in visual artifacts. | 1 | 0.5–6 |
| Relight | How strongly the new character's lighting is changed to match the background. High = new character lighting fully adapts to the environment; low = it keeps the lighting from the character reference. | 1 | 0–1.5 |
| Color correction | Turn it on if the colors of your render become too saturated and/or over-exposed. | Off | On/Off |
| Accelerator | Higher values accelerate render times for faster renders. Might reduce detail and color fidelity at high values. | 1 | 0–1.5 |
| Shift | Higher values favor overall composition and large shapes; lower values favor fine detail such as detailed textures. | 5 | 1–10 |
| Context size | When doing long renders, the render is split in smaller parts and attached together. The Context size is the number of frames of those parts. | 300 | 0–600 |
| Context overlap | Number of frames where a render part overlaps with the next one. Small values work best for high movement while higher value is better for more static/slow movement. | 1 | 0–10 |
| Dynamic reference | When enabled, a new reference image is generated between render parts, which allows for better transitions for high movement videos. For static/slow movement videos, disabling it ensures better consistency. | Off | On/Off |
| Seed | Random number that will be the starting point of the generation. Try different values for slight variations. | 42 | — |

### Troubleshooting

| Symptom | Fix |
| --- | --- |
| Facial features clipped (big eyebrows, long chin) | Increase Grow face mask. |
| Features (horns, spiky hair) clipped | Increase Grow Mask (replacement mode). |
| Background detected as the character | Raise Masking threshold. Use a more specific Masking prompt (replacement mode). |
| Character not detected at all | Lower Masking threshold toward 0.1. Use a more general Masking prompt like _"person"_ (replacement mode). |
| Lighting doesn't match the scene | Raise Relight toward 1.5. |
| Identity drifts across long shots | Keep Face strength near 1.0. Use a more distinctive reference. |

---

## Mago Inpaint

**Type: precise localized edits.** Edits a masked region while leaving the rest intact. Inputs: a source video, a [mask](/guide/workspaces/mask), an image reference showing what the masked region should look like, and a descriptive prompt of the post-edit scene.

### Inputs

| Input | Description |
| --- | --- |
| Image reference | Shows the desired result for the masked area. |
| Mask | Created in the [Mask workspace](/guide/workspaces/mask). |
| Prompt | Descriptive — write the scene as it should look *after* the edit. |

### Mask settings

| Setting | Tooltip | Default | Range |
| --- | --- | --- | --- |
| Invert Mask | When enabled, the mask is inverted so the masked area becomes unmasked and vice versa. | Off | On/Off |
| Expand mask by | Grow the mask outward by this value (px) in all directions. | 0 | 0–50 |
| Blur mask | Blur the mask border, softening the transition between the edited and preserved regions. | 0 | 0–50 |

### Advanced settings

| Setting | Tooltip | Default | Range |
| --- | --- | --- | --- |
| Steps | Total diffusion steps: more steps result in sharper and more detailed results but slower processing. | 6 | 4–20 |
| Level of detail | Controls the level of detail of the generation. A higher number will help render finer details and textures. | 40 | 20–80 |
| Interpolation | The interpolation mode renders only one every two frames and uses interpolation to fill in the gaps. Quicker, costs less credits, and might be less flickery. The output might be less detailed on occasion. | On | On/Off |
| Context size | When doing long renders, the render is split in smaller parts and attached together. The Context size is the number of frames of those parts. | 80 | 80–100 |
| Context overlap | Number of frames where a render part overlaps with the next one. Small values work best for high movement while higher value is better for more static/slow movement. | 1 | 1–24 |
| Dynamic reference | When enabled, a new reference image is generated between render parts, which allows for better transitions for high movement videos. For static/slow movement videos, disabling it ensures better consistency. | On | On/Off |
| Prompt strength | The CFG is the prompt strength. Higher values will enforce more strongly the prompt instructions. A value too high might result in visual artefacts. | 1 | 0.5–6 |
| Color consistency | Tints the render so its colors match a reference image. Useful for keeping a consistent look across shots. | 0 | 0–1 |
| Shift | Controls the frame shift amount for temporal alignment. Higher values increase the search range for matching features. | 5 | 1–10 |
| Image sequence export | Choose the format for the image sequence export. EXR formats provide higher quality for professional compositing workflows. | PNG | PNG / EXR 16-bit |

### Prompting

> **Example**
> ❌ _"Replace the teacup with a water bottle."_
> ✅ _"A water bottle is on the table."_
> Mago models don't take instructions — describe what the result should look like.

### Pixel-perfect preservation

Mago Inpaint (like most video models) doesn't operate in pure pixel space — unmasked regions can shift slightly (brightness, color, minor texture) due to compression. For pixel-perfect preservation:

1. Download the mask from the Mask workspace.
2. Render the Mago Inpaint result.
3. In Nuke, After Effects, or Fusion, composite the inpainted result onto the original source using the downloaded mask.

This guarantees unmasked pixels are identical to the source. See [Export & compositing](/guide/export-and-compositing).

---

[← Model catalog](/models/overview) · [Closed-source video models →](/models/closed-source-video-models)
