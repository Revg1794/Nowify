# RHL — AI Design (Brainstorm v0.1)

The AI has to play **real hockey** *and* **fight dirty** — as teammates and as opponents — while staying fair and tunable.
Most games will be **owner + son vs AI**, often with the son in net, so AI teammates matter as much as AI opponents.

---

## 1. AI Pillars
1. **Hockey first.** AI skates in real formations, passes smartly, takes good shots, backchecks.
2. **Brutal with a brain.** AI hits, fights, and uses items *when it makes sense*, not randomly.
3. **Fair.** No cheating: AI has human-like reaction times, can miss, respects telegraphs, can't see in the dark.
4. **Personality.** Teams and star players play differently — you can feel the Ironworkers vs the Drowned.
5. **Great teammates.** AI teammates support human players and **protect the goalie**.
6. **Tunable.** Difficulty comes from sliders (reaction time, accuracy, decision quality), not rubber-banding.

---

## 2. Architecture (3 layers)

### Layer 1 — Team Brain (one per team)
- Reads the game state: puck possession, zone, score, clock, Hype, injuries, penalties, items on ice.
- Picks the **team tactic**: Breakout, Attack, Cycle, Forecheck, Defend, Collapse (protect crease), Hunt (target a player), Item Rush.
- Assigns **roles** to each skater every ~0.5 s: Puck Carrier, Support, Net-Front, Point, Forechecker, Backchecker, Enforcer, Item Chaser.
- Handles **line changes** (stamina, injuries) and **goalie pull** (late in game when trailing).

### Layer 2 — Player Brain (one per AI skater)
- Executes its role using **utility scoring**: every possible action gets a score, the best one (with a little randomness) wins.
- Example actions and what raises their score:
  | Action | Score goes up when… |
  |---|---|
  | Shoot | Good angle, open lane, goalie out of position, close to net |
  | Pass | Teammate open, better shooting chance than self, under pressure |
  | Deke / skate | Space ahead, defender committed |
  | Body check | Target has puck, high speed available, target near boards/hazard |
  | Drop gloves | Rival nearby, teammate was hurt, high Aggression, Hype low (wants to raise it) |
  | Use item | Item fits situation (puck mod when shooting, chain when defender nearby) |
  | Grab item | Item close, not leaving a dangerous gap, puck far away |
  | Protect goalie | Opponent crashing the crease, own goalie hurt |
  | Avoid hazard | Telegraph active nearby |

### Layer 3 — Motor Control
- Converts decisions into stick inputs like a human: steering, sprinting, stick aim.
- **Reaction delay + aim error** come from difficulty sliders, so the AI "plays the same game" you do.

### UE5 Tech
- **StateTree** (or Behavior Trees) for role states, **Utility scoring** for action choice.
- **EQS (Environment Query System)** for finding open ice, passing lanes, shooting spots, safe item paths.
- **Influence map** of the rink (who controls which ice) updated a few times per second.
- **Perception:** sight cones, hearing (telegraph sounds), and **light-aware vision** (dark arenas/Blackout/headlamps-off actually hide you).

---

## 3. Hockey Behavior

| Situation | AI behavior |
|---|---|
| **Breakout** | D retrieves puck, wingers go to boards, center swings low for a pass |
| **Offensive zone** | Cycle down low, point shots with net-front screen, look for one-timers and rebounds |
| **Forecheck** | 1-2-2 (safe) or 2-1-2 (aggressive) depending on team style & score |
| **Defensive zone** | Man/zone hybrid, block shots, clear crease, collapse when goalie is hurt |
| **Neutral zone** | Trap (defensive teams) or stretch passes (fast teams) |
| **Power play / penalty kill** | Box formation on PK, umbrella on PP |
| **Shot selection** | Weighs angle, distance, traffic, goalie position, shot type (one-timer > wrist > slapshot from far) |
| **Line changes** | Changes on the fly when tired; avoids changing when the puck is in its own zone |

---

## 4. Combat Behavior

