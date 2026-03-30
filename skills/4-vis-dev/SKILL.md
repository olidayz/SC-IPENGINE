---
name: 4-vis-dev
description: "Visual development — define what this IP looks like as a system. Takes world bible + story window, produces Visual Language Document (art direction rules), character visual packages, and location visual packages. Three sub-skills in sequence: (1) Art Director establishes the visual grammar, (2) Characters applies it to people, (3) Locations applies it to spaces. Art direction runs first; characters and locations run in parallel after VLD approval."
---

# 4-VIS-DEV

Define what this IP looks like. Produce the visual rules that constrain everything downstream.

---

## Summary

- **Art-direct** the world — establish the visual grammar (color, light, material, composition, motifs)
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

Three sub-skills. Art direction is the bottleneck — everything depends on it.

### Stage 1: Art Director (load `4a-art-director.md`)

The rules. Establish the visual grammar that constrains everything downstream.

**Run** 5 perspective clusters (7 principles as lens) → **Synthesize** into Visual Language Document → **Gate check** → **PRESENT to user for review.**

**Exit:** User approves VLD (with adjustments). Proceed to Stage 2.

### Stage 2: Characters + Locations (load `4b-characters.md` and `4c-locations.md` — parallel)

Applications. Apply the VLD to people and spaces.

**Characters:** 3-6 from story window. Each gets a full visual package (silhouette, costume, props, faction, arc). Constrained by VLD.

**Locations:** 5-8 from story window + world build. Each gets a full visual package (atmosphere, texture, history, faction). Constrained by VLD.

**Gate check** on each → **Coherence checks (silent)** → **PRESENT** two-layer output.

### Two-Layer Output Structure (Stage 2)

The Stage 2 output serves two audiences: the human reviewing creative direction, and the downstream pipeline consuming visual data. Structure every Stage 2 output as:

| Layer | Purpose | Audience |
|-------|---------|----------|
| **1. Summary Tables** | Character Overview table + Location Overview table at the top of each section. One row per character/location. Scannable checkpoint with an Image Prompt column containing a ready-to-use generation prompt. | Human review + visual sampling |
| **2. Full Packages** | Complete character visual packages (6 principles) and location visual packages (6 principles) with full prose depth. Every detail the downstream stages need. | Pipeline (5-scenes, 6-shots, 7-motion) + human deep-read |

**Summary Table columns — Characters:** Character, Role, Silhouette, Palette, Signature Detail, Visual Arc, Image Prompt.
**Summary Table columns — Locations:** Location, Territory, Register, Key Visual Idea, Threshold, Image Prompt.

### Image Prompt Requirements

Image prompts live in the summary tables and serve as the visual sampling layer — direction confirmation, not production frames. 6-shots (Stage 6) generates production-quality prompts later.

**Characters:** Each prompt generates a two-panel split frame (LEFT close-up, RIGHT wide shot). The prompt must be self-contained, include VLD style anchors (e.g., "Fincher procedural," "Succession corporate"), specify lighting, palette, signature detail, and body-in-space. Approx 120-150 words.

**Locations:** Each prompt generates a single establishing shot capturing the location's key visual idea. Self-contained, includes VLD style anchors, specifies palette, lighting, architecture, key textures, and emotional register. Approx 80-120 words.

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

**Exit:** VLD + Characters (with image prompts) + Locations (with image prompts) ready for 5-scenes.

---

## Announce Block

> **Activating IP Engine — 4-VIS-DEV.**
> **World:** [world title]
> **Story:** [story window title]
> **Visual Mode:** [Constructed / Revealed / Hybrid]
> **Taste filter:** Active — aesthetic references + PASS/FAIL.
> **Stage 1:** Art direction (VLD) → **Review** → **Stage 2:** Characters + Locations (parallel)

---

## Downstream

- **5-scenes** expects: VLD (for shot-aware writing), character visuals (for action/description), location visuals (for scene-setting)
- **6-shots** expects: VLD (palette, lighting, composition rules), character designs + image prompts (for framing and consistency), location packages + image prompts (for establishing shots and spatial reference)
- **7-motion** expects: Complete visual package for animation consistency
