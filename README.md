# Best Wee Friends

> A 3D cel-shaded action-adventure. A lost festival-goer, her magical pashmina, and a dark jungle that slowly learns to love her back.

## Project Structure

```
bestweefriends/
├── Game/           # Unity 6 project (URP, cel-shaded)
├── Art/            # Blender source files (.blend)
│   ├── Characters/
│   ├── Environment/
│   └── FX/
├── docs/
│   ├── GDD.md          # Game Design Document — start here
│   ├── TECH_SPEC.md    # Technical decisions and pipeline
│   ├── ART_BIBLE.md    # Visual direction and Blender export guide
│   └── LEVELS/
│       └── 01_tulum.md # Level 1 design + vertical slice scope
└── README.md
```

## Key Docs

| Doc | What it covers |
|-----|---------------|
| [GDD](docs/GDD.md) | Story, mechanics, world, enemies, music system |
| [Tech Spec](docs/TECH_SPEC.md) | Unity setup, render pipeline, Blender pipeline, audio |
| [Art Bible](docs/ART_BIBLE.md) | Visual style, protagonist design, export settings |
| [Level 1 — Tulum](docs/LEVELS/01_tulum.md) | Vertical slice scope and layout |

## Tools

- **Engine:** Unity 6 (6000.3.11f1)
- **3D / Animation:** Blender 5.1.2
- **Render Pipeline:** URP with Toony Colors Pro (cel-shading)
- **Platform:** macOS (dev) → Windows (release)
- **Version Control:** Git + Git LFS (see TECH_SPEC.md for LFS setup)
