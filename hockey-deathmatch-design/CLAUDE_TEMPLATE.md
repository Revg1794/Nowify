# RHL: Redline Hockey League

Copy this file to the root of the `rhl-game` repo as `CLAUDE.md` — Claude Code reads it automatically every session.

## Project
- Arcade blood-sport hockey game in Unreal Engine 5 (C++ + Blueprints), assets from Blender, ComfyUI, and free libraries.
- Personal project for the owner and their son. $0 budget. PC only, offline only.
- Full design: `Docs/START_HERE.md` (read first), then the other docs in `Docs/`.

## Rules
- Feel first, art second. Don't start hero art until the vertical slice feel is approved.
- SURPRISE: the son doesn't know about this project yet. Owner tests everything until the reveal; after that the son tests game feel (skating, shooting, goalie). Owner approves art and story.
- Every asset goes through the review pipeline in `Docs/GAME_DESIGN.md` §7 before it's "done".
- Data-driven design: items, sliders, teams, players, arenas live in Data Assets / Data Tables.
- Reusable automation scripts (Blender, Unreal Python, ComfyUI workflows) go in `Tools/`.
- Large raw source files stay out of git (`RHL_Source/` folder outside the repo); Unreal content uses Git LFS.
- Commit after each working step. Update `Docs/` when a design decision changes.

## Layout
- `Source/RHL/` — C++ gameplay code
- `Content/RHL/` — Characters, Arenas, Items, Audio, UI, Data, VFX, Maps
- `Tools/` — Blender / Unreal / ComfyUI automation
- `Docs/` — design documents
