# Particle Life — Build Plan

## What This Is

A self-contained Particle Life simulation deployed as a single static HTML file.
No build step, no dependencies, no frameworks. Vanilla JS + Canvas API only.

## Done When

- `index.html` opens in a browser and renders at 60fps
- Particles are colored by species and exhibit emergent lifelike behavior
- Tap to randomize rules, double-tap to reset positions
- Mobile-first, fills full viewport on iPhone 11 Pro Max (414×896pt)
- No console errors

## How Particle Life Works

- N particles across K species (distinguished by color)
- A K×K attraction matrix: values -1.0 (strong repulsion) to +1.0 (strong attraction)
- Force falloff: distance < `r_min` → always repel; `r_min` ≤ distance < `r_max` → apply matrix force with smooth falloff
- Each frame: accumulate forces → update velocities with dampening → update positions
- Wrap-around boundaries

## Defaults

- 6 species, 80 particles per species (480 total)
- `r_max`: 120px, `r_min`: 20px
- Velocity dampening: 0.85 per frame
- Force scale: 0.5

## File Structure

```
particle-life/
├── index.html     ← deliverable (HTML + CSS + JS all inline)
├── AGENTS.md
└── docs/
    └── 2026-03-17-particle-life-plan.md  ← this file
```

## Steps

- [ ] 1. Create `AGENTS.md`
- [ ] 2. Build `index.html` — full-viewport canvas, dark background (`#0a0a0f`), UI overlay
- [ ] 3. Implement simulation: species arrays, attraction matrix, force loop, wrap-around
- [ ] 4. Implement render loop: `requestAnimationFrame`, semi-transparent clear for trail effect (`rgba(0,0,0,0.15)`), particles as colored circles (4–6px)
- [ ] 5. Add UI: species color legend, live FPS counter, "Randomize Rules" + "New Simulation" buttons
- [ ] 6. Add touch: `touchstart` on buttons, prevent scroll on canvas
- [ ] 7. Mobile polish: viewport meta tag, canvas resizes on orientation change, buttons min 44×44pt
- [ ] 8. Verify: 60fps, no console errors, works on mobile viewport

## Visual Details

- Background: `#0a0a0f`
- Particle colors: vivid and distinct — red, cyan, yellow, magenta, lime, orange
- Trail: clear with `rgba(0,0,0,0.15)` each frame instead of solid clear
- UI overlay pinned to bottom of screen

## Mobile

- `<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">`
- Canvas: `window.innerWidth × window.innerHeight`, resize on `orientationchange`
- Buttons large enough to tap (min 44×44pt), text min 16px

## Methodology

Follow the engineering standards in `refs/DEVELOPMENT.md` (in the Zocots workspace root).
Key points: write tests before implementation where applicable, explicit "Done When" conditions,
no committed broken state.

## Compaction Recovery

Re-read this file and check what files exist in this directory before continuing.
Do not restart completed steps.
