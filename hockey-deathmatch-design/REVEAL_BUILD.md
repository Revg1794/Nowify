# RHL — The Reveal Build (Brainstorm v0.1)

The first version the son sees. Goal: **he picks up the controller and immediately feels it's a real hockey game —
and that it was made for him.** Small scope, high polish where he'll notice it most: **goalie feel**.

---

## 1. Reveal Goals
1. **It feels like real hockey** (he plays NHL games — skating, shooting, and goalie must feel right).
2. **Goalie is the star.** He loves playing goalie; the goalie experience gets the most polish.
3. **It's clearly RHL** — not a generic hockey prototype: the Meridian broadcast vibe, a hit that's brutal, a taste of items.
4. **It's personal.** His profile, his name called by the announcer, his mask.
5. **Zero friction.** No crashes, no debug text, controllers just work.

---

## 2. What's In

| Feature | Reveal version |
|---|---|
| **Arena** | **The Pit** — with a light art pass (it's an abandoned rink: grime, graffiti, flickering lights — Megascans makes it look good cheaply) |
| **Players** | Hockey-geared characters (basic Blender gear on the shared body), two team color sets (Dockrats navy/red vs a rival) — no star players yet |
| **Goalie** | Full goalie controls, directional saves, **Perfect Save**, positioning, crease defense (blocker punch, stick slash), behind-the-goalie cam |
| **Skating / shooting** | Tuned skating, passing, wrist shot, slapshot; Arcade + **Pro skill-stick** schemes |
| **Hits** | Body checks with hit tiers, hitstop, rumble, glass rattle |
| **Fight** | One working fight (skill-based) |
| **Items (taste)** | 3 items: **Glass Bottles**, **Lead-Weighted Puck**, **Crease Salt** (goalie) — simple drops |
| **Modes** | **Shootout of Death vs AI** · **3v3 Exhibition** vs AI (co-op: son in net + owner skating, AI fills the rest) · Practice (The Pit, free skate) |
| **AI** | Basic skater AI + AI goalie + AI shooters (Pro difficulty, tuned so he's challenged but not crushed) |
| **Presentation** | Meridian ident + "REDLINE HOCKEY LEAGUE" title screen, scorebug, goal horn, crowd loop, Dale's calls (TTS — a handful of lines) |
| **Profiles** | Pre-made **"Brick Wall"** (Pro controls, goalie, assists off) and **"The Captain"** |
| **Personal touch** | Dale says **"In net tonight… BRICK WALL!"**; a pre-made goalie mask design for him; his favorite number on his jersey |
| **Controllers** | Xbox + PlayStation both working, correct button icons |
| **Replays** | Instant replay of goals/saves (recorder exists from the vertical slice) |

## 3. What's Out (later)
Career, Franchise, Challenges, creation suite, star players, other arenas, full item set, Spawn/Event Directors (beyond simple drops), Zamboni, menus beyond the basics, voice cameos (recorded *after* the reveal, together).

---

## 4. The Reveal Moment (suggested flow)

1. **Hand him the controller** — screen shows a black Meridian ident, then the title: **RHL: REDLINE HOCKEY LEAGUE**.
2. **Signing Day (mini):** a contract appears with his profile name — "Press A to sign your death waiver." Dale: "The newest Bayonne Dockrat… in net… BRICK WALL!"
3. **Shootout of Death — Gauntlet-lite:** he's in net vs 5 AI shooters. Short, intense, shows saves + goalie attacks. (Easy to restart: "one more.")
4. **3v3 game together:** son in net, owner skating, AI teammates & opponents, 2 short periods. Big hits, a fight, a bottle or two, a lead puck to the chest.
5. **After:** show him the design docs/concept art and the arena list — invite him in as **co-designer & official goalie tester**. Then plan the **voice recording session** together.

---

## 5. Quality Checklist (must pass before the reveal)

### Stability
- [ ] 60 fps (split-screen too) on the RTX 5080
- [ ] 30+ minutes of play with no crash
- [ ] No debug text, placeholder errors, or "Hello World" anywhere
- [ ] Quick restart / rematch in 1–2 button presses

### Controls
- [ ] Xbox and PlayStation controllers both work, auto icons, no setup needed
- [ ] Pro skill-stick scheme feels natural to an NHL-games player (owner tests against NHL muscle memory as best as possible)
- [ ] Goalie controls responsive; Perfect Save timing feels fair

### Feel (owner signs off)
- [ ] Skating has weight but isn't sluggish
- [ ] Shots feel powerful; slapshots sound like cannons
- [ ] Hits feel brutal (hitstop, shake, rumble, crowd)
- [ ] Goalie movement and saves feel satisfying — **top priority**
- [ ] AI goalie is beatable but not a sieve; AI shooters test him

### Look & Sound
- [ ] The Pit looks moody and intentional (not gray boxes)
- [ ] Players wear readable hockey gear and team colors
- [ ] Core sounds: skates, puck, posts, hits, crowd, goal horn, Dale's lines

---

## 6. Camera Plan for Co-op
- Behind-the-player (owner) + behind-the-goalie (son) needs **2-player split-screen**.
- **Fallback** if split-screen isn't ready or smooth: shared **broadcast camera** for the co-op game (behind-the-goalie cam still used in the shootout).

---

## 7. Biggest Risks (and plans)
| Risk | Plan |
|---|---|
| PlayStation controller support on PC | Solve early (plugin or Steam Input) — test with his actual controller |
| Goalie feel not matching NHL expectations | Prioritize goalie tuning; owner plays lots of shootouts vs AI; reference NHL goalie behavior |
| AI looks dumb | Keep 3v3 (simpler), Pro difficulty, tune with headless sims & replays |
| Split-screen performance | Profile early; fallback to broadcast cam |
| Characters look unfinished | Gear + team colors + helmets/visors hide a lot; good lighting in The Pit |

---

## 8. Keeping It a Surprise
- Repo stays **private**; design docs not left open on screen.
- Playtest when he's not around (headphones — goal horns are loud).
- Pre-made profile & mask are ready but hidden until reveal day.

---

## 9. After the Reveal (next steps with him)
- Ask him: what feels off in net? Favorite goalie style? Mask ideas? Which arena next? Which star goalie first?
- He becomes the **feel tester** (per `START_HERE.md`).
- **Record the PA announcer cameo lines** together (`AUDIO.md`).
- Next milestones: combat layer → item system & Crowd Hype → The Plant + first stars.

---

## Open Questions
- His jersey number (and any favorite colors) for his profile and mask?
- Gore level for the reveal: Off / Low / Full?
- Reveal team: **Bayonne Dockrats** (Career start) — OK?
