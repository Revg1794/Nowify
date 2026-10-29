# RHL — Menus & UI (Brainstorm v0.1)

**Concept: "The Meridian Broadcast Package."** Every screen looks like part of a TV broadcast: scorebugs, lower thirds,
news tickers, sponsor bugs, replay stingers. Clean, glossy, corporate network graphics — that **glitch, crack, and get
blood-splattered** during brutal moments. The contrast (polished network vs. brutal sport) *is* the style.

All menus are fully **controller-first** (Xbox + PlayStation icons auto-switch), with mouse/keyboard support.

---

## 1. Visual Style

| Element | Style |
|---|---|
| Colors | Meridian **white, steel gray, signal red** + each team's colors in matches |
| Fonts (free, open license) | Condensed bold headlines (e.g. Bebas Neue / Oswald / Barlow Condensed), mono font for tickers & stats (e.g. Roboto Mono) |
| Motion | Fast broadcast wipes, slide-ins, sponsor "bumpers," replay stingers with the Meridian logo |
| Grit layer | Scanlines, signal glitches, cracked glass, blood splatter on panels (respects Gore setting) |
| Sponsors | Fake sponsor bugs everywhere (VoltRush, PainAway, Ironclad) — satire |

---

## 2. Boot & Main Menu

- **Boot:** Meridian network ident → "MERIDIAN PRESENTS: REDLINE HOCKEY LEAGUE" → *Redline Live* intro bumper (skippable).
- **Main menu = the broadcast studio:** a real 3D set (the *Redline Live* desk) with Dale and Knuckles idling, monitors showing
  highlights from **your own replays**, news ticker scrolling real info (your records, Career/Franchise headlines).
- Menu presented like a **TV channel guide**:

| Channel | Contents |
|---|---|
| **PLAY** | Exhibition · Career · Franchise · Challenges · Penalty Shootout of Death · Practice (The Pit) |
| **CREATE** | Custom Player · Custom Team · Custom Arena · Goalie Mask Editor · Challenge Editor · House Rules presets |
| **BROADCAST** | Replay Library · Replay Editor · Highlight Reels · Year in Blood |
| **LEGACY** | Stats & Records · Trophy Case (medals, cups) · Memorial Wall (all deaths across modes) · Profiles |
| **SETTINGS** | Controls · Gameplay Sliders · Audio · Video · Gore & Violence · Accessibility |
| **EXTRAS** | Custom Music Folder · Credits (with family credits) · Unlocks gallery |

---

## 3. Player Profiles & Couch Join

- **Profiles** (e.g. owner + son): each stores controls scheme (Arcade/Pro), assists, User sliders, favorite team, stats, medals, unlocks.
- **Join screen:** "Press A / ✕ to join" — each controller picks a profile and a side (Home / Away / Spectate).
- Controller icons show **per player** (one on Xbox, one on PlayStation — each sees their own button icons in split-screen).

---

## 4. In-Game HUD (behind-the-player cam, split-screen ready)

### Scorebug (top center — broadcast style)
`[DET 2] [BAY 1]  2nd  07:42  PP 1:12  · VoltRush`
- Team abbreviations + colors, score, period, clock, power play timer, small rotating sponsor bug.
- In split-screen: **one shared scorebug** at the center seam.

### Crowd Hype Meter
- Styled as a **"RATINGS" meter** attached to the scorebug, with 3 tier notches + Max.
- At Tier 3: flashes **"NETWORK EVENT"** with the event name ("SHIFT CHANGE").
- At Max: the meter cracks open — "FINISHER AVAILABLE" + button prompt.

### Player-Level HUD (around your skater, minimal)
| Element | Design |
|---|---|
| Player ring | Colored ring under your skater (player color) |
| Health / injury | Ring segments darken with damage; small injury icons on the ring (arm, leg, head, bleeding). **No floating health bars.** |
| Stamina | Thin arc on the ring that drains while sprinting/fighting |
| Item slots | Bottom corner of each player's screen: **Active** (big) + **Stored** (small), uses/time remaining |
| Puck indicator | Arrow at screen edge when puck is off-screen |
| Teammates / threats | Small edge arrows; red pulse for an incoming charged hit from behind |

### Telegraphs & Alerts
- **Item drop:** ice marker + edge arrow + item icon, countdown pip.
- **Hazards:** red warning stripes on the ice + edge alert ("CONVEYOR — LEFT").
- **Network Event:** full broadcast banner for 1–2 s.

### Kill Feed (lower third)
- "**KOWALSKI** ELIMINATES **RUSSO** — *brought to you by Ironclad Life Insurance*"
- Big hits, fights, goals also get lower-third callouts.

