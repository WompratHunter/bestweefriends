# Art Bible — Best Wee Friends

*Last updated: 2026-09-26*

---

## Visual Identity

**Best Wee Friends** is cel-shaded in the tradition of *The Legend of Zelda: Wind Waker* — bold outlines, flat colour fills with hard-edged shadow steps, minimal texture detail. The art should read clearly at a distance and be expressive rather than realistic.

This is **not** hyperrealistic. Every element should feel like it was drawn by someone who loves festivals, jungles, and late-night neon.

---

## Reference Games

| Game | What We Borrow |
|------|---------------|
| *Wind Waker* | Art direction, colour palette per zone, outline weight, 2-step shadow ramp |
| *Sword and Sea* | Traversal animation feel, how the "sail" (our pashmina) fills and moves |
| *Hi-Fi Rush* | How music and world energy interact visually |
| *Sable* | Desert zone reference: vast, warm, slightly mysterious |

---

## Cel-Shading Principles

### Shadow Ramp
- **2 steps** — lit colour + one shadow tone. Occasionally a third mid-tone for characters.
- Shadow colour is NOT grey. It is always a **tinted shadow**:
  - Zone 1 (Jungle): shadow is cool blue-purple (feels damp, oppressive)
  - Zone 2 (Desert): shadow is deep ochre-orange (scorched)
  - Zone 3 (Ice): shadow is pale lavender-white (cold, ghostly)
  - Zone 4 (Forest): shadow is warm amber-green (alive, glowing)

### Outlines
- World-space outlines on all characters and significant props
- **Characters:** 1.5–2px equivalent thickness
- **Environment props:** 0.75–1px (recede behind characters visually)
- **Background elements:** No outline or very faint — forces depth without fog
- Outline colour: dark version of the object's dominant hue, never pure black (feels flat)

### Textures
- Flat colour fills. Texture maps used sparingly — only where surface variation adds read (bark, stone, fabric weave).
- No PBR roughness/metallic. Toon specular only: small, hard, white highlight.
- Avoid gradients in diffuse textures — let the shader do the lighting work.

---

## Colour Palette

### Zone 1 — Jungle (Dark)
| Role | Hex | Description |
|------|-----|-------------|
| Sky | `#1a1a2e` | Near-black night blue |
| Foliage lit | `#2d5a27` | Dark forest green |
| Foliage shadow | `#1a3318` | Near-black green |
| Stone | `#4a4040` | Warm grey-brown |
| Fog | `#2a2a3e` | Blue-black haze |
| Pashmina (muted) | `#8b6b9e` | Desaturated purple — alive but suppressed |
| Spirit (dark) | `#1a0a2e` | Deep indigo-black |
| Spirit glow | `#4a2080` | Violet energy |

### Zone 4 — Electric Forest (Light) — Target Endpoint
| Role | Hex | Description |
|------|-----|-------------|
| Sky | `#1a0a3e` | Deep night but rich, warm |
| Tree lights | `#f0c040` | Warm gold |
| Ground | `#3d6b3d` | Vibrant grass |
| Pashmina (full colour) | `#ff6b9e` | Hot pink-magenta, fully saturated |
| Ambient light | `#a060ff` | Purple-blue festival glow |

*Intermediate zones: blend between Zone 1 and Zone 4 as a gradient across the game's arc.*

---

## Character Design

### [PROTAGONIST]

**Body:**
- Small, slight frame. Not athletic-hero proportions — relatable, human.
- Medium-length blonde hair, slightly tousled (she woke up in a bog)
- Slightly stylised proportions: head slightly larger than realistic, eyes expressive

**Outfit (modelling priority order):**
1. Baggy cargo/festival pants — relaxed fit, slight taper at ankle. Primary colour TBD.
2. Mesh black crop top — a mesh layer over a coloured bandeau
3. Colourful bandeau underneath the mesh — warm colours (orange, pink, yellow)
4. Right wrist: **kandi** — stack of plastic bead bracelets. Model as a chunky cylinder of colour blocks.
5. Left wrist: **festival wristband** — thin, yellow/orange, slightly ratty
6. When idle: pashmina draped loosely over shoulders

**Face style:**
- Wind Waker-adjacent: large expressive eyes, simple nose, defined mouth
- Eyebrows do the heavy lifting for emotion

**Poly budget (vertical slice):**
- Character mesh: ~3,000–5,000 tris (low-poly is correct for this style)
- No LOD system for vertical slice

**Rig:**
- Standard humanoid rig compatible with Unity's Humanoid avatar system
- Finger bones optional for vertical slice (kandi can be a static mesh attachment)
- Facial rig: blend shapes for at minimum Idle, Effort, Fear, Joy

