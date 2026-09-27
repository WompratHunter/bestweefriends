# Level 01 — The Jungle (Tulum)

*Zone 1 · Vertical Slice · Last updated: 2026-09-26*

---

## Overview

The first level is the vertical slice — the proof that every core system works together. It is small, dense, and focused. It does not try to be a full level; it tries to be a perfect moment.

**Player experience arc:** Disoriented → afraid → empowered → hopeful

**Duration target:** ~5–10 minutes of play

---

## Narrative Beats

| # | Beat | What Happens |
|---|------|-------------|
| 1 | **Wake-up** | [PROTAGONIST] comes to face-down in a fog-covered bog. Muffled sound. Blurry vision clears. She's alone. |
| 2 | **The pashmina finds her** | The pashmina — draped limp over her back — slowly rises. It wraps itself around her wrists. The first moment of warmth in the level. |
| 3 | **The forest speaks** | Distant movement in the trees. The fog thickens. The music shifts. |
| 4 | **First contact** | A shadow spirit rushes from the undergrowth. Combat begins. |
| 5 | **Earning the glide** | After defeating the first wave — or mid-combat — a beat where the pashmina demonstrates it can lift her (tutorial prompt or environmental necessity). |
| 6 | **The stone head** | She passes the large mossy stone head. Ancient, enormous. A silent witness. The jungle is older than whatever festival happened here. |
| 7 | **The clearing** | She breaks into the trampled grassy clearing. The density lifts. The sky is visible. The stone pyre is ahead. |
| 8 | **Final wave** | Last group of spirits attacks at the pyre. Hardest fight in the slice. |
| 9 | **The brightening** | The pyre's crack emits a warm glow as the final spirit disperses. Ambient colour shifts — the first hint of warmth. |
| 10 | **The glide out** | [PROTAGONIST] grabs the pashmina, lifts off, and glides past the pyre. The desert stretches ahead in the distance, hazy and golden. Fade to black / end of slice. |

---

## Layout

```
[BOG START]
     |
  dense fog, muddy ground, roots
  no clear path — follow the light/sound
     |
[STONE HEAD]  ← landmark, ancient, massive
     |
  thinner trees, signs of festival debris
  (a tent, dead string lights, a wristband)
     |
[FIRST COMBAT AREA]
  small clearing in the jungle
  spirits attack from multiple directions
     |
  light opens slightly after combat
     |
[TRAMPLED CLEARING]
  grass is worn flat — people were here
  festival debris increases subtly
     |
[STONE PYRE] ← end landmark, cracked down the middle
  final combat encounter here
  pyre cracks glow after spirits defeated
     |
[GLIDE SEQUENCE]
  pashmina carries her over the pyre
  desert visible ahead
[END]
```

---

## Environment Spec

### Bog (Start Area)
- Muddy, waterlogged ground — dark brown/black
- Ground fog particle system — low, dense, barely see the floor
- Roots and low vegetation block easy movement — player must navigate
- Lighting: near-zero. Only ambient cool blue. Very dark.
- Sound: ambient — wet, heavy, insect sounds muffled

### Jungle Path (Mid)
- Dense tree canopy — almost no sky visible
- Occasional dead string lights hanging from branches (cold, flickering, wrong)
- Festival debris: one crumpled tent, a scattered drink container, a wristband on the ground. Subtle.
- The stone head: position on the LEFT side of the path so it's hard to miss but doesn't block traversal
  - Scale: head is ~6 metres tall from chin to crown
  - Covered in thick moss and vines — the stone face is partially obscured but readable
  - Expression: neutral, ancient. Not threatening. Just watching.

### First Combat Clearing
- Small — ~15m diameter
- Enough space to dodge-roll and use the pashmina whip
- 3 shadow spirits in first wave (patrol → aggro)
- After combat: single point light source flickers on (a dead stage light comes to life briefly). Mood lift, not full brightness.

### Trampled Clearing (Pre-Pyre)
- Open sky visible — first time in the level
- Sky: still dark, but you can see stars
- Ground texture transitions from forest mulch to flattened grass
- Ambient light: very slightly warmer than the jungle sections
- Spirit count: 0 initially — the calm before the stone pyre

