# Global Timeline Workspace

[← Upscale](/guide/workspaces/upscale) · [Workspaces](/guide/overview#the-five-workspaces) · [Next: Timeline & tracks →](/guide/timeline-and-tracks)

---

The Global Timeline is the cross-shot review surface for a project. It shows pinned renders from every shot in sequence, arranged in the order the shots appear in the project.

> 📸 **Screenshot needed:** `workspaces/global-timeline.png`
> _Global Timeline with several pinned shots._

## Purpose

Mago is designed around long-form projects — many users work on sequences of dozens or hundreds of shots. The Global Timeline solves the problem of maintaining consistency across that work:

- **Style consistency** — does the visual treatment hold from shot to shot?
- **Character continuity** — does the character look the same in shot 12 as in shot 47?
- **Color & lighting consistency** — do successive shots match without jarring transitions?
- **Pacing review** — does the sequence flow as intended?

## How to use it

1. Render each shot and pick the best result.
2. On the best render track in each shot, click **Pin to Global Preview**. _Only one pin per shot is allowed._
3. Open the Global Timeline tab — all pinned renders appear in order.
4. Review the sequence. If a shot looks inconsistent, return to its shot view, generate a new render, and update the pin.
5. Iterate until the sequence is internally consistent.

## As a preview before export

The Global Timeline is the recommended final preview before exporting individual shots for an external editing or compositing pipeline. Catching inconsistencies here is cheaper than discovering them in a finishing tool.

> **📐 Design note** — Mago does not produce a single concatenated final video. Each shot exports separately, and final assembly happens in your editing tool. The Global Timeline preview shows what the assembled sequence will look like. See [Export & compositing](/guide/export-and-compositing).

---

[← Upscale](/guide/workspaces/upscale) · [Workspaces](/guide/overview#the-five-workspaces) · [Next: Timeline & tracks →](/guide/timeline-and-tracks)
