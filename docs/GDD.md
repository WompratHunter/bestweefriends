# Game Design Document — Best Wee Friends

*Last updated: 2026-09-26 · Status: Living document — update as decisions are made*

---

## Table of Contents

1. [Pitch](#pitch)
2. [Story](#story)
3. [Protagonist](#protagonist)
4. [The Pashmina](#the-pashmina)
5. [Core Mechanics](#core-mechanics)
6. [World Progression](#world-progression)
7. [Music System](#music-system)
8. [Enemies — The Spirits](#enemies--the-spirits)
9. [Friends You Meet](#friends-you-meet)
10. [Vertical Slice Milestone](#vertical-slice-milestone)

---

## Pitch

A lone festival-goer wakes up lost in a dark, angry jungle. She has no map, no phone, no friends — just a living pashmina that wraps itself around her in her first moment of fear. Together they fight through hostile jungle spirits, cross a burning desert, brave frozen peaks, and finally arrive at the warmth of an electric forest alive with light and music. The world gets brighter every time she wins.

**Closest references:**
- **Gameplay:** *Sword and Sea* (traversal feel) + *The Legend of Zelda: Wind Waker* (combat, art direction)
- **World:** Jungle festival culture — Tulum, Electric Forest, Burning Man, Tomorrowland — as an exaggerated caricature, never named directly

---

## Story

### Setup
[PROTAGONIST] is found face-down in a fog-covered bog, deep in a jungle that feels *wrong*. She doesn't know how she got here. The jungle is dark, the air is thick, and something is watching.

Before she can get her bearings, the pashmina — a brightly-coloured scarf she'd been wearing — pulls itself off her shoulders, wraps around her wrists, and rears up like something alive. It woke her up. It's not done yet.

Spirits rush from the undergrowth. She and the pashmina fight them off. This is the beginning.

### Central Conflict
The jungle is in pain. A massive, shapeless dark energy — the jungle's collective rage at having its peace shattered by human festivals — has turned its spirits hostile. This isn't pure evil; it's a rejection. As [PROTAGONIST] fights, connects, and earns her way through the jungle, the energy doesn't so much *lose* as it *lets go*. The world brightens not because she conquered it, but because it accepted her.

### The Arc
| Zone | Emotional State | World Tone |
|------|----------------|------------|
| 1 — Jungle (Tulum) | Fear, confusion, wonder | Dark, foggy, oppressive |
| 2 — Desert | Determination, exhaustion | Harsh, blinding, relentless |
| 3 — Ice | Isolation, grief, stillness | Frozen, quiet, eerie |
| 4 — Electric Forest | Joy, belonging, arrival | Vibrant, warm, alive |

---

## Protagonist

**Name:** TBD — placeholder `[PROTAGONIST]`

**Age:** Mid-20s

**Visual Design:**
- Small frame, medium-length blonde hair
- Baggy cargo/festival pants
- Mesh black crop top
- Colourful bandeau underneath
- Kandi bracelet on right wrist (the plastic bead bracelets traded at festivals)
- Yellow and orange festival wristband on left wrist
- The pashmina (when not in use) drapes around her shoulders

**Vibe:** Young raver who ended up somewhere she did not plan. She's not a trained fighter — she figures it out. Her combat style should feel improvised and personal, not military.

**Character Arc:**
She starts scared. She ends at home.

**Visual Arc (passive):**
Her outfit stays the same, but as the world brightens, the colour bleeds back into everything around her — and subtly, her accessories catch more light. No explicit costume change; the *world* is what transforms.

---

## The Pashmina

The first and most important "wee friend." It is not a weapon. It is not a tool. It is the game's other protagonist.

### Personality
- Never speaks
- Expresses itself through **motion** — excited rippling, hesitant pulling, urgent snapping
- Expresses itself through **colour** — muted/dark in hostile areas, vivid and warm in safe ones
- Makes sound when moving: fabric swoosh, a low musical flutter — not creature sounds, not music, just *presence*

### Traversal
Inspired by *Sword and Sea*'s fluid sailing feel — but grounded, not vast.

- **Glide:** [PROTAGONIST] grabs the pashmina's ends; it fills and lifts her, carrying her forward like a low magic carpet. Feels like surfing. Not fast by default — deliberate, wave-like rhythm.
- **Burst:** A charged dash along the glide axis. Short range, high speed, limited use (short cooldown or stamina cost). Not for covering ground — for threading gaps and dodging.
- **Not for vast distances:** Traversal is close-quarters and expressive. Large open spaces are crossed on foot; the pashmina is for obstacles, gaps, and aerial play.

### Combat
The pashmina fights alongside [PROTAGONIST]. She can use her own body (kicks, grabs, throwing objects) AND direct the pashmina as a separate attack vector.

| World State | Pashmina Combat Role |
|-------------|---------------------|
| Dark zones | Defensive — shields, parries, short-range wrap attacks |
| Brightening zones | Balanced — extended reach, can bind enemies |
| Light zones | Full offence — long-range whip, area sweeps, power strikes |

As the game progresses and the world brightens, combat gets faster, more fluid, and more powerful. This is the mechanical expression of the emotional arc.

---

## Core Mechanics

### Movement
- Run, jump, double jump (pashmina-assisted)
- Glide (pashmina)
- Burst (pashmina)
- Wall interaction TBD in later design pass

### Combat
Moderate depth — not a button-masher, not a deep combo system.

- **Lock-on target** (Wind Waker style)
- **Light attack** — fast, [PROTAGONIST]'s own fists/kicks
- **Heavy/pashmina attack** — slower, longer range, more impact
- **Dodge roll** with a timing window for parry effect
- **No skill trees for vertical slice** — unlock combat depth through story beats (earning a new pashmina mode = new move set)

### Camera
Third-person, over the shoulder. Lock-on toggles to orbital camera around target. TBD: exact camera behaviour over traversal.

---

## World Progression

### Zone 1 — The Jungle (Tulum)
*Dark, dense, oppressive. Ancient stone. Fog. Ruins of something that used to be a celebration.*

Key landmarks: massive moss-covered stone heads, collapsed stone infrastructure, remnants of festival lighting now gone dark.

Tone: Rezz, dark techno, dark bass. Heavy, low, grinding.

### Zone 2 — The Desert
*Blinding light, but not warm — harsh. Exposed. No shelter.*

Spirits here are parched, angular, aggressive. The pashmina becomes a sail.

Tone: Harder techno, industrial, relentless. Starting to feel the pull of something better.

### Zone 3 — Ice
*Stillness. Silence. The spirits here are sorrowful, not angry.*

The coldest part of the emotional arc. Something happened here. Something was lost.

Tone: Ambient, glacial. A pause before the finale.

### Zone 4 — Electric Forest (Rothbury, Michigan)
*Trees strung with light. The air hums. The world is alive.*

The final zone. Full pashmina power. The dark energy releases. The jungle — all of it, retroactively — was always capable of this.

Tone: Uplifting trance, vibey dubstep. A homecoming.

---

## Music System

Music is a **mechanic** as much as it is atmosphere.

### Adaptive Layers
Each area has a minimum of two music layers:
- **Calm layer** — ambient, minimal, environmental. Active when no enemies are present.
- **Combat layer** — full track kicks in when enemies engage. Transitions on attack detection.

Transitions are crossfaded, not abrupt. The music should feel like it was always there, waiting.

### Tonal Arc
| Zone | Music Direction |
|------|----------------|
| 1 — Jungle | Rezz-esque dark bass / murky techno |
| 2 — Desert | Hard techno / industrial |
| 3 — Ice | Ambient / glacial / near-silence |
| 4 — Forest | Uplifting trance / vibey dubstep |

### Placeholder Strategy
All music is placeholder until licensed tracks are acquired. Use royalty-free EDM tracks that match the tonal direction per zone. License target tracks are a later milestone.

### Implementation
Unity built-in Audio Mixer with audio snapshots (calm → combat transition). Migrate to FMOD when the system needs more than two states.

---

## Enemies — The Spirits

### Zone 1 Spirits (Vertical Slice)
**Form:** Shadow/smoke — dark, wispy, barely solid. They move like disturbed fog given intent. No defined anatomy. They flow.

**Behaviour (basic AI):**
- Patrol / idle when [PROTAGONIST] is not detected
- Aggro at detection range
- Rush attack (direct)
- One ranged dark-energy projectile (telegraphed)

**Defeated state:** They don't die — they *dispel*. Small bloom of colour, brief brightening of the immediate area, then gone.

### Future Zones
Enemy design per zone is its own design pass. Each zone's spirits reflect the environment (desert spirits: cracked, angular, sand-formed; ice spirits: crystalline, slow, fragile but numerous).

---

## Friends You Meet

The "wee friends" of the title. These are NPCs [PROTAGONIST] encounters along her journey. Their exact nature, number, and role in gameplay are a future design pass. Design principles:

- Each friend is tied to a zone
- Meeting them marks a narrative turning point
- They leave something behind — an ability unlock, a change in the pashmina, a moment of brightness
- None of them are playable characters in the vertical slice

The pashmina is the **first** wee friend. Everything else flows from that relationship.

---

## Vertical Slice Milestone

*See [`docs/LEVELS/01_tulum.md`](LEVELS/01_tulum.md) for full detail.*

**Goal:** One small, complete, polished section that proves every core system works together.

**Scope:**
- [PROTAGONIST] with locomotion, jump, glide, burst
- Pashmina with basic traversal and combat
- 1–2 spirit enemy types with basic AI
- One fully cel-shaded environment (jungle bog → clearing)
- Calm/combat music layer transition working
- The moment the world brightens (after defeating spirits)
- Ends: glide past the stone pyre, desert visible in distance

**Definition of done for vertical slice:**
Every system is rough but functional. The *feel* of the game is present. You can show it to someone and they understand what it is.
