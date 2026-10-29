# RHL — Custom Teams & Logo Editor (Brainstorm v0.1)

Detailed design for **Create Team** (expands `GAME_DESIGN.md` §6). Presented as a Meridian
**"Expansion Franchise Application"** — you're pitching a new team to the league, and the network "approves" it at the end.

---

## 1. Flow Overview

| Step | Screen | What you set |
|---|---|---|
| 0 | **Quick Start** | Template (Industrial, Prison, Coastal, Frontier, Corporate, Street) or Randomize |
| 1 | **Identity** | City, team name, abbreviation, motto, rival team |
| 2 | **Colors** | Primary, secondary, accent, + metallic/neutral |
| 3 | **Logo Editor** | Primary logo, shoulder logo, wordmark, alternate |
| 4 | **Uniforms** | Home, away, alternate jerseys; pants, socks, helmets, goalie gear colors |
| 5 | **Arena** | Base arena shell, hazards, center-ice logo, boards, banners, lighting, weather default |
| 6 | **Presentation** | Goal horn, goal song, walkout music, chant, mascot, jumbotron intro |
| 7 | **Roster** | Custom players, generated players, stars (via trades/edits), lines |
| 8 | **Team Style** | AI tactics profile (how your team plays when AI controls it) |
| 9 | **Network Approval** | Broadcast segment: Dale & Knuckles react to your team reveal → Save |

All steps skippable; Randomize + lock on every step; Undo/Redo.

---

## 2. Identity
- **City:** any real city (pick from list or type one). Announcers use it ("The Duluth…").
- **Team name:** free text + **name generator** (adjective + noun from RHL-style word lists: "Rustbelt Hounds," "Pittsburgh Pipefitters").
- **Abbreviation:** 3 letters for the scorebug (auto-suggested).
- **Motto:** shown on banners and the team intro ("Nobody Leaves Clean").
- **Rival:** pick an RHL team → rivalry games get extra Hype, and AI teams play harder against you.
- **TTS:** team name & city generated for announcers at save (preview button).

---

## 3. Colors
- 3 team colors + 1 neutral (white/black/gray/metal).
- **Palette presets** inspired by the RHL style (Rust & Steel, Blood & Bone, Toxic, Navy & Rope, Gold & Black).
- **Contrast check:** warns if colors are hard to tell apart from opponents or under dark-arena lighting (readability rule).
- Colors flow automatically into logos, jerseys, arena boards, and UI.

---

## 4. Logo Editor (the big one)

### Canvas
- Square canvas with grid & snapping, zoom, safe-area guides.
- **Up to 32 layers per logo** (keeps performance & file size small).
- Layer list: reorder, hide, lock, duplicate, group, rename.
- **Symmetry mode:** mirror left/right while editing.

### Shape Library (all original art made for RHL)
| Category | Examples |
|---|---|
| Animals | Rat, dog, wolf, bear, boar, crow, shark, gator, snake, bull, hawk |
| Skulls & bones | Skulls (many styles), crossbones, teeth, jaws |
| Weapons & tools | Hockey sticks, chains, hooks, wrenches, sledgehammers, cleavers, pickaxes, anchors, gears |
| Industrial | Smokestacks, factories, cranes, containers, rivets, hazard stripes |
| Hockey | Pucks, nets, skates, masks, crossed sticks, center-ice circles |
| Shapes & badges | Shields, crests, circles, banners, stars, diamonds, ribbons |
| Elements | Flames, lightning, blood drips, splatter, cracks, ice shards, waves |
| Letters | Full alphabets & numbers in several styles |

- **Dev note:** shape library is generated with **ComfyUI** (concepts) → cleaned up and **vectorized** → imported as crisp shapes.

### Shape Tools
- Move, rotate, scale, skew, flip, stretch.
- Color from team palette or custom.
- **Effects per layer:** outline (multiple strokes), drop shadow, bevel/emboss (for jersey crests), gradient, inner glow.
- **Masks:** clip a layer to the one below it (e.g. splatter only inside the shield).

