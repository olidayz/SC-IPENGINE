# 6B-CHARACTER-SHEETS

Generate character reference sheets — one image per character, portrait + turnaround on white background. Run BEFORE scene shots to lock character appearance.

---

## Purpose

Character sheets are the casting step. Two phases:

1. **Cast** — For each character, generate **5 portrait variations** (16:9 landscape). Same costume, same signature detail — different person wearing it. User selects one.
2. **Lock** — Selected cast gets a full turnaround reference sheet (16:9 landscape, white background). This locked sheet becomes the reference all downstream scene shots match against.

No scene shots (6a) until every character is cast and locked.

---

## Anti-Patterns

| Anti-Pattern | Signal | Why It Dies |
|-------------|--------|------------|
| **The Fashion Shoot** | Character sheet looks stylized, dramatic, moody — like an editorial spread | Character sheets are REFERENCE, not content. Neutral background. Even lighting. No atmosphere. The point is clarity, not beauty. |
| **The Vague Description** | Character description is generic ("a young woman in casual clothes") | Pull every detail from the 4b character package. Specific garments, specific colors, specific features, specific details. Vague input = inconsistent output. |
| **The Solo Portrait** | Just a single front-facing headshot | The sheet must show multiple angles — front, 3/4, profile, face close-up — so downstream prompts can reference the character from any position. |
| **The Busy Background** | Character placed in a location or scene | White or neutral background ONLY. The character is isolated from environment. Environment comes later in scene shots. |
| **The Costume Change** | Multiple outfits shown on the same sheet | One costume state per sheet. If the character has a primary and secondary state (from the 4b package), generate separate sheets. |
| **The Abstract Face** | Expression described with mood/psychology ("the face of someone hiding a secret," "a look of quiet determination") | Image generators render muscles, not feelings. Use only physical descriptions: mouth closed, brow smooth, eyes forward, jaw unclenched. No inner states. |

### Renderability Rule

**Every description in the prompt must be physically renderable.** If an image generator can't build it from the words alone, rewrite it.

| Don't Write | Write Instead |
|-------------|--------------|
| "the face of someone who is listening carefully" | "mouth closed, eyes forward, brow slightly raised" |
| "performing ordinary attention" | "neutral expression, mouth closed, eyes level" |
| "a look of quiet determination" | "jaw set, lips pressed together, eyes narrowed slightly" |
| "radiating warmth" | "slight smile, eyes crinkled at corners" |
| "concealing something" | "neutral expression, mouth closed, eyes forward" — the concealment is a story concept, not a visual |
| "exhausted but enduring" | "slight shadows under eyes, shoulders lowered, mouth relaxed" |
| "a body that takes up less space than it's entitled to" | "shoulders slightly forward, arms close to torso, feet together" |

**The test:** Read the description aloud. Can you physically pose a human actor to match it? If yes, it's renderable. If it requires the actor to "feel" something to get it right, it's abstract. Rewrite.

---

## What Goes on a Character Sheet

A single image containing:

