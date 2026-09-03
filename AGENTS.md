# AGENTS.md

## Project

Asteroids clone — vanilla HTML5 Canvas + JS, zero dependencies, no build step.

## Files

- `index.html` — single entry, loads `game.js`
- `game.js` — all game logic (ship, asteroids, bullets, particles, HUD, game loop)

## Run

Open `index.html` in a browser, or: `npx serve .`

## Architecture

- Single-file game engine in `game.js` (~423 lines)
- Game loop: `requestAnimationFrame` → `update(dt)` → `draw()`
- States: `playing` → `dead` (respawn timer) → `gameover`
- Space is toroidal (entities wrap at canvas edges)
- Asteroids split into 2 smaller pieces on destruction (size 3→2→1)

## Conventions

- All rendering via `ctx` (Canvas 2D), no DOM manipulation beyond setup
- Input via `keys` map + `justPressed` for single-fire actions
- Entity classes: `Ship`, `Asteroid`, `Bullet`, `Particle` — each has `update(dt)`, `draw()`, and `dead` flag
- Constants at top of file: `RADII`, `SPEEDS`, `POINTS` arrays indexed by asteroid size
