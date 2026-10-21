# ARCOLOGY

A game about running a vast arcology on the Hudson at 34th Street. One file, no server. Open `index.html` or play at https://ftrain.github.io/arcology/.

You are the operator. Each day you can build one system (residential decks, fusion and solar, desalination, vertical farms, reclamation, clinics and schools, commercial floors, transit links) or adjust rent, then the day runs. Shortfalls hurt morale; morale moves people in or out; people pay rent. Keep it alive for a year.

The simulation is deterministic per seed. The seed is in the URL hash, so `#42` is always the same year. "Autoplay" hands the tower to a simple operator that fixes the worst shortfall it can afford, so the game can play itself.

This is v1, built the way Simon Willison built [Battle Drones](https://simonwillison.net/2026/Oct/20/battledrones/): a static page, a playable version first, then make it more fun.

## How it is built

`.claude/skills/vibe-game/SKILL.md` is the method, distilled from that post: a static page, numbered versions that stay playable, a self-play mode so the game can test itself, then rebalance from simulated runs. Claude Code loads it automatically when working in this repo.
