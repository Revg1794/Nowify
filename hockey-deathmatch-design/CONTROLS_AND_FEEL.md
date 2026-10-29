# RHL — Controls & Game Feel (Brainstorm v0.1)

Target: PC with **Xbox AND PlayStation controllers** for couch play (layout shown in Xbox buttons; PlayStation equivalents: A=✕, B=○, X=□, Y=△, LB/RB=L1/R1, LT/RT=L2/R2), plus keyboard/mouse support.
All bindings remappable (UE5 Enhanced Input).

---

## 1. Game Feel Pillars

1. **Weight & momentum.** Skaters accelerate, glide, and carve. Speed takes time to build and time to lose. Speed = hitting power.
2. **Every hit lands hard.** Hitstop, camera shake, rumble, glass rattle, crowd roar — scaled to impact speed.
3. **Responsive, never floaty.** Input buffering, fast animation cancels, generous pass/puck-pickup assist.
4. **Readable chaos.** Even with items and fights, you always know where the puck is and who's dangerous.
5. **Easy to pick up, deep to master.** Simple Arcade controls by default; advanced techniques for skilled players.

---

## 2. Controller Layout — Arcade Scheme (default)

### Skater — With the Puck
| Input | Action |
|---|---|
| Left stick | Skate |
| Right stick | Aim shot/pass direction (optional — defaults to auto-aim) |
| **X** | Shoot — tap = wrist shot, **hold = charge slapshot** |
| **A** | Pass — tap = pass, hold = saucer/hard pass |
| **B** | Deke / protect puck (spin move) |
| **Y** | Dump / flip the puck |
| **RT** | Sprint (uses stamina) |
| **LT** | Hard stop / tight turn (snow spray) |
| **RB** | Use item (puck carrier can only use **puck mods**) |
| **LB** | Swap active ↔ stored item |

### Skater — Without the Puck
| Input | Action |
|---|---|
| **X** | Body check — tap = quick check, **hold = charged check** (power scales with speed) |
| **A** | Switch player (nearest to puck) |
| **B** | Poke check / stick lift |
| **Y** | Stick attack (slash/hook; uses equipped stick weapon) |
| **RB** | Use item (weapon / deployable / power-up) |
| **LB** | Swap active ↔ stored item |
| **R3 (click)** | **Drop the gloves** — challenge nearest opponent to a fight |
| **L3 (click)** | Taunt (small Hype gain, risky) |
| **Y + B** (max Hype, near weakened opponent) | **Finisher / signature move** |

### D-Pad
| Up | Down | Left | Right |
|---|---|---|---|
| Line change | Call for pass | Team strategy (aggressive / defensive) | Target lock (enforcer focus on one player) |

### Fight Mode — Skill-Based (timing & blocking)
Fights reward reading and timing, not mashing:
- **Telegraphs:** every punch has a readable wind-up (haymakers slow and obvious, jabs fast and weak).
- **Block:** holding block reduces damage but drains stamina; guard breaks if held too long.
- **Perfect block / parry:** block right as a punch lands → opponent staggers, opens a counter window.
- **Dodge:** ducking a haymaker at the right moment → free counter-hit.
- **Jersey control:** grabbing controls distance; whoever has the grip lands punches faster.
- **Stamina:** punching and blocking drain it; a gassed fighter's punches telegraph longer.
- **Win:** knock opponent down (injury/Hype) or pull jersey over their head (big damage window).
- Mashing is punished (whiffed punches leave you open). Recovering from a stun uses a **timed** button press, not mashing.

| Input | Action |
| Input | Action |
|---|---|
| **X** | Jab (left) |
| **Y** | Haymaker (right) |
| **B** | Block |
| **A** | Duck / dodge |
| **LT** | Grab jersey |
| **RT** | Pull jersey over head (opens big damage window) |
| Left stick | Lean / circle |
| **A** at the right moment when stunned | Recover (timed) |

### Goalie
| Input | Action |
|---|---|
| Left stick | Position in crease |
| Right stick | Directional save / dive (butterfly, stack pads, glove, blocker) |
| **X** | Poke check |
| **A** | Pass / clear |
| **B** | Freeze the puck (cover) |
| **Y** | Goalie weapon attack (spiked blocker, stick hook) |
| **RB** | Use goalie item (crease traps, etc.) |
| **LT** | Hug post |

---

## 3. "Pro" Scheme — Skill Stick (HIGH PRIORITY)
The son is an experienced NHL-games player, so a skill-stick scheme that feels familiar to sim-hockey players is a **launch requirement**, not an extra.
- Right stick: pull back + flick forward = slapshot, flick = wrist shot, rotate/side-to-side = dekes, stick handling.
- Manual pass power (hold) and aim.
- Checks on right stick (flick toward opponent) with combat actions moved to face buttons.
- Two presets selectable per player: **Arcade** (buttons) and **Pro** (skill stick). Each player picks their own on the couch.

