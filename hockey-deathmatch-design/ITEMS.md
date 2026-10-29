# RHL — Weapons & Items (Brainstorm v0.1, first-pass numbers)

Every item with exact effects and **starting numbers**. All values live in Data Assets and get tuned through
play + headless sims (`SPAWN_DIRECTOR.md` §9). Grounded & brutal: everything could exist in a rink, garage, or back alley.

---

## 1. Core Combat Numbers (baseline for all items)

### Health
| | Value |
|---|---|
| Skater health | **100** |
| Goalie health | **150** (+30% damage reduction inside the crease — Crease Authority) |
| Regen | None during a shift; full heal on line change **except injuries** |

### Body Hits (no items) — from `CONTROLS_AND_FEEL.md` hit tiers
| Tier | Damage | Extra |
|---|---|---|
| Bump | 5 | Stumble, puck loose |
| Check | 15 | Knockdown 1.0 s |
| Crush | 30 | Ragdoll 2.0 s, 15% injury chance (+10% into boards/glass) |
| Hazard hit (into hooks, hot boards, etc.) | +15–40 | Per hazard |
| Punch (jab / haymaker) | 4 / 12 | Haymaker staggers |
| Slapshot to the body | 10 | 25% to the head = concussion chance 20% |

### Downed → Killed (elimination rule)
- At **0 HP** a player is **Downed**: they collapse and crawl toward the bench (slow, can't act).
- A Downed player who takes **any Crush hit, weapon hit, hazard hit, or a finisher** is **Killed** (out of the game until line-change respawn; permadeath in Career/Franchise if enabled).
- If they reach the bench (or ~8 s pass) they're just **out for the shift**.
- **Rookie Mercy:** AI never kills Downed players on Rookie.
- Target **time-to-down** without items: **4–5 Crush-level hits**. With a strong item: **2–3**.

### Status Effects
| Effect | Numbers | Cleared by |
|---|---|---|
| **Bleed** | 2 HP/s until bench (stacks up to 3 = 6 HP/s) | Bench, Taped-Up kit |
| **Burn** | 4 HP/s for 3 s; −15% puck control | Time; ice/slush |
| **Stun** | 0.8–1.5 s no control | Smelling Salts |
| **Slow** | −30% speed for 3 s | Time |
| **Slip** | Lose footing, 1 s down, puck loose | — |
| **Blind** | Vision blur/white-out 2–3 s | Time |
| **Pulled** | Yanked 3–5 m toward attacker | — |
| **Pinned/Trapped** | Can't move 2–4 s (mash-free: timed button to escape early) | Time / teammate hit |
| **Broken bone** | Injury (arm: −30% shot power/accuracy; leg: −20% speed) — lasts the game (+ Career/Franchise recovery) | Medic between games |

---

## 2. Item Rules (recap)
- **1 active + 1 stored slot**; grabbing when full replaces stored.
- **Puck carriers** can only use **puck mods**.
- Items **despawn** after 20 s on the ice.
- Stick mods replace your stick **visually** and break after their uses (stick returns to normal).
- Every item has a **tell** (sound + visual) so it's counterable.
- Gore setting changes visuals only, never numbers.

---

## 3. Stick Mods (melee — swing with Y / stick attack)

| Item | Rarity | Uses | Damage | Effect | Tell / Counter |
|---|---|---|---|---|---|
| **Taped Razor Blades** | Rare | 6 swings | 10 | **Bleed** ×1 per hit | Glint on blade · block with stick (poke check timing) |
| **Nail-Studded Stick** | Uncommon | 6 | 14 | 20% Bleed | Nails visible · keep distance |
| **Bike-Chain Wrap** | Uncommon | 5 | 12 | **Pulled** 3 m on hit; can strip puck from range (2.5 m) | Chain rattle · skate away at speed |
| **Aluminum Bat-Stick** | Uncommon | 5 | 18 | Big knockback; 25% Stun | Metallic ring on wind-up |
| **Sledgehammer Stick** | Rare | 3 | 30 | Knockdown + **cracks ice** (2 m slush patch, 8 s) | Slow 0.8 s wind-up · dodge/dash |
| **Skate-Blade Stick** | Legendary | 4 | 22 | Bleed ×2; Downed targets → instant Kill | Shriek sound · glowing red outline |
| **Meat Hook** (Butchers arena flavor) | Rare | 4 | 12 | **Pulled** 5 m; into a wall hook = +25 | Hook swing whoosh |

Stick mods: puck control −20% while equipped (you're holding a weapon).

---

## 4. Puck Mods (next shot(s) — usable by puck carriers)

| Item | Rarity | Shots | Hit damage | Effect on goalie/players | Notes |
|---|---|---|---|---|---|
| **Lead-Weighted Puck** | Uncommon | 3 | 25 | 30% **Broken bone** on body hit; goalie takes 20 dmg on save | Slower puck (−15%), harder to stop cleanly (rebounds) |
| **Frozen Iron Puck** | Uncommon | 3 | 20 | Shatters on the post into shrapnel (10 dmg, 2 m) | Normal speed |
| **Barbed-Wire Puck** | Rare | 3 | 15 | **Bleed** ×2 on hit; goalie glove/blocker damage | Rattling sound in flight |
| **Road-Flare Puck** | Legendary (pack of 3) | 3 | 15 | **Burn**; lights up dark arenas (Blackout/The Shaft); leaves fire trail on ice 3 s | Bright, easy to track — good for goalies to see |
| **Firecracker Puck** | Rare | 1 | 10 + 3×5 pops | Pops around landing spot: **Blind** 1.5 s, scatters players | Crackle fuse sound 0.5 s |

Goal scored with a puck mod: **+Hype bonus** (+50%).

---

## 5. Thrown Weapons (aim with right stick, throw with RB)

| Item | Rarity | Uses | Damage | Effect | Notes |
|---|---|---|---|---|---|
| **Glass Bottles** | Common | 3 | 8 | 15% Stun; leaves **broken glass** (2 m, 6 s): 5 dmg + Slip | Crowd-thrown classic |
| **Rink Salt** (bucket) | Common | 2 | 0 | **Blind** 2 s + **Slow** 3 s in a cone | Short range (4 m) |
| **Padlock in a Sock** | Uncommon | 2 | 20 | **Stun** 1.2 s | Spin-up 0.4 s (tell) |
| **Chain** | Uncommon | 3 | 14 | **Pulled** 4 m / trip | Can trip a skater at full speed (Slip + 10) |
| **Broken Hockey Stick (spear)** | Common | 1 | 16 | 30% Bleed | Long range, slow |

---

## 6. Deployables (place on the ice — RB)

| Item | Rarity | Duration | Effect | Counter |
|---|---|---|---|---|
| **Broken Glass** (handful) | Common | 10 s | 5 dmg + Slip to anyone crossing | Visible glint; skate around |
| **Spike Strip** | Uncommon | 12 s | 12 dmg + Slip + 20% Bleed | Visible; jump-hop (tap A) over at speed |
| **Bear Trap** | Legendary | 20 s or 1 trigger | **Trapped** 3 s + 20 dmg + 40% broken leg | Faint click when nearby; teammates can pry open (1 s) |
| **Oil Slick** | Uncommon | 10 s | Zero friction zone (players and puck slide) | Visible sheen |
| **Smoke Can** | Uncommon | 8 s | Blocks vision in 5 m radius (AI too) | — |

Limit: max 2 active deployables per team on the ice.

---

## 7. Skater Power-Ups (instant / timed)

| Item | Rarity | Duration | Effect |
|---|---|---|---|
| **Smelling Salts** | Common | Instant (held — auto-trigger) | Auto-recover from next Stun/knockdown; clears Blind |
| **Hockey Tape (Taped Knuckles)** | Common | 30 s | Punches +100% damage; haymaker always staggers |
| **Painkillers** | Uncommon | 20 s | Ignore knockdowns (except Crush), injury effects suppressed; −30% damage taken |
| **Steel-Toe Skates** | Uncommon | 30 s | Trips/kicks deal 15 + Slip; hard stops spray ice that Blinds 1 s |
| **Riot Padding** | Rare | 30 s | −50% damage taken, immune to Bleed; −15% speed |
| **Adrenaline Shot** | Rare | 10 s | +25% speed, +30% acceleration, hits gain one tier (Check → Crush) |
| **Taped-Up Kit** | Uncommon | Instant | Stop all Bleed, +25 HP (not above 100) |

---

## 8. Goalie Items (separate pool — `GOALIE.md`)

| Item | Rarity | Duration / uses | Effect |
|---|---|---|---|
| **Crease Salt** | Common | 15 s | Crease area: attackers Slow + Slip chance 30% |
| **Taped-Up Pads** | Common | Instant | Repair broken gear + 30 HP |
| **Tar-Coated Glove** | Uncommon | 30 s | Glove saves always catch (no rebounds) |
| **Steel-Toe Skates (goalie)** | Uncommon | 30 s | Pad kicks from butterfly: 15 dmg + Slip |
| **Weighted Goalie Stick** | Uncommon | 30 s | Slash/poke 20 dmg; poke check range +30% |
| **Goalie Stick Hook** | Uncommon | 4 uses | Pull a skater into the post: 18 dmg + Stun 1 s |
| **Crease Traps (chains)** | Rare | 20 s | Chains around crease edge: crossing = Pulled + 12 dmg |
| **Nail Board** | Rare | 1 trigger / 20 s | Placed in crease: 20 dmg + Bleed + Slip |
| **Iron Mask** | Rare | 1 hit | Blocks one headshot/head hit completely |
| **Spiked Blocker** | Rare | 30 s | Shots deflected off blocker shatter (puck mods neutralized); touching blocker = Bleed |
| **Weighted Leg Pads** | Rare | 30 s | Can't be knocked down; +20% low save area; −20% lateral speed |
| **Blood in the Crease** | Legendary | 45 s | +10 HP per save (+20 on Perfect Save) |

---

## 9. Signature Moves & Finishers (not items — Hype Max)
| Rule | Value |
|---|---|
| Finisher | Kills any Downed or ≤25 HP target; star signature moves per `STAR_PLAYERS.md` |
| Hype cost | Uses the full Max meter (drops to Tier 1) |
| Range | 2.5 m, target must be stunned, pinned, downed, or low HP |
| Rookie Mercy | AI won't finisher Downed players on Rookie |

---

## 10. Item → Hype Values
| Event | Hype gain |
|---|---|
| Item hit | +2 |
| Status effect applied (Bleed/Burn/Stun) | +3 |
| Downed with an item | +8 |
| Kill with an item | +12 |
| Goal with a puck mod | +15 |
| Goalie item save/hit | +4 |

---

## 11. Balance Principles
1. **No one-shot kills** from full health (except Legendary on a Downed player / finishers).
2. **Every item has a counter** (dodge, block, distance, teammate help).
3. **Melee needs commitment** (wind-ups), **thrown needs aim**, **deployables need prediction**.
4. **Puck mods favor offense** but goalies always have a chance (rebounds, tracking).
5. **Legendary = big but readable** (glowing outlines, unique sounds).
6. Item damage multiplied by **Weapon Damage** slider; frequency by **Item Frequency** slider.

### Tuning targets (check via sims)
- Item kills: **~30–40%** of all kills (the rest from hits, fights, hazards).
- Average items used per player per game (Normal): **4–6**.
- No single item above **15%** of all item kills.
- Puck-mod goal share: **~15–20%** of goals.

---

## 12. Item Count Summary
| Category | Count |
|---|---|
| Stick mods | 7 |
| Puck mods | 5 |
| Thrown | 5 |
| Deployables | 5 |
| Skater power-ups | 7 |
| Goalie items | 12 |
| **Total** | **41** |

### Starter set for the item-system milestone (6 items)
Glass Bottles · Nail-Studded Stick · Lead-Weighted Puck · Spike Strip · Adrenaline Shot · Crease Salt (goalie)

---

## Open Questions
- Downed → Killed rule OK (crawl to bench vs finished off)?
- Any items to cut or add?
- Should certain items be **arena-exclusive** (Meat Hook only in Kold Kut, Road-Flare more common in The Shaft)?