- **Target selection:** prefers puck carriers, injured players, rivals, and players near boards/hazards.
- **Hits:** builds speed before charging; times hits at the boards; avoids hits that leave its net open.
- **Fights:** AI fighters have styles (Brawler / Boxer / Grappler) and **read telegraphs** based on Fight Skill slider —
  low skill = rarely blocks; high skill = parries and counters.
- **Items:** knows each item's best use (stored in the item's data):
  | Item type | AI uses it… |
  |---|---|
  | Puck mods | When it has a shooting chance |
  | Stick mods | Near an opponent with the puck or a rival |
  | Thrown | At players in a straight line / slowed / fighting |
  | Deployables | In passing lanes or in front of its own crease when defending |
  | Power-ups | Before a rush (adrenaline), when hurt (painkillers), before a fight (taped knuckles) |
- **Hazard awareness:** reacts to telegraphs with a delay (difficulty-based); smart AI baits you into hazards.
- **Crowd awareness:** when Hype is low, enforcers pick fights to fire up the crowd; at Max Hype, AI goes for finishers.
- **Revenge:** if an AI's goalie or star is hit, teammates target the attacker for a while.

---

## 5. Goalie AI (opponent goalie + AI backup when son isn't in net)
- Positions using angle and depth; shuffles/T-pushes with the puck.
- **Save reaction** = reaction time + read of the shooter's wind-up + error, all from Goalie sliders.
- Perfect-save chance scales with difficulty; screens and deflections reduce it (fair: AI can be screened).
- Plays the puck behind the net, freezes it under pressure, uses goalie items, fights crease crashers.
- Will **leave the net to fight** rarely (personality-based — e.g. Gator Fontenot does it often).

---

## 6. AI Teammates (playing WITH owner + son)

### Supporting the Human Skater (owner)
- Gets open for passes, calls for the puck, screens the goalie, retrieves rebounds.
- Follows **D-pad strategy** (Aggressive / Defensive) and **target lock** (focus one opponent).
- Doesn't steal the spotlight: on lower assist settings, AI teammates feed the human more.

### Protecting the Human Goalie (son) — "Bodyguard" logic
- **Crease defense:** at least one AI defender guards the crease when opponents crash the net.
- **Clear the crease:** AI hits/pushes players who screen or hit the goalie.
- **Revenge:** anyone who hits your goalie gets hunted (feeds the Revenge buff).
- **Rebound cleanup:** AI teammates clear rebounds away from the crease.
- **Bodyguard intensity** setting: Low / Normal / High.

### Line Calls
- Human can call a line change; AI handles the rest automatically.

---

## 7. Team & Star Personalities

Each team has a **style profile** (data asset) that shifts AI scoring weights.

| Team | AI style |
|---|---|
| Detroit Ironworkers | Heavy forecheck, lots of big hits, slow but punishing |
| Gary Slagdogs | Dirty: slashes, burns, targets injured players, item-heavy |
| Winnipeg Wardens | Reckless: fights constantly, poor defense, high Hype |
| Las Vegas High Rollers | Skill: passing plays, dekes, avoids fights, refs favor them |
| New Orleans Drowned | Speed: stretch passes, rushes, uses thin ice |
| Anchorage Butchers | Physical defense, hooks, grinds along the boards |
| Bayonne Dockrats | Opportunistic: traps, deployables, counterattacks |
| Sudbury Deep | Disciplined trap defense, patient, uses darkness |
| Meridian All-Stars | Does everything well; adapts to how you play |

**Star players** add signature tendencies (Kowalski pins players on the boards; Ace dekes and dives; Malachi goes for finishers).

### Adaptive AI (Meridian All-Stars / high difficulty)
- Tracks your habits during a game (always shooting glove side, always deking left, always fighting) and adjusts.

---

## 8. Goalie Targeting (important for the son)
- Slider: **Goalie Targeting** (AI column) controls how often AI crashes the crease, hits, or attacks the human goalie.
- Default: **Normal** — AI tests the goalie, but doesn't make the game "attack the goalie simulator."
- **Cooldown:** after attacking the goalie, the AI backs off for a while (unless in Revenge mode or Career story moments).
- Goalie items (crease traps, salt, nail board) make the AI more cautious about crashing the net.

---

