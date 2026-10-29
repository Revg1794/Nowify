# RHL — Item Spawn Director (Brainstorm v0.1)

The **Spawn Director** is one system that decides **what** item appears, **when**, **where**, and **how it's delivered**.
It's the "dungeon master" of each match: it keeps games chaotic but fair, pulls players away from the puck at the right
moments, and makes the Crowd Hype system feel like it controls the arena.

---

## 1. Goals
1. **Pacing:** items arrive in waves that create moments, not a constant clutter.
2. **Fairness:** both teams get real chances; drops are telegraphed; no instant unavoidable deaths.
3. **Comebacks:** the trailing team gets slightly better odds (adjustable).
4. **Hype matters:** a louder crowd = better and more frequent items.
5. **Hockey stays first:** items create *choices* (chase the item or the puck?), never replace hockey.
6. **Tunable without code:** everything lives in Data Tables / Data Assets + sliders.

---

## 2. The Four Decisions

### WHEN — The Drop Budget
- The Director keeps a **Drop Budget** that fills over time. When it's full enough to afford an item, a drop happens.
- **Budget fill rate** is affected by:
  | Input | Effect |
  |---|---|
  | Base rate | ~1 drop every 35–50 s (Normal item frequency) |
  | Crowd Hype tier | Tier 1 ×1.0 · Tier 2 ×1.3 · Tier 3 ×1.6 |
  | Item Frequency slider | Off ×0 · Classic ×0.5 · Normal ×1 · Chaos ×2.5 |
  | Match clock | Last 2 minutes of a period ×1.25 (late drama) |
  | Items already on ice | Each uncollected item slows fill (prevents clutter) |
- **Hard limits:** max items on ice (default 3; Chaos 6), min gap between drops (default 12 s).
- **Quiet windows:** no drops during faceoffs, goal celebrations, or the first 20 s of a period.

### WHAT — Weighted Rarity Tables
- Every item has a **rarity**, a **weight**, and **conditions**.

  | Rarity | Examples | Delivery |
  |---|---|---|
  | **Common** | Bottles, rink salt, hockey tape (taped knuckles), smelling salts | Crowd throws |
  | **Uncommon** | Nail-studded stick, chain, weighted puck, padlock-in-sock, painkillers | Crowd throws / arena delivery |
  | **Rare** | Sledgehammer stick, razor stick, barbed-wire puck, riot padding, adrenaline shot | Sponsor drops |
  | **Legendary** | Network-only items (e.g. chainsaw-free but brutal: skate-blade stick, flare puck pack) | Network Events (Tier 3 / Max Hype) |

- **Hype tier caps the rarity:** Tier 0–1 → Common/Uncommon · Tier 2 → up to Rare · Tier 3 → up to Legendary.
- **Weight modifiers:**
  - **Catch-up:** trailing team's side gets better rarity odds (scaled by goal difference & Catch-Up slider).
  - **Anti-repeat:** the same item can't drop twice in a row; recently dropped items get lower weight.
  - **Situational:** e.g. more puck mods when a team has had no shots for a while; more defensive items for a team being bullied; fewer lethal items when someone is already badly injured (prevents pile-ons — optional).
  - **Arena flavor:** each arena boosts certain items (The Plant: chains & sledges; Kold Kut: hooks & blades; The Barge: salt & flares).
  - **Hazard/Event links:** Blackout or The Shaft → more flare pucks; Whiteout → more flares.

### WHERE — Spawn Location Scoring
- Each arena has **Spawn Points** placed by hand (ice spots, crease-side spots, board-side spots, penalty box).
- The Director **scores** candidate points and picks from the best few (with some randomness):
  | Factor | Rule |
  |---|---|
  | Fairness | Prefer points roughly equidistant to the nearest player of each team |
  | Catch-up | Slight bias toward the trailing team's players |
  | Puck tension | Prefer spots **away from the puck** (forces a choice: puck or item) — but not too far |
  | Safety | Never inside the crease (except goalie items), never on top of a player, never in a hazard's active zone |
  | Variety | Avoid the last 2 spawn spots used |

### HOW — Delivery (per arena)
- Every drop has a **telegraph** first: announcer call, sound sting, light/marker on the ice (2–4 s), then the delivery animation.
  | Arena | Delivery style |
  |---|---|
  | The Pit | Crowd throw (bare-bones) |
  | The Plant | Rides in on conveyor hooks |
  | Mill No. 9 | Crane bucket drop |
  | The Yard | Contraband thrown over the wall |
  | The Jackpot | Gold briefcase lowered from ceiling |
  | The Barge | Floats up frozen in the ice (slapshot to free it) |
  | Kold Kut | Carts roll out of cold storage |
  | Pier 13 | Crane drops a crate |
  | The Shaft | Ore carts on rails |
  | Meridian Dome | Drone delivery with camera spotlight |
- **Universal deliveries (any arena):** Crowd throws, Sponsor drops, **Zamboni of Doom** (intermission/event), **Penalty box loot**.

---

## 3. Special Drop Rules

| Rule | Behavior |
|---|---|
| **Penalty box loot** | Player serving a penalty gets 1 random item (Common/Uncommon) on release |
| **Zamboni of Doom** | Random event (once per game max, Hype Tier 2+): Zamboni drives a path across the ice dropping 2–3 items; it kills/injures anyone in its path (telegraphed path line) |
| **Network Event drops** | At Tier 3: 1 Legendary or an arena-specific "item rain" (e.g. Jackpot) |
| **Revenge drop** | If your goalie is badly hurt, your team's next drop odds improve |
| **Despawn** | Uncollected items vanish after 20 s (blink warning at 15 s) |
| **Item slots** | Grabbing when full replaces the **stored** slot (per design rules) |
| **Puck carrier rule** | Puck carriers can grab only puck mods; other items stay on the ice for teammates |