### Text Tool
- Several fonts (block, condensed, script, stencil, distressed, old-school hockey).
- **Arc / warp** (curved banners, top/bottom arcs), letter spacing, outline, shadow.

### Grit Filters (RHL style)
- **Distress** (worn print), **scratches**, **blood splatter**, **rust**, **burn**, **stencil spray** — strength slider.
- Applied to the whole logo or per layer.

### Logo Variants
| Variant | Used on |
|---|---|
| **Primary** | Jersey chest, center ice, menus, scorebug |
| **Shoulder / secondary** | Jersey shoulders, helmets, boards |
| **Wordmark** | Banners, jumbotron, away jerseys (optional) |
| **Alternate** | Alternate jersey, merch, ice behind nets |

"Auto-generate secondary" button: builds a shoulder logo from the primary (simplified icon).

### Live Preview
Toggle previews on: jersey chest, shoulder, helmet, **center ice**, boards, banner, jumbotron, goalie mask, scorebug.

### Presets & Sharing
- Start from **logo templates** (badge + animal + text layouts).
- Save logos to a **Logo Library** (reuse across teams, masks, and players' tattoos).
- Export/import with the team file.

---

## 5. Uniforms

### Jersey Designer
| Part | Options |
|---|---|
| Template | Classic stripes, modern, retro, prison stencil, work-wear, minimal |
| Body | Base color, yoke, hem stripes (count/width), sleeve stripes, side panels |
| Logo | Chest logo, shoulder logos (on/off, which variant) |
| Numbers | Font, fill, outline (1–2), placement (back, sleeves, chest) |
| Nameplate | Font, color, arc |
| Captain marks | "C" / "A" style |
| Sponsor patch | Fictional sponsor slot (VoltRush, PainAway, etc.) or none |
| Wear | Clean → battle-worn; blood amount follows Gore setting |

- **Home / Away / Alternate** jerseys, each fully designable; "Invert for away" button.
- **Pants, socks, helmet** colors and stripe patterns; helmet decals (logo, numbers).
- **Goalie gear defaults:** team colors applied to pads/glove/blocker + default mask design (from Mask Editor).

---

## 6. Arena (links to Custom Arena in `ARENAS.md`)
- **Base shell:** pick any arena's style (factory, mill, prison yard, casino, barge, meatpacking, port, mine, The Pit).
- **Hazards:** pick from that shell's hazards (or mix, where compatible); hazard intensity.
- **Network Event:** choose which event your arena triggers at Tier 3.
- **Ice:** center-ice logo, faceoff circle colors, behind-net logos, ice condition (clean → scarred).
- **Boards:** sponsor ads, team colors, wear.
- **Banners:** motto, "retired numbers," fake championship banners.
- **Lighting & weather defaults:** time of day, weather, lighting mood.
- **Crowd type:** workers, inmates, rich bettors, locals, miners, punks.
- **Item delivery style** (from the shell's options).

---

## 7. Presentation
| Element | Options |
|---|---|
| Goal horn | Library (factory whistle, siren, ship horn, jackpot bells, air horn, foghorn…) |
| Goal song | Library or **custom music folder** |
| Walkout music | Library or custom |
| Crowd chant | Pick from chant library or a team-name chant (TTS-generated) |
| Mascot | Pick from library (rat, dog, bear, hooded figure, butcher…) — appears in the stands, on the jumbotron, in intros (and *maybe* gets hit by a puck) |
| Jumbotron intro | Templates (fire, smoke, factory, prison lockdown, glitch) using your logo & colors |

### Mascots on the Ice (DECISION: yes, sometimes)
Mascots are people in suits — grounded, a little sad, very RHL.
| Moment | What happens |
|---|---|
| **Intermission Chaos** | Between periods: mascot races, mascot brawls, or the mascot rides the Zamboni (watchable or skippable) |
| **Mascot Invasion** (rare, during play) | Home mascot runs onto the ice for ~10 s at Hype Tier 2+ — can **drop an item** (Spawn Director delivery), get in the way, and **be checked** for a Hype bonus (crowd boos or cheers) |
| **Goal / win celebrations** | Mascot appears on the jumbotron or bangs on the glass |
| **Network Event tie-ins** | Some arenas: mascot leads the event (e.g. the Dockrats' rat swings from the crane) |

- Mascots get knocked down and limp off (no deaths — they're staff; gore off for mascots).
- Mascots are never targeted by AI on purpose (AI only hits them if they're in the way).
- Setting: **Mascots on Ice: Off / Rare (default) / Often**.
- Every RHL team gets a mascot too (e.g. Ironworkers' "Rusty," Dockrats' "The Rat," Butchers' "Cleaver," Wardens' "Officer Cuffs," High Rollers' "Lucky Chip").

---

## 8. Roster
- Fill with: **custom players**, **auto-generated players** (by team style), **free agents**, or **duplicate a roster** from an RHL team.
- Stars can't be copied, but can be added through Franchise trades/free agency — or edited roster files (Edit Player).
- Set lines, captain/alternates, starting goalie and backup.
- **Auto-fill** button for empty slots.

---

## 9. Team Style (AI tactics profile)
Sliders that shape how AI-controlled players on your team behave (uses `AI.md` style profiles):
- Aggression · Forecheck intensity · Fight frequency · Discipline · Item usage · Speed vs. physical · Goalie protection (Bodyguard)

---

## 10. Network Approval (save screen)
- Dale and Knuckles react to your team on *Redline Live*: logo reveal, jersey turntable, arena flyover, name callout.
- Knuckles gives a grim one-liner based on choices ("Pink jerseys in a blood league. Bold.").
- Save → choose: **Exhibition library**, **Franchise expansion team**, or both. Export as a file.

---

## 11. Franchise Integration
- Add your team as an **expansion team** when starting a Franchise (league grows to 9–12 teams).
- **Expansion Draft (DECISION: yes):**
  - Each existing team **protects** a list (default: 7 skaters + 1 goalie; setting: 5/7/9 skaters).
  - Stars can be protected automatically (setting: **Protect Stars: On / Off**).
  - You pick **one unprotected player from each team** (broadcast-styled draft board, Dale & Knuckles commentary).
  - Fill the rest with custom players, free agents, or auto-generated players.
  - Co-op franchise: both owners alternate picks (or co-sign each pick).
- Your custom arena becomes your home arena; upgrades in Franchise modify it.

---

## 12. Tech Notes
- **Logo stored as data**, not images: list of layers (shape ID, transform, colors, effects, text, filters). Tiny files, re-renders at any resolution.
- Logos rendered to **Render Targets** at needed sizes (jersey, ice, jumbotron) and cached as textures for gameplay.
- Jerseys: shared jersey mesh with UV regions for chest/shoulders/numbers/nameplate; **material layers** for colors, stripes, wear, blood.
- Center ice & boards: decal/material slots on the shared rink core.
- Text: font atlases; warping done in the logo render pass.
- Contrast check uses color-difference math against all other teams + dark-lighting simulation.
- Team file = JSON with embedded logo data, uniforms, arena settings, presentation choices, roster references.

---

## 13. Build Order
1. Identity + colors + simple uniform (base colors) — enough to play as a custom team
2. Logo Editor core: layers, shape library (starter set), transforms, colors
3. Text tool + effects + grit filters
4. Jersey designer (stripes, numbers, nameplate, home/away/alt)
5. Logo variants + live previews (jersey, ice, helmet, jumbotron)
6. Presentation (horn, music, chant, mascot, jumbotron intro)
7. Arena customization (shell, hazards, ice, boards, banners)
8. Roster tools + Team Style
9. Network Approval segment + export/import
10. Franchise expansion + expansion draft
11. Expand shape library over time

---

## Decisions (Oct 2026)
- Logo layers: **32** (expand later if needed).
- **Mascots come onto the ice sometimes** (Rare by default; see §7).
- **Expansion Draft: yes** (see §11).
