# RHL — Audio & Soundtrack (Brainstorm v0.1)

Audio sells the brutality. A hit without a bone crunch and crowd roar is just two models touching.
**$0 pipeline:** ComfyUI (local music, SFX, and TTS models), Freesound (CC0), and home-recorded foley.

---

## 1. Audio Pillars
1. **Every hit is heard.** Layered, speed-scaled impacts — you can tell a bump from a kill with your eyes closed.
2. **The crowd is alive.** Reacts to everything, builds with Hype, chants, boos, goes silent.
3. **It's a TV broadcast.** Announcers, sponsor stings, PA voice, organ — Meridian is always talking.
4. **Every arena sounds different.** A mine echoes; a casino rings; a prison yard is cold and empty.

---

## 2. Music

### Overall Style: "Industrial Blood-Sport"
- **Core:** industrial metal, sludge/groove metal, hardcore punk, heavy distorted synths.
- **Hockey identity:** the classic **arena organ** — but twisted (detuned, distorted, sinister). Organ stings for goals, kills, fights.
- **Broadcast identity:** Meridian's clean, corporate TV jingles — deliberately cheerful, contrasting with the violence.

### Where Music Plays
| Moment | Music |
|---|---|
| Main menu | Meridian broadcast theme → slow industrial build |
| Menus / creation suite | Low-key industrial loops |
| Team intros / walkouts | Each team's anthem (8 + All-Stars) |
| In-game | **Adaptive**: arena crowd + organ during play; music swells with Hype |
| Goals | Team's goal song + horn |
| Fights | Drums kick in; crowd chant layer |
| Network Events | Event sting + intense track |
| Career broadcast segments | Meridian news/sports jingles |
| Endings | Unique track per ending |

### Adaptive Music (by Crowd Hype)
| Hype Tier | Music layer |
|---|---|
| 0 | Arena ambience, organ noodling, PA |
| 1 | Low drum pulse |
| 2 | Bass + guitars |
| 3 | Full track (Network Event) |
| Max | Finisher sting, everything drops out → impact → crowd explodes |

### Team Anthems & Goal Songs
| Team | Anthem style | Goal horn |
|---|---|---|
| Detroit Ironworkers | Heavy industrial, factory machinery percussion | Factory whistle |
| Gary Slagdogs | Sludge metal, dirty and slow | Steam blast |
| Winnipeg Wardens | Chain-gang chant over hardcore drums | Prison siren |
| Las Vegas High Rollers | Glitzy brass + slot jingles (ironic) | Jackpot bells |
| New Orleans Drowned | Brass band gone dark, swampy blues-metal | Ship horn |
| Anchorage Butchers | Cold, droning doom metal | Bone saw + horn |
| Bayonne Dockrats | Street punk, scrappy and fast | Tugboat horn |
| Sudbury Deep | Low drones, tribal drums, mining clanks | Mine evacuation alarm |
| Meridian All-Stars | Polished corporate synth-pop that turns menacing | Network jingle |
| Custom teams | Pick from library or **custom file** | Pick from horn library |

### Custom Soundtrack
- **Custom music folder:** drop your own MP3/OGG/WAV files in a folder → use as menu music, goal songs, or in-game playlist. (Personal project = use whatever you like.)

---

## 3. Crowd System

- **Layered crowd:** ambient murmur → cheering → roaring, blended by Hype and action intensity.
- **Reactions:** big hits ("OHHH!"), near misses, goals, kills (shock → roar), fights (rising chant), boring play (boos, whistling).
- **Chants:** "FIGHT! FIGHT!", team chants, player-name chants for stars, "SIEVE!" at a goalie who lets in goals, "WE WANT BLOOD!"
- **Arena-specific crowds:**
  - The Yard: inmates banging on fences, no cheering — growls and chants
  - The Jackpot: polite clapping, slot noise, betting murmur
  - The Shaft: miners banging pickaxes on rock
  - Pier 13: small, loud, ship horns
- **Silence moment:** at a finisher, the crowd goes dead silent for a beat before erupting.

---

## 4. Announcers & Voices

