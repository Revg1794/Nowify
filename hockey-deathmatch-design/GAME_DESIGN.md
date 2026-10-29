# RHL: Redline Hockey League — Game Design Document (Draft v0.2)

> **Title:** RHL — Redline Hockey League (see `TITLE_IDEAS.md` for history and name checks)
> **Engine:** Unreal Engine 5 · **DCC:** Blender · **Target hardware (dev):** PC with RTX 5080
> **Project type:** Personal passion project for the owner and their son. **$0 budget** — only cost is Claude usage. Free tools and free/AI-generated assets only.
> **Toolchain:** Unreal Engine 5, Blender, ComfyUI (local AI generation on the RTX 5080), Claude Code.
> **Platform:** PC only (Windows). **Offline only** — no online multiplayer, no console release planned.
> **Status:** Brainstorm / pre-production. This doc is the handoff for Claude Code sessions on the dev PC.

---

## 1. Vision

A high-quality (AAA-presentation) **arcade blood-sport hockey game** set in a **dystopian televised league: the Redline Hockey League (RHL)**.
The title is also the in-world league name — the game *is* the broadcast.
It is still hockey — **goals win games** — but killing, maiming, and brutalizing opponents is a core tactic.
A media network runs the league and rewards spectacle: the more brutal the match, the higher the ratings.

**Pillars**
1. **Hockey first.** Skating, passing, and scoring must feel great on their own.
2. **Momentum is damage.** Speed = hitting power. Skating skill is combat skill.
3. **Grounded and brutal.** Real-world, improvised weapons. No sci-fi. Injuries matter.
4. **The crowd is a player.** The Crowd Hype system drives items, events, and career rewards.
5. **Published-game quality.** Every asset passes a review pipeline before it's "done."

**Tone references:** Rollerball (1975), NHL Hitz, Mutant League Hockey, Mortal Kombat finishers, The Running Man, Slap Shot.

---

## 2. Core Rules

- Teams: 3v3 (arcade default) and 5v5, plus goalies.
- Win condition: most goals at the end of regulation. Sudden-death overtime (literal).
- Killing is possible **without items** (body checks, fights, boards) — items amplify it.
- **Death / respawn:** dead players return on the next **line change**. A kill gives the other team a temporary power play.
- **Penalties:** the penalty box is dangerous; serving time grants a random item.

### Core Mechanics
- **Momentum damage:** hit damage scales with skating speed.
- **The puck as a weapon:** slapshots hurt.
- **Fights:** dropping gloves triggers a close-camera brawl mini-game while play continues around it.
- **Destructible arena:** cracking/breaking ice, boards that can be damaged.

### Injury System (locational)
| Injury | Effect |
|---|---|
| Broken arm | Weaker shots, worse stickhandling |
| Leg injury | Reduced top speed / acceleration |
| Concussion | Blurred / swimming vision, delayed controls |
| Bleeding | Health drains until you reach the bench — or die |

### Violence Settings
- **Gore level:** Off / Low / Full (blood amount, dismemberment-style effects, injury visuals).
- **Finisher camera:** On / Off.
- Lets the game scale for different ages and moods.

---

## 3. Items & Power-Ups (Grounded & Brutal)

### Delivery
- **Crowd throws** — fans hurl items over the glass (quality scales with Hype).
- **Sponsor drops** — branded crates lowered from the jumbotron (fictional sponsors, satire).
- **Frozen in the ice** — glowing under the surface; slapshot/break the ice to free it.
- **Zamboni of Doom** — drives through mid-period, drops loot, kills anything in its path.
- **Penalty box loot** — random item on serving time.
- **Telegraphed spawns** — announcer call-out + ice marker; players trade puck position for loot.

### Skater Stick Mods (limited uses / time)
- Razor-blade taped stick (bleed)
- Nail-studded stick
- Bike-chain wrapped stick
- Sledgehammer stick (heavy knockback, cracks ice)
- Aluminum bat-stick
- Skate-blade stick (bleed)

### Puck Mods
- Lead-weighted puck (bone-breaking)
- Frozen iron puck
- Barbed-wire wrapped puck
- Road-flare puck (burns, lights up dark arenas)

### Thrown / Deployables
- Chains, bottles from the crowd, broken glass (trip hazard), padlock-in-a-sock, rink salt (blinds + slows)

### Skater Power-Ups (temporary)
| Power-up | Effect |
|---|---|
| Painkillers | Ignore knockdowns |
| Smelling salts | Instant recovery from stun/knockdown |
| Taped knuckles | Double fight damage |
| Steel-toe skates | Kicks and trips deal damage |
| Riot padding | Damage resistance, slower |
| Adrenaline shot | Speed burst (= harder hits) |

