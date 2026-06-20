# River Raid — HTML5

A faithful, single-file HTML5 remake of the classic vertical-scrolling river shooter,
modeled on the Atari 8-bit (800XL) version. Pure vanilla JavaScript + Canvas — no build
step, no dependencies. Just open `index.html`.

## Play

Open `index.html` in any modern browser, or play the published version on GitHub Pages
(see below).

### Controls

**Desktop**
- ◀ ▶ — steer
- ▲ — accelerate, ▼ — brake
- Space — fire
- P — pause

**Mobile**
- Tilt the device left/right to steer (tap the **TILT ⟳** badge to re-center to your hold)
- On-screen buttons for fire / accelerate / brake
- Tilt steering is auto-calibrated to however you're holding the phone when you press Start

## Gameplay

Fly up the river, shoot tankers, helicopters, jets and bridges, and fly over fuel depots
(don't shoot them) to refuel. Crashing into the banks, an enemy, or a bridge costs a plane.
Each bridge is a checkpoint: destroy it to advance, and if you crash you restart at the
last bridge. From bridge 4 onward, hot-air balloon blockades appear.

## Authenticity notes

- River and object generation follow Carol Shaw's original algorithm (16-bit LFSR section
  generator, one object per block, the difficulty-scaled enemy curve, and the original
  ship/helicopter/jet enemy mix).
- Map geometry was extracted from the original game's map data.
- The player jet and score font match the sprites in the original ROM.

## Publish to GitHub Pages

This repo is ready to publish. The included workflow (`.github/workflows/deploy.yml`)
deploys the site to GitHub Pages on every push to `main`.

One-time setup with the GitHub CLI:

```bash
# from this folder
git init -b main
git add .
git commit -m "River Raid HTML5"

# create a public repo and push (requires: gh auth login)
gh repo create river-raid --public --source=. --push

# enable Pages to build from the GitHub Actions workflow
gh api -X POST repos/{owner}/river-raid/pages -f build_type=workflow
```

Then your game is live at `https://<your-username>.github.io/river-raid/`.

(If you prefer the web UI: create a public repo, push these files, then
**Settings → Pages → Build and deployment → Source: GitHub Actions**.)
