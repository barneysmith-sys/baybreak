# BAYBREAK.exe art spec: drop-in PNG slots

The game renders at 480 x 270 game pixels. Each slot below replaces a code-drawn layer when its PNG is present.

To add one, save the PNG in `assets/art/` with the exact name and size below, then add its key to `ART_SRC` in `index.html`:

```js
const ART_SRC={bay:'assets/art/bay-panorama.png', l5_near:'assets/art/l5-near.png'};
```

## Rules for every asset

- Side elevation only. A flat, orthographic view straight on, with no street perspective and no vanishing points.
- True pixel art at 1 image pixel = 1 game pixel. No anti-aliasing, no soft brushes, no upscaled images.
- Transparent background wherever the layer behind should show through. Use PNG with alpha, either fully on or fully off.
- Limited palette, about 48 to 64 colors per layer. Light comes from the left (west, late afternoon).
- No real company logos or wordmarks.

## Slots

| Key | File | Size (px) | What it is |
|---|---|---|---|
| `bay` | `bay-panorama.png` | 1000 x ~150 | Far layer for Levels 4 and 5. Already included, built from the approved Level 05 sheet. |
| `l5_near` | `l5-near.png` | 3700 x 270 | Level 5 street-front facades. The sky is transparent. The sidewalk top follows the street line: y = 124 from x 0 to 170, sloping down to y = 210 at x = 980, then flat at y = 210 to the end. Leave cross-street gaps at x 1100 to 1170 and 2380 to 2450. |
| `l5_mid` | `l5-mid.png` | 1800 x 270 | Level 5 mid skyline, with the building bases near y = 210 and the sky transparent. |
| `cablecar` | `cablecar.png` | 124 x 68 | Cable car facing left, wheels touching the bottom edge. The roof walking line is at y = 8. |
| `roadster` | `roadster.png` | 92 x 28 | Roadster body facing right, without wheels. The wheel centers are at (20, 21) and (71, 21), radius 6. |

Gameplay positions such as collisions, résumés and hazards are defined separately in code, so new art cannot break the level. Keep important silhouettes clear of the street at the bottom 60 px, where the rider plays.


## Level 05 illustrated layers (v1.4)

| File | Layer | Parallax |
|---|---|---|
| `l5-far.png` | Sunset sky, hills, Bay Bridge, water, Ferry Building | 0.10 |
| `l5-downtown.png` | Downtown towers; blank sign panels carry the fictional brands | 0.30 |
| `l5-near-flat.png` | Victorian street front, tiled and stepped down the hill | 1.00 |
| `l5-cablecar-{0,1,2}.png` | Cable car frames (playable car and background car) | 1.00 |
| `l5-car-{0..3}.png` | Traffic and background cars | 1.00 |
| `npc-{0..4}.png` | Pedestrians | 1.00 |

Brand names, colours and sign boxes live in `BRANDS` and `L5_SIGN_LAYOUT` in `index.html`. Sign boxes are in `l5-downtown.png` pixel coordinates.
To swap in higher-resolution art later, replace a PNG with one at the same pixel scale and keep the file name.
