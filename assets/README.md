# assets/

## Hero — 7A locked grid

The hero (`hero-home` / turn 7A of the "Hero Explorations" Claude Design
canvas) lays four wave/zigzag **tapes** and nine draggable **stickers** over
a Swiss grid, at the exact frame coordinates from the design file. Source art
came from `…/PERSONAL STUDY/UX/FINAL FOLDER` (+ `/TAPE`) and repo photos,
re-encoded here as WebP. The photo cut-outs keep their own aspect ratio
(`.stk--sq` letterboxes them in a square box — no cropping). The grid
collage is full-bleed; only the claim card, tapes and stickers stay
size-capped (tapes + stickers ride a centred `.hero__frame`, max-width
1280).

| file                   | placed as (in `STICKERS` / `TAPES`, `index.html`) | source |
|------------------------|---------------------------------------------------|--------|
| `tape-1.webp`          | tape, top-left                                    | `FINAL FOLDER/TAPE/Frame 261.png` |
| `tape-2.webp`          | tape, top-right                                   | `FINAL FOLDER/TAPE/Frame 262.png` |
| `tape-3.webp`          | tape, lower-left                                  | `FINAL FOLDER/TAPE/Exclude.png` |
| `tape-4.webp`          | tape, right                                       | `FINAL FOLDER/TAPE/Frame 259.png` |
| `fig-s1.webp`          | square cut-out, top-right (Gatha avatar)          | `Gatha 1.webp`, centre-cropped |
| `fig-s2.webp`          | square cut-out, upper-left (NYC model)            | `nycmodel.webp`, centre-cropped |
| `fig-s3.webp`          | square cut-out, lower-right (matcha)              | `matcha.webp` |
| `fig-s4.webp`          | square cut-out, mid-right (cheesecake)            | `cheesecake.webp` |
| `fig-s5.webp`          | square cut-out, top-right (pink heart paperclip)  | `FINAL FOLDER/CLIP HEART.png` |
| `sticker-logomark.webp`| origami quatrefoil, centre                        | `FINAL FOLDER/logomark.png` |
| `sticker-baby.webp`    | baby photo, lower-left                            | `FINAL FOLDER/GATHA BABY PIC.png` |
| `sticker-lotus.webp`   | lotus, bottom-right                               | `FINAL FOLDER/LOTUS.png` |
| `sticker-ipod.webp`    | iPod, bottom-centre (on the checker base)         | `FINAL FOLDER/ipod 3.png` |

The ruler edge, graph-paper column, dot-field bands, checker base and
isometric column are all pure CSS/SVG generated in `index.html` — no assets.

Stickers spring in after the intro, then drag anywhere on the hero; every
fresh load snaps them back to the design placement (drag offsets live only in
memory). A missing sticker file just leaves a gap — nothing breaks.

## Work-panel photos + clippies

Selected-work carousel. Card thumbnails and the hover cut-outs (`CORNER_SEQ`
in `index.html`) reuse the project photos:

| file                  | notes |
|-----------------------|-------|
| `nycmodel.webp` `CHAICROISSANT.webp` `cheesecake.webp` `Gatha 1.webp` `matcha.webp` `wip logo 1.webp` | card thumbs + corner cut-outs |
| `wizzy.png`           | project-02 thumbnail — transparent PNG @2x. Its Figma SVG drew every pixel block as its own `<path>` (3,996 paths / 265 KB) and stuttered under the hover springs; raster is 8.5 KB. `.qc__img[src$=".png"]` keeps `image-rendering:pixelated`. |
| `chat.svg`            | project-02 corner cut-outs 0,3 — 36 KB, 552 paths. |
| `spark2.svg`          | project-02 corner cut-outs 1,2 — 30 KB, 444 paths. |