---

## 4. Goalie Item Pool (separate)
- Goalies can't chase items, so goalie items come **to them**:
  - **Crowd behind the net** throws goalie items over the glass into the crease.
  - **Crease drop** telegraph: small marker at the goalie's feet, 2 s, then item lands.
- **Own budget:** separate, slower fill (default ~1 goalie item every 60–90 s), boosted by:
  - Hot Streak (consecutive saves)
  - Team being outshot heavily
  - Goalie being targeted/hit (revenge)
- Goalie item rarity follows the same Hype caps.

---

## 5. Mode & Story Overrides

| Mode | Director behavior |
|---|---|
| **Exhibition** | Fully controlled by settings & sliders |
| **Practice (The Pit)** | Manual spawn menu — pick any item, place anywhere |
| **Challenges** | **Scripted drops** per challenge ("only bottles," "one Legendary at 0:30") |
| **Penalty Shootout of Death** | One item per shooter/goalie before each attempt (chosen by Hype or random) |
| **Franchise** | Uses league rules settings; simmed games ignore it |
| **Career** | Normal Director + **story rigging** (below) |

### Career Story Rigging (the network cheats)
- **Act 1 playoffs at The Jackpot:** odds tilted toward the High Rollers.
- **Act 3:** Holloway's network rigs the Director **against you** — worse drops, more hazards near you, sponsor drops "accidentally" land near rivals.
- **Live Feed path:** once Knuckles is on your side, he "glitches" a fair drop or two your way.
- Rigging is shown in-world (announcer slips, suspicious camera cuts) so it feels like story, not unfair code.

---

## 6. Settings & Sliders (connects to `DIFFICULTY_SLIDERS.md`)
- **Item Frequency:** Off / Classic / Normal / Chaos
- **Catch-Up Logic:** Off → Strong
- **Max Items on Ice**
- **Item Toggles:** turn individual items on/off (custom lobbies, kid-friendly mode)
- **Legendary Items:** On / Off
- **Zamboni of Doom:** On / Off
- **Goalie Items:** On / Off

---

## 7. Data Setup (for implementation)

### `ItemDefinition` (Data Asset, one per item)
| Field | Example |
|---|---|
| ID / Name | `Item_LeadPuck` / "Lead-Weighted Puck" |
| Category | StickMod / PuckMod / Thrown / Deployable / PowerUp / Goalie |
| Rarity | Uncommon |
| Base Weight | 10 |
| Min Hype Tier | 1 |
| Usable by | Skater / PuckCarrier / Goalie |
| Duration / Uses | 3 shots |
| Arena weight multipliers | The Plant ×1.5 |
| Mesh / Pickup Mesh / VFX / SFX | references |
| Gameplay Ability | `GA_LeadPuck` (GAS) |
| Announcer line set | `VO_Item_LeadPuck` |

### `SpawnDirectorConfig` (Data Asset, per mode/arena)
Base rate, max items, min gap, quiet windows, Hype multipliers, catch-up strength, despawn time, delivery types allowed.

### Spawn Points (placed actors in each arena)
Type (Ice / Boards / Crease / PenaltyBox), allowed deliveries, enabled/disabled by hazards.

---

## 8. Director Loop (pseudocode)

```
Every 0.5s:
  if quiet window or items_on_ice >= max: return
  budget += base_rate * hype_mult * frequency_mult * clock_mult * clutter_mult * dt
  if budget < next_drop_cost or time_since_last_drop < min_gap: return

  rarity_cap = cap_from_hype(current_hype_tier)
  candidates = items where enabled, min_hype <= tier, rarity <= rarity_cap
  weights = base_weight * arena_mult * catchup_mult * situational_mult * anti_repeat_mult
  item = weighted_random(candidates, weights)

  point = best_scored_spawn_point(fairness, catchup, puck_tension, safety, variety)
  delivery = pick_delivery(arena, item.rarity, point)

  telegraph(item, point, delivery)   // announcer + sting + ice marker, 2–4s
  deliver(item, point, delivery)
  budget -= item_cost(item.rarity)
  log_for_debug(item, point, weights)
```

---

## 9. Debug & Tuning Tools
- **On-screen overlay:** current budget, next drop ETA, Hype tier, catch-up multiplier, last 5 drops.
- **Spawn point visualizer:** colored scores on every spawn point.
- **Force spawn** console commands (`rhl.spawn Item_LeadPuck`).
- **Match log** (CSV): every drop with time, item, location, who picked it up, what it did — used to balance.
- **Sim mode:** run 100 AI-vs-AI matches headless and summarize item stats (pickup rates, kills per item, win-rate impact).

---

## 10. Build Order
1. Basic timer drops + random item + random spawn point (milestone 3 start)
2. Drop Budget + Hype multipliers + limits
3. Rarity tables + Hype caps
4. Spawn point scoring (fairness, puck tension, safety)
5. Telegraphs + crowd-throw delivery
6. Catch-up logic + anti-repeat
7. Goalie pool
8. Arena deliveries + Zamboni + penalty box loot
9. Debug overlay + match logs + headless sims
10. Mode overrides (Challenges, Shootout, Career rigging)

---

## Open Questions
- Default item frequency: is ~1 drop every 35–50 s right for a normal game, or more chaotic?
- Should Career rigging be obvious (you can feel it) or subtle?
- Should individual item toggles be part of a saved "house rules" preset for couch games?
