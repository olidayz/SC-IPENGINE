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
Curated Scenes (from 5-SCENE-BUILDER)
    ↓
Load VLD + Locked Cast + Location Prompt Anchors (from 4-VIS-DEV)
    ↓
SETTINGS (6-settings) — dress every location, lock props, write Set Sheet Prompt Blocks
    ↓
Shot Decomposition (6a) — break scene into shots, build Scene Template from Set Sheets + Prompt Anchors
    ↓
JSON Prompt Generation (6a) — 10 variations per shot (camera × lens × light)
    ↓
User selects best stills from generated images
    ↓
MOTION SEQUENCE (6c) — assign camera movement, subject action, environmental motion to selects
    ↓
Video prompt output — JSON prompts for video generation, sequenced as an edit
```

**Note:** Character casting and locked sheets live in 4-VIS-DEV (`4d-casting.md`). Location Prompt Anchors are written in 4c. By the time you reach 6-shots, every character and location has a Prompt Anchor in the Name Registry. 6-settings expands locations into full Set Sheets with specific props, furniture, and dressing before any prompts are generated.

## Files

| File | Purpose | Load When |
|------|---------|-----------|
| `6-settings.md` | Set Sheets — dress every location with specific props, furniture, surfaces, lights. Produces Set Sheet Prompt Blocks for 6a ENVIRONMENT BLOCKs + Prop Registry for portable objects. | After scene curation, BEFORE 6a |
| `6a-shots.md` | Core engine — shot decomposition + JSON prompt generation, variation axes, scene template system, VLD integration, quality gates. ENVIRONMENT BLOCKs built from Set Sheet Prompt Blocks. | When generating scene shots |
| ~~`6b-character-sheets.md`~~ | **Moved to 4-VIS-DEV as `4d-casting.md`** — casting + locked sheets now happen in vis-dev | N/A — load from 4-vis-dev |
| `6c-motion.md` | Motion/video prompts — takes approved stills from 6a, assigns camera movement + subject action + environmental motion, sequences into edit, outputs JSON | When building video sequences from approved stills (run AFTER 6a selects) |
| `references/shot-taxonomy.md` | Tagged shot library — 100+ shot types organized by category, browsable by emotion and scene type, each with 9:16 vertical notes | Reference during 6a generation and planning |
| `references/camera-movements.md` | Tagged camera movement library — 80+ movements organized by category, with speed variants, combinations, emotional function, and 9:16 vertical notes | Reference during 6c generation and planning |

## Integration

**Required:**
- **Style Lock** from 4-VIS-DEV Stage 0 — locked medium/aesthetic, prompt DNA (REQUIRED)
- **Visual Language Document** from 4-VIS-DEV Stage 1 — palette anchors, lighting keywords, texture keywords, composition cues, anti-prompt warnings, negative prompts (REQUIRED)
- **Name Registry** from 4-VIS-DEV — all character/location proper names + Visual Shorthands + Prompt Anchors (REQUIRED)
- **Locked Character Sheets** from 4-VIS-DEV Stage 3 (4d-casting) — Prompt Anchors pasted verbatim into CHARACTER BLOCKs (REQUIRED for character shots)
- **Character visual packages** from 4-VIS-DEV — body in space, visual arc, faction gradient (REQUIRED for character shots)
- **Location visual packages** from 4-VIS-DEV — atmosphere, texture, thresholds, expanded into ENVIRONMENT BLOCKs (REQUIRED for location shots)
- **Scene** from 5-SCENE-BUILDER — title + hook line with proper names (REQUIRED)

**Optional:**
- Story window from 3-STORIES — emotional context, narrative position
- World bible from 2-WORLDS — faction context, world rules

## Invocation

- "Dress the sets" / "Lock the settings" → Load 6-settings.md, generate Set Sheets + Prop Registry for curated scenes
- "Generate shots for [scene title]" → Load 6a-shots.md, run decomposition + prompts (requires Set Sheets)
- "Shoot [scene title]" → Same
- "Give me prompts for [scene]" → Same
- "Shot breakdown for scenes [X, Y, Z]" → Run multiple scenes in sequence
- "More prompts for shot [N]" → Generate additional variations for a specific shot
- "Reshoot with [constraint]" → Regenerate with modified VLD or framing rules
- "Cast the show" / "Generate character sheets" → Load 4-vis-dev/4d-casting.md (lives in vis-dev now)
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
