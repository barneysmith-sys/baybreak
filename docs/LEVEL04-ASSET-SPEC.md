# Level 04 Golden Gate Gauntlet: asset export specification

This is the exact list of art the Golden Gate section needs, sized to the BAYBREAK.exe engine. Every file drops into `assets/l4/`. The game swaps each sheet in as soon as the file exists, so assets can arrive in batches.

The art guide poster is the style reference. Nothing is cropped from it.

## 1. Engine facts every asset must respect

| Fact | Value |
|---|---|
| Game canvas | 480 × 270 game pixels, scaled up with nearest-neighbour |
| Skater density | **3 art pixels per game pixel** (`RIDER_PX = 3`) |
| Skater cell | 170 × 148 art px, feet anchor at (85, 144) |
| Skater on screen | about 31 × 35 game px; standing height 40 game px (120 art px) |
| Road surface | game y = 226 on the bridge deck |
| Light | warm sunset rim light from the right, cool violet shadow on the left |

**Characters, vehicles, animals and props use 3× density, like the skater.** That is the fix for the stick-figure problem. **Environment layers use 1× density**, like the Roadster opening and the Level 05 layers.

## 2. Delivery rules (all files)

- One PNG per sheet, **true transparency**, no background colour, no labels, no text overlays.
- Pixel art at native size. **No anti-aliasing, no blur, no resampling.** Hard 1 px dark outline on characters.
- **Fixed grid:** every frame of a sheet uses the same cell size. Frames run left to right; animations run top to bottom in the order listed.
- Feet (or wheels) sit on the bottom anchor row of each cell, horizontally centred, the same in every frame, so nothing jitters.
- Characters face **left** (towards the oncoming skater) unless noted. The game mirrors them when needed.
- Palette: rich 16-bit sunset. Oranges, magentas, violets and deep blues, with the Golden Gate's International Orange (#C0362C).
- Real logos are not allowed. Waymos stay unbranded, or carry a small original "W"-free mark.

## 3. Characters and vehicles (3× density)

Cell sizes are in art pixels. The game size in brackets is cell ÷ 3.

### A. Venture capitalists: `vc-1.png` … `vc-6.png`
Six distinct adults (mixed genders and skin tones), each with a different look: fleece vest, puffer, blazer, sunglasses, backpack, laptop, coffee, phone.

- Cell **128 × 132** (43 × 44 game), anchor (64, 128). Standing height 114 to 120 art px, matching the skater. (Widened from 96: backpacks and raised arms need the room. Confirmed with `vc-1.png`.)
- Rows: `idle` 4 · `walk` 6 · `throw-money` 6 · `surprised` 3 · `cheer` 4
- Sheet size: 768 × 660 (6 columns × 5 rows; unused cells transparent)
- Keep thrown banknotes close to the hand, or leave them out: the game adds flying money itself.

### B. Waymo-style robotaxi: `waymo.png` (updated: larger SUV)
White SUV, side view, roof lidar dome, small side sensors, friendly. Gameplay size is now **80 × 28 game px** (body length × roof height), with the sensor dome to 36.

- Cell **264 × 120** art px (88 × 40 game), anchor (132, 117) = bottom-centre of the tyres.
- Body **240 art px long**, from x 12 to x 252 in the cell (the 80-game-px collision box).
- **Flat roof exactly 84 art px above the anchor** (28 game px, the landable surface), spanning at least x 60 to x 170.
- Lidar dome top **108 art px** above the anchor (36 game px).
- Wheel centres at x 60 and x 204, 15 art px above the anchor, radius 21. **Identical in every frame.**
- Rows: `drive` 4 (hubcaps turn about a quarter spoke per frame) · `yield` 2 (brake lights on, no glow halo) · `roof-ready` 1 (subtle blue roof highlight)
- Sheet size: 1056 × 360. **Source art should be drawn about 400 px long** and scaled down, never up.

### C1. Corgis: `corgi-1.png` … `corgi-4.png`
Four distinct corgis: classic red, tricolour, sable, and one with a bandana. Big ears, fluffy rear, tongue out. Never shown hurt.

- Cell **72 × 48** (24 × 16 game), anchor (36, 46). Body about 60 × 39 art px (the 20 × 13 game collision box).
- Rows: `run` 6 · `bark` 3 · `hop` 4 · `idle` 4 (tail wag)
- Sheet size: 432 × 192

### C2. Dog walkers (adult women only): `walker-1.png` … `walker-6.png`
Six distinct women, with different outfits, hairstyles, skin tones and accessories (iced coffee, tote bag, phone, sunglasses).

- Cell **128 × 132**, anchor (64, 128).
- Rows: `walk` 6 · `idle` 4 · `sip-coffee` 3 · `leash-high` 2 (arm raised, used for the duck-under-the-leash obstacle; hand at about 108 art px above the anchor)
- Sheet size: 768 × 528

### D. Finale performers and visitors
All use cell **128 × 132**, anchor (64, 128), unless noted.

| File | Who | Rows (frames) |
|---|---|---|
| `sax.png` | Saxophone player | `play` 4 |
| `drummer.png` | Drummer with bucket kit (cell **132 × 132**) | `play` 4 |
| `painter.png` | Painter with easel and a small Golden Gate canvas (cell **132 × 132**) | `paint` 4 |
| `tourist-1.png`, `tourist-2.png` | Tourists with cameras | `idle` 2 · `photo` 3 (flash frame) |
| `pedestrian-1.png`, `pedestrian-2.png` | Scenic walkers | `walk` 6 |
| `cyclist.png` | Rider plus bike (cell **108 × 108**, anchor (54, 104)); collision 78 × 90 art px | `ride` 4 |

