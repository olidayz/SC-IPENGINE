# SC-IPENGINE

A six-stage pipeline for generating, developing, and producing creative intellectual properties at scale. Built as a repeatable skill system for Claude — each stage produces outputs that feed into the next.

## Pipelines

### Full Pipeline (Franchise-Scale IP)
```
1-IDEAS → 2-WORLDS → 3-STORIES → 4-VIS-DEV → 5-SCENES → 6-SHOTS → Production
                                      ↑
                              Style Lock → VLD → Characters + Locations → Casting
                                                                            ↓
                                                            Name Registry + Prompt Anchors
```

### Short-Form Pipeline (Viral Content)
```
1-IDEAS → spark selected → SHORT-FORM → Concept Lock → Production Prompts → Generate
```
Formats: Stills, Loops (3-5s), Hooks (5-15s), Carousels, Micro-Trailers, Character Intros.
Can also run post-pipeline on a completed IP.

### Stage 1: IDEAS — Spark Generation
Generate 30-50+ IP concepts from any subject using 8 ideation families and 73 lenses. Each spark is a title + paragraph. Includes thumbnail visual hook generation.

### Stage 2: WORLDS — World Building
Expand a selected spark into a franchise-scale world: core identity, factions, characters, objects, history, conflicts, franchise architecture.

### Stage 3: STORIES — Story Development
Find narratives inside completed worlds. 5 prompt families generate 10-12 story seeds, developed into full Story Windows via 5 Sauce Mothers.

### Stage 4: VIS-DEV — Visual Development
Define the visual language: Visual Language Document (art direction rules), character visual packages, location visual packages.

### Stage 5: SCENES — Scene Generation
Generate 250+ scene ideas across 5 invocations: Extract + Expand, Generate + Invent, Weird Territory, Participation, Counter-Narrative.

### Stage 6: 6-SHOTS — Production Assets
Generate production-ready image and video prompts:
- **6a: Shot Prompts** — JSON image prompts with locked Scene Template system, 10 variations per shot
- **6b: Character Sheets** — Turnaround reference images (16:9 landscape, white background)
- **6c: Motion** — Video prompts from selected stills (camera movement + subject action + environmental motion)

Reference libraries:
- **Shot Taxonomy** — 164 tagged shot types across 12 categories
- **Camera Movement Taxonomy** — 134 tagged movements across 10 categories

### Contexts
Creative filters loaded before any generation:
- Taste profile (12 principles)
- Spacecadet brand calibration (4 dimensions)
- Alien strangeness dial (1-10)
- Speculative tech seeds (2,452 seeds)
- Film/TV reference library (350+ films, 60+ shows)

## Repo Structure

```
skills/
├── 1-ideas-titles-thumbs/     ← Stage 1: Spark generation
├── 2-worlds/                   ← Stage 2: World building
├── 3-stories/                  ← Stage 3: Story development
├── 4-vis-dev/                  ← Stage 4: Visual development
│   ├── 4-style-lock.md        ← Style/medium selection
│   ├── 4d-casting.md          ← Character casting (5 variations → lock)
│   └── references/
│       └── style-directions.md ← 18 mediums + 35 aesthetics
├── 5-scene-builder/            ← Stage 5: Scene generation
│   └── references/
├── 6-shots/                    ← Stage 6: Production assets
│   ├── 6-settings.md          ← Set sheets + prop registry
│   └── references/
│       ├── shot-taxonomy.md    ← 164 tagged shot types
│       └── camera-movements.md ← 134 tagged camera movements
├── short-form/                 ← Alt pipeline: viral short-form content
│   ├── sf-concept.md          ← Concept lock (format + hook + viral mechanic)
│   └── sf-prompt.md           ← Production prompts by format
└── ip-engine-contexts/         ← Creative contexts & filters
    └── references/
        └── speculative-tech-seeds/
```

## Usage

Each skill folder contains a `SKILL.md` router that describes when and how to invoke the skill. Load the skill files into Claude as project knowledge or user skills.

### Production workflow (Stage 6):
```
VLD approved → 6b Character Sheets → 6a Shot Prompts → Select best → 6c Motion Prompts → Generate
```

### Key rules:
- All image prompts output as JSON
- Medium locked per scene (set in VLD)
- Scene Template system: locked fields copy-pasted verbatim, only camera/lens/light varies
- Renderability rule: no psychology, only physics in all descriptions
- Light consistency: interior and exterior must agree on sun position, time of day, shadow direction
- Character sheets generated before scene shots

## Built by
Spacecadet × Claude
