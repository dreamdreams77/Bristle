# Bristle and the Unfolding Map

A playable, single-file HTML adventure: a honey badger named Bristle unfolds a world that has been folded up like a paper map. No build step, no dependencies.

## Run it
- Open `index.html` in any modern browser, or
- Host it: push to GitHub, then **Settings > Pages > Deploy from branch > main / root**. The game lives at `https://<user>.github.io/<repo>/`.

(The Fredoka font loads from Google Fonts; the game works without it using a fallback font.)

## Controls
| Action | Keyboard | Touch |
|---|---|---|
| Move | A / D or arrows | on-screen arrows |
| Jump (press again in mid-air for Fennick's boost) | Space / W | jump button |
| Glide | hold jump in the air | hold jump |
| Companion power | **E** | star button |
| Switch companion power | **Q** | n/a |
| Shop | E next to Sable's stall in the Hollow | star button |

## What is in it
- 12 regions: the Hollow plus Mystic Forest, Candy Coast, Crystal Caves, Moonlit Marsh, Clockwork Desert, Floating Islands, Ancient Ruins, Hidden Dream Realm, Sky Kingdom, Underground Kingdom, Frostfold Peaks and The Tidal Deep (low-gravity swimming), ending at the Heart Gate
- 11 companions with painted sprites (plus Sable the shopkeeper). Ten have powers: Bram, Rascal, Zinnia, Ophelia, Ferris, Cumin, Nodd, Sir Biscuit, Dilly, Pemmican and Marlo (bubble float). Fennick gives the mid-air jump.
- 8 mini-bosses: Lantern Leech, Cog Scorpion, Stone Sentinel, Nightmare Knitter, Cannon Duchess, Magma Mole, Snowdrift Golem, Hermit Crab Brute
- Sable's shop, Creature Cards, secret acorns, rain-revealed platforms
- 15 citizens across the world (press E to talk: hints and 14 citizen requests), Marlo's pearl quest in the Tidal Deep, 7 timed races (Acorn Dash, Sugar Rail Rush, Deep Rail Dash, Reef Rush, Cloud Hop, Glacier Glide, Dreamdive Dash)
- Sketchbook of quests with Renown ranks, more shop items, and automatic saving (Continue on the title screen)

## Art pipeline
All art is painted procedurally at load time (brush strokes, grain, rim light, outlines) into layered canvases: backgrounds, midground, props, characters, foreground foliage, and FX. It is **not** hand-painted bitmap art.

- Click **Art manifest** in the game to see every asset (id, file name, size, alpha, use, frames, source) and download `asset_manifest.json`.
- To replace any generated asset with a real painted PNG, set `window.ARTPACK = { "char_bristle_run_0": "art/bristle_run_0.png", ... }` before the script runs. Keep the same pixel size as listed in the manifest.
- All assets are original and project-owned; no third-party art is used.

## Design document
The full game design document (all 19 sections) was written alongside this build.
