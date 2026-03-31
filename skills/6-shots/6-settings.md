# 6-SETTINGS

Lock the physical contents of every space before shooting. For each curated scene's location, produce a **Set Sheet** — the exact props, furniture, signage, dressing, and environmental objects that exist in the space. The Set Sheet becomes the source for ENVIRONMENT BLOCKs in 6a Scene Templates.

No guessing. No improvising. Every object in every prompt comes from the Set Sheet.

---

## Summary

| Attribute | Spec |
|-----------|------|
| **Purpose** | Lock the physical contents of every location and key props before 6a shot generation |
| **Input** | Curated scenes from 5-SCENE-BUILDER + Location Prompt Anchors + 4c location packages + VLD + Name Registry |
| **Output** | One Set Sheet per location + one Prop Registry for portable/character-held objects |
| **Position** | After scene curation (5), before shot generation (6a) |

---

## Why This Exists

The 4c location package describes how a space FEELS — architecture, scale, faction signature, sensory depth. A Set Sheet describes what's PHYSICALLY IN IT — the specific chair, the specific mug, the specific stain on the specific wall. Without Set Sheets, every 6a Scene Template invents objects on the fly, and the same room has different furniture across different scenes.

---

## What Goes on a Set Sheet

### Per Location

One Set Sheet per named location that appears in the curated scenes. If a location appears in 8 scenes, those 8 scenes share one Set Sheet.

```
## [LOCATION NAME] — Set Sheet

**Prompt Anchor:** [paste from Name Registry — the 30-50 word base description]

### Architecture
- [Fixed structural elements — walls, floor, ceiling, windows, doors, columns. Material, color, condition, dimensions where relevant.]

### Furniture & Fixtures
| Item | Description | Position | Condition |
|------|-------------|----------|-----------|
| [specific item] | [material, color, size — physically renderable] | [where in the space] | [new/worn/broken/modified] |

### Props & Objects
| Item | Description | Position | Story Weight |
|------|-------------|----------|-------------|
| [specific object] | [material, color, size — physically renderable] | [where in the space] | [background / featured / signature] |

### Surfaces & Textures
- [Wall surfaces — paint, paper, exposed material, stains, marks]
- [Floor surfaces — material, wear patterns, stains, transitions]
- [Ceiling — material, fixtures, condition]

### Signage & Text
| Sign/Text | Content | Material | Position |
|-----------|---------|----------|----------|
| [what it is] | [exact text if relevant] | [printed/handwritten/digital/painted] | [where] |

### Dressing by Zone
[If the space has distinct zones (front/back, public/private, etc.), dress each separately:]
- **[Zone A]:** [specific objects, their arrangement]
- **[Zone B]:** [specific objects, their arrangement]

### Light Sources (Practical)
| Source | Type | Color | Position | State |
|--------|------|-------|----------|-------|
| [specific fixture] | [overhead/desk/window/screen/practical] | [warm/cool/specific color] | [where] | [on/off/flickering/dimmed] |

### Time-of-Day Variants
| Time | What Changes |
|------|-------------|
| [Day] | [which lights are off, what natural light does, what's visible] |
| [Night] | [which lights are on, what's in shadow, what's illuminated] |

### Set Sheet Prompt Block
[60-100 words. The paste-ready expansion of this location for use in 6a ENVIRONMENT BLOCKs. Combines the Prompt Anchor with key set dressing details. This replaces improvised environment descriptions in Scene Templates.]
```

### Prop Registry (Portable Objects)

Objects that move between locations or are held/used by characters. These appear across multiple scenes and need consistent descriptions.

```
## Prop Registry

| Prop | Owner/User | Description | Signature? |
|------|-----------|-------------|-----------|
| [prop name] | [character name or "shared"] | [material, color, size, condition, distinctive marks — physically renderable, 15-30 words] | [yes/no — is this a character's signature detail from 4b?] |
```

