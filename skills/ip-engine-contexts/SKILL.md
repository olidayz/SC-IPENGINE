---
name: ip-engine-contexts
description: IP Engine creative contexts and toggles for Spacecadet IP development. Provides taste filtering (12 principles with PASS/FAIL diagnostics), Spacecadet brand calibration (4 dimensions), Alien strangeness dial (1-10), speculative tech seeds (2,452 seeds), and film/TV reference library (350+ films, 60+ shows). Load these contexts before any IP Engine creative generation task. Use when creating IP concepts, world-building, character development, visual direction, or evaluating creative output quality.
---

# IP Engine — Contexts & Toggles

The contexts layer configures how all IP Engine output feels, thinks, and filters. Contexts are lenses, not skills — they shape perspective and quality rather than performing discrete tasks.

---

## Available Contexts

| Context | File | Purpose | Default State |
|---------|------|---------|---------------|
| **Taste Profile** | `CTX-taste-profile.md` | Quality filter across all media — what passes, what fails, collision mode for mass × taste | **Always on** |
| **Spacecadet Brand** | `CTX-spacecadet-brand.md` | Four-dimension amplifier (Sci-Fi, Surreal, Spiritual, Satiraverse) + tech seeds | **Always on** |
| **Alien** | `CTX-alien.md` | Strangeness calibrator — dial 1-10, pushes beyond category conventions | **On at Stage 1, optional elsewhere** |

### Reference Libraries

| Reference | Location | Loaded By |
|-----------|----------|-----------|
| **Film-TV References** | `references/film-tv-references.md` | Taste Profile — when selecting visual/tonal comparables |
| **Speculative Tech Seeds** | `references/speculative-tech-seeds/` | Spacecadet Brand — when building world infrastructure |

### Loading Priority

When multiple contexts are active, they resolve in this order:

```
Taste Profile (quality floor — nothing passes that fails this)
    ↓
Spacecadet Brand (dimension amplification — make it more ours)
    ↓
Alien (strangeness push — make it weirder)
```

---

## How to Load Contexts

### At Session Start

Read this file first. Then, based on which pipeline stage you're entering:

1. Read the relevant `CTX-*.md` files per the routing table
2. Note which reference libraries may be needed
3. Only load reference files (film-tv, tech seeds) when actively needed — don't pre-load

---

## Anti-Patterns

| Don't | Why |
|-------|-----|
| Load all contexts at all stages | Context overload dilutes focus |
| Load tech seeds without a territory | 2,452 seeds with no filter = noise |
| Apply Worldbuilder at Stage 1 | Too early — ideation needs speed, not depth |
| Forget Collision Mode | If it doesn't target specific vision → mass outcome, it's not Spacecadet IP |

---

## Quick Start

**Starting a new IP concept?**
1. Read `SKILL.md` (this file)
2. Read `CTX-taste-profile.md`
3. Read `CTX-spacecadet-brand.md`
4. Set Alien dial (default: 7)
5. Begin at Stage 1 with these three contexts active
6. Add Worldbuilder when entering Stage 2
7. Load tech seeds only when the world needs infrastructure

---

## File Index

```
ip-engine-contexts/
├── SKILL.md                            ← You are here (orchestrator)
├── CTX-taste-profile.md                ← Quality filter (always on)
├── CTX-spacecadet-brand.md             ← Brand dimensions + tech seed routing
├── CTX-alien.md                        ← Strangeness calibrator
└── references/
    ├── film-tv-references.md           ← 350+ films, 60+ TV shows by genre
    └── speculative-tech-seeds/
        ├── SEEDS.md                    ← Seed routing + transformation logic
        ├── seeds_body_life.md          ← 503 seeds: body, enhancement, death
        ├── seeds_mind.md               ← 170 seeds: intelligence, identity, memory
        ├── seeds_space_time.md         ← 44 seeds: dimensions, time, stasis
        ├── seeds_world_environment.md  ← 431 seeds: infrastructure, materials, cities
        ├── seeds_society_control.md    ← 344 seeds: governance, surveillance, economy
        ├── seeds_transport_movement.md ← 500 seeds: vehicles, teleportation, flight
        └── seeds_machines_weapons.md   ← 460 seeds: robots, AI, weapons, defense
```
