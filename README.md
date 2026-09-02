# gathanewfolio

Homepage for **Gatha Bhakta** — a single static `index.html` (inline CSS +
JS, no build). Implemented from the "Gatha Portfolio v4" Claude Design
project.

```
open index.html          # or: npx serve .
```

## What's on the page

- **Petal intro** — the quatrefoil mark blooms centre-screen, then its
  four petals scatter out to become the corners of the claim box while the
  hero fades up. Click the nav mark to replay it. Respects
  `prefers-reduced-motion`.
- **Sticky hero** — hairline claim frame, spinning mark. Move the pointer
  near the frame and six sticker cut-outs spring out from behind it; seven
  pixel-art star/heart scribbles pulse in a loose ring and jump to fresh
  spots every few seconds.
- **Sticky nav** — transparent; its links and mark recolour to stay
  legible over each section (cream over the pink work panel, a computed
  AA-contrast tint over a hovered card's wash).
- **Selected work** — a viewport-framed pink panel: multi-select filter
  chips and a filmstrip you walk with the arrows or the wheel. Hovering a
  card washes the field with that project's colour, springs cut-outs onto
  the thumbnail corners and trails one on the cursor.

Everything is sized in container-query units, so the whole page scales
with the viewport. Collapses to a single column under 720 px.

See [`CLAUDE.md`](CLAUDE.md) for the structure and conventions.

## Assets

`assets/` — six WebP photo stickers (re-encoded from the design project's
PNGs); the work panel's project-02 Wizaur clippies (`wizzy.png` as a
transparent PNG thumbnail, `chat.svg` + `spark2.svg` as the corner
cut-outs); and two hand-authored pixel-art SVGs for the hero scribbles
(`cross-grid.svg`, `pixel-heart.svg`).
