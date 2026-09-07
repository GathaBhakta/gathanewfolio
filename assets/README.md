# assets/

## Hero — 7A locked grid

The hero (`hero-home` / turn 7A of the "Hero Explorations" Claude Design
canvas) lays four wave/zigzag **tapes** and nine draggable **stickers** over
a Swiss grid, at the exact frame coordinates from the design file. Source art
came from `…/PERSONAL STUDY/UX/FINAL FOLDER` (+ `/TAPE`) and the design
project's own `assets/`, re-encoded here as WebP.

| file                   | placed as (in `STICKERS` / `TAPES`, `index.html`) | source |
|------------------------|---------------------------------------------------|--------|
| `tape-1.webp`          | tape, top-left                                    | `FINAL FOLDER/TAPE/Frame 261.png` |
| `tape-2.webp`          | tape, top-right                                   | `FINAL FOLDER/TAPE/Frame 262.png` |
| `tape-3.webp`          | tape, lower-left                                  | `FINAL FOLDER/TAPE/Exclude.png` |
| `tape-4.webp`          | tape, right                                       | `FINAL FOLDER/TAPE/Frame 259.png` |
| `fig-s1.webp`          | square cut-out, top-right (Gatha avatar)          | `Gatha 1.webp`, centre-cropped |
| `fig-s2.webp`          | square cut-out, upper-left (NYC model)            | `nycmodel.webp`, centre-cropped |
| `fig-s3.webp`          | square cut-out, lower-right (chai + croissant)    | `CHAICROISSANT.webp`, centre-cropped |
| `fig-s4.webp`          | square cut-out, mid-right (cheesecake)            | `cheesecake.webp`, centre-cropped |
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

`favicon.svg` — the quatrefoil mark on a `--pink` ground.
`cross-grid.svg` / `pixel-heart.svg` — unused (were the old hero's pixel scribbles); kept for reference.
