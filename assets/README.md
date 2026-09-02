# assets/

The hero's hover interaction flings six cut-out stickers out from behind the
headline. The source art was supplied from the "Gatha Hero" Claude Design
project and re-encoded here as WebP (longest edge 560 px, quality 82) — the
originals were 200 KB–600 KB PNGs; the whole set is now ~370 KB.

| file                  | used as        | on-screen height |
|-----------------------|----------------|------------------|
| `cheesecake.webp`     | left slot 1    | 109 px           |
| `CHAICROISSANT.webp`  | left slot 2    | 120 px           |
| `matcha.webp`         | left slot 3    | 133 px           |
| `nycmodel.webp`       | right slot 1   | 106 px           |
| `Gatha 1.webp`        | right slot 2   | 123 px           |
| `wip logo 1.webp`     | right slot 3   | 101 px           |

## Work-panel clippies

Wizaur pixel-art for project 02 in the selected-work carousel:

| file         | used as              | notes |
|--------------|----------------------|-------|
| `wizzy.png`  | card thumbnail       | transparent PNG @2x (776×992). Its Figma SVG drew every pixel block as its own `<path>` — 3,996 paths / 265 KB — and stuttered under the hover springs. Raster is 8.5 KB and one GPU texture. `.qc__img[src$=".png"]` gets `image-rendering:pixelated` to stay crisp. |
| `chat.svg`   | corner cut-outs 0,3  | 36 KB, 552 paths — few enough to stay smooth at the small corner size, and scales cleanly. |
| `spark2.svg` | corner cut-outs 1,2  | 30 KB, 444 paths. |

To replace one: drop a transparent-background image at the same path (any
web format — update the extension in the `CUTS` array in `index.html` if it
changes). If a file is missing the page shows a labelled placeholder chip in
its slot and nothing breaks.
