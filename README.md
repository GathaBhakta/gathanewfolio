# gathanewfolio

Homepage hero for **Gatha Bhakta** — implemented from the "Gatha Hero" Claude
Design project (turn 4, direction **4a**: *"I design across screens and spaces."*).

Plain static site — no build step. Open `index.html` in a browser, or serve the
folder:

```
npx serve .
```

## What's here

- **Sticky cream hero** with a hairline-framed claim, pink corner ticks, a
  slowly spinning quatrefoil mark in the nav.
- **Hover playground** — moving the pointer over the centre flings six sticker
  cut-outs out from behind the headline on a staggered spring; leaving pulls
  them back. Drop the real art into [`assets/`](assets/README.md) (labelled
  placeholders show until then).
- **Re-rolling scribbles** — three hand-drawn doodles (star / heart / star) that
  redraw themselves and jump to new spots near the edges every 6.5 s.
- **Selected work** — a pink section that scrolls up over the hero; the
  scrollbar flips pink → white as you cross into it.

Respects `prefers-reduced-motion` and collapses to a single column under 720 px.

## Fonts

Lora + DM Sans via Google Fonts (the design overrides the system's JejuMyeongjo
serif with Lora for the hero).
