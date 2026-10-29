# RHL — Goalie Design (Brainstorm v0.1)

The son loves playing goalie, so **goalie is a first-class role**, not an afterthought.
Goal: playing goalie should be as fun, deep, and brutal as playing a skater.

---

## 1. Goalie Pillars
1. **The crease is your kingdom.** Inside it you're a fortress; step out and you're a brawler.
2. **Saves feel like combat.** Reading and timing a save should feel like a perfect block in a fight.
3. **High stakes.** If the goalie dies, the net is empty until the backup gets there.
4. **Personality.** Painted masks, custom pads, named star goalies, signature moves.

---

## 2. Saving

### Save Controls (built on CONTROLS_AND_FEEL.md goalie layout)
- **Left stick:** position / shuffle / T-push across the crease.
- **Right stick:** directional save (glove high, blocker high, pads low, butterfly, stack pads, poke).
- **Pro scheme:** manual save selection like sim hockey games; **Arcade scheme:** assisted positioning, you just time the save.

### Save Mechanics
- **Read the shooter:** shooters have a readable wind-up (like fight telegraphs). Slapshots wind up longer; wrist shots are quicker and harder to read.
- **Perfect Save (timing window):** press save right as the puck arrives → clean catch/rebound control, Hype bonus, and the shooter is briefly stunned ("frozen in shame").
- **Good Save:** stopped, but rebound goes loose.
- **Late/Wrong Save:** goal, or puck hits you (damage — heavy pucks hurt).
- **Desperation save:** dive across the crease (stick extended, or headfirst) — costs stamina, leaves you down.
- **Rebound control:** catch & freeze, direct rebound to corner, or cover.
- **Screens & deflections:** players in front block your view — your view actually gets obstructed in the behind-the-goalie cam.

