# Hockey Deathmatch — Game Design Document (Draft v0.1)

> **Working title:** TBD (see `TITLE_IDEAS.md`)
> **Engine:** Unreal Engine 5 · **DCC:** Blender · **Target hardware (dev):** PC with RTX 5080
> **Status:** Brainstorm / pre-production. This doc is the handoff for Claude Code sessions on the dev PC.

---

## 1. Vision

A high-quality (AAA-presentation) **arcade blood-sport hockey game** set in a **dystopian televised league**.
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

### Goalie Item Set (separate pool)
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

- Exhibition (3v3 / 5v5)
- Online multiplayer (primary long-term mode)
- Career / Campaign: rise through an underground → televised league
- Survival: waves of enemy teams
- Franchise / GM layer: **dead players stay dead** — sign replacements

---

## 6. Art Direction & Asset Quality Standards

**Goal:** assets must look like a real published game. Grounded, gritty, realistic materials (worn, scratched, bloodied, grimy).

### Asset Sources
| Asset type | Source | Blender role |
|---|---|---|
| Players (faces/bodies) | MetaHuman | Model hockey gear, jerseys, pads to fit |
| Environment materials | Quixel Megascans / Fab | Arena modular kit, blockouts |
| Weapons & props | Blender modeling + texturing | Primary tool |
| Animation | Mocap packs (Fab), Mixamo for prototyping | Retargeting & cleanup |
| Hero assets | Freelance artist where it matters | Integration |

### Asset Review Pipeline (every asset)
1. **Reference board first** — real-world photos + published-game references (e.g. NHL 25, The Last of Us, Mortal Kombat 1).
2. **Automated technical checks** (scripted):
   - Poly budget, UV overlap, texel density, texture resolution
   - Naming conventions, LODs, collision
   - Real-world scale (puck = 7.62 cm diameter)
   - Fail = auto-reject
3. **Standardized lookdev renders** — turntable, neutral studio light, in-arena light, close-ups.
4. **Visual critique against checklist** — material realism (roughness variation, wear, grime), silhouette, proportions, lighting response. Fix and re-render.
5. **Human approval** — owner signs off on final renders. Periodic pro 3D artist review for hero assets.

---

## 7. Technical Plan

- **Engine:** Unreal Engine 5 (Lumen, Nanite, Chaos physics, Niagara VFX, Control Rig / physics-based animation for hits & ragdolls).
- **Abilities / items:** Gameplay Ability System (GAS) — buffs, cooldowns, replication.
- **Data-driven items:** each item is a Data Asset (stats, rarity, duration, mesh, VFX). Balance via spreadsheets / data tables.
- **Spawn Director:** decides what/where/when to spawn from score, Hype, and match time.
- **Skeleton:** rig characters to UE5 mannequin skeleton for animation reuse.
- **Automation:** Blender Python API + Unreal Python API / commandlets for asset import, validation, and review renders.
- **Dev machine access:** Claude Code runs on the dev PC (or connects via Remote Control) with Unreal + Blender installed.

---

## 8. Milestones

1. **Vertical slice** — one arena, 3v3, skating, checking, passing, scoring, one kill mechanic. *If skating doesn't feel good, stop and fix it.*
2. **Combat layer** — fights, injuries, momentum damage, ragdolls.
3. **Item system** — GAS setup, 5–6 items, Spawn Director, Crowd Hype v1.
4. **Art pass** — hero arena, MetaHuman players with gear, asset review pipeline live.
5. **Modes** — exhibition polish, then online multiplayer prototype.
6. **Career** — ratings economy, sponsors, permadeath franchise.

---

## 9. Open Questions

- Final title
- Platforms beyond PC (consoles?)
- Team size / whether artists will be hired
- Single-player vs. multiplayer priority
- Monetization (premium? cosmetics via fictional sponsors?)