## 4. Gameplay props (3× density)

| File | Cell (art px) | Frames | Notes |
|---|---|---|---|
| `bill.png` | 24 × 12 | 3 (flutter) | Single banknote, original design |
| `bill-patch.png` | 60 × 12 | 2 | Cash lying on the road (the speed boost) |
| `briefcase.png` | 42 × 30 | 1 | Closed; collision 14 × 10 game |
| `briefcase-ramp.png` | 102 × 51 | 1 | Open lid, money inside; ramp face rises 39 art px over 102 |
| `luggage.png` | 54 × 66 | 1 | Two-case stack; collision 18 × 22 game |
| `token.png` | 30 × 30 | 6 (spin) | Gold funding coin with "$" |
| `iced-coffee.png` | 24 × 30 | 4 (roll) | Clear cup, ice, straw |
| `spill.png` | 120 × 18 | 3 (shimmer) | Coffee puddle with ice; 40 game px wide |
| `ice-cube.png` | 18 × 18 | 2 (sparkle) | |
| `music-gear.png` | 66 × 42 | 2 (case open, drum) | One cell each |
| `note.png` | 24 × 30 | 4 (bob) | Music-note collectible |
| `kicker.png` | 108 × 42 | 1 | Wooden kicker ramp; rises 42 art px over 108 |
| `bench.png` | 132 × 36 | 1 | Park bench; seat top 30 art px above the anchor |

## 5. Environment (1× density, seamless tiles)

All environment art is at game-pixel size (1×). "Seamless" means the left and right edges must join with no visible seam.

| File | Size (game px) | Notes |
|---|---|---|
| `sky.png` | 480 × 200 | Sunset gradient with sun (or keep the current code sky) |
| `clouds.png` | 960 × 120 | Seamless, transparent; scrolls slowly |
| `headlands.png` | 1920 × 120 | Marin Headlands silhouette with dusk lights; seamless; shown at the north end |
| `skyline-far.png` | 2400 × 150 | San Francisco skyline at sunset, transparent sky; fades in as the player heads south |
| `ocean.png` | 480 × 60 | 4 frames stacked vertically (480 × 240): Pacific with sun glitter |
| `fog.png` | 960 × 80 | Seamless, transparent; 2 variants stacked (960 × 160) |
| `tower.png` | 64 × 420 | Golden Gate tower, side view, art-deco recesses, lit; base sits at game y 306 |
| `railing.png` | 64 × 30 | Seamless far-side railing with posts |
| `lamp.png` | 16 × 60 | Bridge lamp post; glow is added in code |
| `road.png` | 64 × 34 | Seamless roadway with lane dash; top row is the drivable surface |
| `sidewalk.png` | 64 × 8 | Seamless pedestrian path |
| `deck-under.png` | 64 × 30 | Seamless orange truss under the deck |
| `cypress-1.png` … `cypress-3.png` | 80 × 120 | Monterey cypress variants (Presidio finale) |
| `overlook.png` | 64 × 24 | Seamless overlook fence |
| `props-env.png` | free layout, transparent | Street signs, barriers, cones, maintenance cart, waterfront light strip: each item on its own transparent area with 4 px gaps |

The suspension cable and the suspender ropes stay code-drawn (they are a curve), but take their colours from `tower.png`.

## 6. How the art connects to gameplay

- Collision boxes stay exactly as they are today. The cell sizes above were chosen so each sprite's visible body matches its current box. That keeps the level's timing, checkpoints and fairness intact.
- The loader maps each file to its slot and uses the current drawing only while a file is missing, so partial deliveries are safe.
- Animation speed per row: 8 fps for walks and runs, 6 fps for idles, 12 fps for throws, barks and hops.

## 7. Suggested generation order

1. `vc-1` … `vc-6`, `bill`, `bill-patch`, `token` (Encounter 01)
2. `waymo`, `kicker` (Encounter 02)
3. `corgi-1` … `corgi-4`, `walker-1` … `walker-6`, `iced-coffee`, `spill`, `ice-cube` (Encounter 03)
4. Finale characters and props (Encounter 04)
5. Environment tiles and layers

## 8. Production status (after the complete reference pack)

| Asset | Status |
|---|---|
| `vc-1` | **Finished and in the game** (approved style and scale) |
| `vc-2` … `vc-6` | Missing. The pack has 1 pose per animation at about 70 px tall; each needs a full sheet like `vc-1` |
| `waymo` | Missing. The pack's cars are 3/4 perspective; the game needs a **side view** |
| `corgi-1` … `corgi-4` | Missing. 1 frame per animation at about 70% size |
| `walker-1` … `walker-6` | Missing. 1 standing pose each |
| Finale characters | Missing. 1 pose each |
| Props | Missing. Crops sit on painted backgrounds; the bench and luggage are cut off by the crop edge |
| Environment | Missing. Crops are small slivers, not full-size seamless tiles |

**What worked for `vc-1`, and should be repeated for every sheet:** one character or object per image, every animation frame drawn, transparent background, figures about 190 px tall (the game scales them down, never up). Loose layouts are fine. Vehicles and props must be drawn in **side view**.
