# 6B-CHARACTER-SHEETS

Generate character reference sheets — one image per character, portrait + turnaround on white background. Run BEFORE scene shots to lock character appearance.

---

## Purpose

Character sheets are the casting step. Before any scene shots (6a) can include a character, that character needs a locked visual reference — a single image showing the character from multiple angles with consistent appearance, costume, and detail. This image becomes the reference that all downstream scene shots match against.

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

### Step 1: Identify Characters

From the story window and scene list, identify which characters need sheets. Only characters who appear in scene shots need sheets.

### Step 2: Extract from 4b

For each character, pull the complete visual package from 4b. Every field in the JSON prompt maps to a specific element of the 4b package:

| JSON Field | 4b Source |
|-----------|-----------|
| `character.description` | Physical description, silhouette, shape language |
| `character.costume` | Costume Logic → Primary state (or Secondary if specified) |
| `character.palette` | Palette section |
| `character.signature_detail` | Signature Detail section |
| `character.posture` | Body in Space → default posture |
| `character.expression` | Inferred from wound/performance — the neutral face, the mask |

### Step 3: Determine Costume State

If the character has a visual arc (start state → end state), determine which state to sheet:
- **Default:** Sheet the start state (how the character first appears)
- **If user specifies:** Sheet the requested state
- **If both needed:** Generate two separate sheets, one per state

### Step 4: Generate Prompt

Build the JSON prompt from the extracted 4b data. The prompt is fully self-contained — it includes everything the generator needs.

### Step 5: Present

Output the JSON prompts. Nothing else.

---

## Output Format

One JSON prompt per character. No headers, no announce blocks, no metadata. Just the prompts.

```
```json
{ complete JSON prompt for character 1 }
```

```json
{ complete JSON prompt for character 2 }
```
```

---

## Pipeline Position

```
4-VIS-DEV (character packages approved)
    ↓
6B-CHARACTER-SHEETS (generate reference images, lock character appearance)
    ↓
6A-SHOTS (scene shots — characters match the locked sheets)
```

Character sheets MUST be generated and approved before any scene shots that include those characters. The sheet IS the casting. Once locked, every scene shot's `subject` field copy-pastes the character description from the approved sheet — ensuring consistency.

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

- "Generate character sheets" → Run for all characters in the current story window
- "Sheet [character name]" → Run for a specific character
- "Cast the show" → Same as generating all character sheets
- "Sheet [character] in end state" → Generate the end-state costume version