`cursor-wand.svg` — the site-wide default cursor everywhere except the hero's own canvas cursors below. A `wandCursor()` DOM overlay (see `index.html`) puts a small pink-outline dot exactly on the real mouse position, then eases this static wand body (held at a constant -30deg tilt, tip pinned per its own `transform-origin`) and 3 small twinkles toward a point offset 18/24px down-right of that dot (`WAND_GAP`) every animation frame, each on its own damping — so the wand and sparkles trail a beat behind the actual pointer and settle a little apart from it rather than sitting on top of whatever the dot itself is hovering (a link's text, say). The 3 twinkle shapes are traced from `FINAL FOLDER/cursore/Sparkle Wand.svg`; each of the 3 sparkles starts its 200ms shape-cycle on a different one of the 3 shapes, so they read as scattered variation rather than one synced blink. Cropped from `FINAL FOLDER/cursore/Cursor Wand.svg` (81×176) down to just the wand body (81×118) — the source file's own 3 trailing sparkle-icon paths were dropped since the overlay draws its own. Kept as SVG rather than rasterized (the project's usual move for a heavily-repeated pixel-art export, see `wizzy.png` below) because it's one static image, not redrawn per-instance. Native `cursor:none` is set site-wide behind `@media (pointer:fine)` to make room for it; `.cell--graph` / `--dot` / `--check` / `--iso` keep their own explicit `cursor: url()` rules below, which still win the cascade, and `wandCursor()` also hides its own DOM overlay there so it doesn't sit on top of them. `cursor.svg`, the old pink-dot pointer this replaced as the hero's default, is unused now — kept for reference.
`cursor-hover.svg` — pink ring (bullseye), shown over the interactive grid regions (`.cell--dot` / `--check` / `--iso`); stickers keep `grab`. The centre dot is the same heart outline as `cursor-crosshair.svg`, sized to sit clearly inside the ring rather than as a tiny dot; no glow/shadow, flat lines only. Hotspot at the exact centre (20,20) on a 40×40 canvas.
`cursor-crosshair.svg` — a plain crosshair (four gapped line segments) shown over `.cell--graph`, but with the usual centre dot swapped for the actual heart outline instead of a square — sized to read clearly as a heart, not shrunk down to a dot. The heart is traced from `FINAL FOLDER/footer/graphics/cross hair.svg` (a 242×242 heart, not a literal crosshair on its own), scaled into the 44×44 canvas's centre gap via `vector-effect="non-scaling-stroke"` so its outline stays a crisp 1.5px regardless of the scale transform. No glow/shadow — flat lines only. Hotspot at the exact centre (22,22).
`favicon.svg` — the quatrefoil mark on a `--pink` ground.
`cross-grid.svg` / `pixel-heart.svg` — unused (were the old hero's pixel scribbles); kept for reference.

## Footer — "sleep breaker"

Port of the `Gatha Footer.dc.html` Claude Design canvas (`assets/` in that
project). Source art for the raster stickers came from
`…/PERSONAL STUDY/UX/FINAL FOLDER/footer/graphics`, re-encoded here as WebP;
the wordmark is the design's own SVG with its embedded C2PA metadata
stripped. The `ft-graph.svg` tile is regenerated in JS instead of shipped as
an asset (same trick as the hero's ruler/graph patterns) — see
`footerPatterns()` in `index.html`.

| file                  | placed as                                | source |
|------------------------|-------------------------------------------|--------|
| `ft-baby-sleep.webp`  | sleeping Gatha × 5 (`.ft__baby`)          | `footer/graphics/Property 1=Default.png` |
| `ft-baby-awake.webp`  | woken Gatha (swapped in on hit)           | `footer/graphics/Property 1=touched.png` |
| `ft-primogem.webp`    | sticker, drag anywhere                    | `footer/graphics/Primogem.png` |
| `ft-heartlock.webp`   | sticker, drag anywhere                    | `footer/graphics/heartlock.png` |
| `ft-pen.webp`         | sticker, drag anywhere                    | `footer/graphics/Pen.png` |
| `ft-diary.webp`       | sticker, drag anywhere                    | `footer/graphics/Diary.png` |
| `ft-ds.webp`          | sticker, drag anywhere                    | `footer/graphics/DS.png` |
| `ft-signature.webp`   | "Gatha" signature mark, over the paper    | `footer/graphics/signature 1.png` |
| `ft-wordmark-dots.svg`| halftone "Gatha" wordmark, bottom bleed   | design project `assets/ft-wordmark-dots.svg` |
| `ft-riso.webp`        | `.ft__riso`, the *first* child of `.ft` — sits under `.ft__graph` and every asset, repeating 640×414 tile, `mix-blend-mode:luminosity` @ 20% opacity | `footer/graphics/Footer  Riso overlay.png`, downsampled 3456×2234 → 1728×1117 |

The design's `Primogem.svg` / `DS.svg` / `Diary.svg` / `Pen.svg` /
`heartlock.svg` exports are per-pixel vector dumps (0.5–1.2 MB each,
same issue as the hero's `wizzy` clippie) — the PNGs are used instead.
The ball and bar are plain CSS shapes tinted with the same generated graph
tile, not images; the play/pause icon is an inline SVG path.
