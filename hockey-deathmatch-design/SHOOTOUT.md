# RHL — Penalty Shootout of Death (Brainstorm v0.1)

A classic hockey shootout — except the **goalie can attack the shooter**, the **shooter can attack the goalie**,
both get **items**, and **damage carries over**. Used as a **standalone mode** and as the **tiebreaker** for tied games.
Perfect for the couch: **son in net, owner shooting** (then swap).

---

## 1. Core Rules

| Rule | Default |
|---|---|
| Rounds | **Best of 5**, then sudden death (options: 1 / 3 / 5 / 7) |
| Order | Teams alternate; each team sets its shooter order (no repeats until everyone has shot) |
| Start | Shooter starts at center ice with the puck; whistle + spotlight |
| **Shot clock** | **8 seconds** to shoot (clock runs from first touch) |
| Shooter limits | Can't retreat back past the red line |
| Goalie limits | Can leave the crease anywhere in the **defensive zone** (but the net is empty while out) — starting rule; tune after playtesting |
| Rebounds | **No rebounds** — one shot only (unless the puck mod says otherwise) |
| Clinch | Ends early when one team can't catch up |

### Outcomes of an attempt
| Outcome | Result |
|---|---|
| **Goal** | Point for shooter's team |
| **Save** | No point |
| **Goalie Strikes Back** — goalie Downs the shooter before the shot | Save + big Hype for the goalie's team |
| **Shooter downs the goalie** | Shooter gets an open net — must still shoot before the clock ends |
| **Shot clock expires** | Miss (crowd boos) |
| **Kill** (either way, Downed then finished/hazard) | Counts as the attempt result above + a skull on the scoreboard |

---

## 2. Health & Damage Carry-Over (the "of Death" part)

| | Rule |
|---|---|
| **Goalies** | Health **carries over** between rounds (150 HP, no healing) — the goalie gets more battered every attempt |
| **Shooters** | Start each attempt at their **current** health (in a tiebreaker: their end-of-game health) |
| **Injuries** | Stay for the whole shootout (broken arm = weaker shot; goalie broken glove = weaker glove side) |
| **Goalie killed** | Backup goalie comes in (fresh). If the backup dies too → a **skater must play goalie** (terrible ratings, great TV) |
| **Shooter killed** | They're out; their next turn is skipped (team must use the next shooter) |
| **Rookie Mercy** | AI won't kill on Rookie; Downed is the max |

Setting: **Carry-Over Damage: On (default) / Off** (Off = everyone fresh each round).

---

## 3. Items

Before each attempt, **both shooter and goalie** get an item.

| Item Mode | How it works |
|---|---|
| **Item Roulette (default)** | A spinning wheel on the jumbotron picks one random item each (crowd goes "OHHH") |
| **Draft** | Each picks 1 of 3 random options (more strategy) |
| **Loadout** | Choose any item from the pool (house-rules fun) |
| **Off** | Pure skill |

- **Shooters** can get: puck mods (Lead, Iron, Barbed-Wire, Road-Flare, Firecracker), power-ups (Adrenaline, Painkillers, Smelling Salts, Taped Knuckles), thrown items (Salt, Bottles, Padlock).
- **Goalies** get goalie items (Tar Glove, Crease Salt, Nail Board, Spiked Blocker, Iron Mask, Weighted Stick, Goalie Hook, Blood in the Crease…).
- Items last **one attempt** only.
- Item rarity rises in later rounds and sudden death (Legendary possible from round 5+).

---

## 4. Moves & Controls

Uses normal controls (`CONTROLS_AND_FEEL.md`) plus:
| Who | Special |
|---|---|
| **Shooter** | Dekes, fakes (fake shot freezes AI goalies briefly), body check/stick attack on the goalie, use item |
| **Goalie** | Poke check, **charge** out of the crease (skate attack), blocker punch, stick slash, glove grab, goalie items |
| **Both** | Perfect Save timing window still applies; skill stick (Pro) supported |

### Hype in the Shootout
- Crowd Hype builds with every attempt (goals, saves, hits, kills).
- At **Max Hype**, the current player gets a moment:
  - **Shooter — "Showtime":** brief slow-mo as you release the shot (more accuracy & power).
  - **Goalie — "The Wall":** larger Perfect Save window + reflex focus for that attempt.

---

## 5. Presentation
- **Arena lights drop**; spotlights on shooter and goalie; drum roll; crowd chants the shooter's (or goalie's) name.
- Dale & Knuckles call every attempt; Tasha does a quick sideline line between rounds ("The goalie's bleeding badly…").
- **Scoreboard:** ✔ goal · ✖ save · 💀 kill · ⏱ clock miss — styled as a Meridian graphic.
- **Instant replay** after every attempt (skippable; helmet cam on goalie attacks).
- Shootout highlights auto-tagged for the replay system (Goalie Reel loves this).

---

## 6. Variants (in the standalone mode)

| Variant | Rules |
|---|---|
| **Classic of Death** | Rules above |
| **Sudden Death** | One round; first miss loses |
| **Gauntlet** | One goalie vs every shooter on a team (12). Goalie wins by allowing ≤ X goals — or by surviving. Made for the son |
| **Last Man Standing** | Downed shooters are eliminated; when a team runs out of shooters, they lose |
| **Double Trouble** | 2 shooters vs 1 goalie per attempt (passing allowed) |
| **Goalie vs Goalie** | Both goalies take turns shooting on each other (goalie-goal heaven) |
| **Blackout Shootout** | Lights off; headlamps, flare pucks, and the spotlight only |

---

## 7. Tiebreaker Use (regular games)
| Setting | Options |
|---|---|
| **Overtime format** | **5-min 3v3 sudden-death OT → Shootout of Death (default)** · straight to Shootout · OT only (ties allowed in Exhibition) |
| Playoffs | OT periods until a goal (classic) or Shootout after first OT (setting) |
| Career | Key story games can force a Shootout of Death (e.g. Act 1 playoff vs Vegas) |

---

## 8. Standalone Mode Setup
- Teams (any, including custom), **who's in net** (per human player: goalie or shooter), shooter order.
- Rounds, item mode, carry-over damage, variant, arena, weather/time, hazards (Off by default; optional "Shootout Hazards").
- **Couch setups:** owner vs son (1 goalie + 1 shooter each team, swap every round), or both vs AI.
- **Records:** shootout wins, save %, Goalie Strikes Back count, kills — on profiles.

---

## 9. AI in the Shootout
- **AI shooters** have tendencies by star/archetype (Ace dekes, Kowalski charges the goalie, Batiste speeds in, Moretti uses items/tricks).
- **AI goalies** pick between staying home or charging out, based on personality (Gator charges often, Lund never leaves).
- Difficulty sliders apply (reaction time, read of fakes).

---

## 10. Build Order
1. Basic shootout: rounds, alternating shooters, shot clock, goal/save, scoreboard (fits right after the vertical slice — great reveal content)
2. Goalie attacks + shooter attacks + Downed/Kill outcomes
3. Health carry-over + backups + skater-in-net
4. Items (Roulette first, then Draft/Loadout)
5. Presentation (spotlights, chants, replays, Showtime/The Wall)
6. Variants (Gauntlet, Sudden Death, Goalie vs Goalie first)
7. Tiebreaker integration + Career scripted shootouts

---

## Decisions (Oct 2026)
- Shot clock: **8 seconds**.
- Goalie range: **anywhere in his defensive zone** (starting point; revisit after playtests).
- **Basic Shootout of Death is part of the reveal build** for the son (build step 1, then step 2 if time allows).