### The Pashmina

**Form:**
- A long rectangular fabric — roughly 200cm × 80cm in world scale
- No anatomy. No face. No eyes. Just fabric.
- Deforms and animates to express personality

**Key animation states:**
| State | Behaviour |
|-------|-----------|
| Resting (on shoulders) | Slight gentle drift, like a breeze |
| Alert | Pulls taut, rises slightly |
| Happy/safe | Ripples in loose waves |
| Danger | Snaps and whips |
| Glide mode | Fills out flat, lifts at the edges like a kite |
| Attack | Rapid crack — like a whip |

**Shader:**
- Toony Colors Pro with a custom fabric shimmer pass (Phase 2)
- Colour shifts with world brightness — muted purple in dark zones, hot pink/magenta at full brightness
- Slight translucency on the fabric (alpha on the shader, not full transparency)

**Simulation:**
- Unity Cloth component for idle/resting drape
- Switched off during gameplay — animation takes over during glide and combat (cloth sim + animation = chaos)

---

## Environment Design

### Zone 1 — Jungle Vertical Slice

**Mood board keywords:** Ancient, oppressive, overgrown, festival-ruined, pre-dawn dark

**Key asset list (vertical slice):**
| Asset | Priority | Notes |
|-------|----------|-------|
| Large stone head (mossy) | P0 | Landmark. Tulum-inspired. Covered in vines. Ancient. |
| Dense jungle trees | P0 | Mid-poly. Flat colour leaves (billboard or simple planes). |
| Ground (bog → trampled grass) | P0 | Two material zones — muddy bog, trampled festival ground |
| Stone pyre (cracked) | P0 | End-of-zone landmark. Split down the middle. Ancient stone. |
| Jungle undergrowth | P1 | Low poly ferns, roots |
| Festival debris | P1 | A crumpled tent, dead string lights, a lost shoe |
| Fog VFX | P1 | Particle system, low, ground-hugging |

**Scale reference:** Stone head should feel *massive* — player can walk under its chin. It is a landmark, not a prop.

**Environmental storytelling:**
The festival debris is subtle — you see it and understand that people were here, and they're gone. Don't overdo it. One tent. A few lights. A wristband on the ground.

### Lighting
- Directional light: nearly horizontal, cold blue-white — perpetual pre-dawn
- Ambient: near-black, cool, very low intensity
- Point lights from: spirit glow (purple), any remaining dead string lights (warm but flickering)
- After spirits are defeated: light sources warm slightly (subtle, not dramatic) — the world brightening starts here

---

## Modelling Conventions

### Naming (Blender and Unity)
```
[Zone]_[Category]_[AssetName]_[Variant]

Examples:
Z1_ENV_JungleTree_A
Z1_ENV_StonePyre
Z1_CHAR_Protagonist
Z1_PROP_FestivalTent
SHARED_CHAR_Pashmina
```

### Polygon Budget
| Category | Poly budget (tris) |
|----------|-------------------|
| Hero character | 3,000–5,000 |
| NPC / enemy | 1,000–2,000 |
| Large landmark | 2,000–4,000 |
| Medium prop | 200–800 |
| Background tree | 100–300 |
| Ground plane (per tile) | 100–400 |

Cel-shading tolerates lower poly counts than PBR because shape reads from outlines, not light.

### UV Mapping
- UV unwrap every mesh — even if the diffuse is flat colour, the normal map and any hand-painted detail needs clean UVs
- Use UV islands: keep related parts together, maximise UV space
- Lightmap UV channel (UV2) needed if Unity baked lighting is used later

---

## Blender Export Checklist

Before every FBX export:
- [ ] Apply all transforms (`Ctrl+A → All Transforms`) in Blender
- [ ] Triangulate modifier added (or **Triangulate Faces** checked in export)
- [ ] Scale set to 0.01 in export
- [ ] Forward: -Z, Up: Y
- [ ] Smoothing: **Face** (not Edge, not Normals)
- [ ] Animation baked if exporting with animation
- [ ] File saved to `Game/Assets/Art/[category]/[AssetName].fbx`
- [ ] Textures exported to same folder as `[AssetName]_Diffuse.png`

---

## Unity Import Checklist

After importing FBX:
- [ ] Set **Normals** to Import (not Calculate) in the model import settings
- [ ] Set Rig to **Humanoid** (characters) or **Generic** (props)
- [ ] Set **Smoothing Angle** to match Blender's (30°)
- [ ] Assign Toony Colors Pro material in the Materials tab
- [ ] Set outline thickness in material settings
- [ ] Verify scale in scene (1 Blender unit = 1 Unity metre after 0.01 export)
