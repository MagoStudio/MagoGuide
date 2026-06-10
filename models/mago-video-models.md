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

### Key settings

| Setting | Recommended | Notes |
| --- | --- | --- |
| ControlNet resolution | Default | Higher = more detail, but can inject artifacts. |
| ControlNet strength | Default to start | Higher = closer to source. Lower for more transformation. |
| Use input as control map | Off | Enable only when the source video *is* a depth/pose map. |
| Output size | 1280 (sweet spot) | Max 1620. Higher costs more, may not improve quality. |
| Steps | Default | More = sharper. Lower for rougher styles. |
| Interpolation | Off for detail-critical | On for cheaper, faster renders. |
| Image sequence export | EXR 16-bit for VFX | PNG otherwise. |
| Prompt influence | Default | How closely the model follows the prompt. |
| Color consistency | Default | Reduces color drift across frames. |
| Seed | Any | Same seed + settings reproduces output. |
| Shift / low step accelerator | Default | Faster, slight color drift. |
| Context size | 150 | Frames per chunk. |
| Context overlap | Default | Lower for high movement, higher for static. |
| Start frame buffer | Default | Warm-up frames at render start. |
| Dynamic reference | On | Disable only for very static shots. |

### Prompting

Mago Transform expects **descriptive** prompts. Describe what the output looks like, not what to do.

> **Example**
> ❌ _"Turn this scene into a wooden castle."_
> ✅ _"A medieval wooden castle at dusk with overcast sky, rough-hewn timber walls, slate roof, torches mounted on the gatehouse."_

---

## Mago Style Transfer

**Type: stylization that closely conforms to the source.** Excels at preserving micro-expressions, lip sync, and fine motion while changing visual style. The strongest fit for AI rendering of acted footage where performance must survive the restyle. Also good for relighting and transformations that stay close to the original geometry.

### Key settings

| Setting | Default | Notes |
| --- | --- | --- |
| Output size | 1280 | Same logic as Transform; max 1920. |
| Steps | Default | More for sharper output. |
| **Video input strength** | 0.5 | Below 0.5 often gives better results for shots over 80 frames. Higher locks closer to the source. |
| Interpolation | Off for fine detail | — |
| Image sequence export | EXR 16-bit for VFX | — |
| Shift / low step accelerator | Default | — |
| Context size | 150 | Frames per chunk. |
| Context overlap | Default | Lower for high movement. |
| Start frame buffer | 1 | Max 5. Increase if flicker appears at render start. |
| Dynamic reference | On | Disable for very static shots. |

### Use cases

- **AI character rendering** — preserve actor performance while replacing the visual treatment.
- **Animation restyling** — re-render an existing animation in a different style.
- **Relighting** — change lighting without changing composition.
- **Look development** — explore visual treatments quickly without rebuilding motion.

### Troubleshooting

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| Flicker at render start | Warm-up too short | Increase Start frame buffer toward 5. |
| Output too close to source | Video input strength too high | Lower below 0.5, especially for shots over 80 frames. |
| Lip sync drifts on long shots | Chunking issue | Reduce context overlap; ensure Dynamic reference is on. |
| Style doesn't apply strongly | Reference too generic / input strength too high | Use a more distinctive reference; lower video input strength. |

More: [Troubleshooting](/guide/troubleshooting).

---

## Mago Character

**Type: character replacement.** Replaces the character in any scene with a character from a reference image, with or without the reference's background. The reference doesn't need to match the source framing — a full-body reference can replace a close-up character.

> **🧪 Recommended pre-step** — Go through [Modify Frame](/guide/workspaces/modify-frame) first. Generate a reference closely matching the source pose using GPT Image 2 or Nano Banana Pro, then use that frame as the Mago Character reference. Dramatically more controllable than a generic reference.

### Settings

| Setting | Default | Notes |
| --- | --- | --- |
| Use Image Background | Off | On = use the reference's background. Off = preserve the original. |
| Output size | 1280 | Same logic as Transform. |
| Steps | Default | More for sharper output. |
| Interpolation | Off for detail | — |
| Pose strength | Default | Lower for exact positioning. Higher for stylistic deviation. |
| Face strength | Default | Lower for precise facial replication. Higher for stylized expressions. |
| Face crop resolution | 512 | Increase to 768/1024 for high-res output or if eyes appear closed. |
| Face crop padding | 0–5 | Increase to 10–20 if facial features are cut off. |
| Masking threshold | 0.3 | Lower (0.1–0.2) if detection fails. Higher (0.4–0.6) if too much is detected. |
| Masking prompt | Descriptive | One or two words: _"character"_, _"person"_, _"robot"_. Multi-subject: _"the person in red"_. |
| Grow mask | 10–15 | 15–25 for spiky hair, flowing clothes, large accessories, horns. |
| Relight | Off | Improves lighting consistency between reference and source. Values above 1 strengthen it. |
| Prompt influence | Default | — |
| Seed | Any | Reproducibility. |
| Shift accelerator | Default | Faster, slight color drift. |
| Context size / overlap / dynamic reference | Defaults | Chunked rendering controls. |

### Troubleshooting

| Symptom | Fix |
| --- | --- |
| Eyes appear closed | Increase Face crop resolution to 768/1024. Increase Face crop padding to 10–20. |
| Eyebrows/forehead cut off | Increase Face crop padding. |
| Features (horns, spiky hair) clipped | Increase Grow mask to 15–25. |
| Background detected as the character | Raise Masking threshold to 0.4–0.6. Use a more specific Masking prompt. |
| Character not detected at all | Lower Masking threshold to 0.1–0.2. Use a more general prompt like _"person"_. |
| Lighting doesn't match the scene | Enable Relight; raise the value if too weak. |
| Identity drifts across long shots | Reduce Pose strength variation. Use a more distinctive reference. |

---

## Mago Inpaint

**Type: precise localized edits.** Edits a masked region while leaving the rest intact. Inputs: a source video, a [mask](/guide/workspaces/mask), an image reference showing what the masked region should look like, and a descriptive prompt of the post-edit scene.

### Settings

| Setting | Notes |
| --- | --- |
| Image reference | Shows the desired result for the masked area. |
| Mask input | From the Mask workspace. |
| Invert mask | Swap masked and unmasked regions. |
| Expand mask | Grow the mask outward. |
| Blur mask | Soften mask edges. |
| Prompt | Descriptive — write the scene as it should look *after* the edit. |
| Steps | More for sharper output. |
| Level of detail | Controls fine detail in the generation. |
| CFG | Prompt-following strength. |
| Shift | Controls the frame shift amount for temporal alignment. |
| Context size / overlap | Chunked rendering controls. |
| Image sequence export | PNG or EXR. |

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