### Goalie Item Set (separate pool — full expanded list in `GOALIE.md`)
- **Spiked blocker** — shots shatter on it; touching it causes bleeding
- **Weighted leg pads** — can't be knocked down
- **Crease traps** — chains/spikes around the crease
- **Goalie stick hook** — drag skaters into the post
- **Iron mask** — survive one headshot puck
- **Blood in the crease** — heal by blocking shots

### Item Design Rules
1. **Puck carrier restriction:** carrier can only use puck mods (creates scorer / enforcer roles).
2. **One active + one stored slot.** No hoarding.
3. **Catch-up logic:** trailing team gets better drop odds.
4. **Everything is telegraphed** (audio + visual cue) so it's counterable.
5. **Lobby options:** Classic (few items), Chaos (many), custom item toggles.
6. **Items despawn** after a short time.

---

## 4. Crowd Hype System (central mechanic)

**Fills from:** brutal hits, kills, fights, goals, style combos (e.g. kill → goal within 10s).
**Drains from:** passive play, stalling.

| Tier | Payout |
|---|---|
| 1 | Crowd throws basic items |
| 2 | Sponsor drops |
| 3 | Network arena event (lights out, Zamboni release, cage drop) |
| Max | Execution-style finisher unlocked |

**Career tie-in:** network **ratings** are the career currency. Boring wins get pay cut; brutal wins earn sponsors, gear, fame.

---

## 5. Modes

Offline only. Full details in `GAME_MODES.md`.

**Launch modes (chosen):**
- **Career: "Death Waiver"** — story mode with **broadcast-style presentation** (no cinematic cutscenes)
- **Franchise: "Ownership"** — owner/GM, permadeath roster
- **Challenges: "Highlight Reel"** — scripted scenarios
- **Penalty Shootout of Death** — standalone mode + overtime tiebreaker
- **Broadcast / Replay mode** — replay editor, highlight clips, export video

**Core (required to support the above):** Exhibition (3v3 / 5v5, local couch multiplayer) and Practice ("The Pit", tutorial).

---

## 6. Custom Player & Custom Team Creation

> Full custom player design: `CUSTOM_PLAYER.md`.

### Custom Player
- **Appearance:** face sculpting, body type, skin, hair/beard, scars, tattoos, missing teeth, broken nose, black eyes.
- **Archetype / position:** Sniper, Playmaker, Two-Way, Enforcer, Goon, Goalie.
- **Weight class (stat trade-off):** Light (speed, agility) / Middle / Heavy (momentum damage, toughness).
- **Fight style:** Brawler (power), Boxer (speed/combos), Grappler (holds, jersey pulls).
- **Backstory / origin (small perk):** Mill Worker, Ex-Con, Street Kid, Washed-Out Prospect, Ex-Military, Farm Kid.
- **Gear:** helmet / cage / visor / **no helmet** (more Hype, more risk), pads, gloves, skates, stick + tape color, jersey number, nameplate.
- **Personality:** signature finisher, celebrations, taunts, walkout intro, goal song, voice type.
- **Persistent damage (career):** scars, missing teeth, and injuries accumulate and show on the model.
- **Permadeath toggle** for career/franchise.

### Custom Team
- **City:** any real city (pick from a list or type one) + team name.
- **Logo editor:** layered shapes, symbols, text, decals (grungy, distressed styles to match the art direction).
- **Colors & jerseys:** primary/secondary/accent; home, away, and alternate jerseys; wear and blood decals.
- **Home arena:** choose a base arena template + hazards + lighting + crowd type + ice condition.
- **Presentation:** goal horn, entrance music, mascot, fictional sponsors on boards.
- **Roster:** custom players + generated free agents; team tactics/playstyle.
- **Use anywhere:** exhibition, challenges, and as your franchise in career mode (expansion team joining the RHL).

### Sharing (offline)
- Export / import custom players and teams as files (share with friends manually). No online service or moderation needed.

### Tech Notes
- **MetaHuman Creator is not available at runtime.** In-game customization needs a modular character system:
  base MetaHuman-compatible bodies + morph targets for face/body + swappable meshes (hair, gear) + material
  parameters/decals (skin, scars, tattoos, blood, wear). Plan this early — it affects the whole character pipeline.
- Logo editor: layered decals rendered to a Render Target, saved as data (not images) so files stay small and re-render cleanly.
- Save locally via SaveGame; export/import via JSON or binary files.
- Scars/injuries as material layers + decals driven by persistent player data.

---

## 7. Art Direction & Asset Quality Standards

**Goal:** assets must look like a real published game. Grounded, gritty, realistic materials (worn, scratched, bloodied, grimy).

