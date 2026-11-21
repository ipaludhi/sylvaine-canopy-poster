# SYLVAINE — a travel poster for a place that isn't there

[![make.fun · the-poster-for-a-place-that-i-2-20261121-0539](https://make.fun/badge/the-poster-for-a-place-that-i-2-20261121-0539.svg)](https://make.fun/bounty/the-poster-for-a-place-that-i-2-20261121-0539?utm_source=github&utm_medium=readme&utm_campaign=the-poster-for-a-place-that-i-2-20261121-0539)
[![rank](https://make.fun/badge/the-poster-for-a-place-that-i-2-20261121-0539/ipaludhi/sylvaine-canopy-poster/rank.svg)](https://make.fun/bounty/the-poster-for-a-place-that-i-2-20261121-0539/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=the-poster-for-a-place-that-i-2-20261121-0539)
[![reward](https://make.fun/badge/the-poster-for-a-place-that-i-2-20261121-0539/ipaludhi/sylvaine-canopy-poster/reward.svg)](https://make.fun/bounty/the-poster-for-a-place-that-i-2-20261121-0539?utm_source=github&utm_medium=readme&utm_campaign=the-poster-for-a-place-that-i-2-20261121-0539)

An entry for the make.fun competition
[The Poster for a Place That Isn't There](https://make.fun/c/the-poster-for-a-place-that-i-2-20261121-0539)
— built for [make.fun](https://make.fun), where people build agents and
programs, enter them, and are scored, ranked and paid in the open.

## The place

**SYLVAINE** is a village in the treetops of an endless forest, seen at blue
hour: one Great Tree holds five lit treehouses joined by rope bridges, the
low sun breaks through the canopy behind it, and fireflies drift over a
forest floor that fades into darkness. The name is the only copy on the
poster — set large in the sky, legible at any size.

Why this place, and not another invented name on the board: the forest lane
was empty (no forest poster in the top 600), and a canopy village is a place
you can *stay* in — lit windows, bridges, a path of light — which is what the
judge's brief asks a poster to promise. The landmark is one tree, not a
skyline, so the eye goes name → treehouses → sun → horizon in one sweep.

## How the poster is made

- `poster.html` — the whole poster as hand-placed inline SVG: sky gradient,
  stars, birds, low sun with glow, three depths of tree line, the Great Tree
  with its canopy and treehouses, rope bridges, fireflies, mist, and the
  forest floor fading out. No image assets, no external resources, no
  randomness.
- `entry.png` — rendered from `poster.html` with headless Chrome at
  1024×1024. Two renders are byte-identical
  (sha256 `398bace5c61eb24b40058e632e552ec10d4f3bf3696c2115c7bc9779636e8776`),
  159,787 bytes, under the 1 MiB gate. Legible at 300 px: the name, the
  houses and the sun all still read.
- `main.ts` — Node 22, standard library only. Copies `entry.png`
  byte-for-byte to `$MAKEFUN_OUTPUT_DIR/entry.png` (or `/output/entry.png`).
  It never deletes or recreates the output directory; it only creates it if
  missing and writes the file inside.

## Run it

```sh
node --experimental-strip-types main.ts   # or: npx tsx main.ts
# with MAKEFUN_OUTPUT_DIR set, the copy lands there; otherwise /output/entry.png
```

To re-render the poster from the source (needs a headless Chromium):

```sh
chromium --headless --disable-gpu --no-sandbox --hide-scrollbars \
  --force-device-scale-factor=1 --window-size=1024,1024 \
  --screenshot=entry.png "file://$PWD/poster.html"
```

## License

MIT — see `LICENSE`.
