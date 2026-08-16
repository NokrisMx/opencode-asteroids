# Repository Guide

## Workflow

- This is a dependency-free static app: there is no install, build, package manifest, or configured lint/test/typecheck command.
- Run it by opening `index.html`, or use `npx serve .` from the repository root and visit `http://localhost:3000`. `serve` is an optional, unpinned external tool.
- Use `node --check game.js` for a focused syntax check. Do not execute `game.js` with Node; it accesses DOM and Canvas APIs at load time.
- Browser-test gameplay changes: rotation/thrust, one shot per Space press, edge wrapping, asteroid splitting/scoring, death/respawn, level advance, and Space restart after game over.

## Architecture And Gotchas

- `index.html` creates the canvas before loading `game.js` as a classic script; `game.js` contains the entire application and starts immediately with `initGame()` plus `requestAnimationFrame(loop)`.
- Canvas size is duplicated in `index.html` (`width`/`height`) and `game.js` (`W`/`H`); update both together.
- Input has separate held (`keys`) and edge-triggered (`justPressed`/`pressed`) state. Space intentionally fires once per key press and also restarts from `gameover`.
- The frame delta is capped at `0.05` seconds. Gameplay and visuals use `Math.random()`, so browser runs are nondeterministic.
- The game states are `playing`, `dead`, and `gameover`; respawn and restart behavior belongs in that state flow rather than in rendering code.
- Power-ups are implemented: speed boost (V), triple shot (3), and shield (S). All three drop randomly from destroyed asteroids (10% each, 30% total) and last 5 seconds. The shield absorbs one asteroid impact.