### Stone Pyre
- Dimensions: ~4m wide, ~3m tall, two roughly-equal halves with a crack from top to bottom
- The crack: dark void. Slightly backlit with deep purple energy — it's sealed, but barely.
- After the final spirits are defeated: crack pulses warm amber/gold from inside. Not fully open — just alive.
- This is the level's emotional climax.

---

## Enemy Encounter Design

### Spirit Type A — Rusher
- Shadow/smoke form, low to the ground
- Behaviour: patrol → rush on detection (direct line charge)
- Attack: collision damage on rush, brief stun window after missing
- Defeat: dispel on any successful pashmina attack or 2 body hits
- Count in vertical slice: 5 total (spread across two waves)

### Spirit Type B — Floater *(stretch goal for vertical slice)*
- Shadow/smoke form, hovers at head height
- Behaviour: circles [PROTAGONIST], telegraphs a dark energy projectile
- Attack: slow dark projectile (dodgeable)
- Defeat: 3 hits
- Count in vertical slice: 1 (final wave only, at the pyre)

### Wave Layout
| Area | Enemies | Notes |
|------|---------|-------|
| First combat clearing | 3× Rusher | Introduction to combat. Spread out, don't swarm immediately. |
| Stone pyre (final) | 2× Rusher + 1× Floater (stretch) | Harder. Use the pyre as cover and obstacle. |

---

## Music Map

| Area | Calm Layer | Combat Layer |
|------|-----------|-------------|
| Bog (start) | Dark ambient — near silence, low drone | N/A |
| Jungle path | Low murky techno pulse, very quiet | N/A |
| First combat clearing | Same pulse | Full dark techno track — heavy, driving |
| Trampled clearing | Brief silence / wind only | N/A |
| Pyre — final combat | Quiet tension | Same or heavier version of combat track |
| After pyre | A single warm musical tone — like a festival sound in the far distance | N/A |
| Glide out | The tone grows — hint of what Zone 4 will sound like | N/A |

---

## Systems Exercised

This scene must prove every core system works:

| System | Tested By |
|--------|----------|
| Locomotion (run, jump) | Navigating the bog and jungle path |
| Pashmina traversal (glide) | Tutorial moment + glide-out ending |
| Pashmina traversal (burst) | Optional during combat for dodging |
| Combat (light attack) | All enemy encounters |
| Combat (pashmina attack) | All enemy encounters |
| Dodge roll | Enemy rush attacks |
| Enemy AI (patrol + aggro) | Rusher spirits |
| Audio (calm → combat transition) | First enemy detection |
| Cel-shading | All environment + characters |
| World brightening (colour shift) | After pyre — ambient colour/light shift |

---

## Greybox → Final Art Order

Build in this order. Do not do step N+1 before step N feels right.

1. **Greybox** — ProBuilder primitives. Get the layout, pacing, and combat spacing right.
2. **Locomotion** — [PROTAGONIST] moves, jumps, and glides in the greybox. Pashmina traversal works.
3. **Combat** — Spirits spawn, patrol, aggro, and die. Combat loop works.
4. **Audio** — Calm/combat music transitions work. Footstep SFX placeholder.
5. **Lighting** — Unity lighting set up for the dark jungle mood. Colour zones working.
6. **Environment art** — Replace greybox with modelled assets (trees, ground, stone head, pyre).
7. **Character art** — Replace [PROTAGONIST] capsule with modelled + cel-shaded character.
8. **VFX** — Fog, spirit dispel effect, pyre glow.
9. **Polish** — Juice. Camera shake. Spirit sound effects. The brightening moment.
10. **Done** — The vertical slice is complete.

---

## Open Questions (for future design pass)

- [ ] Does the bog have a navigational puzzle, or is it pure atmosphere?
- [ ] What exactly triggers the pashmina to demonstrate gliding — player prompted or environmental gap?
- [ ] Do the dead festival lights play any mechanical role?
- [ ] Is the stone pyre interactive in later versions (something to unlock)?
- [ ] Exact camera behaviour during the glide-out sequence
