# 🏒 RHL: Redline Hockey League — START HERE

**For Claude Code on the dev PC:** read this file first. It summarizes every decision made during brainstorming
and tells you exactly where to begin. The other docs in this folder hold the details.

---

## 1. What This Project Is

- **Game:** *RHL: Redline Hockey League* — an arcade blood-sport hockey game in a dystopian TV league run by the **Meridian** network. Still hockey (goals win), but brutal: weapons, injuries, fights, kills.
- **Who it's for:** a personal project for the owner and their son. **Not commercial. $0 budget** — the only cost is Claude usage.
- **Quality bar:** should *look and feel like a published game*. Every asset goes through a review pipeline.
- **Platform:** **PC only (Windows), offline only.** No online, no consoles.
- **Tools:** Unreal Engine 5 · Blender · ComfyUI (local AI on RTX 5080) · Claude Code.
- **Players:** owner + son on the couch, **Xbox and PlayStation controllers**. The son is an experienced NHL-games player and **loves playing goalie** — he'll be the primary game-feel tester **once he's told about it**.
- 🤫 **SURPRISE PROJECT:** the son doesn't know about RHL yet. The owner will reveal it once there's something playable to show. Until then: the owner tests everything, and **nothing involving the son** (feel tests, voice recording) happens.

---

## 2. Decisions at a Glance

| Topic | Decision | Doc |
|---|---|---|
| Title | **RHL: Redline Hockey League** ("Red Ice" rejected — name conflict) | `TITLE_IDEAS.md` |
| Direction | Arcade blood-sport + dystopian broadcast league | `GAME_DESIGN.md` |
| Weapons/items | **Grounded & brutal** (no sci-fi). Random drops: crowd throws, sponsor drops, frozen in ice, Zamboni | `GAME_DESIGN.md` §3 |
| Killing | Possible **without** items; items amplify it | `GAME_DESIGN.md` §2 |
| Goalies | **Own separate item set**, first-class role, star goalie per team, mask editor | `GOALIE.md` |
| Spawn Director | Drop budget + Hype-capped rarity tables + fair spawn-point scoring + arena deliveries; separate goalie pool | `SPAWN_DIRECTOR.md` |
| AI | Team Brain + utility-scored player AI; real formations; fair (reaction delay, no rubber-banding); team personalities; Bodyguard teammates protect the goalie | `AI.md` |
| Franchise | Owner/GM, death-waiver contracts, finances, Meridian demands, feeder-league draft, memorial wall; play any position incl. goalie only | `FRANCHISE.md` |
| Challenges | 56 challenges in 8 packs (incl. goalie, co-op, Legends), Bronze/Silver/Gold, cosmetic unlocks | `CHALLENGES.md` |
| Menus & UI | "Meridian Broadcast Package" style; studio main menu as channel guide; scorebug + Ratings (Hype) meter; no floating health bars; player profiles | `UI.md` |
| Star designs | Names/personalities locked; **Edit Player** feature; **alternate looks** unlockable. Character sheets for 8 star skaters + 9 star goalies (look, gear, stats, voice), team colors & uniforms, readability test | `STAR_PLAYERS.md` |
| Crowd Hype | **Central mechanic** — fuels items, arena Network Events, finishers, Career ratings | `GAME_DESIGN.md` §4 |
| Violence | Gore level setting: Off / Low / Full | `GAME_DESIGN.md` §2 |
| Teams | 8 teams in **real cities** + Meridian All-Stars; **named star players** | `LEAGUE_AND_NETWORK.md` |
| Creation | **Custom players + custom teams** (+ custom arenas), shared by file export/import | `GAME_DESIGN.md` §6 |
| Modes | **Career, Franchise, Challenges, Penalty Shootout of Death, Broadcast/Replay** + Exhibition, Practice | `GAME_MODES.md` |
| Career | 3 seasons, broadcast-style storytelling (no cutscenes), mentor death **preventable**, 4 endings | `CAREER_STORY.md` |
| Camera | **Behind the player** default (behind the goalie when in net); split-screen for couch | `CONTROLS_AND_FEEL.md` |
| Controls | Arcade scheme + **Pro skill-stick scheme (launch requirement)**, per player | `CONTROLS_AND_FEEL.md` |
| Fights | **Skill-based**: telegraphs, blocks, parries, dodges | `CONTROLS_AND_FEEL.md` |
| Arenas | 8 team arenas + The Pit + Meridian Dome; **weather & time-of-day options** | `ARENAS.md` |
| Difficulty | **User & AI sliders** (speed, strength, etc.), per-player on the couch, presets | `DIFFICULTY_SLIDERS.md` |
| Music | **Hip-hop & rock** + twisted arena organ; **custom music folder** | `AUDIO.md` |
| Voices | Local TTS; **owner & son voice the Arena PA announcer** | `AUDIO.md` |

