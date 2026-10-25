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
| Ground Pound (in the air; smashes honey crates, bigger mushroom bounces, reveals nearby secret acorns) | S / Down | ⤓ button |
| Air Dash (not during timed races, 0.85s cooldown) | Shift / X | » button |
| Companion power | **E** | star button |
| Switch companion power | **Q** | n/a |
| Shop | E next to Sable's stall in the Hollow | star button |

## What is in it
- 12 regions: the Hollow plus Mystic Forest, Candy Coast, Crystal Caves, Moonlit Marsh, Clockwork Desert, Floating Islands, Ancient Ruins, Hidden Dream Realm, Sky Kingdom, Underground Kingdom, Frostfold Peaks and The Tidal Deep (low-gravity swimming), ending at the Heart Gate
- 11 companions with painted sprites (plus Sable the shopkeeper). Ten have powers: Bram, Rascal, Zinnia, Ophelia, Ferris, Cumin, Nodd, Sir Biscuit, Dilly, Pemmican and Marlo (bubble float). Fennick gives the mid-air jump.
- 8 mini-bosses: Lantern Leech, Cog Scorpion, Stone Sentinel, Nightmare Knitter, Cannon Duchess, Magma Mole, Snowdrift Golem, Hermit Crab Brute
- Sable's shop, Creature Cards, secret acorns, rain-revealed platforms
- 15 citizens across the world (press E to talk: hints and 14 citizen requests), Marlo's pearl quest in the Tidal Deep, 7 timed races (Acorn Dash, Sugar Rail Rush, Deep Rail Dash, Reef Rush, Cloud Hop, Glacier Glide, Dreamdive Dash)
- 23 honey crates to smash (Ground Pound or Air Dash), acorn chains that pay bonus acorns, and a fold-map strip showing your progress and Seam Stones
- 33 roaming Burrs across regions 1-12: stomp, dash into or ground-pound them (side contact just knocks you back). Clear a region's patrol for +3 acorns; chain stomps and mushroom bounces without landing for Air Combos (+1 acorn every 3). Progress is saved.
- Depth-of-image pass: a directional light per region (rim light and long cast shadow on Bristle, lit lips, ambient occlusion and cast shadows on ground and platforms), hazy far ridges, cave ceilings, foreground blur and bokeh, sun/moon glow with shafts, and dark-zone lighting with Seam Stone light pools. Bloom on bright areas and a soft contrast curve add punch at full quality. Heavier effects switch off automatically on slower devices.
- Level design that uses the moves: thorn patches and timed ember/steam vents (knockback, no health loss), bramble gates that need a dash or pound to open (+3 acorns), crumbling slabs in the caves and ruins, and updraft gusts with orb trails in the Sky Kingdom and ruins
- Three acorn upgrades in Sable's shop (Longer dash, Double dash, Titan pound); a Ground Pound shockwave staggers nearby mini-bosses so you can stomp them; alert Burrs charge when you get close; hit-stop on big hits; companions cheer your wins; each new region opens with a title card and a paper-fold sweep
- Synthesised sound (jump, pound, dash, pickups, chains, bosses, region fanfares) and a quiet generative music bed per region; press **M** or the speaker button to mute
- Wind-swept grass that parts around Bristle and the Burrs
- Per-region weather (pollen, leaves, sprinkles, embers, snow, bubbles), colour grading, screen shake and impact FX
- Sketchbook of quests with Renown ranks, more shop items, and automatic saving (Continue on the title screen)

## Art pipeline
All art is painted procedurally at load time (brush strokes, grain, rim light, outlines) into layered canvases: backgrounds, midground, props, characters, foreground foliage, and FX. It is **not** hand-painted bitmap art.

- Click **Art manifest** in the game to see every asset (id, file name, size, alpha, use, frames, source) and download `asset_manifest.json`.
- To replace any generated asset with a real painted PNG, set `window.ARTPACK = { "char_bristle_run_0": "art/bristle_run_0.png", ... }` before the script runs. Keep the same pixel size as listed in the manifest.
- All assets are original and project-owned; no third-party art is used.

## Design document
The full game design document (all 19 sections) was written alongside this build.
