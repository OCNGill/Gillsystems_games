<p align="center">
  <img src="https://raw.githubusercontent.com/OCNGill/Gillsystems-AMD-Radeon-llama-cpp-Update-AI-Stack/main/Gillsystems_logo_stuff/Gill%20Systems%20Logo.png" alt="Gill Systems Logo" width="800">
</p>

# Gillsystems Games

> *"Systems should serve humans" — games are the delivery vehicle.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Portfolio](https://img.shields.io/badge/Games-4-orange)](#game-portfolio)
[![Engine](https://img.shields.io/badge/Engine-HTML5%20Canvas%20%7C%20WebGL-blue)](#tech-stack)
[![Live](https://img.shields.io/badge/Live-gillsystems.net-brightgreen)](https://gillsystems.net)
[![Cloud deps](https://img.shields.io/badge/Cloud%20deps-none-success)](conductor/product-guidelines.md)
[![Docs](https://img.shields.io/badge/7D-Documented-lightgrey)](CHANGELOG.md)

**Gillsystems_games** is the umbrella repository for the Gillsystems open-source game
portfolio: a set of small, fully offline, browser-playable games plus the product
definition, track registry and agent roster that govern them. Every game ships under the
MIT license, runs with zero cloud dependencies, and deploys to
[gillsystems.net](https://gillsystems.net).

This repo holds the portfolio documentation and **Deadwood_alien_shooter.html** — the
other games live in their own repositories under the same GitHub org.

## Contents

- [Game Portfolio](#game-portfolio)
- [What's In This Repo](#whats-in-this-repo)
- [Architecture](#architecture)
- [Quick Start](#quick-start)
- [Tech Stack](#tech-stack)
- [Product Guidelines](#product-guidelines)
- [Development Workflow](#development-workflow)
- [Quality Assurance](#quality-assurance)
- [Deployment Map](#deployment-map)
- [Documentation & 7D](#documentation--7d)
- [Agent Roster](#agent-roster)
- [License](#license)
- [Support / Donate](#support--donate)

---

## Game Portfolio

| Game | Status | Engine | Where |
|---|---|---|---|
| **Deadwood alien shooter** | **LIVE** on gillsystems.net | three.js r157 (vendored) | This repo — `Deadwood_alien_shooter.html` |
| **Escape from Duxbury** | **LIVE**, fixes applied | Canvas 2D / vanilla JS | [`Escape-From-Duxbury`](https://github.com/OCNGill/Escape-From-Duxbury) |
| **Pilgrim Trail** | MIT licensed, pending deploy | Canvas / JS | [`Pilgrim-Trail-Game`](https://github.com/OCNGill/Pilgrim-Trail-Game) |
| **The Commander** | UE 5.8 project initialized | Unreal Engine 5.8 + Blender | [`The-Commander-Boomer-Shooter`](https://github.com/OCNGill/The-Commander-Boomer-Shooter) — target: itch.io / Steam |

## What's In This Repo

```
Gillsystems_games/
├── Deadwood_alien_shooter.html   # Single-file three.js alien shooter (the playable game)
├── vendor/
│   └── three.umd.js              # three.js r157 vendored — offline, no CDN
├── conductor/                    # Product definition, tracks, workflow, tech stack
│   ├── product.md                # What / Why / Architecture / Quick Start / Deployment
│   ├── product-guidelines.md     # Release rules for every game
│   ├── tracks.md                 # Active / completed / future track registry
│   ├── tech-stack.md             # Approved rendering + language stack
│   ├── workflow.md               # Develop → QA → CHANGELOG → deploy → tracks
│   └── CHANGELOG.md              # Symlink to the repo-root CHANGELOG.md (one log, zero drift)
├── CHANGELOG.md                  # 7D change log (Keep-a-Changelog format, ESV verse per milestone)
├── ROSTER.md                     # Agents covering the games portfolio
└── LICENSE                       # MIT
```

## Architecture

```
                    GILLSYSTEMS GAMES PORTFOLIO

  This repo (umbrella)                     Sibling repos (OCNGill org)
  ┌───────────────────────────┐             ┌───────────────────────────────┐
  │ Deadwood_alien_shooter.html│            │ Escape-From-Duxbury/          │
  │   └── vendor/three.umd.js  │            │   Canvas/JS point & click     │
  │ conductor/ (governance)    │            │ Pilgrim-Trail-Game/           │
  │ CHANGELOG.md  ROSTER.md    │            │   Canvas/JS resource survival │
  └─────────────┬─────────────┘            │ The_Commander_Boomer_Shooter/ │
                │                           │   Unreal Engine 5.8 + Blender │
                │                           └───────────────┬───────────────┘
                │                                           │
                └───────────────┬───────────────────────────┘
                                ▼
                 local file://  ──▶  gillsystems.net (live)
                                       └──▶ GitHub Pages (static mirror)
```

## Quick Start

1. Clone the repository: `git clone git@github.com:OCNGill/Gillsystems_games.git`
2. Open `Deadwood_alien_shooter.html` in any modern browser — no build step, no server, no network (three.js is vendored).
3. Read [`conductor/tracks.md`](conductor/tracks.md) to see what is active and what is next.
4. Play the sibling games from their own repos — links in the [portfolio table](#game-portfolio).
5. When a game changes, deploy it to gillsystems.net through the website repo and update the conductor tracks.

## Tech Stack

- HTML5 Canvas / WebGL (three.js for Deadwood)
- Vanilla JavaScript (ES6 modules)
- CSS custom properties for theming
- **No build step** — direct browser execution

## Product Guidelines

Every game in the portfolio follows the rules in
[`conductor/product-guidelines.md`](conductor/product-guidelines.md):

- MIT license for all public releases
- Zero cloud dependencies — fully offline playable
- Canvas/WebGL for rendering, no heavy frameworks
- Sovereign AI integration optional (local llama.cpp only)
- QA verified in headless Chrome before deploy

## Development Workflow

1. Develop in the game's own repo.
2. QA in headless Chrome (CDP).
3. Update `CHANGELOG.md` with an ESV verse for the milestone.
4. Deploy to gillsystems.net.
5. Update `conductor/tracks.md`.

## Quality Assurance

Core loops are exercised live in headless Chrome over CDP before anything ships —
start → hit → kill → wave transition → reload → death → restart, with zero JS console
exceptions. The Deadwood fixes (restart mechanic, alien body placement, swept-segment
bullet collision, wave-timer guard, `window.__dw` QA hook) were all verified that way;
see [`CHANGELOG.md`](CHANGELOG.md) for the recorded runs.

## Deployment Map

| Target | Role |
|---|---|
| [gillsystems.net](https://gillsystems.net) | Live deployment |
| GitHub Pages | Static hosting mirror |
| Local `file://` | Development and QA |

## Documentation & 7D

- [`CHANGELOG.md`](CHANGELOG.md) — change log in `## [YYYY-MM-DD]` format, newest first, with an ESV verse and reason per milestone.
- [`ROSTER.md`](ROSTER.md) — agents covering the games portfolio, plus per-game repo status.
- `conductor/` — product definition, track registry, workflow and tech stack for the portfolio.
- Fleet governance: `MASTER_CHARTER.md` in [Gillsystems-Commanders-Hermes](https://github.com/OCNGill/Gillsystems-Commanders-Hermes) and the canonical agent roster in the `Agents` repo.

## Agent Roster

| Agent Name | Role | Games Covered |
|---|---|---|
| Commander Hermes | Oversees all game repos | All |
| Geordi | Architecture for Boomer Shooter (UE5) | The_Commander_Boomer_Shooter |
| Liara | Research (game engines, assets) | All |
| Coder | Code execution (JS/UE5/Blender) | All |
| Scribe | 7D documentation compliance | All |
| Sentinel | Security audit (no cloud deps) | All |
| Major-Gaben | Deck/HTPC deployment testing | All |

Full detail lives in [`ROSTER.md`](ROSTER.md).

## License

MIT — © 2026 Stephen Gill / Gillsystems. See [`LICENSE`](LICENSE).

## Support / Donate

If these games give you a good time, fuel the next one:

**[paypal.me/gillsystems](https://paypal.me/gillsystems)**