1. **Front view** — full body or 3/4 body, facing camera
2. **3/4 view** — the character turned approximately 45 degrees
3. **Profile view** — side view showing silhouette
4. **Back view** (optional, if the character's back is distinctive — a hoodie, a hair detail, a posture tell)

All views on the same image. White or neutral light grey background. Even, flat, shadowless lighting — the goal is accurate color and detail representation, not mood.

**Additionally include if the character has them:**
- Signature detail callout (if small — the watch, the earring, the stone — show it at readable scale)
- Facial detail (if important — specific expression, specific feature)

---

## Input

**Required:**
- Character visual package from 4b (silhouette, palette, costume logic, signature detail, body in space, visual arc)
- VLD medium declaration (the sheet is generated in the same medium as the scene shots — if the show is cinematic photography, the sheet is cinematic photography)

**Optional:**
- Visual arc position (start state or end state — specify which costume state to sheet)

---

## JSON Prompt Format

Each character sheet is a single JSON prompt:

```json
{
  "format": "horizontal 16:9 landscape",
  "style": "[locked medium from VLD/scene declaration]",
  "type": "character reference sheet",
  "background": "pure white, seamless, no shadow, no environment",
  "lighting": "even, flat, studio softbox, shadowless, neutral color temperature, full detail visibility",
  "character": {
    "name": "[character name]",
    "description": "[full physical description from 4b — age, ethnicity, build, features]",
    "costume": "[exact costume from 4b primary or secondary state]",
    "palette": "[character's personal color range from 4b]",
    "signature_detail": "[the ONE detail from 4b — described at close-up level]",
    "posture": "[default posture from 4b body-in-space]",
    "expression": "[default/neutral expression]"
  },
  "layout": {
    "views": ["front full-body", "three-quarter view", "profile view"],
    "arrangement": "side by side on white background, evenly spaced, same scale",
    "annotations": false
  },
  "negative": [
    "no background environment",
    "no dramatic lighting",
    "no shadows on background",
    "no props beyond signature detail",
    "no action poses",
    "no atmospheric effects",
    "no color grading",
    "no lens effects",
    "no narrative context"
  ]
}
```

---

## Generation Process

### Phase 1: CASTING

#### Step 1: Identify Characters

From the Name Registry, identify all characters who need sheets. Every named character gets cast.

#### Step 2: Extract from 4b + Registry

For each character, pull:
- **Name** and **Visual Shorthand** (from Name Registry)
- **Silhouette, Costume, Signature Detail, Palette, Body in Space** (from 4b package)
- **Style Lock** prompt DNA (from 4-style-lock)
- **VLD** lighting/palette anchors

#### Step 3: Generate 5 Casting Variations Per Character

Each variation is a **16:9 landscape portrait** — face and upper body dominant, white or neutral background, even lighting. Same character design, different casting.

**What varies across the 5:**

| Element | Varies |
|---------|--------|
| **Face** | Bone structure, features, age, ethnicity, skin tone |
| **Build** | Height, weight, musculature, proportion |
| **Age** | Within a plausible range for the role |
| **Energy** | Expression, gaze, tension in the face |
| **Micro-details** | Scars, hair texture, weathering, grooming |

**What stays locked across all 5:**

| Element | Locked |
|---------|--------|
| **Costume** | Primary state from 4b |
| **Signature detail** | The ONE thing from 4b |
| **Silhouette** | Shape language from 4b |
| **Background** | White/neutral, no environment |
| **Format** | 16:9 landscape |

**Casting prompt structure:**

```json
{
  "format": "horizontal 16:9 landscape",
  "style": "[locked medium from Style Lock / VLD]",
  "type": "character casting variation",
  "background": "pure white, seamless, no shadow, no environment",
  "lighting": "even, flat, studio softbox, shadowless, neutral color temperature",
  "character": {
    "name": "[character name]",
    "variation": "[1-5]",
    "cast_description": "[specific face/build/age/energy for THIS variation — physically renderable]",
    "costume": "[exact costume from 4b primary state]",
    "palette": "[character's color range from 4b]",
    "signature_detail": "[the ONE detail from 4b]",
    "posture": "[default posture from 4b]",
    "expression": "[physically renderable neutral expression]"
  },
  "layout": {
    "views": ["front upper-body portrait", "three-quarter view"],
    "arrangement": "side by side on white background"
  },
  "negative": [
    "no background environment",
    "no dramatic lighting",
    "no shadows on background",
    "no action poses",
    "no atmospheric effects"
  ]
}
```

#### Step 4: Present for Selection

Present all 5 variations per character. One character at a time.

> **Casting: [CHARACTER NAME]**
> **Design:** [visual shorthand from registry]
>
> **Variation 1:** [1 sentence — the casting pitch: age, energy, distinguishing features]
> **Variation 2:** ...
> (etc.)

User selects one variation per character.

#### Step 5: Build Prompt Anchor

For the selected variation, write a **Prompt Anchor** — a 30-50 word physically renderable description combining the cast face/build with the locked costume and signature detail. This is the portable character description that gets pasted verbatim into every downstream prompt.

```
**[CHARACTER NAME] — Prompt Anchor:**
[30-50 words: specific face, build, age, features, costume, signature detail. Physically renderable only.]
```

Update the Name Registry with the Prompt Anchor column.

---

### Phase 2: LOCKED SHEETS

After casting is approved, generate the full turnaround reference sheets for the locked cast.

#### Step 6: Determine Costume State

If the character has a visual arc (start state → end state), determine which state to sheet:
- **Default:** Sheet the start state (how the character first appears)
- **If user specifies:** Sheet the requested state
- **If both needed:** Generate two separate sheets, one per state

#### Step 7: Generate Locked Sheet Prompt

Build the full turnaround JSON prompt using the selected cast description. The prompt is fully self-contained.

---

## Output Format

**Phase 1 (Casting):** 5 JSON prompts per character. Present with casting pitch lines.

**Phase 2 (Locked Sheets):** One JSON prompt per character using the selected cast. Includes Prompt Anchor for downstream use.

```
## [CHARACTER NAME] — Locked Sheet

**Prompt Anchor:** [30-50 words — paste verbatim into all downstream prompts]

```json
{ complete turnaround JSON prompt }
```
```

---

## Pipeline Position

```
4-VIS-DEV (character packages + Name Registry approved)
    ↓
6B Phase 1: CASTING (5 variations per character → user selects → Prompt Anchors written)
    ↓
6B Phase 2: LOCKED SHEETS (turnaround reference for selected cast)
    ↓
6A-SHOTS (scene shots — characters match locked sheets, prompts paste Prompt Anchors verbatim)
```

No scene shots until every character is cast and locked. Once locked, every scene shot's `subject` field copy-pastes the Prompt Anchor from the locked sheet — ensuring consistency across all generated images.

---

## Quality Gates (Run Silently)

| Gate | Test | Kill If |
|------|------|---------|
| **4b Fidelity** | Does the prompt match the 4b character package exactly? Every detail present? | Any missing costume element, palette drift, or wrong signature detail |
| **Medium Lock** | Is the sheet in the same medium as the scene shots? | Medium mismatch between sheet and downstream scenes |
| **Background Clean** | Is the background specified as white/neutral with no environment? | Any location, atmosphere, or narrative context leaking in |
| **Lighting Neutral** | Is the lighting flat and even, not dramatic or moody? | Any mood lighting, dramatic shadow, or atmospheric effects |
| **Multi-Angle** | Does the layout specify front + 3/4 + profile minimum? | Single-angle portrait instead of turnaround |
| **Specificity** | Is every physical detail specific, not generic? | "A woman in a sweater" instead of "Nigerian-American woman, early 30s, navy crewneck sweater, small gold stud earrings" |

---

## Invocation

- "Cast the show" / "Cast the characters" → Phase 1: generate 5 casting variations per character
- "Lock [character name]" / "Lock the cast" → Phase 2: generate locked turnaround sheets for selected variations
- "Generate character sheets" → Both phases in sequence
- "Sheet [character name]" → Run for a specific character (both phases)
- "Recast [character name]" → Re-run Phase 1 for a specific character with 5 new variations
- "Sheet [character] in end state" → Generate the end-state costume version
