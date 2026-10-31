# Turbo Pitch — single-file build

`index.html` is the whole project in one file: **23.4 MB**, no external references.

Open it directly (double-click, `file://` works) — there is nothing to install and no server
needed.

## What is inside

| inlined | what it is |
|---|---|
| `boot.js` | the runtime shim and the start-up sequence |
| `rocketcars.js` | 85-car rocket pack (quantised geometry, base64) |
| `ultragarage.js` | 60-car ultra pack (same layout) |
| `Ultra-Library.js` | the Ultra library — 116 wheels, 53 toppers, 12 antennas, 96 vinyls, 26 celebrations, 52 boosts |
| `ultraboosts.js` | the recorded boost layers (`B.core / diamonds / rings / stream / halo / light / streaks / hero`) |
| `boostflame.js` | garage.html's own `BoostFlame` engine, running the boosts |
| `ultracelebs.js` | the recorded celebration spawns |
| `pitchgrass.js`, `kenneycars.js` | grass tufts, Kenney car pack |
| `game.js` | the game itself, every patch v8 … v118 |
| `pitch-grass.jpg`, `pitch-grass-n.png`, `pad-ps.webp`, `pad-xbox.webp` | inlined as data URIs |

## Verified

Opened from `file://`:

```
RLX          object
ULTRA_LIB    object
self-tests   409, 0-2 environment-dependent failures (the same ones the multi-file build shows in the menu)
```

The menu reports the full catalogue: CARS 140 · WHEELS 256 · TOPPERS 110 · ANTENNAS 62 ·
DECALS 376 · BOOSTS 83 · BALLS 18 · GOAL FX 107.

## Rebuilding

```
python3 ../tools/build_single_html.py
```

It reads `index.html`, inlines the nine scripts plus `Ultra-Library.js` (which `game.js` would
otherwise inject at runtime), turns the four images into data URIs, and writes this file.