## 9. Difficulty (ties to `DIFFICULTY_SLIDERS.md`)

| Preset | Reaction time | Decision quality | Fight skill | Goalie | Notes |
|---|---|---|---|---|---|
| Rookie | Slow (~400 ms) | Simple choices, mistakes | Rarely blocks | Beatable | Good for learning |
| Pro | ~250 ms | Solid | Some blocks | Solid | Normal |
| All-Star | ~180 ms | Smart passes, uses hazards | Parries often | Strong | Challenging |
| Prime Time | ~130 ms | Adaptive, exploits weaknesses | Counters | Elite | For the son |

- **No rubber-banding** (AI doesn't get faster when losing). Comebacks come from the item catch-up logic only.
- Individual sliders override presets (Aggression, Fight Frequency, Item Usage, Hockey IQ, Goalie Targeting).

---

## 10. Refs (AI)
- Simple ref AI calls penalties based on Penalty Frequency slider and what it can "see" (refs miss things in dark arenas/fights at a distance).
- Calls: tripping, slashing, weapon use (only certain items), too many fights, goalie interference (lol, rarely).
- **Biased refs:** The Jackpot (favor High Rollers) and **subtle Career rigging** (Act 3).

---

## 11. Debug & Testing
- On-screen AI debug: each AI's role, top 3 action scores, target, perception.
- Influence map overlay.
- **Headless AI-vs-AI sims** (shared with Spawn Director sims): shot totals, goals, hits, fights, items used — check that games look like hockey.
- Replay system review: watch AI-vs-AI games in Broadcast mode to spot dumb behavior.

---

## 12. Build Order
1. Vertical slice: basic skater AI — chase puck, pass, shoot, simple positioning; basic goalie AI.
2. Team Brain + roles + formations (breakout, offensive zone, defensive zone).
3. Body checks + targeting.
4. Fight AI (styles, telegraph reading).
5. Item usage + hazard awareness (with item system milestone).
6. Teammate support + Bodyguard logic.
7. Team/star personalities.
8. Difficulty presets + sliders.
8b. **Trash talk barks** (Level 1, see §13).
9. Refs.
10. Adaptive AI (All-Stars / Prime Time).

---

## 13. AI Trash Talk — Level 1 (Context Barks)

Short voice lines AI players say when something happens. Added **after core AI works** (not in the vertical slice).

### Triggers
| Event | Example |
|---|---|
| Big hit landed / taken | "Stay down!" / "That all you got?" |
| Goal scored / allowed | "Too easy." / "Wake up, goalie!" |
| Fight starts / won / lost | "Let's go!" / "Who's next?" |
| Item picked up / used | "Oh, you're done now." |
| Goalie lines | "SIEVE!" after a goal · "Can't see it, can you?" when screening · "Lucky save." |
| Save made (AI goalie) | "Not tonight." |
| Low Hype / boring play | "Crowd's falling asleep!" |
| Rival nearby | Star-specific taunts |

### System
- Uses the **same event system as the announcers**: game event → pick a line → play it.
- **Cooldowns** per player and globally; never repeats the same line back-to-back.
- **Ducks under announcers** (announcer lines always win).
- Positional audio from the speaking player; subtitles if enabled.
- Rookie mercy setting also tones down the meanest lines.
- Setting: **Trash Talk: Off / Low / Normal** (Audio settings).

### Line Budget (~500–700 lines, generated with local TTS)
| Speaker | Lines |
|---|---|
| Each star skater (9) | 20–40 unique lines (Kowalski barely talks; Ace never shuts up) |
| Each star goalie (9) | 15–25 unique lines |
| Generic voice types (4) | ~50 lines each |

### Build Step
Added after step 8 (Difficulty presets) in the AI build order: **8b. Trash talk barks.**

## Decisions (Oct 2026)
- Bodyguard default: **Normal** (Low / High still selectable).
- **Rookie mercy: yes** — on Rookie, AI won't finish off or deliberately kill badly injured players (it still hits and fights).
- **AI trash talk: Level 1 (context barks)** — approved. See §13.
- Level 2 (personalized/memory-based trash talk) — not planned; maybe later for Career only.
