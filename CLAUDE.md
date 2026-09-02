# gathanewfolio

Single-page portfolio for **Gatha Bhakta**. One file, no build:
`index.html` holds the markup, an inline `<style>`, and one inline
`<script>` IIFE. Assets (stickers, pixel-art scribbles) live in `assets/`.

Ported from the **"Gatha Portfolio v4"** Claude Design project
(`0e8d345a-8be7-4dfe-a2de-a6aac10e02a2`, file `Gatha Portfolio v4.dc.html`
→ `gatha-portfolio-v4.js`). Design iteration happens there; this repo is
the standalone implementation.

## Layout

`.stage` is the scroll container (`overflow-y:auto`, `container-type:
inline-size`, proximity scroll-snap). Its children, in order:

1. **`.intro`** — fixed overlay. The quatrefoil mark blooms centre-screen,
   then its four petals fly out to become `.claim`'s corner ticks and the
   hero fades up behind them. `.stage--intro` holds the hero content back
   while it plays. `prefers-reduced-motion` skips straight to the end.
   Clicking the nav mark replays it.
2. **`.nav`** — `position:sticky`, `height:var(--nav-h)`, transparent.
   Overlays the hero (which is pulled up under it by a negative
   `margin-top:var(--nav-h)`). Over a `[data-solidbg]` section the links +
   mark switch colour: to cream on the base pink panel, or — when a card's
   pastel wash is showing — to a WCAG-AA monochrome of that wash computed
   by `navInkOn()` and published as `--nav-ink`.
3. **`.hero`** — sticky, full viewport. `.claim` box centred; on scroll it
   fades + scales down 3% as the work panel rises over it. Grazing the
   claim's edge (`edgeDist()` + hysteresis) springs six sticker cut-outs
   out from behind it; seven pixel-art scribbles pulse and re-roll around
   it every 6.5 s.
4. **`.work`** — one screen-framed pink panel, the **7b × 7c hybrid**
   carousel. Multi-select filter chips, a filmstrip walked by the arrows
   or the wheel (wheel only intercepts once `.work` has fully settled
   against the top). Hovering a card tints the whole field to its wash,
   springs four cut-outs onto the thumbnail corners (7c) and trails a
   fifth on the cursor (7b). Cards are fixed-height + top-aligned so a
   filter change never shifts them. The colophon is the frame's footer.

## Conventions

- **Everything sizes off the viewport** via container-query units —
  `cqw`/`cqh` on `.work` (`container-type:size`), `cqw` elsewhere on
  `.stage`. `clamp(px, Ncqw, px)` throughout; avoid fixed px.
- Colour tokens and easings are CSS custom properties on `:root`
  (`--cream --pink --ink --ease --ease-out …`). `--nav-h` is CSS-driven
  (`clamp(46px,5.2cqw,72px)`), not measured in JS.
- The script is plain ES5-style `var` + `function` for `file://` use.
  Helpers: `asset(name)` → `assets/<encoded name>`, `byId`, `$`.
- Hero sticker photos are WebP (~370 KB total) re-encoded from the design
  project's source PNGs. The work panel's project-02 Wizaur clippies:
  `wizzy` is transparent PNG @2x (the card thumbnail) — its Figma SVG was
  a 3,996-path 265 KB pixel grid that janked the carousel, so it stays
  raster with `image-rendering:pixelated` on `[src$=".png"]`. The corner
  cut-outs `chat` / `spark2` are kept as SVG (~30–36 KB each) — few enough
  nodes to stay smooth, and they scale cleanly at the small corner size.
  Hero scribbles are hand-authored pixel SVGs (`cross-grid`, `pixel-heart`).

## Working here

The `git` remote is `origin` (private, `GathaBhakta/gathanewfolio`).
Changes are auto-committed + pushed to `main` by a `Stop` hook in
`~/.claude/settings.json` — but commit deliberately with real messages
during a work session; the hook only sweeps up leftovers.

Open `index.html` directly in a browser to check work (add `?v=<n>` to
dodge the `file://` cache).
