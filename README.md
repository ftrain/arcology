# ARCOLOGY

A game about running a vast arcology on the Hudson at 34th Street, for a hundred years. One file, no server. Open `index.html` or play at https://ftrain.github.io/arcology/.

You are the operator. Each week you can commission a project, order a refit, or adjust rent, then the week runs. Projects take as long as they would: a residential deck is a year and a half, a fusion plant two years, a transit link three. Everything wears out at about nine percent a year unless it is refitted. Shortfalls hurt morale; morale moves people in or out; people pay rent. The city throws heat waves, grid faults, nor'easters, strikes and inspectors at you. Keep it alive for 5,200 weeks.

The simulation is deterministic per seed. The seed is in the URL hash, so `#42` is always the same century. "Autoplay" hands the tower to a simple operator that refits what is tired, builds ahead of growth, and keeps a reserve, so the game can play itself; "Hold a year" skips 52 quiet weeks.

This is v1, built the way Simon Willison built [Battle Drones](https://simonwillison.net/2026/Oct/20/battledrones/): a static page, a playable version first, then make it more fun.

## How it is built

`.claude/skills/vibe-game/SKILL.md` is the method, distilled from that post: a static page, numbered versions that stay playable, a self-play mode so the game can test itself, then rebalance from simulated runs. Claude Code loads it automatically when working in this repo.