### The Booth
| Voice | Role | Style |
|---|---|---|
| **Dale "The Voice" Marrow** | Play-by-play | Over-the-top, sponsor plugs mid-kill ("That hit brought to you by Ironclad Life Insurance!") |
| **Rene "Knuckles" Dupree** | Color commentary | Gravelly, dry, honest, ex-enforcer insight; quietly anti-network |
| **Tasha Vane** | Rinkside reporter | Professional, interviews, injury reports |
| **Arena PA announcer** | In-arena | Echoing goal/penalty calls ("Penalty… for attempted murder… two minutes.") |
| **Holloway** | Career segments | Smooth, calm, threatening |

### Announcer Line Categories
- Game start/period start/end, goals, saves, big hits, kills, fights, finishers
- Items picked up/used, hazards & Network Events, injuries, penalties
- Player names (stars + **custom players**), team names, arena intros
- Running storylines (rivalries, streaks, Career story callbacks)
- Sponsor reads (the satire)
- **Goalie lines:** Perfect Saves, Hot Streaks, goalie fights, goalie goals

**Estimated size:** ~1,500–3,000 lines across all voices. Local TTS makes this realistic.

### Custom Player Names
- When creating a custom player, the game generates announcer lines saying the name using **local TTS** — Dale and the PA can actually call your custom player's name.
- Nickname picker as backup ("The Rookie," "The Butcher," "Number 13").

### Player Voices
- Grunts, effort sounds, pain, trash talk, celebrations — a set per voice type (custom players pick one).

---

## 5. Sound Effects

| Category | Sounds |
|---|---|
| **Skating** | Stride, glide, carve, hard-stop spray, crossovers; speed-based pitch/intensity |
| **Puck** | Stickhandling taps, pass slaps, wrist shot, slapshot crack, post ping, crossbar, glass, net ripple |
| **Hits** (tiered) | Bump (pad thud) → check (heavy thud, board shake) → crush (glass rattle, bone crack) → kill (sickening crunch, crowd gasp) |
| **Boards & glass** | Board rattle, glass thump, glass crack/shatter, chain-link clang |
| **Fights** | Gloves dropping, jersey grabs, punches (jab vs haymaker), blocks, parry clank, knockdowns |
| **Weapons** | Chain whip, razor slice, sledge smash, bottle shatter, padlock-in-sock thud, flare hiss |
| **Goalie** | Glove snap, blocker deflect, pad thump, butterfly slide, mask hit ring |
| **Hazards** | Conveyor motors, molten hiss, sirens, slot wheel, ice cracking, blizzard wind, container drop, cave-in rumble |
| **Broadcast** | Replay whoosh, TV stingers, sponsor jingles, commercial bumpers |
| **UI** | Menu clicks with industrial/metal flavor |

### Arena Acoustics
- Each arena gets its own reverb/ambience: echoey mine, open-air prison yard, tight container stacks, factory hall, glossy casino.
- Weather layers: rain on metal roofs, wind, thunder.

---

## 6. Mix Priorities
1. Hits / injuries / weapons
2. Puck (players must hear shots and posts)
3. Announcers (duck music and crowd under them)
4. Crowd reactions
5. Music
6. Ambience

- **Split-screen:** shared mix, centered on the action between both players.
- Controller **rumble** synced with major hits, shots, and goals.

---

## 7. Audio Settings
- Volume sliders: Master, Music, SFX, Crowd, Announcers, Voice (players), Ambient
- Announcer frequency: Off / Low / Normal / Max
- Music: On / Off / Custom folder only
- Gore audio: Normal / Reduced (ties to Gore Level setting)
- Subtitles for announcers & broadcast segments

---

## 8. $0 Production Pipeline

| Need | Source |
|---|---|
| Music tracks & anthems | **ComfyUI** local music models (e.g. ACE-Step for full songs with vocals; Stable Audio Open for loops/stings) |
| Organ stings | ComfyUI + free organ samples/soundfonts |
| SFX | **Freesound (CC0)**, Stable Audio Open, **home foley** (smashing ice, hitting pads, slapping hockey sticks) |
| Announcers & voices | **Local TTS** in ComfyUI (check model licenses); or record our own |
| Crowd | Freesound crowd recordings + layered/processed loops |
| Implementation | **UE5 MetaSounds** (adaptive music, crowd layers, speed-based skating audio), Sound Classes/Mixes for ducking |

---

## Open Questions
- Music style: industrial metal / punk direction OK, or a different genre (hip-hop, rock, electronic)?
- Custom music folder — wanted?
- Should the owner/son voice any characters (e.g. PA announcer cameo)?
