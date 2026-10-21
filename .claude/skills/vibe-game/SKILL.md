---
name: vibe-game
description: Build a browser game the way Simon Willison built Battle Drones (simonwillison.net, 20 Oct 2026) - a static HTML game grown through numbered, playable versions, each kept online; the agent playtests it against itself, rebalances from simulated matches, writes its own tools and release notes. Use when asked to make, grow, or "make more fun" a game, simulation, or toy that should run in a browser with no server.
---

# Vibe-coding a browser game

Distilled from Simon Willison, "Battle Drones - a vibe coded RTS with audio-based multiplayer" (https://simonwillison.net/2026/Oct/20/battledrones/): 12 versions and 321 agent commits took a Command & Conquer clone from "barely a proof of concept" to a game he calls genuinely fun. These are the moves that got it there.

## The medium

- **Static HTML and JavaScript.** One `index.html` the player opens, served from GitHub Pages. No server to keep alive. Add a server only for something a static page truly cannot do (he added a tiny stateless WebSocket relay on Fly.io for online multiplayer, and only after audio multiplayer gave a tester a headache).
- **Libraries the models know inside out**: Phaser for 2D, Three.js for 3D. 3D models, terrain, sprites and the whole soundtrack can be written in code; no asset files are needed. If an image-generation API key is available, the agent can generate sprites and look at them to iterate.
- **It becomes a PWA for free.** Keep it cacheable and it plays offline.

## The loop

1. **v1 is an MVP, started with questions.** "Let's start with a MVP design, ask me some questions." Get something recognizable as the genre with the core verbs (select, direct, build) and a basic AI opponent. It will not be fun yet. That is fine.
2. **Number every version and keep them all playable.** `v1/`, `v2/`, ... next to the current build, so anyone can see the history and old prompts can be compared with their results.
3. **Add an AI-vs-AI (self-play) mode early.** The game must be able to play itself without you. This is what makes everything after possible.
4. **"Make it a LOT more fun."** When it looks like a game but is boring, say exactly that. Let the agent run long: it should simulate many self-play matches (Battle Drones ran over a thousand), read the results, and rebalance, add catch-up mechanics, openers, call-down powers, objectives, juice, adaptive music, new modes, progression. Measure: games still undecided after N minutes, share of comebacks from behind.
5. **Then get ambitious one axis at a time**: a port to 3D, a new unit class, a new map. Each is one prompt and one version.
6. **Design when the sim shows a gap.** When a unit or mechanic goes unused, write a long design prompt that creates a strategic reason to use it (his Archipelago map: uplinks on islands only reachable by troop carrier). End it with "First research and then critique this design. Only build after we have agreed on any modifications."
7. **Brainstorm in short rounds** for big additions ("Don't overthink this yet"), then settle rules in a few follow-ups before building.
8. **Let the agent write the release notes** for each version, with the numbers from the simulated playtests.

## Engineering rules that paid off

- **Deterministic simulation**: seeded RNG, fixed tick, and custom `sin`/`cos` if replays must match across browsers. This is what makes replays, recorded agent battles, and lock-step multiplayer possible.
- **Seeded random content** (maps, daily challenges) so a result can be named and reused.
- **Tools are free.** Build a model browser, a replay viewer, a probe, a debug page, whatever helps the agent or the player see what is going on. Keep them in `tools/` or as extra HTML pages.
- **Expose the game to agents**: a non-visual, fog-of-war-respecting state query plus command tool lets LLMs play each other; record and replay those battles.
- **Mutators and a daily seeded challenge** are cheap replayability.

## Caveats he noted

- Long agentic runs burn tokens; a single prompt can still solve something hard (audio modem multiplayer).
- Audio-based multiplayer works but the tones can cause headaches; warn, and offer another path.
- The author's own taste and design input matter more as the game matures; the agent can only carry "make it more fun" so far.