## 4. Keyboard & Mouse (basic)
WASD skate · Mouse aim · LMB shoot/check (hold to charge) · RMB pass · Shift sprint · Ctrl stop · Space deke/poke · E item · Q swap item · F drop gloves · Tab switch player.

---

## 5. Core Systems

### Skating
- Acceleration curve, top speed, glide friction, **edge carving** (turn radius grows with speed).
- Hard stops spray snow and kill momentum; crossovers when turning at low speed.
- **Stamina:** sprinting and fighting drain it; low stamina = slower, weaker hits → encourages line changes.

### Hit Tiers (based on speed + charge + weight class)
| Tier | Result |
|---|---|
| Bump | Stumble, lose puck |
| Check | Knocked down, minor damage |
| Crush | Ragdoll into boards/glass, injury chance |
| Kill | Lethal (needs high speed, low health, weapon, or hazard) |

### Puck
- Real physics puck (bounces, rolls on edge, deflects) with a **sticky assist** on stick contact so handling feels clean.
- Shot power/accuracy affected by injuries (broken arm) and items.

### Assists (per player — good for mixed skill levels)
| Setting | Options |
|---|---|
| Pass assist | Full / Partial / Off |
| Shot aim assist | Full / Partial / Off |
| Auto-switch player | On / Off |
| Auto-skate defense | On / Off |
| Game speed | Slow / Normal / Fast |
| AI difficulty | Rookie → Prime Time |

### Couch Play
- Up to 4 controllers (Xbox and PlayStation mixed); same team (co-op vs AI) or versus.
- Each player picks their own control scheme (Arcade / Pro) and assist level.
- Each player keeps their own assist settings.
- Player indicator rings in each player's color.

---

## 6. Feedback & "Juice"

| On… | Feedback |
|---|---|
| Big hit | Hitstop (2–6 frames by tier), camera shake, rumble, glass rattle, crowd roar, blood (per gore setting) |
| Crush / kill | Brief slow-mo + broadcast replay angle, announcer call |
| High speed | Wider FOV, skate audio pitch up, ice spray, subtle motion blur |
| Goal | Horn, crowd, camera push, Hype spike, announcer |
| Fight start | Crowd chants, camera tightens, ring of players forms |
| Item pickup | Distinct sound + glow per item type |
| Injury | Limp/hold arm animation, icon ring under player (no floating health bars) |

## 7. Cameras
- **Behind the Player (DEFAULT):** third-person chase cam behind your skater — brutal and immersive.
  - Needs extra readability: puck indicator when off-screen, teammate/opponent arrows at screen edge, slightly raised height and wide FOV so you can see passing lanes, smooth swing when switching players.
  - Split-screen for couch play when each player uses this cam (2-way horizontal/vertical, 4-way).
- **Broadcast:** classic side view, pans and zooms with play (also available as shared single-screen couch option).
- **End-to-end:** vertical, follows attack direction.
- **Auto-cameras:** zoom on fights, finishers, and big hits; instant replays after goals/kills.

---

## 8. Tech Notes (UE5)
- **Skating:** custom movement mode on Character Movement Component (low friction, momentum, carving) — not physics-driven bodies, so it stays controllable.
- **Puck:** physics body with substepping / CCD so fast shots don't tunnel through sticks, nets, or boards.
- **Hits:** Physical Animation Component + ragdoll blend for reactions; hitstop via short custom time dilation on involved actors.
- **Input:** Enhanced Input with context mappings (Skater / Fight / Goalie / Menu), remappable.
- **PlayStation controllers on PC:** UE handles Xbox (XInput) natively; DualShock 4 / DualSense need extra support — use a raw-input/SDL controller plugin or Steam Input (add the game to Steam as a non-Steam game). Decide during vertical slice.
- **Button prompts:** auto-switch icons (Xbox vs PlayStation) based on the last controller used (CommonUI input icons).
- **Split-screen:** UE local multiplayer split-screen for behind-the-player cam.
- **Juice:** Niagara (ice spray, blood, sparks), Camera Shakes, Force Feedback assets, MetaSounds for dynamic crowd.

## 9. Vertical Slice — Feel Test Checklist
1. Skating alone feels good (accel, glide, carve, stop) — **tune this first, before anything else**
2. Puck handling + passing feel clean
3. Wrist shot / slapshot feel powerful
4. Body checks scale with speed and feel brutal
5. One fight works start to finish
6. Behind-the-player camera is readable (puck indicator, edge arrows)
7. Xbox + PlayStation controllers on one couch, split-screen, both having fun
8. Pro (skill stick) scheme feels right to an experienced NHL-games player

---

## Decisions (Oct 2026)
- Controllers: **Xbox and PlayStation** (mixed on one couch).
- Default camera: **Behind the Player** (split-screen for couch).
- Son = experienced NHL-games player → **Pro skill-stick scheme is a launch requirement**; he's the primary feel tester. Default assists per player: Pro/Off for him, Arcade/Partial for the owner.
- Fights: **skill-based** — timing, blocking, parries, dodges.
