# Technical Specification — Best Wee Friends

*Last updated: 2026-09-26*

---

## Table of Contents

1. [Tech Stack](#tech-stack)
2. [Project Structure](#project-structure)
3. [Render Pipeline & Cel-Shading](#render-pipeline--cel-shading)
4. [Blender → Unity Pipeline](#blender--unity-pipeline)
5. [Audio System](#audio-system)
6. [Platform Targets](#platform-targets)
7. [Windows Build from Mac](#windows-build-from-mac)
8. [Version Control — Git + LFS](#version-control--git--lfs)
9. [Learning Path](#learning-path)

---

## Tech Stack

| Tool | Version | Role |
|------|---------|------|
| Unity | 6000.3.11f1 (Unity 6) | Engine |
| Blender | 5.1.2 | 3D modelling, rigging, animation |
| URP | Bundled with Unity 6 | Render pipeline |
| Toony Colors Pro | Asset Store (latest) | Base cel-shading |
| Unity ShaderGraph | Bundled with URP | Shader customisation (later) |
| Unity Audio Mixer | Bundled | Adaptive music (calm/combat) |
| Git + Git LFS | — | Version control |

---

## Project Structure

```
bestweefriends/
├── Game/                        # Unity project root
│   ├── Assets/
│   │   ├── Art/                 # Imported FBX/textures from Blender
│   │   │   ├── Characters/
│   │   │   ├── Environment/
│   │   │   └── FX/
│   │   ├── Audio/
│   │   │   ├── Music/
│   │   │   └── SFX/
│   │   ├── Materials/           # Unity materials & shaders
│   │   ├── Prefabs/
│   │   ├── Scenes/
│   │   │   └── 01_Tulum/        # Vertical slice scene
│   │   └── Scripts/
│   │       ├── Player/
│   │       ├── Pashmina/
│   │       ├── Combat/
│   │       ├── Enemies/
│   │       └── Audio/
│   ├── Packages/
│   └── ProjectSettings/
├── Art/                         # Blender source files (.blend) — NOT imported directly
│   ├── Characters/
│   │   ├── Protagonist/
│   │   └── Pashmina/
│   ├── Environment/
│   │   └── Zone01_Jungle/
│   └── FX/
├── docs/
│   ├── GDD.md
│   ├── TECH_SPEC.md
│   ├── ART_BIBLE.md
│   └── LEVELS/
│       └── 01_tulum.md
├── .gitignore
├── .gitattributes               # Git LFS rules
└── README.md
```

**Rule:** Blender `.blend` files live in `Art/`. Unity never imports `.blend` directly — only exported `.fbx` files land in `Game/Assets/Art/`.

---

## Render Pipeline & Cel-Shading

### Why URP
- Unity's Universal Render Pipeline is the modern standard for stylised/cel-shaded games
- Lower overhead than HDRP, better mobile/PC compatibility, works with Toony Colors Pro
- All new projects should use URP — do not use Built-in pipeline

### Phase 1 — Toony Colors Pro (Asset Store)
Buy and import [Toony Colors Pro 2](https://assetstore.unity.com/packages/vfx/shaders/toony-colors-pro-2-8105). This is the fastest path to Wind Waker-style shading.

Key settings to achieve Wind Waker look:
- **Ramp shading:** 2–3 step hard ramp (not smooth gradient)
- **Outline pass:** World-space outline, ~0.5–1.5 thickness. Darker than the fill, not pure black.
- **Specular:** Flat/toon specular, small hard highlight — not metallic PBR
- **Shadow colour:** Tinted (cool/blue tint in dark zones, warmer in light zones) — adjust per zone

### Phase 2 — ShaderGraph Customisation
Once comfortable with Unity, extend Toony Colors Pro by:
- Adding a **world brightness** parameter that shifts shadow colour and ramp tint per zone
- Adding pashmina-specific shader (fabric shimmer, colour shift by world state)
- Custom outline thickness per object category (thicker on characters, thinner on background props)

Do not attempt Phase 2 until the vertical slice is complete.

---

## Blender → Unity Pipeline

### General Rules
- Model and rig in Blender
- Export as **FBX** to `Game/Assets/Art/[category]/`
- Re-import / re-export when the source changes
- Never move or rename an FBX after Unity has assigned materials to it — Unity ties materials to import paths

### FBX Export Settings (Blender)
Open the FBX exporter in Blender (`File → Export → FBX`):

| Setting | Value | Why |
|---------|-------|-----|
| **Scale** | 0.01 | Blender metres → Unity units (1 unit = 1 metre in Unity) |
| **Apply Transform** | ✅ Yes | Clears Blender's transform before export |
| **Forward** | -Z | Unity uses a left-handed Y-up coordinate system |
| **Up** | Y | Same reason |
| **Mesh → Smoothing** | **Face** | Keeps hard-edge cel-shaded look. Do NOT use Edge or Normals — they can break outlines. |
| **Mesh → Triangulate Faces** | ✅ Yes | Unity's importer handles this, but explicit is safer |
| **Armature → Only Deform Bones** | ✅ Yes | Reduces rig noise in Unity |
| **Bake Animation** | ✅ Yes (if exporting animation) | Bakes constraints into keyframes |

### Texture Export
- Export textures as **PNG** (not JPEG — avoid compression artefacts on flat cel-shaded colour)
- Cel-shading minimises texture complexity: you often need only a **diffuse/albedo** map and a **normal** map
- Do NOT use PBR roughness/metallic maps — they're wasted on a toon shader
- Name convention: `[AssetName]_Diffuse.png`, `[AssetName]_Normal.png`

### Iteration Workflow
1. Edit in Blender
2. Export FBX to `Game/Assets/Art/[category]/[AssetName].fbx`
3. Unity auto-reimports on focus (or press `Ctrl+R` in Project window)
4. Reassign material if first import; material persists on subsequent re-imports

---

## Audio System

### Phase 1 — Unity Audio Mixer (current)
Two snapshot states per zone:
- `Calm` — ambient layer only
- `Combat` — full track layer crossfades in

**Implementation steps (when building the vertical slice):**
1. Create an `AudioMixer` asset (`Audio/MixerMain.mixer`)
2. Add two snapshots: `Calm`, `Combat`
3. Trigger `AudioMixer.TransitionToSnapshots()` on enemy detection / enemy clear
4. Crossfade time: ~1.5 seconds feels natural for EDM

### Phase 2 — FMOD (future)
Migrate when the system needs more than 2 states per zone, or when zone transitions need musical bridging. FMOD Studio is free for indie projects under $200k revenue.

### Placeholder Music
Use royalty-free EDM from [Pixabay](https://pixabay.com/music/) or [Uppbeat](https://uppbeat.io/) that matches zone tone. Do not use copyrighted tracks in early builds — they will break YouTube/Twitch demos and Steam review.

| Zone | Placeholder search terms |
|------|--------------------------|
| 1 — Jungle | "dark techno", "dark bass", "industrial ambient" |
| 2 — Desert | "hard techno", "driving bass" |
| 3 — Ice | "ambient minimal", "dark ambient", "ice" |
| 4 — Forest | "uplifting trance", "progressive house", "euphoric" |

---

## Platform Targets

| Platform | Status | Notes |
|----------|--------|-------|
| macOS | Dev only | Unity editor, Blender, all tools run natively |
| Windows | Primary release | Cross-compile from Mac — see below |
| Steam Deck | Stretch goal | Proton compatibility; test post-launch |
| Console | Not in scope | Requires devkit/publisher access |

---

## Windows Build from Mac

Unity 6 can produce a Windows `.exe` directly from macOS. No Windows machine required to *build*. Testing the Windows build natively requires either a Windows machine or a VM.

### Building
1. In Unity: `File → Build Settings`
2. Switch platform to **Windows, Mac, Linux**
3. Target: **Windows 64-bit**
4. Click **Build** — Unity cross-compiles on Mac

### Testing Options (cheapest first)
| Option | Cost | Notes |
|--------|------|-------|
| **GitHub Actions** | Free (up to limits) | Upload a build, let CI run it and screenshot it. Janky but free. |
| **UTM / Parallels + Windows ISO** | ~$0–$100 | Run Windows VM on Mac. Needs a Windows licence (free trial available). UTM is free; Parallels is paid but slicker. Recommended for M-series Macs. |
| **Shadow PC / GeForce NOW** | ~$12–$30/mo | Cloud Windows PC, stream to Mac. Good for play-testing if you don't have a VM. |
| **A cheap Windows PC** | $300+ | The long-term answer if this ships commercially |

**Recommended now:** Install [UTM](https://mac.getutm.app/) (free) + Windows 11 ARM ISO (free from Microsoft). It runs well on Apple Silicon and lets you natively test the Windows build.

---

## Version Control — Git + LFS

Unity and Blender projects generate large binary files. Git without LFS will bloat the repository.

### Setup (run once)

```bash
# In the project root
git init
git lfs install

# Track large binary types
git lfs track "*.blend"
git lfs track "*.fbx"
git lfs track "*.png"
git lfs track "*.jpg"
git lfs track "*.wav"
git lfs track "*.mp3"
git lfs track "*.ogg"
git lfs track "*.psd"
git lfs track "*.unitypackage"
git lfs track "Game/Assets/**/*.asset"   # Unity serialized assets

git add .gitattributes
git add .gitignore
git commit -m "init: project scaffold with Git LFS"
```

### `.gitignore` highlights
The `.gitignore` at the root excludes:
- `Game/[Ll]ibrary/` — Unity's local cache, regenerated automatically
- `Game/[Tt]emp/` — Unity temp files
- `Game/[Bb]uild/` — Build output (track build artefacts elsewhere)
- `Game/[Ll]ogs/` — Unity editor logs
- `Art/**/__pycache__/` — Blender Python cache

See `.gitignore` in the repo root for the full list.

---

## Learning Path

Recommended order for a Unity/Blender beginner working toward the vertical slice:

### Month 1 — Foundations
1. **Unity:** Complete Unity's official [Junior Programmer pathway](https://learn.unity.com/pathway/junior-programmer) (free)
2. **Blender:** Complete [Blender Guru's Donut tutorial](https://www.youtube.com/playlist?list=PLjEaoINr3zgEPv5y--4MKpciLaoQYZB1Z) — the standard beginner path
3. Goal: You can make a cube move in Unity. You can model and texture a simple object in Blender.

### Month 2 — Core Systems
1. Build basic player locomotion in Unity (CharacterController or Rigidbody)
2. Build a simple third-person camera
3. Model [PROTAGONIST] in Blender (low-poly draft — correct shape, not final detail)
4. Export [PROTAGONIST] to Unity and get the URP cel-shader on her

### Month 3+ — Vertical Slice
Build the vertical slice scene piece by piece. Start with greybox (Unity ProBuilder primitives) — get the gameplay feeling right before investing in final art.

**Do not model final art before the greybox feels good.**
