# RHL — Difficulty & Gameplay Sliders

Owner request: **settings sliders for User and AI** (speed, strength, etc.), like sim hockey games — tune the game exactly how you like it.

---

## 1. How It Works

- Two columns of sliders: **User** (human-controlled players) and **AI** (CPU-controlled players).
- Range: **0–100**, default **50** (= normal). Changes show a live preview description ("AI skaters are 20% faster").
- **Presets:** Rookie, Pro, All-Star, Prime Time (hardest), plus **custom presets** you save and name.
- Available in **Settings** and in the **pre-game Exhibition setup**.
- **Per-player sliders (couch):** each human player can optionally have their own User slider set (e.g. son on hard settings, owner on easier).
- **Career / Franchise:** sliders allowed; chosen preset is shown on the save file. Changing mid-season is allowed.
- **Reset to Default** button on every page.

---

## 2. Slider List (User & AI each)

### Skating
| Slider | Effect |
|---|---|
| Top Speed | Max skating speed |
| Acceleration | How fast you reach top speed |
| Agility | Turning, carving, edge work |
| Stamina | Drain rate of sprinting / fighting |
| Balance | Resistance to being knocked down |

### Offense
| Slider | Effect |
|---|---|
| Shot Power | Speed of shots |
| Shot Accuracy | How close shots go to the aimed spot |
| Pass Speed | Speed of passes |
| Pass Accuracy | Error on passes |
| Puck Control | Stickhandling; chance of losing the puck on contact |
| Deke Effectiveness | How well dekes beat defenders/goalies |

### Physical & Combat
| Slider | Effect |
|---|---|
| Hit Power (Strength) | Body check force and damage |
| Toughness / Health | Damage taken from hits, pucks, weapons |
| Fight Power | Punch damage |
| Fight Skill | Block/parry/dodge timing windows (AI: how often it reads your punches) |
| Weapon Damage | Item/weapon damage multiplier |
| Injury Frequency | Chance of injuries (broken arm, concussion, etc.) |

### Goalie
| Slider | Effect |
|---|---|
| Goalie Reflexes | Save reaction speed / timing window size |
| Goalie Positioning | How well goalie cuts angles (AI) / assist strength (User) |
| Rebound Control | Size of loose rebounds |
| Goalie Toughness | Damage resistance in the crease |

### AI Behavior (AI column only)
| Slider | Effect |
|---|---|
| Aggression | How often AI hits and targets players |
| Fight Frequency | How often AI drops the gloves |
| Item Usage | How smart and how often AI uses items |
| Positioning / Hockey IQ | Defensive structure, passing lanes, offensive support |
| Goalie Targeting | How often AI goes after your goalie |

---

## 3. Game-Wide Sliders

| Slider | Effect |
|---|---|
| Game Speed | Overall pace |
| Puck Speed | Speed of puck movement |
| Item Frequency | Off → Chaos |
| Hazard Intensity | Off → Maximum |
| Crowd Hype Gain | How fast Hype builds |
| Penalty Frequency | How often refs call penalties |
| Catch-Up Logic | Off → Strong (better drops for trailing team) |
| Period Length | Minutes per period |

---

## 4. Tech Notes
- Each slider maps to a multiplier on a base stat (Data Tables) — gameplay code reads final values from one **Difficulty Subsystem**, so tuning never needs code changes.
- Presets stored as Data Assets; custom presets saved via SaveGame.
- User/AI split applied per controller: human-possessed pawns use User (or that player's per-player set), AI-possessed pawns use AI values. Switching players re-applies instantly.