### Doc Reading Order
1. `START_HERE.md` (this file)
2. `GAME_DESIGN.md` — the master design
3. `CONTROLS_AND_FEEL.md` — needed first for the vertical slice
4. `GOALIE.md`
4b. `SPAWN_DIRECTOR.md` — needed for the item system milestone
4c. `AI.md` — basic AI needed for the vertical slice
5. `ARENAS.md`
6. `LEAGUE_AND_NETWORK.md`
6b. `STAR_PLAYERS.md`
7. `GAME_MODES.md`
8. `DIFFICULTY_SLIDERS.md`
8b. `FRANCHISE.md`
8c. `CHALLENGES.md`
8d. `UI.md`
9. `CAREER_STORY.md`
10. `AUDIO.md`
11. `TITLE_IDEAS.md`

---

## 3. Step 1 — Create the RHL Repository

These docs currently live in the unrelated `Nowify` repo (branch `ccr-c8043368-hl5s78`, folder `hockey-deathmatch-design/`).
Move them into a dedicated **private** repo:

1. On GitHub, create a **private** repo, e.g. `rhl-game`.
2. On the PC:
   ```bash
   git clone https://github.com/revg1794/nowify.git nowify-temp
   cd nowify-temp && git checkout ccr-c8043368-hl5s78 && cd ..
   git clone https://github.com/revg1794/rhl-game.git
   mkdir rhl-game/Docs
   cp nowify-temp/hockey-deathmatch-design/*.md rhl-game/Docs/
   cp rhl-game/Docs/CLAUDE_TEMPLATE.md rhl-game/CLAUDE.md
   ```
3. Set up **Git LFS** before adding any Unreal content (see §4), then commit and push.
4. Optional: delete the `ccr-c8043368-hl5s78` branch from Nowify afterward.

> Or just tell Claude Code on the PC: *"Read START_HERE.md and do Step 1."*

---

## 4. Step 2 — PC Setup Checklist

### Core software
- [ ] **Unreal Engine 5** — latest stable 5.x via the Epic Games Launcher
- [ ] **Visual Studio 2022** (Community, free) with **"Game development with C++"** workload (needed for C++ projects)
- [ ] **Blender** — latest LTS release
- [ ] **Git** + **Git LFS** (`git lfs install`)
- [ ] **ComfyUI** (Desktop or portable build), using the RTX 5080
- [ ] **Claude Code** installed on Windows, opened in the `rhl-game` folder
- [ ] **Audacity** (free) — for cleaning up voice recordings

### Free asset accounts
- [ ] **Epic Games account** → **Fab** (free Megascans content for Unreal, monthly free assets)
- [ ] **MetaHuman** (free with Unreal)
- [ ] **Mixamo** (free Adobe account) — prototype animations
- [ ] **Freesound** account — CC0 sound effects
- [ ] Epic's **Game Animation Sample** project (free) — high-quality locomotion animations

### ComfyUI models to install (verify current versions/licenses when installing)
| Purpose | Suggested models |
|---|---|
| Concept art, textures, logos, posters | FLUX or SDXL family checkpoints |
| Image → 3D base meshes (props) | Hunyuan3D 2.x or TRELLIS (via ComfyUI custom nodes) |
| Music (hip-hop/rock with vocals) | ACE-Step |
| Loops, stingers, SFX | Stable Audio Open |
| Voices (announcers, characters) | A local TTS model with voice options (e.g. Kokoro, F5-TTS, XTTS) |

### Repo hygiene (Unreal + Git)
- [ ] Unreal `.gitignore` (Binaries/, Intermediate/, Saved/, DerivedDataCache/, .vs/)
- [ ] `.gitattributes` with LFS tracking for `*.uasset`, `*.umap`, `*.fbx`, `*.blend`, `*.png`, `*.tga`, `*.exr`, `*.wav`, `*.mp3`
- [ ] ⚠️ **GitHub free LFS has limited storage/bandwidth.** Unreal projects grow fast. Plan: keep raw/source files (huge textures, ComfyUI outputs, `.blend` backups) **outside git** in a local `RHL_Source/` folder with a backup drive; commit only what the project needs. Revisit if storage runs out.