### Goalie HUD
- Optional **positioning ring** (angle/depth guide; shown based on assist level).
- **Save streak** counter → "HOT STREAK" banner at 5+.
- **Perfect Save** flash text + brief crowd cut-in.
- Gear damage icons (mask, glove, blocker, pads).

### Fight HUD
- Minimal: both fighters' stamina + guard meters at top, "Guard Break" flash, recovery timing prompt.
- Telegraphs are read from animations (no on-screen "block now" by default; optional on assist settings).

### Other
- **Finisher prompt:** button icons over the target.
- **Subtitles** for announcers/trash talk (bottom, broadcast caption style).
- **Replay overlay:** "REPLAY" bug + Meridian wipe in/out; skip with one button.
- **HUD options:** Full / **Minimal** / Off; HUD scale; per-element toggles.

---

## 5. Pause Menu — "We'll Be Right Back"
- Pausing triggers a quick **"commercial break"** transition (fake sponsor ad freeze-frame), then the pause menu.
- Options: Resume · Controls · Sliders · Settings · Line changes/strategy · Restart · Quit.
- Each player can open their own controls/assists from pause.

---

## 6. Post-Game — "Final Score"
1. **Final score bumper** (broadcast style).
2. **Three Stars of the Game** (hockey tradition) — with RHL categories: goals, saves, kills, hits, fights.
3. **Stats:** shots, saves, hits, fights won, items used, kills, injuries.
4. **Injury Report** (and deaths) — styled as a grim medical bulletin.
5. **Ratings** earned (Career/Franchise), medals/unlocks earned.
6. Options: Watch Highlights · Save Replay · Rematch · Continue.

---

## 7. Loading Screens
- Fake sponsor ads (ComfyUI-generated), **Knuckles' Tips** ("Keep your head up near the boards, kid."),
  news ticker headlines, arena intros with weather/time-of-day info.

---

## 8. Mode Hubs

| Mode | Hub style |
|---|---|
| **Career** | Locker room set: your stall, your phone (texts), a TV playing Meridian segments, calendar of games |
| **Franchise** | **Owner's Office**: desk with phone (events, trade offers), TV (league news), roster board, budget sheet, **Memorial Wall** behind the desk. Co-op co-sign screen with both controller icons |
| **Challenges** | Highlight Reel "episode guide" — packs as seasons, challenges as episodes with medal slots |
| **Shootout of Death** | Dark arena, spotlight on shooter vs goalie select |
| **Replay Editor** | Simple timeline, camera presets (Broadcast, Behind Player, Cinematic, Slow-Mo), Meridian overlay toggle, export video |

---

## 9. Creation Suite UI
- 3D preview center screen (rotate/zoom with right stick), tabs on left, options on right.
- **Goalie Mask Editor:** mask in 3D, layer list, decals/shapes/colors, mirror symmetry, presets.
- **Logo Editor:** layered shapes, text, grunge filters, preview on jersey/ice/jumbotron.
- Quick **Randomize** button for players/teams.

---

## 10. Accessibility & Comfort
- Subtitles (size, background), UI text size
- Colorblind modes (team colors + hazard colors)
- **Flash reduction** (lightning, Blackout, camera flashes, glitch effects)
- Screen shake intensity, hitstop intensity, motion blur toggle
- Hold vs toggle (sprint, block), full remapping
- HUD opacity

---

## 11. Tech Notes
- **UMG + CommonUI** (controller navigation, input routing per player, auto Xbox/PS icons).
- Split-screen: per-player HUD widgets + one shared scorebug overlay.
- Broadcast effects: UI materials (scanlines, glitch, crack masks), Sequencer/UMG animations for wipes.
- Main menu & hubs as small 3D levels (Blender sets + MetaHumans), not flat screens.
- Art: ComfyUI for sponsor ads, backgrounds, icons drafts; final icons cleaned/vectorized for crispness.
- All text in string tables (easy edits, subtitles).

---

## 12. Build Order
1. Vertical slice: simple scorebug, item slot placeholder, puck arrow, basic pause, controller join
2. Profiles + couch join + per-player icons
3. Hype meter, kill feed, telegraph UI (with item/Hype milestone)
4. Goalie HUD + fight HUD
5. Post-game (Three Stars, stats)
6. Main menu studio set + channel guide
7. Mode hubs (Challenges → Franchise office → Career locker room)
8. Creation suite UI (player → team → mask → logo → arena → challenge editor)
9. Broadcast polish: glitches, sponsor bumpers, loading screens, "commercial break" pause
10. Accessibility pass

---

## Open Questions
- Default HUD: Full or Minimal?
- "Commercial break" pause transition — fun or annoying? (Can be turned off.)
- Profile names to pre-create (owner + son)?
