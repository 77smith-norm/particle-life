# AGENTS.md — Particle Life

## What This Is
A self-contained Particle Life simulation as a single static HTML file. Vanilla JS + Canvas API only. No build step, no dependencies, no frameworks.

## Build & Test
- No build step — just open `index.html` in a browser
- Verify: 60fps, no console errors, works on mobile viewport
- Test on iPhone 11 Pro Max viewport (414×896pt)

## Project Structure
- `index.html` — the deliverable (HTML + CSS + JS all inline)
- `docs/` — plan file: `2026-03-17-particle-life-plan.md`

## Done When
- `index.html` opens in a browser and renders at 60fps
- Particles are colored by species and exhibit emergent lifelike behavior
- Tap to randomize rules, double-tap to reset positions
- Mobile-first, fills full viewport on iPhone 11 Pro Max (414×896pt)
- No console errors

## Key Parameters
- 6 species, 80 particles per species (480 total)
- `r_max`: 120px, `r_min`: 20px
- Velocity dampening: 0.85 per frame
- Force scale: 0.5
- K×K attraction matrix: values -1.0 to +1.0
- Force falloff: distance < r_min → always repel; r_min ≤ distance < r_max → matrix force with smooth falloff
- Wrap-around boundaries

## Visual Details
- Background: `#0a0a0f`
- Particle colors: vivid — red, cyan, yellow, magenta, lime, orange
- Trail: `rgba(0,0,0,0.15)` clear each frame
- UI overlay pinned to bottom

## Mobile
- Viewport meta: `width=device-width, initial-scale=1, user-scalable=no`
- Canvas: `window.innerWidth × window.innerHeight`, resize on orientation change
- Buttons min 44×44pt, text min 16px

## Compaction Recovery
Re-read `docs/2026-03-17-particle-life-plan.md` and check what files exist before continuing. Do not restart completed steps.
