# RHL — Franchise Mode: "Ownership" (Brainstorm v0.1)

You own an RHL team. Build a roster, keep players alive (or don't), keep the network happy, and win the **Meridian Cup**.
Play every game, sim them, or mix — and you can play any position, including **goalie only**.

---

## 1. Setup

| Option | Choices |
|---|---|
| Team | Any of the 8 RHL teams **or** a custom expansion team (from the Creation Suite) |
| League size | 8 teams (default) · 10 or 12 with custom/expansion teams |
| Season length | 14 / **28 (default)** / 56 games |
| Playoffs | Top 4 (default) or top 6; best-of-3 / best-of-5 / best-of-7 |
| Permadeath | Off · **Stars Only** · **Full (default)** |
| Finances | **Simple (default)** — Standard/Hardcore are optional later additions |
| Network Pressure | Off · Normal · Brutal (how much Meridian interferes) |
| Difficulty | Uses `DIFFICULTY_SLIDERS.md` presets/sliders |
| Co-op | 1 or **2 owners** (owner + son co-manage the same team) |

---

## 2. Season Flow

```
Preseason → Regular Season → Trade Deadline → Playoffs → Meridian Cup Final → Offseason
Offseason: Awards & Memorial → Retirements → Contracts → Draft → Free Agency → Training Camp
```

- Each game: **Play** (any position, or goalie only) or **Sim** (instant result with box score + highlights).
- Between games: news ticker, injury reports, events, trade offers, sponsor messages — all broadcast-styled.
- **Year in Blood** recap at season end (auto highlights from played games).

---

## 3. Roster

- **Roster:** 12 skaters + 2 goalies (3v3 or 5v5 lines auto-built; editable).
- **Lines:** set lines, power play, penalty kill, enforcer line.
- **Backup goalie matters:** if your starter dies or is injured, the backup plays.
- **Player attributes** (1–99): Skating, Shooting, Passing, Puck Control, Checking, Toughness, Fighting, Hockey IQ, Stamina, Discipline; goalies: Reflexes, Positioning, Rebound Control, Crease Toughness.
- **Traits** (personality): Enforcer, Showboat, Loyal, Greedy, Reckless, Clutch, Fan Favorite, Injury Prone, Network Darling, Hates the Network.
- **Morale:** affected by ice time, contract, teammates dying, winning, how you treat them.
- **Aging & progression:** players improve with ice time and training, decline after ~30; injuries can permanently lower stats.
- **Persistent bodies:** scars, missing teeth, injuries show on the player model (same system as Career).

---

## 4. Contracts & Death Waivers

Every RHL contract includes a **death waiver**.

| Term | What it means |
|---|---|
| Salary | Per season |
| Length | 1–5 seasons |
| Death payout | Amount paid to the family if the player dies (you pay it) |
| Medical clause | Guaranteed medical level (affects injury recovery) |
| No-trade clause | Stars may demand it |
| Network bonus | Bonus paid if the player hits ratings targets |

- **Low death payout** = cheaper contract, but players with families refuse, and morale drops when teammates die.
- Holdouts, contract demands, and players asking for a trade after a teammate dies.

---

## 5. Finances

| Revenue | Expenses |
|---|---|
| Ticket sales (price vs. riot risk) | Player salaries |
| **Network share** (based on your ratings) | **Death payouts** |
| Sponsors (VoltRush, PainAway, etc.) | Medical staff & facilities |
| Merch (star players sell more) | Arena upgrades & maintenance |
| Playoff revenue | Security (fewer riots), scouting, travel |

- **Ticket pricing vs. riots:** high prices + losing = angry fans → riots damage the arena and cost money.
### Simple Finances (DEFAULT — decision)
Keep money light so Franchise is about hockey, roster, and survival:
- **One team budget** per season (set by last season's ratings + wins + playoff run).
- **Salary cap**: player salaries must fit under it.
- **Death payouts** come out of the budget (so deaths still sting).
- **Upgrades & staff** are bought from the budget with simple prices.
- **No** ticket pricing, merch, travel, debt, or bankruptcy. Riots become a simple random event after bad losses.
- The full table above is kept only as reference for optional Standard/Hardcore modes later (not planned for launch).

---

## 6. The Network (Meridian) Relationship

- **Ratings** come from brutal, exciting games, star power, rivalries, and playoff runs.
- Meridian sends **demands**: "Play Kowalski more," "We want a fight with Gary on Friday," "Lose this one — the High Rollers need the win."
- **Comply:** money, better refs, better item odds (subtle).
- **Refuse:** fines, bad refs, worse Director odds, your games moved to bad time slots (lower revenue).
- **Network Review:** if ratings are terrible for a whole season, Meridian threatens to **revoke your franchise** (story pressure + budget cut; no game over in Simple finances).
- Network Pressure setting controls how often this happens.

---

## 7. Draft & Scouting (Feeder Leagues)

Players come from the RHL's grim talent pipeline:

| Feeder league | Typical prospects |
|---|---|
| **Prison League** | Tough, fearless fighters, low discipline (Wardens get bonus access) |
| **Mill & Factory Leagues** | Strong, durable, decent skills |
| **Street / Pond Leagues** | Fast, creative, fragile |
| **Juniors (sanctioned)** | Balanced, high potential, expensive |
| **Washouts** | Ex-pros cut from other leagues — skilled, older, injury history |
| **Overseas** | Random gems, scouting needed |

- **Scouting fog:** prospect ratings are ranges until scouted (scouting budget + scouts' skill).
- **Draft:** 3 rounds, lottery for worst teams.
- **Free agency:** offseason bidding vs. AI teams; mid-season free agents fill holes after deaths.

---

## 8. Trades & AI General Managers

- AI GMs have personalities: **Shark** (fleeces you), **Loyal** (won't trade stars), **Desperate** (overpays when losing), **Network Puppet** (Vegas — trades favored by Meridian).
- Trade value considers age, contract, stats, injuries, traits.
- Trade deadline mid-season; AI teams make trades with each other too.

---

## 9. Staff

| Staff | Effect |
|---|---|
| Head Coach | Tactics, player development, team style |
| Enforcer Coach | Fighting & checking development |
| Goalie Coach | Goalie development (great for son's goalie) |
| Team Medic | Injury recovery speed, **chance to save a dying player** |
| Trainer | Stamina, aging slowdown |
| Scout | Scouting accuracy |
| Equipment Manager | Gear durability, small item-related perks |

---

## 10. Arena Upgrades

- **Capacity** (more tickets), **Security** (fewer riots), **Medical Bay** (better survival odds), **Training Rink** (development).
- **Hazards:** install/upgrade your arena's hazards (more Hype and ratings, but they hurt your players too).
- **Item delivery** style and **sponsor boards**.
- **Presentation:** jumbotron, goal horn, music, ice logos.

---

## 11. Events Between Games (random, broadcast-styled)

- Player arrested / suspended · Sponsor scandal · Rival owner insults · Holdout · Player's family asks for money
- Fan riot after a loss · Network demand · Star wants a trade · Rookie becomes a fan favorite
- Choices with consequences (money, morale, ratings, network favor).

---

## 12. Legacy

- **Memorial Wall:** every player who died on your team — name, number, stats, how they died. Shown in the arena.
- **Retired numbers** and **Hall of Fame**.
- **Records:** franchise and league records (goals, saves, kills, shutouts, fights).
- **Dynasty tracking:** Meridian Cups, seasons owned, legendary players.

---

## 13. Playing Games in Franchise
- Play as **any skater**, **goalie only** (son), or **coach mode** (switch players like Exhibition).
- Couch co-op: owner skater + son goalie on your franchise team.
- Played games give more ratings and better player development than simmed games (reward for playing).

---

## 13b. Co-op Franchise (DECISION: yes)
- **Two owners on one save** (owner + son), on the same couch.
- **Shared control:** either player can manage lines, sim/play games, and handle events.
- **Big decisions need both** (optional, on by default): trades, contracts over a set amount, releasing players, draft picks in round 1.
  Both players confirm with their own controller — a "co-sign" screen.
- **Roles (optional):** e.g. son = **Goalie Coach & Starting Goalie** (goalie decisions are his), owner = **GM** (contracts & trades).
- **Game nights:** son in net, owner as skater, AI fills the rest — the default couch setup for played games.
- Each player keeps their own controls, assists, and User sliders.

---

## 14. Sim Engine (tech)
- Stat-based game simulation: uses player attributes, lines, tactics, injuries, team style, Hype, and random events (fights, deaths, injuries).
- Produces box scores, play-by-play text, and highlight "headlines."
- Tune with headless AI-vs-AI sims so simmed results match played-game stats (goals, injuries, deaths per game).
- Save: one Franchise save file per franchise (SaveGame), autosave after every game.

---

## 15. Build Order
1. League structure, schedule, standings, sim engine (simple)
2. Roster, lines, attributes, injuries, permadeath
3. Contracts + death waivers + **Simple finances** (budget, cap, death payouts)
4. Draft + free agency + trades (basic AI GMs)
5. Network relationship + events
6. Staff + arena upgrades
7. Legacy (memorial wall, records)
8. AI GM personalities, scouting fog
9. **Co-op franchise** (two owners)
10. (Optional, later) Standard/Hardcore finances

---

## Decisions (Oct 2026)
- Default season length: **28 games**.
- **Co-op franchise: yes** (two owners, co-sign big decisions, optional roles).
- Finances: **Simple** (budget, salary cap, death payouts). Standard/Hardcore not planned for launch.
