# Troubleshooting

[← Workflows & recipes](/guide/workflows-recipes) · [User Guide](/guide/overview) · [Next: Export & compositing →](/guide/export-and-compositing)

---

Common problems and their fixes, grouped by symptom.

- [Flicker](#flicker)
- [Identity drift](#identity-drift)
- [Mask issues](#mask-issues)
- [Face issues (Mago Character)](#face-issues-mago-character)
- [Render time issues](#render-time-issues)
- [Prompt issues](#prompt-issues)

---

## Flicker

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| Flicker at the start of a Style Transfer render | Warm-up too short | Increase Start frame buffer toward 5. |
| Flicker throughout a long render | Chunking issue | Increase Context overlap. Ensure Dynamic reference is on. |
| Flicker in Mago Transform with depth ControlNet | Depth ambiguity in low-contrast scenes | Switch to SoftEdge ControlNet for the same shot. |

## Identity drift

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| Character changes appearance across a long shot (Mago Character) | Pose strength too high or weak reference | Lower Pose strength. Use a more distinctive reference. |
| Character changes across a chunked render | Dynamic reference disabled or context size too large | Enable Dynamic reference. Reduce Context size to 100–120. |
| Closed-source character replacement drifts | Inherent to closed-source models | Switch to Mago Character for stricter identity. Use Elements (Kling 3.0 Motion Control) for multiple reference angles. |

## Mask issues

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| Mask too tight, visible seams in render | Mask too conservative | Increase Expand by 5–10 px. Increase Blur. |
| Pixel shift in unmasked regions of an inpaint result | Compression in video models, not a bug | Download the mask. [Composite externally](/guide/export-and-compositing#mask-export) for pixel-perfect preservation. |

## Face issues (Mago Character)

| Symptom | Fix |
| --- | --- |
| Eyes appear closed | Increase Face crop resolution to 768/1024. Increase Face crop padding. |
| Eyebrows or forehead clipped | Increase Face crop padding to 10–20. |
| Expression doesn't match the source | Lower Face strength. |
| Face too stylized away from intended look | Raise Face strength. |
| Lighting doesn't match the scene | Enable Relight. Increase the value if the correction is weak. |

## Render time issues

| Symptom | Fix |
| --- | --- |
| Render taking many hours | Contact support — this is usually an error. [Refunds](/guide/credits-plans-modes#the-queue) are available. |
| Render time estimate keeps growing | Known issue. Wait for completion or contact support. |
| Renders queuing in Credits mode despite available credits | Likely GPU saturation. Wait, or switch to Relaxed mode for non-urgent work. |

## Prompt issues

| Symptom | Fix |
| --- | --- |
| Mago model not changing the scene much | Verify the prompt is [descriptive, not instruction-based](/guide/prompting-guide). Make the description more specific. |
| Closed-source model changing too much | Add preservation directives: keep the character, composition, lighting, framing. |
| Nano Banana Pro confusing source and reference | Add explicit phrasing: _"use the first image as the reference"_. |
| Output looks generic | Use a stronger reference image. Be more specific in the prompt. |

---

> **🆘 Still stuck?** Use the in-app **Debug Info** panel (**Ctrl + Shift + D**) to copy diagnostic info and share it with support. See [Help & support](/guide/help-and-support).

[← Workflows & recipes](/guide/workflows-recipes) · [User Guide](/guide/overview) · [Next: Export & compositing →](/guide/export-and-compositing)
