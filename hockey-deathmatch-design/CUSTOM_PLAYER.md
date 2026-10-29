# RHL — Custom Player Creation (Brainstorm v0.1)

Detailed design for the **Create Player** suite (expands `GAME_DESIGN.md` §6). Same system powers **Edit Player**
(`STAR_PLAYERS.md` §6) and the Career create-a-player.

---

## 1. Flow Overview

Presented as a **Meridian "Draft Combine" broadcast**: you're a prospect being measured, photographed, and scouted.

| Step | Screen | What you set |
|---|---|---|
| 0 | **Quick Start** | Pick an archetype template or Randomize → jump to any step or finish |
| 1 | **Identity** | Name, nickname, number, hometown (real city), nationality, age, shoots/catches L/R |
| 2 | **Origin** | Backstory (gives a perk) |
| 3 | **Position & Archetype** | Position + playstyle archetype |
| 4 | **Body** | Height, weight class, build |
| 5 | **Face** | Head, features, skin, hair, facial hair |
| 6 | **Marks** | Scars, tattoos, teeth, broken nose, black eyes |
| 7 | **Gear** | Helmet, visor/cage, gloves, pads, skates, stick, tape (goalies: mask, pads, glove, blocker) |
| 8 | **Ratings** | Attribute points |
| 9 | **Fighting** | Fight style + signature finisher |
| 10 | **Traits** | 2 strengths |
| 11 | **Presentation** | Voice, walkout, celebrations, taunts, goal song |
| 12 | **Combine Results** | Broadcast-style scouting report + Dale announcing your name → Save |

- Every step can be skipped; defaults come from the archetype.
- **Randomize** buttons on every step, with **lock** toggles (randomize face but keep hair, etc.).
- **Undo / Redo** everywhere.

---

## 2. Identity
- **Name & nickname:** free text. Dale/PA call your name via local TTS (generated at save); preview button.
  If TTS pronunciation is off: phonetic spelling field, or fall back to nickname/number calls.
- **Number:** 0–99 (00 allowed).
- **Hometown:** pick any real city (announcers mention it: "Out of Duluth, Minnesota…").
- **Age:** 18–45 (affects starting ratings in Franchise and progression speed).

---

## 3. Origins (backstory + small perk)

| Origin | Perk | Flavor |
|---|---|---|
| **Mill Worker** | +Toughness, slower stamina drain | Grew up in a steel town |
| **Ex-Con** | +Fighting, crowd Hype bonus from fights | Prison League graduate |
| **Street Kid** | +Agility & dekes | Pond and street leagues |
| **Washed-Out Prospect** | +Hands & Hockey IQ, −Toughness | Cut from the "real" leagues |
| **Ex-Military** | +Discipline, faster injury recovery | Came home with nothing |
| **Farm Kid** | +Strength & Balance | Hauled hay, hits like it |
| **Dock Rat** | +Item pickup speed, trap effectiveness | Bayonne waterfront |
| **Miner** | Better vision in dark arenas | Underground since 16 |

