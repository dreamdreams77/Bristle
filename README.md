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
- 19 honey crates to smash (Ground Pound or Air Dash), acorn chains that pay bonus acorns, and a fold-map strip showing your progress and Seam Stones
- 23 roaming Burrs across regions 1-12: stomp, dash into or ground-pound them (side contact just knocks you back). Clear a region's patrol for +3 acorns; chain stomps and mushroom bounces without landing for Air Combos (+1 acorn every 3). Progress is saved.
- Depth-of-image pass: a directional light per region (rim light and long cast shadow on Bristle, lit lips, ambient occlusion and cast shadows on ground and platforms), hazy far ridges, cave ceilings, foreground blur and bokeh, sun/moon glow with shafts, and dark-zone lighting with Seam Stone light pools. Bloom on bright areas and a soft contrast curve add punch at full quality. Heavier effects switch off automatically on slower devices.
- Level design that uses the moves: thorn patches and timed ember/steam vents (knockback, no health loss), bramble gates that need a dash or pound to open (+3 acorns), crumbling slabs in the caves and ruins, and updraft gusts with orb trails in the Sky Kingdom and ruins
- Three acorn upgrades in Sable's shop (Longer dash, Double dash, Titan pound); a Ground Pound shockwave staggers nearby mini-bosses so you can stomp them; alert Burrs charge when you get close; hit-stop on big hits; companions cheer your wins; each new region opens with a title card and a paper-fold sweep
- Trees, lollipops, reeds, kelp and other props sway in the wind and lean away from Bristle; the Moonlit Marsh and Tidal Deep have wet-floor reflections, the marsh pits fill with rippling water, and the Tidal Deep gets caustic light and a shimmering surface
- Synthesised sound (jump, pound, dash, pickups, chains, bosses, region fanfares) and a quiet generative music bed per region; press **M** or the speaker button to mute
- Wind-swept grass that parts around Bristle and the Burrs
- Per-region weather (pollen, leaves, sprinkles, embers, snow, bubbles), colour grading, screen shake and impact FX
- Sketchbook of quests with Renown ranks, more shop items, and automatic saving (Continue on the title screen)

## Art pipeline
All art is painted procedurally at load time (brush strokes, grain, rim light, outlines) into layered canvases: backgrounds, midground, props, characters, foreground foliage, and FX. It is **not** hand-painted bitmap art, but every one of the 127 assets can be replaced by a real painted PNG, with no code changes.

### Painted art workflow
1. In the game, click **Art manifest > Download art template**. You get `bristle_art_template.zip`: every current asset as a PNG named after its id (`char_bristle_run_0.png`, `bg_ground_3.png`, ...), plus `asset_manifest.json` and a ready-made `pack.json`.
2. Paint over the PNGs. Keep the file names. Keep transparency where the manifest says `alpha: yes`.
3. Use them any of these ways:
   - **Drop the PNGs onto the game page**, or **Art manifest > Load painted PNGs**. They are saved in your browser (IndexedDB) and reapplied on every visit. **Clear painted art** removes them.
   - **Ship them with the game**: put the files in an `art/` folder next to `index.html` together with `art/pack.json` (`{"scan":true}` loads `art/<id>.png` for every asset; or list `{"assets":{"<id>":"file.png"}}`). Works on GitHub Pages / any web host. Use `?art=path/to/pack.json` for a different pack.
   - **Inline**: set `window.ARTPACK = { "char_bristle_run_0": "art/bristle_run_0.png", ... }` before the script runs (works from `file://` too).
4. The Art manifest screen shows which assets are painted (🎨) and warns about size mismatches.

### Sizes and rules
- Same size as the manifest, **or an exact 2x/3x/4x multiple** for crisper art (the game keeps the extra resolution). Anything else is resampled to the manifest size and flagged.
- Tileable textures (`bg_ground_*`, `mid_lip_*`, `fx_grain`) are always used at the manifest size and must tile seamlessly; the game rebuilds their patterns when you swap them.
- `fg_leaf` is blurred by the game for depth of field, so paint it sharp.
- Characters are drawn centred on the same baseline as the template; keep feet where the template has them.
- Props that sway (trees, lollipops, reeds, kelp, mushroom/dream/frost props) are sheared from the ground line, so painted versions sway automatically; keep the trunk base at the bottom of the sprite.
- Water and hazards are art-pack assets too: `fx_water_body` (marsh pit water, tiles horizontally), `fx_caustics` (Tidal Deep light, tiles both ways), `fx_vent_ember`/`fx_vent_steam`, `fx_gust`, `prop_vent`, `prop_thorn`, `prop_gate` (tiles vertically), `prop_crate`, `prop_orb`, `char_burr_spikes` (rotates) and `char_burr_body` (the Burr's eyes are drawn in-engine so they keep following Bristle).
- All assets are original and project-owned; no third-party art is used.

## Design document
The full game design document (all 19 sections) was written alongside this build.