### Asset Sources
| Asset type | Source | Blender role |
|---|---|---|
| Players (faces/bodies) | MetaHuman | Model hockey gear, jerseys, pads to fit |
| Environment materials | Quixel Megascans / Fab | Arena modular kit, blockouts |
| Weapons & props | Blender modeling + texturing | Primary tool |
| Animation | Free: Mixamo, UE5 sample animations (Game Animation Sample), free Fab packs | Retargeting & cleanup |
| Concept art, textures, logos, UI | **ComfyUI** (local) | Apply to models / materials |
| AI-generated 3D props | **ComfyUI** image-to-3D (e.g. Hunyuan3D / TRELLIS) | Retopology, UV, cleanup, LODs |

### $0 Asset Pipeline (Blender + ComfyUI + free libraries)
| Need | Free source |
|---|---|
| Characters | **MetaHuman** (free) + Blender for gear/jerseys |
| Environments & surfaces | **Quixel Megascans / Fab** free content for Unreal |
| Props / weapons | Blender modeling; ComfyUI image-to-3D for base meshes → Blender cleanup |
| Textures & materials | ComfyUI (seamless textures, grime, decals, logos) + Megascans |
| Concept art / reference | ComfyUI |
| Logos, jerseys, sponsor ads, posters, UI | ComfyUI + Blender/UE text |
| Animation | Mixamo, UE5 Game Animation Sample, free Fab packs |
| Voices | Local TTS in ComfyUI (check each model's license) |
| Music | Local music generation in ComfyUI (e.g. ACE-Step / Stable Audio Open) |
| Sound effects | Freesound (CC0), Stable Audio Open, recorded at home |

**Rule:** AI-generated assets go through the same review pipeline as everything else — AI output usually needs cleanup (retopology, UVs, texture fixes) before it looks published-quality.

### Asset Review Pipeline (every asset)
1. **Reference board first** — real-world photos + published-game references (e.g. NHL 25, The Last of Us, Mortal Kombat 1).
2. **Automated technical checks** (scripted):
   - Poly budget, UV overlap, texel density, texture resolution
   - Naming conventions, LODs, collision
   - Real-world scale (puck = 7.62 cm diameter)
   - Fail = auto-reject
3. **Standardized lookdev renders** — turntable, neutral studio light, in-arena light, close-ups.
4. **Visual critique against checklist** — material realism (roughness variation, wear, grime), silhouette, proportions, lighting response. Fix and re-render.
5. **Human approval** — owner (and son) sign off on final renders.

---

## 8. Technical Plan

- **Engine:** Unreal Engine 5 (Lumen, Nanite, Chaos physics, Niagara VFX, Control Rig / physics-based animation for hits & ragdolls).
- **Abilities / items:** Gameplay Ability System (GAS) — buffs, cooldowns, effects (single-player, no replication needed).
- **Data-driven items:** each item is a Data Asset (stats, rarity, duration, mesh, VFX). Balance via spreadsheets / data tables.
- **Spawn Director:** decides what/where/when to spawn from score, Hype, and match time.
- **Modular characters:** shared skeleton + morph targets + swappable gear meshes (required for star players AND custom players).
- **Skeleton:** rig characters to UE5 mannequin skeleton for animation reuse.
- **Broadcast presentation:** Career story told through the Meridian broadcast — pre-game shows, announcer segments, interviews, text/news tickers, jumbotron, still images. Sequencer for short in-engine broadcast shots.
- **Voice:** local text-to-speech in ComfyUI (announcers, reporters, star players). Optional: owner/son record lines themselves.
- **Replay system:** UE5 Replay system (DemoNetDriver) or a custom recorder of transforms/events; Sequencer-style camera tools for the editor; video export via Movie Render Queue.
- **Automation:** Blender Python API + Unreal Python API / commandlets for asset import, validation, and review renders.
- **Dev machine access:** Claude Code runs on the dev PC (or connects via Remote Control) with Unreal + Blender installed.

---

## 9. Milestones

1. **Vertical slice** — one arena, 3v3, skating, checking, passing, scoring, one kill mechanic. *If skating doesn't feel good, stop and fix it.*
2. **Combat layer** — fights, injuries, momentum damage, ragdolls.
3. **Item system** — GAS setup, 5–6 items, Spawn Director, Crowd Hype v1.
4. **Art pass** — hero arena, MetaHuman players with gear, asset review pipeline live.
5. **Modes** — exhibition polish, Practice, Penalty Shootout of Death, Challenges, Broadcast/Replay mode.
6. **Creation suite** — custom player (modular characters) + custom team (logo editor, jerseys, arena options).
7. **Franchise** — GM layer, permadeath roster, budgets.
8. **Career** — story via broadcast presentation, ratings economy, sponsors, star player roster.

---

## 10. Open Questions

- Trademark / Steam / domain check for "RHL" and "Redline Hockey League" (avoid confusion with NHL/AHL marks in logo design)
- Gore level settings (see §2)