Origin also changes **Career dialogue lines** (Tasha's interview questions reference it).

---

## 4. Position & Archetypes

### Skaters
| Archetype | Strengths | Weaknesses |
|---|---|---|
| **Sniper** | Shot power & accuracy | Toughness, checking |
| **Playmaker** | Passing, vision, puck control | Fighting |
| **Two-Way** | Balanced | No elite skill |
| **Enforcer** | Fighting, checking, toughness | Hands, speed |
| **Power Forward** | Strength + shooting | Agility |
| **Speedster** | Top speed, acceleration | Strength, balance |
| **Goon** | Max fighting & intimidation, Hype gain | Hockey skills (very low) |
| **Defensive D** | Positioning, shot blocking, hits | Offense |
| **Offensive D** | Point shots, passing | Defensive positioning |

### Goalies
| Style | Strengths | Weaknesses |
|---|---|---|
| **Butterfly** | Low shots, rebound control | High glove/blocker |
| **Hybrid** | Balanced | — |
| **Stand-Up** | High shots, positioning | Low shots, recovery |
| **Aggressive** | Challenges shooters, poke checks, crease fighting | Leaves net open, rebounds |
| **Brawler Goalie** | Crease Toughness, goalie fights, Hype | Reflexes |

---

## 5. Body

| Setting | Options |
|---|---|
| Height | 5'6" – 6'8" (affects reach, size, balance) |
| Weight class | **Light** (speed, agility) · **Middle** (balanced) · **Heavy** (momentum damage, toughness, slower turns) |
| Build | Lean / Athletic / Stocky / Heavy / Huge — fine sliders for shoulders, arms, torso, legs |
| Posture | Upright / Hunched / Aggressive lean (animation set offset) |

- Height and weight class apply small **automatic stat modifiers** (shown live in a side panel).

---

## 6. Face
- **Preset heads** (a library of MetaHuman-based faces) as starting points, then **sliders**: head shape, jaw, cheekbones, brow, nose (incl. broken/crooked), eyes, ears, lips, chin, neck.
- **Skin:** tone, age, weathering, freckles, pores/roughness.
- **Hair:** styles (buzz, mullet, slick back, long, braids, bald, shaved sides, mohawk…), color, gray amount.
- **Facial hair:** beard/mustache styles, length, color; "playoff beard" growth option in Career.
- **Eyes:** color, bloodshot, black eye (left/right).

---

## 7. Marks (the RHL look)
| Category | Options |
|---|---|
| Scars | Library of scars (face, neck, hands, arms) — place, rotate, scale, depth |
| Tattoos | Library + text tattoos (knuckles, neck, forearms); color or faded ink |
| Teeth | Full / chipped / missing (choose which) / gold tooth / mouthguard color |
| Injuries (cosmetic) | Broken nose, cauliflower ear, missing ear, stitches, bandages, burn marks |
| Grime | Sweat, blood, ice, soot amount (match-time overrides) |

- **Career/Franchise:** new scars and missing teeth get **added automatically** from injuries (persistent damage). You can view the "injury history" on the body.

---

## 8. Gear

### Skater
- **Helmet:** classic, modern, old-school no-visor, **no helmet** (more Hype, more risk).
- **Face:** none, half visor, tinted visor, cage, full shield.
- **Gloves, elbow/shin/shoulder pads, pants, skates, socks:** styles, colors, wear level, tape.
- **Stick:** wood / composite / old aluminum look, blade curve, tape color & pattern, knob style.
- **Extras:** mouthguard, neck guard, wristbands, eye black, chains/rosary/dog tags (cosmetic).

### Goalie
- **Mask:** fiberglass / modern / cage / welding-style / bare-faced (crazy) → **Mask Editor** (layers, decals, team logo, skulls, flames, teeth, blood).
- **Pads, glove, blocker, chest protector, pants:** styles, colors, patterns, wear, tape, spikes (cosmetic).
- **Goalie stick:** paddle style, tape, knob.

### Gear rules
- Gear is **mostly cosmetic**; a few pieces have small trade-offs (no helmet = Hype bonus + concussion risk; heavy pads = protection − agility).
- Jersey/socks/pants colors come from the **team**, not the player.

---

## 9. Ratings — Point-Buy

| Mode | How ratings work |
|---|---|
| **Exhibition / Franchise** | **Point-buy:** archetype sets a base; spend a pool of points; caps per attribute (no 99s everywhere). Optional **Sandbox** toggle = free sliders (any values) |
| **Career** | Start as a low-rated rookie (archetype + origin shape the base). Grow through play (see §12) |

### Attributes
- **Skaters:** Speed, Acceleration, Agility, Balance, Stamina · Shot Power, Shot Accuracy, Passing, Puck Control, Dekes, Hockey IQ · Checking, Toughness, Fighting, Discipline
- **Goalies:** Reflexes, Positioning, Rebound Control, Glove, Blocker, Low Shots, Recovery, Puck Handling, Crease Toughness, Stamina

- Live **Overall rating** + a radar chart vs. league average and vs. a chosen star ("You vs Kowalski").

---

## 10. Fighting
- **Fight style:** Brawler / Boxer / Grappler (goalies: Crease Brawler / Mask Off).
- **Stance & animation set** preview.
- **Finisher:** pick from unlocked finishers (generic set at start; more from Challenges/Career).

---

## 11. Traits
Pick **2 strengths**. (No flaw-for-points system — decision.)

| Strengths |
|---|
| Clutch, Iron Jaw, Sniper's Eye, Hype Machine, Bodyguard, Puck Hound, Grinder, Quick Hands, Rink Rat (hazard-savvy), Fan Favorite |

Goalie traits: Brick Wall, Hot Hand (Hot Streak easier), Rebound King, Crease King.

> Negative traits (Glass Jaw, Short Fuse, Rattled, etc.) may still exist on **generated/star players** in Franchise for personality, but custom players don't pick them.

---

## 12. Presentation
- **Voice type:** pick from the generic voice sets (grunts, effort, trash-talk lines).
- **Walkout:** library (stick tap, glove punch, skate lap, pray, stare at camera, etc.).
- **Celebrations:** pick 3 (goal), 1 (kill), 1 (fight win), goalie: 2 (big save) + 1 (win).
- **Taunt:** pick 2.
- **Goal song / walkout music:** from library or **custom music folder**.

---

## 13. Combine Results & Saving
- **Broadcast scouting report:** Knuckles reads a short scouting blurb generated from your choices ("Big body, hands like bricks, and he'll drop the gloves with anyone.").
- **Draft card** image (stats, photo) — saved as a shareable image.
- **Save options:** add to **Free Agents**, to a specific team, to a Franchise **draft class**, or keep in the **Custom Player library**.
- **Export / import** as a file.
- Limits: plenty of slots (e.g. 100 custom players).

---

## 14. Progression (Career & Franchise)
- **Ratings XP** from played games (goals, saves, hits, fights, Hype, Challenges).
- Spend XP on attributes (costs rise as ratings rise).
- **Milestone perks:** unlock new finishers, celebrations, walkouts, gear.
- **Aging:** peak ~26–31, decline after; injuries can permanently lower stats.
- **Look changes over a career:** scars, gray hair, beard growth, missing teeth.

---

## 15. Tech Notes
- One **Player Definition** data structure for stars, generic, and custom players (identity, appearance params, gear IDs, ratings, traits, presentation).
- **Modular character system:** shared skeleton, face/body morph targets, swappable meshes, material layers (skin, scars, tattoos, grime, blood).
- **Preview stage:** small 3D booth with lighting presets (studio, The Plant, The Shaft dark, Kold Kut whiteout), camera presets (full body, face, gear close-up), right-stick orbit/zoom.
- **Controller-first sliders:** coarse/fine adjustment, symmetry toggle, reset per slider.
- **TTS name generation** runs at save via local ComfyUI/TTS; cached audio files per player.
- Saved as SaveGame + exportable JSON.

---

## 16. Build Order
1. Player Definition + modular character base (needed for stars too)
2. Identity, Position/Archetype, Body, basic Gear, Ratings (point-buy)
3. Face presets + sliders, hair, facial hair
4. Marks (scars, tattoos, teeth)
5. Goalie gear + Mask Editor
6. Fighting, Traits, Presentation
7. Combine Results broadcast + draft card + TTS name calls
8. Progression (Career/Franchise)
9. Edit Player (reuses everything)

---

## Decisions (Oct 2026)
- Ratings: **point-buy by default**, optional **Sandbox** toggle.
- **No flaws-for-points.** Custom players pick 2 strengths only.
- Career: **one player per save** (skater *or* goalie).
