# Upscale Models

[← Image models](image-models) · [Model catalog](index)

---

Two upscale models, used in the [Upscale workspace](../guide/workspaces/upscale). Upscaling is almost always a **final pass** — fix the look first, then upscale.

## Creative Upscaler

Partially reconstructs the render at higher resolution. Adds detail, can fix artifacts. Best for restoration work or when more detail is desired.

### Settings

| Setting | Notes |
| --- | --- |
| Prompt | Optional. Describes the desired output. |
| Output size | Native 1080p. |
| **Denoise** | **Most important.** 0.3 for light detail, 0.7–0.8 for heavy restoration. Higher = more model freedom; lower preserves the original more strictly. |
| Steps | More for sharper output. |
| Interpolation | Speed vs. quality trade-off. |
| Tile width count | Higher allows more detail but can create visible tiling. Lower keeps overall consistency. |
| Tile height count | Same logic as width count. |
| Context size / overlap | Standard chunked rendering controls. |
| Negative prompt | Exclude unwanted artifacts. |

### Use cases by denoise

- **Light detail enhancement** — denoise 0.3. Adds a small amount of detail to a working render.
- **Mid-level reconstruction** — denoise 0.5. Visible detail while keeping the original mostly intact.
- **Heavy restoration** — denoise 0.7–0.8. For damaged, blurry, or very low-res input. Output deviates noticeably.

## Upscaler

Simple, non-creative upscaler. Clean enlargement without reconstruction.

- **Upscale factor:** ×2 or ×4 — the only meaningful setting.
- **Use when:** the input is already what you want, just at the wrong size. Final-pass output preparation.

## Upscaling workflow

1. Validate the look at lower resolution (1280).
2. Render the full clip at 1280.
3. Click **Edit this Render** on the final track.
4. Switch to the Upscale tab.
5. Pick **Upscaler** for predictable enlargement, or **Creative Upscaler** (denoise 0.3–0.5) for reconstruction.
6. **Generate full clip.**

---

[← Image models](image-models) · [Model catalog](index)