### How Claude Code drives the tools
- **Blender:** headless Python scripts — `blender --background --python script.py` — for modeling, cleanup, UVs, export, and **review renders**. (A community Blender MCP server is an option for interactive control.)
- **Unreal:** editor **Python** scripting (enable the Python Editor Script Plugin) for imports, materials, LODs, level setup; command line builds (`UnrealEditor-Cmd.exe`, `RunUAT`); C++ compiled via Visual Studio toolchain.
- **ComfyUI:** its local HTTP API — Claude Code submits saved workflows (JSON) and collects outputs.
- **Screenshots:** high-res screenshots/renders from Unreal and Blender so Claude can visually review assets.

---

## 5. Step 3 — Create the Unreal Project
- [ ] New **C++** project (Blank or Third Person template), named `RHL`.
- [ ] Enable plugins: **Enhanced Input**, **Gameplay Abilities (GAS)**, **CommonUI**, **Python Editor Script Plugin**, **Chaos** (default), **MetaSounds**, **Control Rig**, **Movie Render Queue**.
- [ ] Folder structure under `Content/RHL/`: `Characters/`, `Arenas/`, `Items/`, `Audio/`, `UI/`, `Data/`, `VFX/`, `Maps/`.
- [ ] Commit the empty project.

---

## 6. Step 4 — First Build: The Vertical Slice

**Goal:** prove the game feels good. **Do not build anything else until skating feels right.**

### Build order
| # | Task | Done when… |
|---|---|---|
| 1 | **The Pit** (graybox) — rink at real NHL size (61 m × 26 m), boards, glass, two nets | Rink loads, correct scale |
| 2 | **Skating movement** — custom movement mode: acceleration, glide, carving, hard stops, sprint/stamina | Owner approves (son re-tests after the reveal) |
| 3 | **Behind-the-player camera** + puck/off-screen indicators | Readable at speed |
| 4 | **Puck physics** + stickhandling + sticky assist | Puck feels clean |
| 5 | **Passing + shooting** (wrist shot, slapshot) — Arcade scheme | Shots feel powerful |
| 6 | **Goalie** — movement, directional saves, Perfect Save timing | Owner approves (son tunes it after the reveal) |
| 7 | **Body checks** — speed-scaled hit tiers, hitstop, camera shake, rumble | Hits feel brutal |
| 8 | **One fight** — skill-based (jab, haymaker, block, parry) | Fight is fun start to finish |
| 9 | **3v3 Exhibition** with basic AI + goals/score/periods | Full game playable |
| 10 | **Couch play** — 2 controllers (Xbox + PlayStation), split-screen | Both players having fun |
| 11 | **Pro skill-stick scheme** | Son says it feels right |
| 12 | **Basic sliders** (speed, strength) for User/AI | Tunable without code |

### Placeholder art is fine here
Use mannequins, gray boxes, and simple materials. Art comes **after** the feel is proven.

### After the vertical slice (see `GAME_DESIGN.md` §9 Milestones)
Combat layer → Item system & Crowd Hype → Art pass (The Plant, MetaHuman players) → Modes → Creation suite → Franchise → Career.

---

## 7. Working Rules for Claude Code

1. **Feel first, art second.** No hero art until the vertical slice feel is approved.
2. **Surprise rule:** the son doesn't know yet. Owner tests everything until the reveal; after the reveal, the son becomes the feel tester for skating, shooting, and goalie. Owner approves art and story. Voice-cameo recording happens after the reveal.
3. **Every asset goes through the review pipeline** (`GAME_DESIGN.md` §7): reference → automated checks → standard renders → critique → owner approval.
4. **Data-driven everything:** items, sliders, teams, players, arenas in Data Assets/Data Tables — tuning without code changes.
5. **Save tokens:** use ComfyUI for bulk generation (free, local); use Claude for code, automation, and review. Keep scripts reusable in `Tools/`.
6. **Small, tested steps.** Build → play → adjust. Commit after each working step.
7. **Keep docs updated.** When a design decision changes, update the relevant doc in `Docs/`.

---

## 8. First Message to Send Claude Code on the PC

> Read `Docs/START_HERE.md` and the docs it lists. Then help me with Step 2 (PC setup checklist) — check what's
> already installed and tell me what's missing. After that, create the Unreal project (Step 3) and start the
> vertical slice with The Pit and skating movement.
