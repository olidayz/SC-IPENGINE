---
name: 4-vis-dev
description: "Visual development — define what this IP looks like as a system. Five sub-skills: (0) Style Lock selects the visual medium/aesthetic, (1) Art Director establishes the visual grammar, (2) Characters + Locations designed and named, (3) Casting generates 5 landscape variations per character — user selects, locked sheet + Prompt Anchor produced. Style Lock → VLD → Characters + Locations → Casting → Locked Sheets + Name Registry with Prompt Anchors."
---

# 4-VIS-DEV

Define what this IP looks like. Produce the visual rules that constrain everything downstream.

---

## Summary

- **Lock the style** — choose visual medium (live action, animation, anime, hybrid, etc.) with test prompts for comparison
- **Art-direct** the world — establish the visual grammar within the locked style (color, light, material, composition, motifs)
- **Design** 3-6 key characters as visual systems (silhouette, costume, props, arc)
- **Design** 5-8 key locations as visual systems (atmosphere, texture, history, faction)
- **Include** image prompts in summary tables for visual sampling and direction confirmation
- **Evaluated** against 7 Art Director principles, 6 Character principles, 6 Location principles + taste filter

---

## Integration

- **Load:** `daniel-taste-profile/SKILL.md` → Full profile — aesthetic refs + PASS/FAIL (REQUIRED)
- **Input:** Complete world build from 2-worlds — all stages (REQUIRED)
- **Input:** Story window from 3-stories — protagonist, ensemble, locations, emotional register (REQUIRED)
- **Reference:** `vis-dev-references.md` → Principle benchmarks, positive/negative examples (REQUIRED)
- **Reference:** `ip-engine-contexts/references/film-tv-references.md` → Visual benchmarking (OPTIONAL)
- **Reference:** `ip-engine-contexts/CTX-spacecadet-brand.md` → Brand dimension check (OPTIONAL)
- **Reference:** `universal-contexts/CTX-alien.md` → If alien dial adjustment needed (OPTIONAL)

---

## World Visual Mode Detection

Before generating, classify the world's visual nature. This informs how the perspective clusters weight their options.

| Mode | Signal | Approach |
|------|--------|----------|
| **Constructed** | Sci-fi, fantasy, alt-history — the world LOOKS different | Build the visual system from world mechanics outward. Material and Frame clusters lead. |
| **Revealed** | Thriller, drama, satire — the world looks familiar but FEELS different | Find the visual distortion within realism. Atmosphere and Emotion clusters lead. |
| **Hybrid** | Some elements constructed, some revealed | Layer the unfamiliar onto the familiar. All clusters balanced. |

---

## Staged Development

Five sub-skills. Style lock is the first gate, casting is the last.

### Stage 0: Style Lock (load `4-style-lock.md`)

The medium. Choose the visual style before building anything. Animation? Anime? Live action? Hybrid?

**Run** style recommendations (3-5 directions from `references/style-directions.md`) → **Generate** 4 vertical money shot test prompts per direction → **PRESENT to user for selection.**

**Exit:** User locks one style. All downstream work inherits it. **→ Save Style Lock to IP Bible (Stage 4: Visual Development > Style Lock).**

### Stage 1: Art Director (load `4a-art-director.md`)

The rules. Establish the visual grammar that constrains everything downstream.

**Run** 5 perspective clusters (7 principles as lens) → **Synthesize** into Visual Language Document → **Gate check** → **PRESENT to user for review.**

**Exit:** User approves VLD (with adjustments). Proceed to Stage 2. **→ Save VLD to IP Bible (Stage 4: Visual Development > VLD).**

### Stage 2: Characters + Locations (load `4b-characters.md` and `4c-locations.md` — parallel)

Applications. Apply the VLD to people and spaces.

**Characters:** 3-6 from story window. Each gets a full visual package (silhouette, costume, props, faction, arc). Constrained by VLD. **Each character gets a concept image generated** — a single visual that shows the character design before casting begins. This is not the locked cast — it's a "this is the vibe" image that lets the user see and adjust the design before committing to casting variations.

**Locations:** 5-8 from story window + world build. Each gets a full visual package (atmosphere, texture, history, faction). Constrained by VLD.

**Gate check** on each → **Coherence checks (silent)** → **Generate concept images per character** → **PRESENT** two-layer output with images.

### Two-Layer Output Structure (Stage 2)

The Stage 2 output serves two audiences: the human reviewing creative direction, and the downstream pipeline consuming visual data. Structure every Stage 2 output as:

| Layer | Purpose | Audience |
|-------|---------|----------|
| **1. Summary Tables** | Character Overview table + Location Overview table at the top of each section. One row per character/location. Scannable checkpoint with an Image Prompt column containing a ready-to-use generation prompt. | Human review + visual sampling |
| **2. Full Packages** | Complete character visual packages (6 principles) and location visual packages (6 principles) with full prose depth. Every detail the downstream stages need. | Pipeline (5-scenes, 6-shots, 7-motion) + human deep-read |

**Summary Table columns — Characters:** Character, Role, Silhouette, Palette, Signature Detail, Visual Arc, Image Prompt.
**Summary Table columns — Locations:** Location, Territory, Register, Key Visual Idea, Threshold, Image Prompt.

### Character Concept Images (Generated Before Casting)

Every character gets a **concept image** generated at this stage — BEFORE casting. This is the design preview: "here's what this character looks like based on the visual package." The user reviews the concept image and can adjust the design (costume, signature detail, silhouette, faction gradient) before committing to the casting step.

**This is NOT the cast.** The concept image shows the design direction — the costume, the world, the vibe. Casting (Stage 3 / 4d) finds the specific FACE to wear it. The concept image may show a generic or stylized figure; casting locks the actual person.

