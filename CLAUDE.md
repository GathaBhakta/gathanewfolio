# gathanewfolio

Single-page portfolio for **Gatha Bhakta**. One file, no build:
`index.html` holds the markup, an inline `<style>`, and one inline
`<script>` IIFE. Assets (tapes, stickers, photos) live in `assets/`.

Design lives in the Claude Design project `Gatha Bhakta Hero Mockups`
(`0e8d345a-8be7-4dfe-a2de-a6aac10e02a2`). The hero is a port of **turn 7A**
of `Hero Explorations.dc.html` (`hero-home.js` — "the locked grid"). The work
panel is still the 7b×7c hybrid from `Gatha Portfolio v4.dc.html`. Design
iteration happens in the project; this repo is the standalone implementation.

## Layout

`.stage` is the scroll container (`overflow-y:auto`, `container-type:
inline-size`, proximity scroll-snap). Its children, in order:

1. **`.intro`** — fixed overlay. The quatrefoil mark blooms centre-screen,
   then its four petals fly out to become the claim card's corner ticks
   (`.claim__tick`) and the hero fades up behind them. `.stage--intro`
   holds the frame back while it plays. `prefers-reduced-motion` skips
   straight to the end. Clicking the nav mark replays it.
2. **`.nav`** — `position:sticky`, `height:var(--nav-h)`, transparent.
   Overlays the hero (which is pulled up under it by a negative
   `margin-top:var(--nav-h)`). Over a `[data-solidbg]` section the links +
   mark switch colour: to cream on the base pink panel, or — when a card's
   pastel wash is showing — to a WCAG-AA monochrome of that wash computed
   by `navInkOn()` and published as `--nav-ink`.
3. **`.hero`** — sticky, full viewport, `overflow:hidden`,
   `container-type:inline-size`. Turn **7A**, a **full-bleed splash**: one
   Swiss `.grid` (`position:absolute;inset:0`) with **clamped side columns
   + a flexible middle** (`clamp(…3.125cqw…) clamp(…19.097cqw…) minmax(0,1fr)
   clamp(…22.222cqw…)`, four `%` rows) so the pattern regions reach every
   screen edge at any width — `.ruler` edge (absolute, `left:0`),
   `.cell--graph` paper column, `.cell--dot` bands, `.cell--check` base,
   `.cell--iso` column. Ruler / graph / dot / checker tiles are SVG data
   URIs built in JS (`heroGrid` IIFE, `GS=38` module); the iso column
   extrudes pink-lit blocks on dwell. The `.cell--claim` (middle column)
   carries the dot field and centres a `.claimbox` (`width:min(100%,720px)`)
   holding the card + corner ticks + live text ("Gatha designs both —
   Screens & Spaces", positioned in `%` of the box); every claim type
   measure is `min(Ncqw, px)`-capped so it holds its design size past
   ~1280 instead of growing with the splash. `.tape` × 4 and `.stk` × 9
   ride a centred `.hero__frame` overlay (`max-width:1280px`,
   `pointer-events:none`; `.stk` re-enables it to drag). Stickers spring in
   after the intro and reset to placement every load (offsets in memory
   only). On scroll the whole hero fades + scales down 3% under the work
   panel.
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
  `.stage`. Grid tracks and claim-text positions are `%`; `clamp(px,
  Ncqw, px)` for type. Avoid fixed px. The narrow layout is a
  `@container (max-width:820px)` block that collapses the grid to the
  claim card alone.
- Colour tokens and easings are CSS custom properties on `:root`
  (`--cream --pink --pink-ink --pink-rule --ink --ease --ease-out …`);
  `--petal` / `--petal-off` are on `.stage`. `--nav-h` is CSS-driven
  (`clamp(46px,5.2cqw,72px)`), not measured in JS.
- The script is plain ES5-style `var` + `function` for `file://` use.
  Helpers: `asset(name)` → `assets/<encoded name>`, `byId`, `$`.
- Hero tapes + stickers are WebP re-encoded from `…/PERSONAL STUDY/UX/
  FINAL FOLDER` (+ `/TAPE`) and the design project's `assets/` — see
  `assets/README.md` for the file → placement map. The five `fig-s*`
  square cut-outs are centre-cropped project photos (except `fig-s5`, the
  pink heart paperclip). The work panel's project-02 clippie `wizzy` is
  transparent PNG @2x — its Figma SVG was a 3,996-path 265 KB pixel grid
  that janked the carousel, so it stays raster with
  `image-rendering:pixelated` on `[src$=".png"]`; corner cut-outs `chat` /
  `spark2` stay SVG (~30–36 KB each).
- The favicon is `assets/favicon.svg` — the quatrefoil mark on a `--pink`
  ground — linked from `<head>` as `rel="icon" type="image/svg+xml"`.

## Working here

The `git` remote is `origin` (private, `GathaBhakta/gathanewfolio`).
Changes are auto-committed + pushed to `main` by a `Stop` hook in
`~/.claude/settings.json` — but commit deliberately with real messages
during a work session; the hook only sweeps up leftovers.

Open `index.html` directly in a browser to check work (add `?v=<n>` to
dodge the `file://` cache).
