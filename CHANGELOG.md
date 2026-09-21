# CHANGELOG — Gillsystems_games

All notable changes to Gillsystems games. Format based on Keep a Changelog.

## [Unreleased] — 2026-09-20

### Fixed — Deadwood_alien_shooter.html

- **Restart mechanic added (was a dead end).** Game over previously showed "JACK HAS FALLEN" with no way back into the game short of a page reload. Added an "⚡ RIDE AGAIN" button (HUD, styled) plus `restartGame()` / `resetAliens()`: clears bullets and effects from the scene, respawns the wave-1 alien roster, resets health/ammo/kills/score/wave/player position/yaw-pitch, refreshes HUD, and re-engages pointer lock. Game-over panel now also reports kills and wave reached.
- **Alien body geometry misplacement.** `alien()` chained `.position.y` on the return value of `Object3D.add()`, which returns the *parent* group, not the added mesh — both body spheres were being dropped at the alien's feet (and twice clobbered the group's own position). Bodies are now explicitly positioned (y=0.9 / y=1.5) before being added.
- **Bullet tunnelling through aliens.** Hit detection sampled a single point per frame against a 100 u/s tracer — at low FPS one frame step (up to 10 units) jumped clean past the 1.5-unit hit radius. Replaced point sampling with a swept-segment test (closest point on the bullet's per-frame travel segment to the alien center), so hits register at any framerate.
- **Zombie wave timer.** The 2-second `setTimeout` that spawns the next wave could fire after the player died (spawning aliens into a dead game). The callback now bails if `state.gameOver`.
- **QA hook.** Exposed `window.__dw` (state, aliens, bullets, shoot, restartGame, etc.) for automated verification of the core loop.

### Verified

Core loop exercised live in headless Chrome via CDP: start → hit (60→10 hp) → kill (+100 score, kill feed) → wave 2 transition (10 aliens, HUD update) → reload (6/6) → death (game-over panel + restart button) → restart (full state reset) → post-restart live fire. Zero JS console exceptions.

---

> **"For which of you, desiring to build a tower, does not first sit down and count the cost, whether he has enough to complete it?"** — Luke 14:28 (ESV)
>
> Chosen because this session began with diagnosis before a single edit — reproducing the breakage, root-causing it, and verifying the repair in a live browser before claiming victory. Counting the cost first is how towers get finished.
