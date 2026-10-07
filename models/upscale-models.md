# Upscale Models

[← Image models](/models/image-models) · [Model catalog](/models/overview)

---

Three models (Creative Upscaler, Upscaler and Mago SDR-to-HDR) live in the [Upscale workspace](/guide/workspaces/upscale). Upscaling is almost always a **final pass** — fix the look first, then upscale.

## Creative Upscaler

Partially reconstructs the render at higher resolution. Adds detail, can fix artifacts. Best for restoration work or when more detail is desired.

### Settings

| Setting | Tooltip | Default | Range |
| --- | --- | --- | --- |
| Prompt | Write the prompt here | A detail-oriented upscale prompt is pre-filled | Free text |
| Output size | Size of the longest side of your output. Aspect ratio from original video is always respected. | 1920 | 1280–1920 |
| Steps | Total diffusion steps: more steps result in sharper and more detailed results but slower processing. Lower steps can help achieving less refined styles. | 6 | 3–10 |
| Detail enhancement | Higher values will give AI more freedom to invent elements from the original input. It's good to retrieve quality and/or correct artefacts but could lead to other artefacts in some cases. Keep this value low if your input video is well detailed already. | 0.4 | 0.1–0.9 |
| Interpolation | The interpolation mode renders only one every two frames and use interpolation to fill in the gaps. As a result, the render is quicker and costs less credits. The output might be less detailed in occasions. | Off | On/Off |
| Images format | Choose the format for the image sequence export. EXR formats provide higher quality for professional compositing workflows. | PNG | PNG / EXR 16-bit |
| Tile width count | A higher count will allow for more detailed upscaling, but might create artefacts. A lower count will maintain overall consistency. | 2 | 1–4 |
| Tile height count | A higher count will allow for more detailed upscaling, but might create artefacts. A lower count will maintain overall consistency. | 2 | 1–4 |
| Context size | When doing long renders, the render is split in smaller parts and attached together. The Context size is the number of frames of those parts. | 77 | 9–101 |
| Context overlap | Number of frames that overlap between consecutive context windows. Higher values provide better continuity but slower processing. | 10 | 1–10 |

### Use cases by detail enhancement

- **Light detail enhancement** — 0.3. Adds a small amount of detail to a working render.
- **Mid-level reconstruction** — 0.5. Visible detail while keeping the original mostly intact.
- **Heavy restoration** — 0.7–0.9. For damaged, blurry, or very low-res input. Output deviates noticeably.

## Upscaler

Simple, non-creative upscaler. Clean enlargement without reconstruction. Use when the input is already what you want, just at the wrong size — final-pass output preparation.

### Settings

| Setting | Tooltip | Default | Range |
| --- | --- | --- | --- |
| Upscale factor | Choose the upscaling factor. x2 doubles the resolution, x4 quadruples it. | x2 | x2 / x4 |
| Images format | Choose the format for the image sequence export. EXR formats provide higher quality for professional compositing workflows. | PNG | PNG / EXR 16-bit |

## Mago SDR-to-HDR

Expands brightness and colour range for HDR displays. It does not add detail — pick it when the grade needs HDR headroom. The longest side of the output follows **Output size**. Output is always written as a 16-bit EXR image sequence.

### Settings

| Setting | Tooltip | Default | Range |
| --- | --- | --- | --- |
| Output size | Size of the longest side of your target output resolution. Lower resolutions will give faster and cheaper results, at the expense of quality | 1280 | 512–1920 |
| Context size | When doing long renders, the render is split in smaller parts and attached together. The Context size is the number of frames of those parts | 49 | 24–81 |
| Context overlap | Number of frames where a render part overlaps with the next one. Small values work best for high movement while higher value is better for more static/slow movement | 10 | 0–24 |

Render length runs from 8 to 2000 frames. Available in Relaxed and Unlimited modes.

## Upscaling workflow

1. Validate the look at lower resolution (1280).
2. Render the full clip at 1280.
3. Click **Edit this Render** on the final track.
4. Switch to the Upscale tab.
5. Pick **Upscaler** for predictable enlargement, or **Creative Upscaler** (detail enhancement 0.3–0.5) for reconstruction.
6. **Generate full clip.**

---

[← Image models](/models/image-models) · [Model catalog](/models/overview)
