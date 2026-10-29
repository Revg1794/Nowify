# RHL — Replay & Broadcast Editor (Brainstorm v0.1)

Every game is "on TV," so every game is **recorded**. The replay system feeds instant replays, post-game highlights,
the main-menu monitors, *Year in Blood*, Career "leaked footage" — and a full **Broadcast Editor** for making your own highlight videos.

---

## 1. Recording

- **Always recording** every match — including **simmed games** (see §1b).
- Stored as **data, not video**: player/puck/item transforms, animation states, ragdoll poses, events (goals, hits, kills, saves, fights, items, Hype, hazards), camera cuts, audio cues.
  Small files; re-rendered from any camera later.
- **Auto-tagging:** every event is tagged (who, what, where, Hype tier) so highlights can be found automatically.
- **Storage:** last **20 full matches** kept automatically; **favorite/lock** to keep forever; saved clips kept separately.

### 1b. Simmed Matches (DECISION: record them too)
Simmed games don't play out physically, so they're recorded differently:
| Layer | What's stored | Cost |
|---|---|---|
| **Sim Log** (always) | Full play-by-play events, box score, injuries/deaths, Hype swings, Three Stars | Tiny (KB) |
| **Sim Highlights** (always) | Top moments (by Excitement Score) are **re-enacted** as short staged clips: AI players placed into the situation and played out in-engine for ~5–15 s, then recorded as normal replay data | A few seconds of processing per highlight, done in the background |
| **Full Engine Sim** (optional per game) | The whole game is played AI-vs-AI in the background at high speed → a complete, real replay | Slower (minutes per game) — offered for **playoff/important games** or toggled on in settings |

- Sim highlights feed the same places as played games: post-game, main menu monitors, Year in Blood, Memorial Wall ("final play").
- Re-enacted clips are tagged "SIM" in the library.

---

## 2. Automatic Highlights

### Excitement Score (picks the best moments)
| Event | Score |
|---|---|
| Goal | 10 (+5 puck mod, +10 goalie goal, +5 game-winner) |
| Kill | 12 (+8 finisher / signature move) |
| Crush hit | 5 (+5 into hazard) |
| Perfect Save | 6 (+4 during Hot Streak) |
| Fight won | 6 |
| Network Event | 8 |
| Mascot Invasion | 4 |
| Multiplier | ×1.5 at Max Hype · ×1.3 last 2 min of a period |

### Where highlights appear
| Place | What |
|---|---|
| **Instant replay** | After goals, kills, big saves (skippable, 1 button) |
| **Intermission** | "Period in Review" — top 3 moments |
| **Post-game** | Highlights + **Three Stars** clips |
| **Main menu monitors** | Your best recent moments loop in the studio |
| **Year in Blood** | End-of-season reel (Career & Franchise) — top 10 of the season |
| **Career Leaked Footage** | Story segments sometimes reuse **your own** replays with a grainy security-cam filter ("Meridian doesn't want you to see this…") |

---

## 3. Replay Viewer

- **Controls:** play/pause, scrub, frame step, speed **0.1× – 2×**, jump to next/previous event.
- **Event list:** jump straight to any goal, kill, save, fight.
- **Follow target:** any player, the puck, or a free point.

### Cameras
| Camera | Description |
|---|---|
| **Broadcast** | Classic TV side view |
| **Behind Player** | The gameplay camera |
| **Goalie Cam** | Low behind-the-net view |
| **Helmet Cam (POV)** | First-person from any player — brutal for hits and fights |
| **Ice Level** | Camera skimming the ice surface |
| **Orbit** | Circle around the action |
| **Drone / Free Cam** | Fly anywhere (both sticks) |
| **Arena Cams** | Fixed cameras: jumbotron cam, rafters, penalty box, behind the glass |
| **Security Cam** | Grainy corner camera with timestamp (leaked-footage style) |

---

## 4. Broadcast Editor

### Timeline
- Mark **In/Out** to cut clips from any replay → clips go to a **Clip Library**.
- Build a **Reel** by placing clips on a timeline (drag, trim, reorder).
- **Camera keyframes:** set camera positions/angles at points in time; the editor smoothly moves between them.
- **Speed ramps:** slow-mo into impact, speed back up (preset "Hit Ramp" and "Goal Ramp").