**User actions on concept images:**
- **Approve** → design confirmed, proceed to casting with this direction
- **Edit** → adjust the visual package (change costume, swap signature detail, shift palette) → regenerate concept image
- **Spacecadetify** → run brand dimensions against the character design, amplify strangeness → regenerate

### Image Prompt Requirements

Image prompts live in the summary tables and serve as the visual sampling layer — direction confirmation, not production frames. 6-shots (Stage 6) generates production-quality prompts later.

**Characters:** Each prompt generates a concept image showing the character in their primary environment. The prompt must be self-contained, include VLD style anchors (e.g., "Fincher procedural," "Succession corporate"), specify lighting, palette, costume, signature detail, and body-in-space. Approx 120-150 words. Generated inline via Image Gen API.

**Locations:** Each prompt generates a single establishing shot capturing the location's key visual idea. Self-contained, includes VLD style anchors, specifies palette, lighting, architecture, key textures, and emotional register. Approx 80-120 words. Generated inline via Image Gen API.

**Rules:**
- Every prompt is fully independent — no prompt references another prompt.
- Include VLD reference shorthand as style direction (not just labels).
- Include anti-prompt guidance where critical (e.g., "no heroic composition, no noir glamour").
- Prompts are platform-agnostic but optimized for the current generation tool.

### Coherence Checks (Silent — Surface Only on Failure)

Run all three coherence checks internally after packages are complete. If all pass, note in one line at the bottom: *"All coherence checks passed."* If any fail, fix before presenting. Only surface the specific failure to the user if it requires a creative decision.

**Ensemble Coherence (characters):**
- Silhouette distinction across all characters?
- Faction groupings read visually?
- Sufficient contrast between characters in the same scene?
- Protagonist visual identity carries the most weight?

**Spatial Coherence (locations):**
- Faction territories distinct through environment alone?
- Enough contrast between locations in different registers?
- Thresholds between spaces create visual events?

**Character-Space Coherence (combined):**
- Protagonist's visual design creates tension with their primary location?
- Opponent belongs in their power space?
- Characters crossing territories feel visually displaced?
- Protagonist's physical journey through locations mirrors internal arc?

### Stage 2 Output: The Registry

After characters and locations are complete, compile a **Name Registry** — the single source of truth for all named entities.

```
## Name Registry

### Characters
| Name | Role | Visual Shorthand |
|------|------|-----------------|
| [Full Name] | [story role — one phrase] | [3-5 word visual ID: "scarred cowboy, leather duster, bone spur"] |

### Locations
| Name | Territory | Visual Shorthand | Prompt Anchor |
|------|-----------|-----------------|---------------|
| [Place Name] | [faction or neutral] | [3-5 word visual ID] | [30-50 word portable visual description — paste verbatim into all downstream prompts] |
```

**Location Prompt Anchors are written during 4c** — not deferred to 6a. Every named location gets a prompt-ready visual description immediately so that scenes (Stage 5) and shots (Stage 6) both have visual weight behind the name.

**Downstream rule:** Every prompt in 5-scenes, 6-shots, and 6c-motion must use character and location names from the registry. Never role labels or generic descriptions.

**Exit:** VLD + Characters + Locations + Name Registry ready for casting.

### Stage 3: Casting (load `4d-casting.md`)

Cast the characters. Two phases per character:

**Phase 1 — Cast:** Generate 5 landscape (16:9) portrait variations per character. Same costume, same signature detail — different person wearing it. User selects one.

**Phase 2 — Lock:** Selected cast gets a full turnaround reference sheet (16:9, white background). A **Prompt Anchor** (30-50 words) is written — the portable locked description pasted verbatim into every downstream prompt.

**After casting, the full registry looks like:**

```
### Characters (Post-Casting)
| Name | Role | Visual Shorthand | Prompt Anchor |
|------|------|-----------------|---------------|
| [Full Name] | [story role] | [3-5 words] | [30-50 words — locked cast face/build + costume + signature detail. Paste verbatim.] |

### Locations (from 4c)
| Name | Territory | Visual Shorthand | Prompt Anchor |
|------|-----------|-----------------|---------------|
| [Place Name] | [faction or neutral] | [3-5 words] | [30-50 words — physical environment + materials + light + signature detail. Paste verbatim.] |
```

Both character and location Prompt Anchors are locked before Stage 5 (scenes) begins. Scenes use names for readability; shots expand names into Prompt Anchors for image generation.

**Exit:** VLD + Locked Character Sheets + Location Packages (with Prompt Anchors) + Name Registry ready for 5-scenes → 6a-shots.

---

## Announce Block

> **Activating IP Engine — 4-VIS-DEV.**
> **World:** [world title]
> **Story:** [story window title]
> **Visual Mode:** [Constructed / Revealed / Hybrid]
> **Taste filter:** Active — aesthetic references + PASS/FAIL.
> **Stage 0:** Style Lock → **Stage 1:** Art direction (VLD) → **Review** → **Stage 2:** Characters + Locations → **Stage 3:** Casting (5 variations → select → lock)

---

## Downstream

All downstream stages receive the **Name Registry** and must use proper names in every prompt and description.

- **5-scenes** expects: VLD, Name Registry, character visuals (for action/description), location visuals (for scene-setting). Scene descriptions use character names and location names — never role labels.
- **6-shots** expects: VLD, Name Registry, character designs + visual shorthands (for prompt consistency), location packages + visual shorthands (for establishing shots). Every shot prompt includes the character/location name AND their visual shorthand from the registry.
- **6c-motion** expects: Complete visual package, Name Registry. Motion prompts reference characters and locations by name.
