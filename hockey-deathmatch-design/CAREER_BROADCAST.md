# RHL — Career Broadcast Segments (Brainstorm v0.1)

Career (`CAREER_STORY.md`) is told **only through Meridian's broadcast** and your phone — no cinematic cutscenes.
This doc defines every segment type, how a "game week" flows, how choices work, and how to make it all for $0.

---

## 1. Principles
1. **Short & skippable.** Most segments 20–90 s. Skip = recap card with the key info.
2. **The network spins everything.** Meridian's segments lie; the truth leaks through Knuckles, Tasha, texts, and leaked footage.
3. **Your game shows up.** Segments use your stats, your replays, your scars, your choices.
4. **Static cameras, rich graphics.** TV-style shots (desk, podium, rinkside) + lower thirds, tickers, replays — cheap to make, looks authentic.

---

## 2. A Career "Game Week"

```
Hub (locker room) → Phone check → [Story segment if any]
→ REDLINE TONIGHT (pre-game) → GAME → RINKSIDE WITH TASHA (post-game)
→ Commercial break → News ticker / Tabloid → Hub
```
- Non-story weeks: only pre-game + post-game (or skip straight to the game).
- Story weeks: 1–3 extra segments (Commissioner's Address, Leaked Footage, texts, events).

---

## 3. Segment Catalog

### 1. *Redline Tonight* — Pre-Game Show
| | |
|---|---|
| **Set** | Meridian studio desk (same as main menu) |
| **Cast** | Dale Marrow (host), Rene "Knuckles" Dupree (analyst) |
| **Length** | 30–90 s |
| **Content** | Matchup preview (records, stars, rivalries), your recent stats graphic, injury report, **Knuckles' coded warnings** (Act 1–2), **Knuckles' Breakdown** (telestrator on your own replays) |
| **Interactive** | None (watch/skip) |

### 2. *Rinkside with Tasha Vane* — Post-Game Interview
| | |
|---|---|
| **Set** | Rinkside / tunnel, sponsor backdrop, your player in gear (sweat, blood, new scars) |
| **Length** | 30–60 s, 1–3 questions |
| **Content** | Questions about the game, rivals, deaths, sponsors, the network |
| **Interactive** | **Answer choices** (see §4) with an optional **8-second "live TV" timer** — silence is also an answer |

### 3. *Commissioner's Address*
| | |
|---|---|
| **Set** | Podium with Meridian logo, press flashes |
| **Cast** | Vance Holloway |
| **Length** | 20–45 s, roughly every 4–6 games |
| **Content** | League announcements, rule changes, "tributes" to the dead; escalates from polished → subtly threatening → **speaking directly to you** in Act 3 |

### 4. *Leaked Footage*
| | |
|---|---|
| **Delivery** | Arrives via unknown text ("watch this") or Knuckles' flash drive |
| **Look** | Grainy security cam, timestamp, glitches, muffled audio, subtitles |
| **Content** | Holloway's people in the locker room, referee payoffs, the "Retirement List," and **your own replays** reframed (the hit that "accidentally" killed your mentor) |

### 5. Phone — Texts & Voicemail
| Sender | Role |
|---|---|
| **Desmond Price** — Meridian Talent Relations | The network's offers: throw games, play up rivalries, sponsor deals. Polite, menacing |
| **Mentor** (Frankie / Tommy) | Advice, jokes, warnings — and silence after Act 1 (or recovery texts if saved) |
| **Teammates** | Banter, fear, team group chat after deaths |
| **Tasha Vane** | Starts professional; later secret meetings and evidence |
| **Unknown Number** (Knuckles) | Coded tips, leaked footage |
| **Sponsors** | Deal offers (VoltRush, PainAway, Ironclad) |
| **Family / sibling** | Grounding moments; becomes **Next of Kin** if you die (permadeath) |
| **Rivals** | Threats, and later (Ace) pleas for help |

- **Reply choices** (2–3 options) on important texts; others are read-only.
- Unread badge in the hub; story texts must be read before the next game (or auto-shown).

### 6. Commercial Breaks
- Between segments: 5–15 s fake ads (ComfyUI art + TTS voice + simple motion).
- Sponsors: VoltRush, PainAway, Ironclad Life Insurance, SafeHaven Security, Kold Kut Meats.
- **Ads change with the story:** Ironclad's ad starts listing real dead players ("Protecting families like Frankie Moretti's").
- **You star in ads** if you sign a sponsor deal (your custom player on a VoltRush can, your face on PainAway).
- Skippable; can be turned off in settings.

### 7. Meridian News Ticker & *Sports Desk* Bulletins
- Ticker on every broadcast: scores, injuries, trades, deaths, rumors, story hints.
- Occasional 10–15 s Sports Desk bulletin read by Dale (big trades, deaths, suspensions).

### 8. *The Redline Rag* — Tabloid
- Still-image front page in the hub after big moments: photo (from your replay/Photo Mode) + headline.
- Examples: "ROOKIE SURVIVES — BARELY" · "WHO KILLED THE RAT KING?" · "ACE CRACKS?" · "DOCKRATS' CAPTAIN: NETWORK'S PUPPET?"

### 9. *RHL: Unfiltered* — Network "Reality" Segment
- Meridian's fake behind-the-scenes show: staged locker-room moments, scripted drama.
- Player choice: **play along** (Network Favor) or **break the fourth wall** (Loyalty) — e.g. refusing to fake a fight with a teammate.

### 10. Medical Bulletin
- Meridian medic reads your injury status after bad injuries (cold, clinical, sponsor-branded "PainAway Medical Update").
- Shows on-body injury diagram; tells you games missed.

### 11. Special Story Segments
| Segment | When |
|---|---|
| **Signing Day** | Career opener: contract + death waiver on screen; you "sign" with the controller |
| **In Memoriam** | After deaths: Tasha narrates over slow-mo replays; mentor's tribute (Act 1 end) |
| **Miracle on Pier 13** | If you **saved your mentor** — Meridian reluctantly airs the story |
| **The Trade Press Conference** | Act 2: Holloway offers the High Rollers deal live on air (choice on camera) |
| **Year in Blood** | Season end: Top 10 of your season + stats + who died |
| **Live Feed Hijack** | Ending: broadcast glitches, Knuckles' evidence plays mid-Final |
| **Static** | *Burn It Down* ending: the feed dies |

---

## 4. Interview Choice System (Tasha & press)

| Tone | Effect |
|---|---|
| **Humble** | +Loyalty, small +Network Favor, calms rivals |
| **Trash Talk** | +Hype at next game vs that team, +ratings, rival anger ↑ |
| **Company Line** | +Network Favor (reads the sponsor script) |
| **Defy the Network** | +Loyalty, −Network Favor, Holloway notices |
| **Silence** (timer runs out / choose to stay quiet) | Neutral; certain story moments read silence as defiance |

- Each answer has a short preview of its tone, not the exact line.
- Context options appear sometimes (e.g. "Dedicate the win to Frankie").
- Your **origin** and **rivals** change the questions asked.

---

## 5. Dynamic Content
| Pulled from your game | Used in |
|---|---|
| Stats (goals, saves, kills, hits, fights) | Redline Tonight graphics, Year in Blood |
| Replays & photos | Breakdown, In Memoriam, tabloid covers, Leaked Footage |
| Scars & injuries | Interview shots (your player looks how your career has gone) |
| Rivals & who you've hurt/killed | Questions, texts, Holloway's address |
| Choices & meters | Which segments/variants appear; ad content |
| Custom player name | Dale/Tasha say it (pre-generated TTS name clips) |

### Voice approach (honest constraint)
- All story lines are **pre-written and pre-generated** with local TTS.
- Dynamic bits (your name, team, numbers) use **stitched clips** (pre-made name/number/team audio) or appear **on-screen only** (stats graphics).
- No runtime AI speech needed — keeps it reliable and fast.

---

## 6. Sample Scripts

### Signing Day (Career opener)
> *Black screen. A contract slides in. Fine print: "…releases Meridian Media Group from all liability in the event of serious injury or death…"*
> **TASHA (V.O.):** "Every season, hundreds sign. Most of them, you'll never hear about."
> *[Press A to sign]*
> **DALE:** "And there it is, folks — the newest Bayonne Dockrat! Odds of surviving the season… thirty-one percent! *Redline Live* is brought to you by Ironclad Life Insurance."

### Redline Tonight — Act 1, Week 4 (Knuckles' coded warning)
> **DALE:** "Big one tonight at The Jackpot! The kid's been a highlight machine — Knuckles, what's the key?"
> **KNUCKLES:** "Keep your head up, kid. Refs in Vegas got real bad eyesight… especially when somebody pays for glasses."
> **DALE:** *(laughs too loud)* "Ha! Classic Knuckles. We'll be right back!"

### Rinkside — after a teammate dies
> **TASHA:** "You lost a teammate tonight. What do you say to his family?"
> [Humble] "He was the best of us." · [Company Line] "He knew the risks. Ironclad will take care of them." · [Defy] "Ask the league why the refs watched it happen." · *(silence)*

### Commissioner's Address — Act 3
> **HOLLOWAY:** "This league has always rewarded those who understand what the fans want. *(looks into camera)* I'm sure our Dockrats captain understands. We'd hate for the Final to be… anyone's last game."

---

## 7. Production ($0)
| Need | How |
|---|---|
| Sets | Studio desk, podium, rinkside tunnel, locker room — Blender + Megascans (studio desk shared with main menu) |
| Characters | MetaHumans (Dale, Knuckles, Tasha, Holloway, Desmond Price) with idle/talking loops |
| Lip-sync | Audio-driven facial animation from the TTS lines (MetaHuman tools support generating facial animation from audio — verify version on install) |
| Voices | Local TTS, one voice per character |
| Graphics | UMG broadcast package (lower thirds, tickers, stat cards) from `UI.md` |
| Ads & tabloids | ComfyUI images + simple motion + TTS voice-over |
| Leaked footage | Staged in-engine scenes + security-cam filter (replay system) |
| Assembly | Each segment = Sequencer shot list + data (lines, choices, conditions) |

### Segment Data (one Data Asset per segment)
Type · cast · set · lines (with conditions: act, meters, mentor alive, rivals) · choices & effects · dynamic slots (stats, replays) · camera shots · skippable recap text.

### Line Count Estimate
~1,500–2,000 Career lines (Dale ~500, Tasha ~400, Knuckles ~300, Holloway ~150, Price ~100, others ~300) + ~40 ads.

---

## 8. Build Order
1. Segment framework (data asset, Sequencer shot player, skip/recap) + studio desk set
2. Redline Tonight + Rinkside with Tasha (choices & meters)
3. Phone/texts + news ticker
4. Commissioner's Address + Medical Bulletin
5. Commercial breaks + tabloids
6. Leaked Footage (needs replay system)
7. Special story segments (Signing Day, In Memoriam, Trade Press Conference, endings)
8. RHL: Unfiltered + Year in Blood
9. Lip-sync pass + polish

---

## Open Questions
- 8-second interview timer: on by default, or off?
- Your custom player starring in sponsor ads — fun?
- Meridian rep name "Desmond Price" OK?
