---
name: 6-shots
description: "IP Engine Stage 6: Generate cinematographic shot breakdowns and image generation prompts for curated scenes from 5-SCENE-BUILDER. Takes a scene (title + hook line), decomposes it into a flexible number of shots (camera moments), then generates 10+ image generation prompts per shot varying lens/framing and style/medium. Every prompt is constrained by the world's Visual Language Document. Use when generating shots, image prompts, cinematography, shot lists, visual breakdowns, or turning scene ideas into production-ready image generation prompts. Triggers: 'generate shots', 'shot breakdown', 'image prompts', 'visualize this scene', 'shoot this', 'give me prompts for', '6-shots', 'shot list', 'production prompts'."
---

# 6-SHOTS

Turn curated scenes into shot breakdowns and image generation prompts.

## Summary

| Attribute | Spec |
|-----------|------|
| **Purpose** | Decompose scenes into shots, generate 10+ image prompts per shot |
| **Input** | Scene (title + hook) from 5-SCENE-BUILDER + VLD from 4-VIS-DEV + medium declaration |
| **Output** | Shot breakdown table + 10 prompt variations per shot |
| **Format** | 9×16 vertical — locked, every prompt |
| **Medium** | Declared per scene before generation — locked across all prompts in the scene |
| **Variation Axes** | Camera angle/composition + lens behavior + lighting micro-shifts (within locked medium) |
| **Platform** | Agnostic — no tool-specific syntax |
| **VLD Constraint** | Every prompt carries palette, lighting, texture, and negative prompts from the VLD |

## Workflow

```
Curated Scene (from 5-SCENE-BUILDER)
    ↓
Load VLD (from 4-VIS-DEV) — palette, lighting, texture, negatives, medium
    ↓
CHARACTER SHEETS (6b) — generate turnaround refs, lock character appearance
    ↓
Shot Decomposition (6a) — break scene into shots, build scene template
    ↓
JSON Prompt Generation (6a) — 10 variations per shot (camera × lens × light)
    ↓
User selects best stills from generated images
    ↓
MOTION SEQUENCE (6c) — assign camera movement, subject action, environmental motion to selects
    ↓
Video prompt output — JSON prompts for video generation, sequenced as an edit
```

## Files

| File | Purpose | Load When |
|------|---------|-----------|
| `6a-shots.md` | Core engine — shot decomposition + JSON prompt generation, variation axes, scene template system, VLD integration, quality gates | When generating scene shots |
| `6b-character-sheets.md` | Character reference sheets — one turnaround image per character on white background, locks character appearance before scene shots | When casting characters (run BEFORE 6a) |
| `6c-motion.md` | Motion/video prompts — takes approved stills from 6a, assigns camera movement + subject action + environmental motion, sequences into edit, outputs JSON | When building video sequences from approved stills (run AFTER 6a selects) |
| `references/shot-taxonomy.md` | Tagged shot library — 100+ shot types organized by category, browsable by emotion and scene type, each with 9:16 vertical notes | Reference during 6a generation and planning |
| `references/camera-movements.md` | Tagged camera movement library — 80+ movements organized by category, with speed variants, combinations, emotional function, and 9:16 vertical notes | Reference during 6c generation and planning |

## Integration

**Required:**
- Visual Language Document from 4-VIS-DEV — palette anchors, lighting keywords, texture keywords, composition cues, anti-prompt warnings, negative prompts (REQUIRED)
- Character visual packages from 4-VIS-DEV — silhouettes, costume, signature details (REQUIRED for character shots)
- Location visual packages from 4-VIS-DEV — atmosphere, texture, thresholds (REQUIRED for location shots)
- Scene from 5-SCENE-BUILDER — title + hook line (REQUIRED)

**Optional:**
- Story window from 3-STORIES — emotional context, narrative position
- World bible from 2-WORLDS — faction context, world rules

## Invocation

- "Generate shots for [scene title]" → Load 6a-shots.md, run decomposition + prompts
- "Shoot [scene title]" → Same
- "Give me prompts for [scene]" → Same
- "Shot breakdown for scenes [X, Y, Z]" → Run multiple scenes in sequence
- "More prompts for shot [N]" → Generate additional variations for a specific shot
- "Reshoot with [constraint]" → Regenerate with modified VLD or framing rules
- "Generate character sheets" → Load 6b-character-sheets.md, run for all characters in story window
- "Sheet [character name]" → Generate sheet for specific character
- "Cast the show" → Same as generating all character sheets
- "Sheet [character] in end state" → Generate end-state costume version
- "Build motion for [scene]" → Load 6c-motion.md, take selects, assign motion, sequence edit
- "Animate my selects" → Same
- "Motion sequence for [prompt IDs]" → Build motion for specific selected stills

## Anti-Patterns

| Don't | Why |
|-------|-----|
| Generate prompts without loading the VLD | Every prompt must be visually constrained. Unconstrained prompts produce generic imagery that doesn't belong to the world. |
| Generate prompts without a declared medium | The medium is locked per scene. Ask the user to declare it before generating. Never vary the medium across prompts — that produces a disjointed set that can't cut together. |
| Write narrative instead of visual description | Prompts describe what the IMAGE contains, not what the STORY means. Meaning is carried by the image, not stated in the prompt. |
| Use platform-specific syntax | Prompts are agnostic. No --ar, no /imagine, no [brackets]. Raw descriptive text only. |
| Repeat the same camera position across all 10 variations | Each variation must explore a DIFFERENT angle, distance, lens, or light emphasis. If two prompts would produce visually similar images, one must change. |
| Ignore negative prompts from the VLD | The VLD's "no" list is as important as its "yes" list. Every prompt carries the anti-prompt warnings. |
| Design shots as independent images | Shots are a SEQUENCE. They must cut together — consistent lighting, palette, costume, time of day across all shots. Design the shot table as an edit, not a collection. |