Props with `Signature: yes` are already defined in the character's Prompt Anchor. The Prop Registry captures their standalone description for close-up shots where the character isn't visible.

Non-signature props (a document, a vehicle, a device, a piece of food) get defined here so they're consistent across every scene they appear in.

---

## Generation Process

### Step 1: Identify Locations in Curated Scenes

From the curated scene list, extract every named location. Group scenes by location.

### Step 2: Load Location Data

For each location, pull:
- **Prompt Anchor** (from Name Registry)
- **4c location package** (architecture, materials, faction signature, set dressing notes, sensory depth)
- **VLD zone** (palette, lighting system, textures)
- **Scene hook lines** set here (what happens in this space — informs which objects are narratively important)

### Step 3: Dress the Set

For each location, work through the Set Sheet template. Every item must be:

| Rule | Why |
|------|-----|
| **Physically renderable** | Image models render objects, not concepts. "A laptop showing bad news" → "A laptop, screen facing away from camera, blue-white glow on face." |
| **Specific** | "A chair" fails. "A folding metal chair, grey, rubber feet, one leg slightly bent" succeeds. |
| **VLD-compliant** | Colors, materials, and textures must belong to this location's VLD zone. No palette drift. |
| **Motivated** | Every object either belongs to the faction/world (environmental dressing) or the narrative (story-relevant prop). No random decoration. |
| **Consistent with 4c** | The Set Sheet expands the 4c package — it doesn't contradict it. If 4c says "raw concrete walls," the Set Sheet doesn't add wallpaper. |

### Step 4: Identify Portable Props

Scan all curated scenes for objects that:
- Move between locations
- Are held or used by characters
- Appear in close-up shots
- Are narratively significant

Add each to the Prop Registry.

### Step 5: Write Set Sheet Prompt Blocks

For each location, write the paste-ready **Set Sheet Prompt Block** — a 60-100 word expansion that combines the Location Prompt Anchor with the most important set dressing details. This block is what 6a pastes into ENVIRONMENT BLOCKs.

The Prompt Block doesn't include everything on the Set Sheet — it includes what the CAMERA SEES in a typical shot. Close-up shots may pull additional details from the full Set Sheet.

### Step 6: Present

One Set Sheet per location + one Prop Registry. User reviews and adjusts before 6a.

---

## Downstream

- **6a Scene Templates** — the ENVIRONMENT BLOCK is built from the Set Sheet Prompt Block. No improvising. If the Set Sheet says "folding metal chairs in rows," every prompt says "folding metal chairs in rows."
- **6a close-up shots** — pull specific object details from the Set Sheet's Props & Objects table.
- **6a character shots** — signature props from the Prop Registry appear consistently.
- **6c motion** — practical light sources from the Set Sheet inform motion lighting.

---

## Announce Block

> **Activating IP Engine — 6-SETTINGS.**
> **Locations:** [list location names from curated scenes]
> **Props:** [count of portable props identified]
> **Source:** Curated scenes from 5-SCENE-BUILDER + 4c location packages + VLD

---

## Anti-Patterns

| Don't | Why |
|-------|-----|
| Dress generically | "A desk with papers" is useless. "A steel-frame desk, faux-wood laminate top, three stacked manila folders, a branded ceramic mug (chipped rim), a desktop monitor angled 20 degrees left" — that's a Set Sheet. |
| Contradict the 4c package | The Set Sheet expands 4c, not overrides it. |
| Over-dress | Not every surface needs 10 objects. Dress to the level a camera would notice. |
| Skip practical lights | Light sources are physical objects. They need to be on the Set Sheet so 6a lighting is consistent. |
| Forget time-of-day variants | The same room looks different at dawn vs. midnight. If scenes in this location span different times, note what changes. |
| Describe function, not form | "A device that tracks dinosaur herds" — image model can't render that. "A handheld metal unit, size of a brick, cracked amber screen, leather wrist strap, two toggle switches on the right side" — that it can. |
