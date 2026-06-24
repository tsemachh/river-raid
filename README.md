# River Raid — HTML5

A faithful, single-file HTML5 remake of the classic vertical-scrolling river shooter,
modeled on the Atari 8-bit (800XL) version. Pure vanilla JavaScript + Canvas — **no build
step, no dependencies, no frameworks**. Just open `index.html`.

**▶ Play it live:** https://tsemachh.github.io/river-raid/

Installable as a Progressive Web App — on a phone, use your browser's *Add to Home Screen*
and it runs full-screen and offline like a native app.

## Controls

**Desktop**

| Key | Action |
| --- | --- |
| ◀ ▶ | steer |
| ▲ | accelerate |
| ▼ | brake |
| Space | fire |
| P | pause |

**Mobile**

- Tilt the device left/right to steer — auto-calibrated to however you're holding the phone when you press Start (tap the **TILT** badge to re-center).
- On-screen buttons for fire / accelerate / brake.
- Tap the **✕** (top-right) to quit a round back to the title — no keyboard needed.
- Haptic buzz on crashes, bridge kills and refuels (Android; iOS Safari blocks the Vibration API).

## Gameplay

Fly up the river, shoot tankers, helicopters, jets and bridges, and fly over fuel depots
(don't shoot them) to refuel. Crashing into the banks, an enemy, or a bridge costs a plane.
Each bridge is a checkpoint: destroy it to advance, and if you crash you restart at the last
bridge. Helicopters hold their fire until stage 4, then grow more aggressive each stage.
Pick a starting bridge on the title screen to jump ahead.

## Authenticity notes

- The river map (bank shapes, islands and bridge spacing) and the enemy distribution are
  derived from the original Atari 800XL River Raid map.
- The player jet and score font match the sprites in the original ROM.
- Sound is synthesized live with the Web Audio API — the engine is the classic rising
  "plane taking off" jet roar.

## Tech / standards

- Single static `index.html` (HTML + CSS + JS inline), plus a small PWA layer.
- **PWA:** `manifest.json` + `service-worker.js` (offline-first app-shell cache) + app icons.
- Mobile-first: responsive full-bleed canvas, `viewport-fit=cover`, tilt controls, fullscreen.
- No external requests at runtime — fully self-contained and offline-capable.

```text
.
├── index.html            # the entire game
├── manifest.json         # PWA manifest
├── service-worker.js     # offline app-shell cache
├── icons/                # app icons (192 / 512 / maskable)
├── .github/workflows/    # GitHub Pages deploy
├── LICENSE               # MIT
└── README.md
```

## Develop

There's nothing to build — open `index.html` directly, or serve the folder:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

(A server, rather than `file://`, is needed for the service worker / PWA to register.)

## Deploy

The repo auto-deploys to GitHub Pages on every push to `main` via
`.github/workflows/deploy.yml`:

```bash
git add .
git commit -m "your message"
git push origin main
```

The site updates at https://tsemachh.github.io/river-raid/ a minute or two later.

## License

[MIT](LICENSE). Independent, non-commercial fan remake for educational purposes; not
affiliated with or endorsed by the River Raid trademark holder.
