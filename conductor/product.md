# Gillsystems Games — Product Definition

## What
Portfolio of open-source browser games published on gillsystems.net. Currently: Deadwood_alien_shooter.html, Escape-From-Duxbury, Pilgrim-Trail-Game, The_Commander_Boomer_Shooter.

## Why
"Systems should serve humans" — games are the delivery vehicle. Each game demonstrates the sovereign AI stack (local inference, zero cloud) and serves as a portfolio piece for the Gillsystems brand.

## Architecture
```
Gillsystems_games/ (this repo - umbrella)
├── CHANGELOG.md
├── conductor/
├── Deadwood_alien_shooter.html (also deployed to gillsystems.net)
└── [other game folders - separate repos]
```

## Quick Start
1. Open Deadwood_alien_shooter.html in browser
2. Check conductor/tracks.md for active game work
3. Deploy to gillsystems.net via website repo

## Node Map
| Host | Role |
|------|------|
| gillsystems.net | Live deployment |
| GitHub Pages | Static hosting |
| Local file:// | Development |
