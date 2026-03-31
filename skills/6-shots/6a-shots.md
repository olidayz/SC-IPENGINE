# 6A-SHOTS

Core engine. Decompose scenes into shots. Generate 10+ image prompts per shot.

---

## Anti-Patterns (Read First)

| Anti-Pattern | Signal | Why It Dies |
|-------------|--------|------------|
| **The Screenplay** | Shot description reads like a script direction ("Character walks to the door, pauses, and turns") | This isn't story — it's a single frozen frame. Each shot is ONE IMAGE. No movement, no sequence, no before-and-after. Describe what the camera SEES at one instant. |
| **The Caption** | Prompt describes what the image MEANS instead of what it CONTAINS ("A scene about grief and concealment") | Image generators render objects, light, and composition — not themes. Translate meaning into visible elements. Grief = specific posture + specific light + specific object. |
| **The Clone Army** | All 10 prompts for a shot produce visually similar images differing only in minor word choices | Each variation must produce a RECOGNIZABLY DIFFERENT image. If you can't immediately tell two outputs apart, the prompt needs a different angle, composition, depth of field, or lighting micro-shift. |
| **The VLD Amnesia** | Prompts use generic lighting ("dramatic lighting") or colors ("warm tones") instead of VLD-specific terms | Every prompt must carry VLD palette anchors, lighting keywords, and texture keywords. "West-facing golden hour through strip-mall window" not "warm light." |
| **The Encyclopedist** | Prompt tries to include every detail from the character/location package in a single image | One shot, one focus. The signature detail OR the body in space OR the costume state. Not all three crammed into one prompt. Hierarchy matters. |
| **The Director's Commentary** | Prompt includes parenthetical explanations of why something is framed this way | No meta. The prompt is instructions for an image, not a film school lecture. Cut everything that isn't visual description. |
| **The Abstract Face** | Expression or body language described with psychology instead of physics ("the face of someone hiding a secret," "a posture of quiet grief") | Image generators render muscles, not feelings. Mouth closed, brow smooth, eyes forward, jaw unclenched. No moods, no inner states, no "the face of someone who..." — only what the body is physically doing. |

### Process Anti-Pattern

| Anti-Pattern | Signal | Why It Dies |
|-------------|--------|------------|
| **The Open Kitchen** | Presenting decomposition rationale, variation-axis planning, or VLD-integration notes to the user | The user sees shots and prompts. The machinery is internal. |

---

## Format Lock: 9×16 Vertical

**Every prompt is 9×16 portrait orientation. No exceptions.** This changes everything about composition:

- **Vertical depth replaces horizontal width.** Foreground/background stacking matters more than left-right balance. Use vertical layers: floor → subject → ceiling/sky.
- **Bodies are framed differently.** Full-body shots have vertical room for headspace and floor. Close-ups are taller — more neck, more hair, more vertical context.
- **Architecture reads differently.** Vertical lines (door frames, building edges, columns, standing figures) are allies. Horizontal lines (tables, rails, shelves) become compositional challenges — use them to anchor the lower or upper third, not to span the frame.
- **Negative space stacks.** A figure in the lower third with empty space above = vulnerability, smallness. A figure filling the upper two-thirds with floor below = grounding, weight.
- **Every prompt must include:** "vertical 9:16 composition" or "portrait orientation" or "tall frame vertical format" in the framing layer. Do not rely on the generator to default to vertical.

### 9×16 Composition Patterns

| Pattern | How It Works in Vertical |
|---------|------------------------|
| **The Stack** | Foreground object at bottom, subject in middle third, environment at top. Three vertical layers in one frame. |
| **The Tower** | Full standing figure, feet near bottom edge, head near top edge. The body fills the vertical axis. Architecture flanks. |
| **The Drop** | Shot looking straight down — a table surface, a lap, hands holding an object, the floor. Pure overhead on a vertical canvas. |
| **The Rise** | Shot looking straight up — ceiling, sky, light source, architecture from below. The subject is the top of the frame or absent. |
| **The Slice** | A vertical sliver of a scene — seen through a doorway, a gap in a fence, a crack in a curtain. The frame within the frame is also vertical. |
| **The Split** | Upper half and lower half are different zones — above/below a table, inside/outside a window, the rail and the pit below it. Horizontal division within vertical frame. |
| **The Close Tower** | Close-up that uses the full vertical — not just face but face + neck + shoulder + whatever's below. More body context than a standard close-up. |

