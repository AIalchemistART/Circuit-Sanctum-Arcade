# Vibeverse Arcade

Vibeverse Arcade is a browser game: an isometric pixel room you walk through, with arcade cabinets that open other games in the browser. It continues the earlier [AI Alchemist's Lair](https://github.com/AIalchemistART/AIalchemistsLAIR) and lives in this repository (`Circuit-Sanctum-Arcade`).

**Live site:** GitHub Pages at [https://aialchemistart.github.io/Circuit-Sanctum-Arcade/](https://aialchemistart.github.io/Circuit-Sanctum-Arcade/)

[vibeversearcade.com](https://vibeversearcade.com) forwards to that GitHub Pages URL.

The published site is the `gh-pages` branch. The default branch, `main`, is an earlier snapshot of the same room. Both use the same engine. `gh-pages` adds more cabinets, touch controls, a web app manifest, and a visitor counter.

## How to play

Move with **WASD** or the **arrow keys**. **Space** jumps. Walk up to a cabinet, jukebox, television, spellbook, trophy, or portal and press **Enter**. **Escape** closes a cabinet menu. **M** toggles the minimap. Middle-mouse drag pans the camera.

Cabinet menus launch the selected game at its own URL. Those games are not stored in this repository. **Neon Swarm** opens [Space Invaders](https://aialchemistart.github.io/SpaceInvaders/) on GitHub Pages.

## Games

The first cabinet (`arcadeEntity.js`) always uses the list below. `arcadeManager.js` also contains a MakeCode list (Space Invaders, Tetris Classic, Galaga, Pac-Man), and that list is not read by the cabinet.

| Cabinet title | Opens |
| --- | --- |
| Neon Requiem | https://aialchemistart.github.io/NeonRequiem/ |
| Synth-Pocalypse Now! | https://aialchemistart.github.io/Synthpocalypse-Now-/ |
| Pixel Survivor | https://pixel-survival.replit.app/ |
| Neon Swarm | https://aialchemistart.github.io/SpaceInvaders/ |
| Pixel Farmer's Quest | https://pixel-harvest.replit.app/ |

The second cabinet reads its list from `arcadeManager2.js`:

| Cabinet title | Opens |
| --- | --- |
| Gnome Mercy | https://gnome-mercy.vercel.app/ |

`gh-pages` adds cabinets 3–12. Titles below are the strings in those manager files. Several later cabinets reuse a title while pointing at a different URL.

| Branch file | Cabinet title in code | Opens |
| --- | --- | --- |
| `arcadeManager3.js` | Fly Pieter | https://fly.pieter.com/ |
| `arcadeManager4.js` | The Agency | https://the-agency.joshse.com/ |
| `arcadeManager5.js` | VibeATV | https://vibeatv.com/ |
| `arcadeManager6.js` | Vibe Disc | https://vibedisc.com/ |
| `arcadeManager7.js` | Vibe Disc | https://copilot.microsoft.com/wham?features=labs-wham-enabled |
| `arcadeManager8.js` | Indiana Bones | https://indiana-bones.vercel.app/ |
| `arcadeManager9.js` | Indiana Bones | https://www.gatesofaetheria.com/ |
| `arcadeManager10.js` | Indiana Bones | https://www.vector-tango.com/ |
| `arcadeManager11.js` | Indiana Bones | https://astro.gobienan.com/ |
| `arcadeManager12.js` | Zans Cards | https://zanscards.com/ |

## The room

The walkable floor is one isometric room, 200 by 80 grid cells (`scene.js`). You start as a wizard sprite.

`sceneData.js` also defines three scene records:

- **startRoom** — the room the door data describes. Its north door leaves this site for the AI Alchemist's Lair at https://aialchemistart.github.io/AIalchemistsLAIR/. The west door was removed from that exit list.
- **circuitSanctum** — scene data only. It is not wired as a destination from the start-room door.
- **neonPhylactery** — scene data only, same situation.

Objects placed in the room from `main.js` include wall and ceiling signs, four rugs, two couches, a jukebox (SoundCloud playlist overlay), a television (YouTube playlist overlay), a spellbook overlay, a trophy that opens https://jam.pieter.com, and vibe portals. `gh-pages` adds further signs, rugs, a second spellbook, and the extra cabinets.

## Tech stack

- Vanilla JavaScript, loaded as ES modules from `index.html` → `main.js`
- Canvas 2D isometric rendering (`isometricRenderer.js`, `scene.js`)
- Web Audio oscillators for cabinet sounds (no audio files in this branch)
- No bundler. `main` has no `package.json`. The `gh-pages` branch has a `package.json` whose start script is `serve .`. The live visitor counter is computed in the browser and does not call a backend.

Because the game uses ES modules, open it through a local static server. Opening `index.html` as a `file://` URL will not load the modules.

## Run it locally

From the repository root:

```bash
python3 -m http.server 8080
```

Then open http://localhost:8080/

Any other static server works the same way (`npx serve .` on the `gh-pages` branch).

## Status

The public site is GitHub Pages from the `gh-pages` branch. `main` still runs the room and the two cabinets above, and it does not include the later cabinets or the touch-control and visitor-counter files.

Scene records for Circuit Sanctum and Neon Phylactery are still in `sceneData.js`. They are not separate walkable rooms on the live floor. The north door is an exit to the Lair, which is the previous project, not a second arcade room inside this build.

There is no automated test suite in this repository.

## License

Vibeverse Arcade is released under the MIT License. See [LICENSE](LICENSE).

Copyright (c) 2025–2026 Matthew Walker (AI Alchemist).
