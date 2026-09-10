# Demiurge Terminal

A procedural star-system simulator that fits in one HTML file. Type a seed phrase and it builds a star, its planets, their continents, weather, rivers, life and history — then lets you watch civilisations rise, fight, launch for other worlds, and leave a chronicle behind.

**Play it:** open `index.html` in a browser, or visit https://demiurge.silaseacret.com.

## About this entry

This was built for **SACM's Vibecoding Night**, a competition to produce the coolest or most interesting piece of software using *only* AI. The rules: no reading the code, no editing the code, no reviewing it — prompts only. Every line here was written by an AI (Claude, via Claude Code) in response to natural-language requests. The human's contribution is the prompts, the feedback ("I can no longer click things?"), and the ideas about what would be interesting.

That constraint shaped the result. Bugs were found by describing symptoms, not by reading stack traces. Features were requested as outcomes ("I want to see the other planets in the sky and click on them") and the AI decided the physics, the data structures and the shaders. The whole thing lives in a single file with no build step because that was the easiest thing for an AI to keep whole across dozens of rounds of changes.

## What it does

Everything on screen is generated from the seed. No textures, no data files, no pre-authored content.

**The system.** A star is drawn with a real spectral class (M through A) and sometimes a companion; its luminosity fixes the habitable zone. Planets are spaced outward, and what each one *is* follows from where it landed — molten close in, rock and water in the zone, ice and gas giants past the snow line, sometimes a debris belt, plus one to three comets on long eccentric orbits.

**Each world.** Tectonic plates are seeded and drifted; their collisions raise mountain belts, rifts open, seafloor subsides away from spreading ridges, and hotspots leave island chains. Rivers erode the result. Prevailing winds carry moisture inland and rain it out against mountains, so rain shadows and deserts fall where they should. Ocean currents move heat poleward along coasts. Biomes, ice caps, snowlines and coastlines are decided per pixel from the temperature and rainfall models, so changing the climate changes the map live.

**History.** A biosphere grows if the world can support one. Civilisations found capitals at the best sites, expand, found cities, advance through technological eras, trade along teal sea lanes, declare wars fought along red fronts, suffer plagues and golden ages, put satellites in orbit and bases on moons, and eventually launch for other planets in the system. Every world runs at once; the ones you're not watching run a lighter model in the background and post only headlines to the chronicle. Slow orbital wobbles bring ice ages on their own, and sea level falls as ice locks up water.

**Things to try.** Rewind the timeline by dragging it. Fire an impactor at a capital. Start a two-thousand-year terraforming campaign on a cold world. Fly to a moon. Zoom out until the neighbouring planets appear in the sky, then click one. Open the codex and copy out the whole system as text.

## How to use it

The page opens into a **field guide** the first time; press `?` to bring it back. The short version:

| Where | What |
|---|---|
| **System** (top left) | The star, its habitable zone, and every body. Click a planet to travel there. *Orrery* shows the whole system; *Codex* writes it up. |
| **Genesis** | Seed phrase. Same phrase, same universe. |
| **Lithosphere / Atmosphere** | Sliders for plates, erosion, sea level, insolation, greenhouse, obliquity, water. Some rebuild the planet; the rest apply instantly. |
| **Instrumentation** | Nine surface channels (natural, elevation, temperature, rainfall, biomes, plates, political, habitability, currents) and overlay toggles. |
| **Intervention** | Click-tools: probe, uplift, subside, impactor, hotspot, seed life, uplift a civilisation. Plus snowball, runaway greenhouse, and terraforming campaigns. |
| **Transport** (bottom) | Play/pause, time rate, the scrubbable timeline, world/system view, camera tracking, sound. |
| **Right rail** | Surface probe (hover or click the globe), map, registry of polities, the chronicle. |

Mouse: drag to orbit, scroll to zoom, click to use the selected tool. Keys: `Space` pause, `1`–`9` channels, `V` orrery, `S` tracking/free orbit, `C` codex, `M` sound, `H` hide panels, `R` new random system, `Esc` back.

Detail arrives with zoom: continents and the other planets far out, cities closer, satellites in orbit up close.

## Running it

It's a static page. Any of these work:

- Double-click `index.html` (or `demiurge.html`, same thing).
- Serve the folder: `python3 -m http.server 8000` then open http://localhost:8000/.
- Push to GitHub and enable Pages.

It loads two things from the network: [three.js](https://threejs.org/) r128 from cdnjs and two typefaces from Google Fonts. Everything else is inline. WebGL is required; a discrete GPU is not, but the *Render quality* setting is there for laptops.

`planet.html` is the same content without the `<!DOCTYPE>` wrapper — it's the form used by the claude.ai artifact host, which adds its own. Use `index.html` everywhere else.

## Files

| File | |
|---|---|
| `index.html` | The game. Open this. |
| `demiurge.html` | Identical copy. |
| `planet.html` | Body-only version for artifact hosting. |

## Credits

Written entirely by Claude (Anthropic) — Opus 5 and Fable 5.1 — in Claude Code, from prompts by [eekrats](https://github.com/eekrats). Simplex noise after Gustavson; Milankovitch, Whittaker biomes, stream-power erosion and the habitable-zone bounds are the usual textbook forms, implemented from memory by the model.