---

## Sequence Design: Shots as Edit

**The shots in a scene are not independent images. They are a sequence that must cut together.**

Before decomposing, design the sequence as an edit. Ask:

1. **What's the visual rhythm?** — Does this scene escalate (wide → medium → close → extreme close)? Oscillate (wide → close → wide → close)? Hold and release (same framing, same framing, same framing → sudden shift)? The rhythm is a creative choice.
2. **What's the angle pattern?** — If shot 1 is eye-level, shot 2 should NOT be eye-level. Push for maximum angle diversity across the sequence: eye-level → overhead → ground → through-object → high angle. The sequence should feel like the camera is alive and moving through the space. But every angle must serve the story — never weird for weird's sake.
3. **What's consistent?** — Across all shots in the sequence, the following must remain locked: lighting direction (the sun doesn't move between shots), color palette (VLD zone doesn't shift), character costume state (no continuity errors), time of day, weather. Consistency is what makes the cuts feel invisible.
4. **What's the entry and exit?** — Shot 1 is how the audience enters the scene. The last shot is how they leave it. The entry should orient. The exit should resonate. Together they bracket the emotional journey.

### Sequence Coherence Rules

| Rule | Why |
|------|-----|
| **No two consecutive shots share the same camera angle** | The sequence must feel dynamic. Two eye-level medium shots in a row = dead cut. |
| **No two consecutive shots share the same framing distance** | Wide-wide or close-close creates stagnation. Alternate distance to create rhythm. |
| **Lighting direction is consistent across all shots** | If the light comes from the left in shot 1, it comes from the left in all shots. The VLD zone determines the source. |
| **Character appearance is locked across the sequence** | Same costume, same hair, same details. No continuity errors between shots. |
| **The sequence has escalation or de-escalation** | The shots should build toward something — increasing intimacy (getting closer), increasing tension (angles getting stranger), or increasing calm (settling into stillness). Flat sequences with no trajectory feel like slideshows, not edits. |
| **Story drives angle, not variety for its own sake** | An overhead shot must be motivated: surveillance, vulnerability, god's-eye judgment, pattern recognition. A ground-level shot must be motivated: the world from below, the child's perspective, the floor where the stones are piled. Never choose an angle just because you haven't used it yet. |

### Dynamic Camera Checklist (Run Before Presenting)

For each shot table, verify:
- [ ] At least 3 different camera angles represented across the sequence
- [ ] No two consecutive shots at the same distance AND same angle
- [ ] At least 1 unconventional angle (overhead, ground, through-object, reflection, etc.)
- [ ] The angle progression tells a story (escalation, exploration, revelation)
- [ ] Every unconventional angle has a narrative motivation (not just variety)

---

## Shot Decomposition

### How Many Shots?

The scene dictates. There is no fixed count. But here's the calibration:

| Scene Type | Typical Count | Why |
|------------|--------------|-----|
| **Texture / object** | 3-5 | The scene IS the detail. Fewer shots, more variation per shot. |
| **Character moment** | 4-7 | The face, the hands, the body in space, the environment. |
| **Location establishing** | 3-5 | Wide, medium, close. Maybe a threshold. |
| **Interaction / collision** | 5-8 | Two characters = two compositions + the space between them + details + the room. |
| **Ceremony / ritual** | 6-10 | Group dynamics, individual faces, objects in use, the space, the light. |
| **World media / artifact** | 2-4 | The artifact itself + context. Fewer shots, the format IS the constraint. |

### Decomposition Process

For each scene, ask:

1. **What's the ICONIC FRAME?** — The single image that IS this scene. If you could only generate one image, this is it. This is always Shot 1.
2. **What's the ENVIRONMENT?** — Where does this happen? Wide establishing context. Often Shot 2.
3. **What's the DETAIL?** — The close-up that rewards inspection. The object, the texture, the signature element. Often the last shot.
4. **What's BETWEEN?** — The medium shots, the relationships, the spatial dynamics. The connective tissue.
5. **What's the FEELING?** — Is there a framing that captures the emotional register without showing a face? An empty chair, a lit window from outside, a worn surface. The mood shot.

Not every scene needs all five. The Iconic Frame is mandatory. Everything else is scene-dependent.

### Shot Table Format

```
| # | Shot | Angle | Description | Register |
|---|------|-------|-------------|----------|
| 1 | [Short name] | [Camera angle + distance] | [1-2 sentences: what the camera sees — subject, framing, key details. 9:16 vertical composition.] | [VLD tonal register] |
| 2 | ... | ... | ... | ... |
```

The Angle column locks the camera position for this shot — all 10 prompt variations share this angle (they vary medium and micro-framing, not the fundamental camera position). This ensures the sequence cuts together: the angle progression is designed at the shot-table level, not the prompt level.

The Description column is the bridge between the scene's hook line and the prompts. It translates narrative into visual composition. All descriptions assume 9:16 vertical framing and the scene's declared medium.

---

## Prompt Generation

### Medium Lock

**The visual medium/style is inherited from the Style Lock (4-vis-dev Stage 0).** If a Style Lock exists, it is the default for all scenes. The user can override per scene (e.g. "shoot this in charcoal" or "editorial illustration"), but the Style Lock is the baseline.

If no Style Lock exists and the user doesn't declare a medium, ask before generating.

The medium declaration appears in the Announce Block and is baked into every prompt as a constant, not a variable.

### Name Registry → Prompt Translation

**Scene hook lines use proper names. Shot prompts must expand those names into visual descriptions.**

The Name Registry is the translation layer between scenes (which use names) and prompts (which need physical descriptions an image model can render).

| Scene says | Prompt must expand to |
|------------|----------------------|
| "Mara" | The **Prompt Anchor** from her Locked Sheet — 30-50 words, pasted verbatim |
| "The Bonefield" | The **Location Visual Shorthand** + relevant details from the 4c location package |

**Rules:**
- Every character in a prompt is identified by their **Prompt Anchor** from the Name Registry (post-casting). Paste verbatim. No paraphrasing.
- Every location in a prompt is expanded from the **Location Visual Shorthand** + 4c package details (architecture, materials, palette, lighting per VLD zone).
- The name itself does NOT appear in the image prompt — image models don't know what "Mara" or "the Bonefield" means. Only the physical description appears.
- The name DOES appear in the shot table and sequence design for human readability.

---

### Scene Template (The Interchangeability Engine)

**The core rule: any prompt from any shot in a scene must cut with any prompt from any other shot in the same scene.** Prompt 1a works with 2c works with 3f works with 4b. Any combination produces a coherent sequence.

This requires that every prompt in the scene shares identical locked language for everything EXCEPT the camera/lens/light layer. To achieve this, build a **Scene Template** before generating any prompts. The template is a set of frozen text blocks that get pasted verbatim into every prompt. Only the variable layer changes.

#### Building the Scene Template

Before generating shots or prompts, construct these locked blocks:

```
SCENE TEMPLATE

FORMAT BLOCK (identical in every prompt):
"[Exact format phrase]"

MEDIUM BLOCK (identical in every prompt):
"[Exact medium phrase]"

ENVIRONMENT BLOCK (identical in every prompt sharing this location):
"[Paste the Set Sheet Prompt Block from 6-settings — verbatim.
This block was built from the Location Prompt Anchor + 4c package + specific
set dressing (props, furniture, surfaces, practical lights).
The location NAME does not appear — only the physical description.
No paraphrasing across prompts. No improvising objects not on the Set Sheet.]"

CHARACTER BLOCK(S) (identical in every prompt featuring this character):
"[Prompt Anchor from Name Registry (post-casting) — pasted VERBATIM.
The character NAME does not appear — only the physical description.
If no casting has been done, build from 4b package: costume, palette,
physical description, signature detail. No synonym drift across prompts.]"

NEGATIVE BLOCK (identical in every prompt):
"[Exact negative phrases — pulled from VLD anti-prompt list.]"
```

#### How Prompts Are Assembled

Every prompt is assembled from the template blocks + one variable insert:

```
[FORMAT BLOCK] + [MEDIUM BLOCK] + [VARIABLE] + [ENVIRONMENT BLOCK] + [CHARACTER BLOCK if visible] + [NEGATIVE BLOCK]
```

The **VARIABLE** layer is the only part that changes between prompts. It contains:
- Camera angle and distance
- Lens behavior (DOF, focal length)
- Which light source is emphasized
- Subject-specific framing (what's in frame, compositional pattern)
- Spatial relationship cues specific to this camera position

The CHARACTER BLOCK appears verbatim whenever the character is visible. If omitted (object close-up, empty space), the character simply isn't in that prompt. When present, always the exact same words.

The ENVIRONMENT BLOCK appears in full for wide shots. For close-ups, use the relevant subset — but always the exact same language for elements that ARE visible.

#### Light Consistency Rule

The Scene Template's light system defines the PHYSICS of the scene. Every prompt — interior and exterior — must be consistent with these physics:

1. **Sun position is fixed.** If the light enters a west-facing window, the sun is in the west. Exterior shots must place the sun in the west. Sky color, shadow direction, and ambient light must agree.
2. **Time of day is fixed.** If interior light is golden hour, exterior sky is golden hour — not morning, not midday, not full dark. The sun hasn't set yet.
3. **Interior/exterior agreement.** If an exterior shot shows the building, the light spilling from the window must match the interior light color and intensity. The window looks the same from both sides.
4. **Shadow direction is fixed.** If the light enters from the left (west), all shadows fall to the right (east). In every prompt. Interior and exterior.
5. **Write a LIGHT NOTE in the Scene Template.** One sentence stating sun position, time of day, and the physics. Example: "Sun in the west, 40 minutes before sunset, golden-hour light entering the west-facing window at approximately 15 degrees above horizon. Exterior sky: warm amber-gold at the western horizon, transitioning to blue overhead." Every prompt references this note.

#### Verbatim Rule

The locked blocks are COPY-PASTE sources. Never rephrase. Never paraphrase. Never use synonyms. Never abbreviate. Never expand.

| This is wrong | This is right |
|--------------|---------------|
| "A church in Ohio" in prompt 3 when the template says "strip-mall church in suburban Ohio, evening service" | Copy-paste the exact template text into every prompt |
| "Brown carpet" in prompt 7 when the template says "brown commercial carpet" | The word "commercial" matters. Copy it. |
| "Folding chairs" in prompt 2 when the template says "folding metal chairs in rows" | "Metal" and "in rows" matter. Copy them. |
| "The window light" in prompt 5 when the template says "west-facing window casting golden-hour light across the room, warm and directional from the left side" | The full phrase is the template. Use it. |

#### Why This Works

The FORMAT, MEDIUM, ENVIRONMENT, CHARACTER, and NEGATIVE blocks are literally identical text across all prompts. Any image generated from any prompt shares the same visual DNA: same color temperature, same materials, same medium, same character look, same anti-list. The ONLY differences are camera position, lens behavior, and light emphasis — exactly what makes real film coverage dynamic while cutting together seamlessly.

You can pull prompt 1a, 2c, 3f, 4b and they'll feel like coverage from the same shoot — same set, same actor, same lights, different camera positions.

#### Template Output

**Present the Scene Template at the top of the output, before the shot table.** The user reviews and can adjust the locked blocks before prompts generate. The template is visible — it's the foundation.

---

### The Anatomy of a Prompt (JSON Format)

Every prompt is output as a JSON object. JSON gives the image generator structured, unambiguous instructions. Each field is a discrete visual decision.

**Locked fields** (identical across all prompts in the scene — pulled from Scene Template):

```json
{
  "format": "vertical 9:16 portrait",
  "style": "[locked medium from scene declaration]",
  "subject": {
    "description": "[locked character description from 4b package]",
    "costume": "[locked costume state]",
    "signature_detail": "[locked signature detail]"
  },
  "environment": {
    "setting": "[locked location description from 4c package]",
    "materials": "[locked material/texture details from VLD]",
    "props": "[locked set dressing details]"
  },
  "negative": ["[locked anti-prompts from VLD]"]
}
```

**Variable fields** (unique per prompt — the only things that change):

```json
{
  "camera": {
    "shot_tag": "[tag from shot taxonomy]",
    "angle": "[camera vertical position]",
    "distance": "[framing distance]",
    "position": "[spatial relationship to subject]",
    "composition": "[compositional pattern — rule of thirds, centered, etc.]"
  },
  "lens": {
    "focal_length": "[mm]",
    "depth_of_field": "[shallow/deep/split]",
    "focus_target": "[what's sharp]",
    "bokeh": "[what's soft and how]"
  },
  "lighting": {
    "primary_source": "[which practical source dominates]",
    "fill_level": "[how much ambient fill]",
    "atmosphere": "[dust, breath, condensation, etc.]",
    "color_temp": "[warm/cool emphasis within VLD zone]"
  }
}
```

**Complete prompt example:**

```json
{
  "format": "vertical 9:16 portrait",
  "style": "cinematic still, 35mm film quality, production lighting",
  "subject": {
    "description": "A woman in her early 30s, Nigerian-American, minimal makeup",
    "costume": "navy crewneck sweater, dark jeans, small gold stud earrings",
    "signature_detail": "smooth grey river stone held in closed right fist, barely visible between fingers",
    "pose": "seated, compact posture, shoulders slightly forward, hands in lap"
  },
  "camera": {
    "shot_tag": "CU-HANDS-IN-LAP",
    "angle": "45-degree down",
    "distance": "close-up",
    "position": "above and in front of subject's lap",
    "composition": "hands centered in vertical frame, left hand open in upper portion, closed right fist with stone in lower portion"
  },
  "lens": {
    "focal_length": "85mm",
    "depth_of_field": "shallow",
    "focus_target": "both hands and stone sharp",
    "bokeh": "lap and surrounding chair dissolving into warm golden blur"
  },
  "environment": {
    "setting": "strip-mall church in suburban Ohio, evening service",
    "materials": "brown commercial carpet, folding metal chair, cream walls, drop ceiling",
    "props": "folding chairs in rows, thirty congregants seated"
  },
  "lighting": {
    "primary_source": "west-facing window golden hour, warm and directional from the left",
    "fill_level": "minimal — natural shadow on the right side",
    "atmosphere": "none",
    "color_temp": "warm amber on lit side, cool natural shadow on right"
  },
  "negative": [
    "no dramatic backlighting",
    "no lens flare",
    "no desaturation",
    "no heroic low-angle",
    "no noir shadow",
    "no cinematic fog",
    "no stained glass",
    "no rain-on-window melancholy",
    "no heroic composition",
    "no church architecture",
    "no steeple",
    "no pulpit"
  ]
}
```

### Prompt Output Rules

- Every prompt is a complete, self-contained JSON object
- Locked fields are **copy-pasted verbatim** from the Scene Template — no paraphrasing, no synonym drift
- Variable fields are the only fields that differ between prompts
- The `shot_tag` field references the shot taxonomy for traceability
- The `negative` array is always present, always complete
- **Renderability rule:** Every description must be physically renderable. No moods, no psychology, no "the face of someone who..." All expressions described as physical positions (mouth closed, brow raised, eyes forward). Test: could you direct an actor to this position using only these words?

### Prompt Length

Target: 60-120 words per prompt. Long enough to constrain the generator. Short enough that every word is load-bearing. If a word could be removed without changing the output image, remove it.

### The 10 Variations

Each shot gets 10 prompts. The MEDIUM is locked for the scene. The 10 prompts vary across three cinematographic axes to produce 10 recognizably different images of the same moment in the same style:

**Axis 1 — Camera Angle + Distance**

The primary variation driver. Each prompt explores a different camera position and framing distance for this shot's subject.

| Variation Type | What Changes |
|----------------|-------------|
| **Distance shift** | Same angle, different crop — pushing closer (ECU, CU) or pulling back (wide, extreme wide) changes what's included and excluded |
| **Angle shift** | Different vertical position — eye-level vs. low angle vs. high angle vs. overhead vs. ground-level. Same subject, different power dynamic |
| **Lateral shift** | Subject centered vs. off-center (left third, right third). Changes the negative space and what the empty frame says |
| **POV shift** | Through-object, over-shoulder, reflection, frame-within-frame. The same moment seen through a different architectural relationship |
| **Unconventional position** | Dutch angle, extreme overhead, floor-level, behind subject, silhouette. The surprising angle that reframes meaning |

**Axis 2 — Lens Behavior**

Secondary variation. Each prompt can specify different optical qualities:

| Variation Type | What Changes |
|----------------|-------------|
| **Depth of field** | Shallow (subject isolated, background bokeh) vs. deep focus (everything sharp, foreground to background). Changes hierarchy of attention |
| **Focal length** | Wide-angle (slight distortion, exaggerated depth) vs. telephoto (compressed layers, flattened perspective). Changes spatial feeling |
| **Focus plane** | What's sharp and what's soft. Foreground sharp / background soft, or reversed. Rack-focus implied (foreground object soft, background subject sharp) |
| **Macro vs. normal** | Extreme close-up rendering texture at near-microscopic scale vs. normal optical behavior |

**Axis 3 — Lighting Micro-Variation**

Tertiary variation. The VLD zone establishes the lighting SYSTEM for the location. Within that system, prompts can micro-vary:

| Variation Type | What Changes |
|----------------|-------------|
| **Source emphasis** | Which practical light source dominates — if the scene has both a desk lamp (amber) and a laptop screen (blue-white), prompts can emphasize one or the other |
| **Fill level** | How much ambient fill — darker prompts let shadows go deeper, lighter prompts open up the shadows. Same sources, different ratios |
| **Atmospheric effect** | Dust in light beams, visible breath, condensation, the specific quality of air between camera and subject |
| **Reflection / bounce** | Light reflecting off surfaces — screen glow on a face, window light on a floor, ambient bounce off a white wall |

**The principle:** These three axes combine to produce 10 prompts that feel like 10 different cinematographer's choices for the same moment. Same scene, same medium, same story beat — but the camera is in a different position, the lens is doing something different, and the light is emphasizing a different source. The result is a pool of images that all belong to the same world and the same sequence, but offer genuine compositional variety for mix-and-match.

**Hard rules across all 10:**
- Medium: LOCKED (identical in every prompt)
- Character costume/appearance: LOCKED (no continuity errors)
- VLD zone palette: LOCKED (no color drift)
- Time of day: LOCKED (same temporal position)
- Lighting system: LOCKED (same sources exist — only the emphasis shifts)
- Negative prompts: LOCKED (every prompt carries the full anti-list)

### VLD Integration

Every prompt carries VLD DNA. Before generating any prompts, extract from the VLD:

| VLD Element | How It Enters the Prompt |
|-------------|-------------------------|
| **Palette anchors** | Specific color names/hex woven into environment description |
| **Lighting keywords** | Exact phrases from VLD placed in the light layer |
| **Texture keywords** | Exact material descriptions from VLD placed in environment |
| **Composition cues** | VLD framing rules inform the lens/framing choice |
| **Anti-prompt warnings** | Placed in Layer 4 as negative constraints |
| **Reference shorthand** | Used as style anchors in Layer 1 when applicable |
| **Negative prompts** | Always appended to every prompt |

### Character Integration

When a shot includes a character, the **Prompt Anchor** from the Name Registry is the primary source — pasted verbatim into the CHARACTER BLOCK. The Prompt Anchor already contains the cast face/build, costume, and signature detail from casting (4d).

| Source | What It Provides | How It Enters the Prompt |
|--------|-----------------|-------------------------|
| **Prompt Anchor** (Name Registry) | Locked cast description — face, build, age, costume, signature detail | Pasted verbatim as the CHARACTER BLOCK. This is the single source of truth. |
| **4b package** (supplement) | Body in space, visual arc position, faction gradient, secondary costume states | Used to inform posture and arc-specific details the Prompt Anchor doesn't cover |
| **Visual arc position** | Start-state or end-state | Determines which costume state appears — override the Prompt Anchor's costume if the scene is in a different arc position |

**If no casting has been done** (no Prompt Anchors exist), build the CHARACTER BLOCK from the 4b package directly: silhouette, palette, costume, signature detail, body in space.

### Location Integration

When a shot is set in a named location, expand the **Location Visual Shorthand** from the Name Registry using the full 4c package. The location name does NOT appear in the prompt — only the physical description.

| Source | What It Provides | How It Enters the Prompt |
|--------|-----------------|-------------------------|
| **Visual Shorthand** (Name Registry) | Quick ID — "red canyon, fossil walls, dawn light" | Starting point for the ENVIRONMENT BLOCK |
| **4c package** (full expansion) | Architecture, scale, materials, faction signature, sensory depth, threshold | Fleshes out the ENVIRONMENT BLOCK with specific colors, textures, objects, VLD zone palette |
| **VLD zone** | Palette, lighting system, composition rules for this territory | Constrains every visual decision in the ENVIRONMENT BLOCK |

The ENVIRONMENT BLOCK is the **Set Sheet Prompt Block** from `6-settings.md` — pasted verbatim into every prompt. It was built from the Location Prompt Anchor + specific set dressing (props, furniture, surfaces, practical lights). Do not improvise objects that aren't on the Set Sheet. For close-up shots that need additional detail, pull from the full Set Sheet's Props & Objects table.

---

## Output Format

For each scene, present:

```
═══════════════════════════════════════════
SCENE [###]: [TITLE]
[Hook line from 5-SCENE-BUILDER]
Format: 9×16 vertical
Medium: [declared medium — locked for all prompts]
═══════════════════════════════════════════

SCENE TEMPLATE (locked JSON fields — identical across all prompts)

{
  "format": "...",
  "style": "...",
  "subject": { ... },
  "environment": { ... },
  "negative": [ ... ]
}

---

SEQUENCE DESIGN
[2-3 sentences: the visual rhythm — how the camera moves through the scene, what escalates or de-escalates.]

SHOT TABLE

| # | Shot | Tag | Description | Register |
|---|------|-----|-------------|----------|
| 1 | ... | [taxonomy tag] | ... | ... |
| 2 | ... | [taxonomy tag] | ... | ... |
...

---

### SHOT 1: [NAME]

**1a**
```json
{ complete JSON prompt }
```

**1b**
```json
{ complete JSON prompt }
```

...through **1j**

---

### SHOT 2: [NAME]

**2a**
```json
{ complete JSON prompt }
```

...

═══════════════════════════════════════════
```

**Each prompt is a standalone JSON object.** Copy-paste ready. The locked fields are verbatim from the Scene Template. The variable fields (camera, lens, lighting) are unique per prompt.

**Prompt numbering:** Letters (a-j) for variations within a shot. Cross-referencing: "1a cuts with 2c cuts with 3f" — all interchangeable because locked fields are identical.

---

## Quality Gates (Run Silently)

| Gate | Test | Kill If |
|------|------|---------|
| **9×16 Lock** | Does every prompt specify vertical 9:16 portrait orientation? | Any prompt missing format specification |
| **Medium Lock** | Does every prompt in the scene use the declared medium? No medium drift? | Any prompt using a different medium than the scene declaration |
| **Template Compliance** | Do all prompts use the exact same FORMAT, MEDIUM, ENVIRONMENT, CHARACTER, and NEGATIVE blocks verbatim? No paraphrasing, no synonym drift? | Any prompt that rephrases a locked block — even slightly. "Faded dark hoodie" when the template says "faded black hoodie" is a failure. |
| **Verbatim Lock** | Are all names, locations, and descriptions identical word-for-word across all prompts? The Scene Template is a copy-paste source — NEVER rephrase, reword, or paraphrase any locked field. | "A church in Ohio" in one prompt and "strip-mall church in suburban Ohio" in another. "Commercial carpet" in one and "brown carpet" in another. Any variation in locked text = failure. |
| **Light Consistency** | Do ALL prompts in the scene — interior AND exterior — describe the same moment in time with physically consistent lighting? If golden hour enters a west-facing window, the exterior sun position, sky color, and shadow direction must agree with that. Interior light direction must match the window position. | Interior says "golden hour from the left" but exterior says "overcast dusk." One prompt says "morning light" another says "evening." Sun in the west but shadows falling west. Any physics contradiction across prompts. |
| **VLD Compliance** | Does every prompt carry VLD palette, lighting, texture, and negatives? | Any prompt missing VLD constraints |
| **Variation Spread** | Are all 10 prompts for a shot cinematographically distinct? Different angles, lenses, or light emphasis? | Two prompts that would produce similar-looking images |
| **Single-Frame Test** | Does every prompt describe ONE frozen moment, not a sequence? | Any prompt containing temporal language ("then," "before," "as she walks") |
| **Render Test** | Could an image generator produce this? No abstract concepts, no invisible states, no sounds, no psychological descriptions? | Prompt contains unrenderable elements ("the feeling of grief," "the sound of silence," "the face of someone hiding," "a posture of quiet determination"). All expressions and body language must be described as physical positions: which muscles, which direction, which state. |
| **Specificity** | Does every prompt contain at least 3 concrete visual details (specific color, specific material, specific object)? | Vague prompts that could produce anything |
| **Character Fidelity** | Do character prompts match their 4b visual package? Right costume state, right palette, right signature detail? | Character described generically or inconsistently with their design |
| **Negative Compliance** | Do all prompts include the VLD's negative prompt list? | Missing "no dramatic backlighting," "no lens flare," etc. |
| **Angle Diversity** | Does the shot table use 3+ different camera angles? No two consecutive shots at the same angle+distance? | Monotonous angle progression, consecutive matching angles |
| **Sequence Coherence** | Is lighting system, palette, character costume, and time of day consistent across all shots and all prompts? | Continuity errors between shots that would break the edit |
| **Dynamic Camera** | Is at least 1 unconventional angle present (overhead, ground, through-object, etc.) with narrative motivation? | All shots at eye-level, or unconventional angles without story reason |
| **Edit Flow** | Does the shot sequence have a trajectory (escalation, de-escalation, reveal)? | Shots feel like a random collection rather than a designed edit |

---

## Multi-Scene Runs

When processing multiple scenes in sequence:

1. Load the VLD once at the start — it constrains all scenes equally
2. Process each scene independently — shot count is scene-specific
3. Cross-reference character appearances — if the same character appears in multiple scenes, their visual design must be consistent across all prompts
4. Flag scenes that share locations — the same location should have consistent environmental details across scenes

---

## Announce Block

> **Activating IP Engine — 6-SHOTS.**
> **Scene:** [title]
> **Hook:** [hook line]
> **Format:** 9×16 vertical
> **Style Lock:** [locked medium/aesthetic]
> **VLD loaded:** [world title] — palette, lighting, texture, negatives active.
> **Cast:** [character names in scene → Prompt Anchors loaded]
> **Location:** [location name → expanded from registry + 4c]
> **Decomposition:** [X] shots identified.
> **Generating:** 10 prompts per shot ([total] prompts).

---

**Exit:** Prompts ready for image generation. User selects, generates, mixes and matches.
