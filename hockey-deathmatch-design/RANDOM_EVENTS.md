# RHL — Zamboni of Doom & Random Events (Brainstorm v0.1)

Random events are the "live TV chaos" layer. They're separate from:
- **Arena hazards & Network Events** (`ARENAS.md`) — arena-specific, Hype Tier 3
- **Item drops** (`SPAWN_DIRECTOR.md`)

Random events are **universal** (any arena), short, telegraphed, and run by an **Event Director**.

---

## 1. The Zamboni of Doom 🚜

### Basics
| | |
|---|---|
| **When** | Max **once per game** during play (Hype Tier 2+, random), plus always appears in **Intermission Chaos** |
| **Driver** | **Earl** — grizzled lifer Zamboni driver, never looks up from his thermos. Sometimes the home mascot rides with him |
| **Telegraph** | 3 s: garage door alarm + flashing amber lights + Dale: "OH NO — HERE COMES EARL!" + **glowing path line** painted on the ice |
| **Path** | Pre-set routes (lap, diagonal, figure-8, zig-zag); shown in full before it moves |
| **Speed** | 4 m/s — slow but **unstoppable** (can't be pushed) |
| **Duration** | 12–18 s, then exits through the other garage door |

### Effects
| Effect | Numbers |
|---|---|
| **Contact** | 40 damage + ragdoll 2.5 s; Downed players hit = **Killed** |
| **Item drops** | Drops **2–3 items** along its path (Spawn Director delivery) |
| **Fresh ice lane** | Leaves a resurfaced strip: **+15% speed** for 10 s on it, puck glides faster |
| **Puck** | Bounces off; it's a moving wall — great for bank passes |
| **Goals** | Play continues; it can screen goalies (son: watch out) |

### Interactions
- **Zamboni Surf:** grab the back bumper (button prompt) to ride it — +speed, you can't use items, any hit knocks you off.
- **Stall it:** Sledgehammer / lead-puck shot to the engine **stalls it 4 s** (Earl swears, restarts).
- **Check someone into it:** +25 damage bonus, huge Hype.
- **Goalies:** it never drives through the crease, but passes close — screens are real.

### Arena Variants
| Arena | Variant |
|---|---|
| The Plant | Rust-bucket Zamboni, sparks dragging behind |
| Mill No. 9 | **Slag Zamboni**: hot lane behind it (Burn for 6 s instead of fresh ice) |
| The Yard | Guards ride the sides, baton anyone nearby |
| The Jackpot | **Gold Zamboni** throwing casino chips (cosmetic) + extra item drop |
| The Barge | Leaks water: slush lane (slow) instead of fresh ice |
| Kold Kut | Spreads rink salt: Slip lane |
| Pier 13 | Earl's on a **forklift** carrying a crate (drops it as loot) |
| The Shaft | Headlights only — in the dark, it's terrifying; ore-cart rattle |
| Meridian Dome | Chrome Zamboni with drone escort and pyro |

---

## 2. Other Random Events

### Major Events (max 1 per period, besides the Zamboni)
| Event | What happens | Duration | Telegraph |
|---|---|---|---|
| **Glass Shatter** | A big hit breaks a glass pane → gap in the boards; players knocked through land in the crowd = **out for the shift** | Until next intermission (or repaired by crew during a stoppage) | Glass crack sound + cracked pane glow on heavy hits |
| **Power Flicker** | Arena lights cut (not in already-dark arenas); jersey reflective strips & sticks glow faintly | 6–10 s | Lights buzz and flicker 2 s first |
| **Lawless Minute** | A ref gets wiped out by a stray hit → **no penalties called** | 60 s | Ref ragdoll + "THE REF IS DOWN!" banner |
| **Bounty** | Meridian puts a price on the top scorer/star: knocking them Downed/Killed = big Hype + ratings | 90 s | Bounty banner + target marker |
| **Fight Spotlight** | Network spotlights two rivals: if they fight within 15 s, double Hype for both teams | 15 s window | Spotlights + crowd "FIGHT!" chant |
| **Ice Crack** | A section cracks: rough ice (−25% speed, puck bounces unpredictably) | 30 s | Crack sound, visible spider-web |

### Minor Events (more frequent)
| Event | What happens | Duration |
|---|---|---|
| **Mascot Invasion** | Mascot runs onto the ice, may drop an item, can be checked (see `CUSTOM_TEAM.md`) | 10 s |
| **Fan on the Ice** | A fan climbs the glass and runs around; check him = Hype (crowd cheers/boos); security tackles him | 10 s |
| **Crowd Barrage** | Fans throw junk: debris on the ice (slips) near the losing team's zone… or the refs | 8 s |
| **VoltRush Power Minute** | Sponsor event: **all Hype gains ×2** | 60 s |
| **Ironclad Double Goal** | Sponsor puck: next goal counts **double** | Until next goal or 60 s |
| **Penalty Box Brawl** | Two opponents in the box at once → the box door jams and they fight | Until fight ends |
| **Squall / Leak** | Weather burst: snow squall (outdoor) or roof leak puddles (indoor) — slush patches | 20 s |
| **Camera Drone Crash** (Meridian Dome only) | Broadcast drone falls onto the ice — small explosion, debris | Instant |

---

## 3. Event Director

### Rules
- **Budget system** (like the Spawn Director): events cost points; budget fills with time and Hype.
- **Limits:** max 1 major per period (+ Zamboni once per game); minors spaced ≥ 45 s apart.
- **Never overlaps** a Network Event, a Zamboni run, or goal celebrations; never in the last 30 s of a tied third period (keep endings clean) — except Sudden Death specials.
- **Hype gating:** majors need Tier 2+; Bounty needs a clear "star" (most goals/kills).
- **Fairness:** events are neutral (no catch-up bias), except **Crowd Barrage** (aims at the losing team's zone — the crowd's angry).
- **Telegraph rule:** every event has ≥ 2 s warning (sound + visual + announcer).

### Default Frequency (Normal)
| Setting | Per 3-period game |
|---|---|
| Off | 0 |
| Rare | Zamboni maybe + 1–2 minors |
| **Normal (default)** | Zamboni (60% chance) + 1–2 majors + 3–4 minors |
| Chaos | Zamboni guaranteed + major every period + minor every ~60 s |

### Settings & House Rules
- **Random Events:** Off / Rare / **Normal** / Chaos
- **Per-event toggles** (e.g. no Glass Shatter, Zamboni only)
- Saved in **House Rules presets** (`SPAWN_DIRECTOR.md` §6)

### Mode Overrides
| Mode | Behavior |
|---|---|
| Exhibition | Settings |
| Practice | Manual trigger menu for any event |
| Challenges | Scripted events (e.g. "Zamboni Season") |
| Shootout of Death | Off (except Power Flicker / Fan on Ice as rare flavor) |
| Career | Normal + **subtle rigging** in Act 3 (events tend to land near you); story-scripted events (Holloway's "special" Zamboni run) |
| Franchise | League setting; simmed games roll events into the Sim Log |

---

## 4. Audio & Broadcast
- Every event has: a sting, Dale + Knuckles call lines, crowd reaction, a lower-third banner (`UI.md`).
- **Earl** gets a few lines (muttering, swearing at players, "Not my problem").
- Events are tagged for replays and add to the **Excitement Score**.

---

## 5. Data Setup
`RandomEventDefinition` (Data Asset): ID, major/minor, cost, min Hype tier, cooldown, duration, allowed arenas/modes,
telegraph (sound, VFX, announcer set, lead time), effects (gameplay abilities / spawned actors), toggles.

---

## 6. Build Order
1. Event Director framework (budget, limits, telegraph pipeline, settings)
2. **Zamboni of Doom** (core run, path telegraph, contact damage, item drops, fresh-ice lane)
3. Minor events: Fan on the Ice, Crowd Barrage, VoltRush Power Minute, Mascot Invasion
4. Majors: Glass Shatter, Power Flicker, Lawless Minute, Bounty
5. Zamboni Surf + stall interactions
6. Arena Zamboni variants
7. Remaining events + Career scripting

---

## Open Questions
- Zamboni Surf — keep (fun but chaotic)?
- Glass Shatter knocking players into the crowd — keep?
- Any event to cut or add?
