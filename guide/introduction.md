# Introduction & Product Philosophy

[← User Guide](/guide/overview) · [Next: Getting Started →](/guide/getting-started)

---

Mago Studio is an AI video transformation and stylization platform built for professional studios.

**Mago is not a video generation product.** It does not create videos from scratch or from text alone. Mago *transforms and stylizes existing footage*. That single fact shapes every choice in the product — and understanding it will make everything else click.

## The five core principles

These principles inform how the product is built and how you get the best results from it.

### 1. Work shot by shot

A project is a collection of shots. Each shot is rendered separately, with its own settings, iterations, and review history. Divide sequences and films into shots and process each in isolation — it's faster than working on long videos, easier to iterate, and produces more controllable results.

> **💡 Tip** — Bulk shot processing is planned for a future release. For now, copy settings from one shot to another to speed up consistent work.

### 2. Iterate at the image level first

The [Modify Frame](/guide/workspaces/modify-frame) workspace is the recommended starting point for most workflows. Before launching a video render, generate a target frame with an image model and validate the look.

**Videos are expensive; images are cheap.** Failing fast at the image level saves credits, time, and frustration. Then use the validated frame as a keyframe or reference for the video model.

### 3. Build up in passes

Complex effects work best split into stages. The **Edit this Render** button on each track lets you chain operations: replace the character on pass one, stylize on pass two, upscale on pass three. Each pass is more controllable than trying to do everything at once.

See the [multi-pass recipe](/guide/workflows-recipes#recipe-multi-pass-pipeline) for the flagship example.

### 4. Frame-perfect output

Mago video models guarantee that a 171-frame input produces a 171-frame output that matches the source frame for frame. Every output frame corresponds to a specific source frame.

This is a deliberate contrast with closed-source models, which apply hidden optimizations and may alter timing, frame count, composition, or character identity. For production work where pacing, lip sync, and continuity matter, this is decisive.

### 5. Descriptive prompts for Mago, instruction prompts for closed-source

Mago models expect a **description** of the desired result — write what the output should look like. Closed-source models (Kling, Seedance, Happy Horse) expect **instructions** — tell them what to do.

> **⚠️ Warning** — This is the single biggest source of bad results when switching between model families. See the full [Prompting guide](/guide/prompting-guide).

## Privacy & confidentiality

Mago does not train on user content. Every project is confidential.

For Enterprise customers, deployment options include private cloud and on-premise installation, with full control over where renders happen and where data is stored. Mago models can be deployed in specific territories, in a client's own infrastructure, or with NDA-grade IP terms.

## Mago models vs. closed-source models

Mago integrates two model families. Picking the right tool starts with understanding the trade-offs:

| Property | Mago models | Closed-source models |
| --- | --- | --- |
| Prompt style | Descriptive (describe the result) | Instruction (tell it what to do) |
| Frame correspondence | Frame-perfect: N in = N out | Approximate, may drift |
| Character identity preservation | Strong with Style Transfer or Inpainting | Variable |
| Lip sync & micro-expression | Strong with Style Transfer | Strong (especially Kling Motion Control) |
| Settings exposure | High (more control, steeper curve) | Low (easier to start) |
| Cost per render | Generally lower | Generally higher |
| Content moderation | Moderated, more permissive for artistic use | Stricter; may block VFX content like blood |
| Deployment flexibility | Mago infra, private cloud, or on-premise | Provider infra only |
| Best fit | Long-form, precision, production pipelines | Quick shots, prototypes, simple transforms |

Full per-model detail lives in the [Model catalog](/models/overview).

---

[← User Guide](/guide/overview) · [Next: Getting Started →](/guide/getting-started)