### Positioning
- Angle cutting: positioning ring on the ice shows ideal depth/angle (assist level controls whether it's shown).
- Hug post, reverse-VH on wraparounds, challenge shooter (come out of crease — bigger angle cover, but exposed).

---

## 3. Goalie Combat

- **Crease Authority:** inside the crease, the goalie takes reduced damage and can't be knocked down by normal checks.
- **Crease defense moves:**
  - **Blocker punch** — shove/punch players screening you
  - **Stick slash** — two-hand slash at ankles of crease crashers
  - **Glove grab** — grab a jersey and pull them down
  - **Pad stack crush** — slide pads into a player's legs to trip them
- **Leaving the crease:** goalie can skate out to fight. **Goalie fights** are rare and huge — big Hype bonus, the crowd goes nuts. But while you're out, your net is empty.
- **Goalie vs goalie fight:** both goalies skate to center ice — maximum Hype event.
- **Goalie gear damage:** pads, mask, and blocker show damage; enough damage = gear breaks (cracked mask = bleeding/vision blur, torn pad = weaker saves on that side).
- **Revenge system:** if your goalie gets hit, your skaters get a **Revenge** buff (faster Hype, harder hits) for 20 s. Protect your goalie!

### If the Goalie Dies
- Net is **empty** while the **backup goalie** skates from the bench (~10 s).
- Backup goalie is weaker (lower stats) unless upgraded in Franchise.
- In Career/Franchise permadeath, a dead starting goalie is a season-defining event.

---

## 4. Goalie Hype & Signature Moves

- **Hot Streak:** consecutive saves build a streak meter. At 5+ saves in a row: brief **reflex focus** (time slows slightly when a shot is released).
- **Goalie finisher — "Mask Off":** at max Hype, slam a downed opponent in the crease with the blocker/stick.
- **Goalie goal:** shoot the puck the length of the ice into an empty net → biggest Hype in the game + announcer meltdown.
- **Shutouts** and **saves while injured** earn bonus ratings in Career.

---

## 5. Goalie Items (expanded set)

| Item | Effect |
|---|---|
| Spiked blocker | Shots shatter on it; touching it causes bleeding |
| Weighted leg pads | Can't be knocked down |
| Crease traps | Chains/spikes around the crease |
| Goalie stick hook | Drag skaters into the post |
| Iron mask | Survive one headshot puck |
| Blood in the crease | Heal by blocking shots |
| **Tar-coated glove** | Catches stick — no rebounds for 30 s |
| **Crease salt** | Scatter salt — crashers slow down and slip |
| **Steel-toe skates** | Kicks out of the butterfly hurt |
| **Weighted goalie stick** | Slash and poke checks deal heavy damage |
| **Taped-up pads** | Restores broken gear mid-game |
| **Nail board** | Lay in the crease — anyone crossing it bleeds |

---

## 6. Star Goalies (one per team)

| Team | Goalie | Style | Signature |
|---|---|---|---|
| Detroit Ironworkers | **"Big Stan" Wozniak** | Huge, blocks everything, slow | **Wall of Steel** — pads lock, almost nothing gets past low for 10 s |
| Gary Slagdogs | **Cass "Ashtray" Molloy** | Dirty, chops ankles, smokes between periods | **Hot Seat** — crease boards glow red, burning crashers |
| Winnipeg Wardens | **Inmate #0013 "The Gatekeeper"** | Silent, chained to the posts (literally can't leave the crease, but huge crease authority) | **Chain Whip** — swings the chain across the crease |
| Las Vegas High Rollers | **Remy "Lucky" LaRue** | Flashy, showboat glove saves, gets lucky bounces | **Snake Eyes** — next 3 shots ring off the post |
| New Orleans Drowned | **Odette "Gator" Fontenot** | Acrobatic, aggressive, plays far out of the net | **Death Roll** — grabs a skater and spins them to the ice |
| Anchorage Butchers | **Bjorn "The Freezer" Strand** | Cold, emotionless, butterfly specialist | **Cold Storage** — freezes the puck and the shooter |
| Bayonne Dockrats | **Tommy "Sieve" Russo** | Washed-up, funny, actually bad (Career underdog goalie) | **Lucky Break** — random miracle save |
| Sudbury Deep | **Elias "Canary" Lund** | Star of the league, headlamp mask, silent | **Cave-In** — collapses crease ceiling on attackers |
| Meridian All-Stars | **Unit 1 "The Firewall"** | Network-built goalie, flawless, emotionless | **Blackout** — arena dims, only the puck glows for him |

---

## 7. Goalie Customization (Creation Suite)

- **Mask painting editor** — the signature goalie feature. Layers, decals, team logos, skulls, flames, teeth, blood splatter, scratches. ComfyUI can generate art for mask designs.
- **Mask style:** classic fiberglass (old-school), modern cage mask, welding mask, hockey mask + chain, bare-faced (crazy, more Hype).
- **Pads / glove / blocker:** colors, patterns, wear, tape, spikes, sponsor logos.
- **Goalie style:** Butterfly, Hybrid, Stand-up, Aggressive (playstyle ratings).
- **Celebrations & taunts:** stick tap, water-bottle spray, mask-tap, throat slash.

---

## 8. Modes for Goalies

- **Career as a Goalie:** create a goalie and play Career entirely in net (separate story beats: "the Dockrats' goalie nobody believes in").
- **Couch co-op dream setup:** **son in net, owner as skater** on the same team vs AI — the game should be balanced for exactly this.
- **Penalty Shootout of Death:** goalie can attack the shooter — goalies' favorite mode.
- **Goalie Gauntlet:** endless shooters, items, and crease crashers. Survive and save.
- **Goalie Challenges:** "Win with a broken glove," "Stop 10 slapshots in a row," "Score a goalie goal."
- **Shooting Gallery (Practice):** a goalie training mode with adjustable shot types and speeds.

---

## 9. Cameras for Goalies
- **Behind the Goalie (default when in net):** low behind-the-net view looking up ice, slightly elevated. Screens actually block your view.
- **Dynamic:** pulls back when play is in the other zone, tightens when shooters approach.
- Broadcast option available.

---

## 10. Tech Notes
- Saves need a large animation set (butterfly, stacks, glove/blocker saves, desperation dives). Use a smaller base set + **IK (Control Rig / Full Body IK)** to reach the exact puck position so saves look precise without hundreds of animations.
- Puck prediction: calculate the shot trajectory on release to drive save timing windows and assist positioning.
- Goalie movement: separate movement mode (shuffle, T-push, butterfly slide) — not skater movement.
- **Feel-test owner: the son.** Goalie is tuned with his feedback.

---

## Open Questions
- Should the goalie be playable in **every** mode (including Franchise sims/Challenges) — assumed yes.
- Any goalie your son would want added (style, look)?
- Should the son help design his own goalie mask? (Great first ComfyUI + Blender project.)