### Transitions
Cut · Meridian wipe · Glitch · Flash · Fade to black · "Commercial break" bumper

### Overlays
- **Scorebug** (on/off), **lower thirds** ("KOWALSKI — 3rd KILL TONIGHT"), player name cards, custom text.
- **Telestrator:** draw on a frozen frame like a TV analyst (arrows, circles, lines) — "Knuckles' Breakdown" style.
- **Sponsor bugs** (fake sponsors).
- **Replay bug** ("REPLAY" in the corner).

### Filters / Looks
Broadcast (clean) · Security Cam / Leaked Footage · VHS · Black & White · Film grain · Night vision (great in The Shaft) · High contrast "Blood Season".
Gore setting always applies.

### Audio
- Game audio (on/off/volume), crowd, **announcer replay calls** (Dale re-calls the play), effects only.
- **Music track:** RHL soundtrack or **custom music folder** song; auto-duck under announcer.

### Templates (one-click reels)
| Template | Result |
|---|---|
| **Redline Live Highlight** | Classic TV highlight with Dale's calls |
| **Top 10 Plays** | Auto-builds a countdown from your best tagged moments |
| **Leaked Footage** | Security cam, glitches, timestamp, no music |
| **Player Spotlight** | All moments for one player (e.g. your custom player or the son's goalie) |
| **Goalie Reel** | Best saves & goalie moments — made for the son |
| **Year in Blood** | Season recap |

---

## 5. Photo Mode
- Pause any replay (or live game, offline) → free camera.
- Field of view, **depth of field**, exposure, tilt, filters (same as editor), frames/borders, logos, sponsor bug.
- Hide HUD/players toggles; **freeze-frame blood & ice spray mid-air**.
- Save screenshots at high resolution (up to 4K / supersampled).

---

## 6. Export & Sharing
- **Export video:** MP4, 1080p / 1440p / 4K, 30 or 60 fps.
- **Export screenshots:** PNG/JPG.
- **Share replay files** (data) between your PCs/friends — replays include required custom team/player data.
- Saved to a local **Highlights** folder.

---

## 7. Mode Integrations
- **Career:** Year in Blood, Leaked Footage segments, Tasha's interviews show clips of your plays.
- **Franchise:** Year in Blood, Memorial Wall shows the player's best moment and their final play.
- **Challenges:** watch your Gold-medal run; replays saved automatically for best scores.
- **Main menu:** studio monitors cycle your highlights.

---

## 8. Tech Notes
- **Custom recorder** (recommended over UE's network replay system for an offline game): records transforms at ~30 Hz, animation state + montage events, ragdoll bone snapshots during physics, item/hazard state, and events. Interpolates on playback.
- Playback spawns "replay actors" (visual-only copies), so gameplay code isn't involved.
- **Cameras:** CineCamera actors driven by the editor; keyframes interpolated with splines.
- **Video export:** verify at build time which runtime capture method works best (UE runtime movie render support vs. frame capture + local FFmpeg encode).
- **Storage estimate:** a few MB per full match (data only).
- Replays tied to game version; old replays may not play after big updates (warn the player).

---

## 9. Build Order
1. Recorder + simple playback (vertical slice — needed to debug hits & feel)
2. Instant replays (goals, kills) + skip
3. Viewer controls + camera modes
4. Event tagging + Excitement Score + post-game highlights + Three Stars clips
5. Main-menu monitors + Year in Blood
6. Clip Library + timeline editor + transitions
7. Overlays, filters, audio, telestrator
8. Templates (Top 10, Goalie Reel, Leaked Footage…)
9. Photo Mode
10. Video export + replay file sharing

---

## Decisions (Oct 2026)
- **Photo Mode: yes.**
- Auto-keep last **20 matches**: yes.
- **Record simmed matches too** (Sim Log + re-enacted Sim Highlights; optional Full Engine Sim) — see §1b.

## Open Questions
- Telestrator — explained; awaiting keep/skip decision.
