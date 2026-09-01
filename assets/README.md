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

`wizzy.png`, `chat.png`, `spark2.png` — Wizaur pixel-art, transparent PNG
exported @2x from Figma (776×992 / 616×582 / 650×650). Used for project 02
in the selected-work carousel: `wizzy` is the card thumbnail, `chat` +
`spark2` the four corner cut-outs. Kept as PNG, not SVG — the Figma SVG
export draws every pixel block as its own `<path>` (3,996 of them for
`wizzy`), ~330 KB total, and stuttered under the hover springs. As PNG the
three come in at ~16 KB. `.qc__img[src$=".png"]` etc. get
`image-rendering:pixelated` so scaling stays crisp.

To replace one: drop a transparent-background image at the same path (any
web format — update the extension in the `CUTS` array in `index.html` if it
changes). If a file is missing the page shows a labelled placeholder chip in
its slot and nothing breaks.
