---
name: short-form
description: "Alt pipeline for short-form viral content. Branches from Stage 1 when a spark is punchy enough to skip world-building and go straight to production. Produces: loops (3-5s), punches (5-15s), carousels, micro-trailers, and character intros. No stills — everything is motion. Two-step pipeline: Concept Lock (angle + format + viral mechanic) → Production Prompt (generation-ready). Triggers: 'make this a meme', 'short-form', 'viral', 'quick hit', 'make this punchy', 'skip the pipeline', 'social content', 'trailer for this', 'character intro', 'loop this'."
---

# SHORT-FORM

Alt pipeline. When a spark doesn't need a world — it needs a feed.

```
IDEAS → spark selected → SHORT-FORM
  ├── Concept Lock (angle + format + viral mechanic + copy)
  └── Production Prompt (generation-ready assets)
```

Not every idea wants 6 stages. Some ideas are born viral — one image, one loop, one 10-second gut-punch. This pipeline catches those and produces them fast.

---

## When to Branch Here

A spark from Stage 1 (or a standalone concept) enters the short-form pipeline when:

| Signal | Example |
|--------|---------|
| **The punchline IS the premise** | "DRACULA IS DEAD" — you don't need a world bible to make this hit. The title is the content. |
| **Single-image energy** | The concept resolves in one frame, not a franchise. |
| **Format-native** | The idea already feels like a specific social format — a meme, a loop, a carousel, a character reveal. |
| **Speed over depth** | The viral window is now, not after 6 stages of development. |
| **Standalone power** | No world context needed. The image/video works for someone with zero lore. |

**This pipeline can also run AFTER the full pipeline** — take a completed IP with VLD, cast, locations, and produce short-form content from it. In that case, it inherits the Style Lock, Prompt Anchors, Set Sheets, etc.

---

## Formats

Everything is motion. No stills. No single images. If a concept feels like "one frame" — make it a loop or a punch.

**LOOP** — Seamless Video
3-5 seconds. Hypnotic. The end flows into the beginning. Infinite scroll fuel.
- **Aspect:** 9:16 vertical
- **Output:** 1 video prompt (subject action + camera + environment loop point)

**PUNCH** — One-Hit Video
5-15 seconds. One idea. One escalation. One payoff. Done.
- **Aspect:** 9:16 vertical
- **Output:** 3-5 shot prompts sequenced as a micro-edit

**CAROUSEL** — Swipe Story
3-7 frames. Each swipe reveals. The format IS the tension.
- **Aspect:** 1:1 or 4:5 (platform-native)
- **Output:** 3-7 generation-ready prompts, sequenced

**MICRO-TRAILER** — World in 15-45 Seconds
Compressed Transmission. Density from frame one. Enough to make someone say "what IS this."
- **Aspect:** 9:16 vertical
- **Output:** 8-15 shot prompts + motion prompts, sequenced
- **Reference:** `5-scene-builder/references/trailer-logic.md`

**CHARACTER INTRO** — Meet [Name]
One character. 5-15 seconds. No dialogue. Presence, environment, signature detail, contradiction.
- **Aspect:** 9:16 vertical
- **Output:** 3-5 shot prompts + motion prompt
- **Reference:** `5-scene-builder/references/trailer-logic.md`

---

## Files

| File | Purpose | Load When |
|------|---------|-----------|
| `sf-concept.md` | 3 Rounds: Seeds → Stories → Format. 9 collision categories, 4 gates, 15 angles, copy moves. | Always first |
| `sf-prompt.md` | Production prompts — shot-by-shot (plain language + JSON), full sequence prompt, first frame prompt. | After Round 3 (format locked) |
| `sf-series.md` | 8 series structures for turning one-offs into content systems. | When building recurring content |
| `references/scroll-grammar.md` | 18 First Frame openers, vertical composition zones, feed color rules, text rules, motion grammar. | **Load at Round 3** (first frame decision) + **sf-prompt** (frame composition) |
| `references/pacing-science.md` | Attention curve, 7 cut rhythms, re-hook techniques, shot duration rules, payoff types. | **Load at sf-prompt** (multi-shot pieces only: punch, micro-trailer, character intro) |

---

## Integration

### Standalone (branching from Stage 1)
- Spark from 1-IDEAS (title + logline)
- Taste profile (always on)
- Spacecadet brand calibration (background)
- No VLD, no cast, no locations required — the concept is self-contained

### Post-Pipeline (branching from completed IP)
- Everything from the full pipeline is available:
  - Style Lock → locked medium/aesthetic for all prompts
  - Name Registry → character names + Prompt Anchors, location names + Prompt Anchors
  - Set Sheets → environment descriptions for location-based content
  - VLD → palette, lighting, negatives
- Short-form inherits all of this. Prompts paste Prompt Anchors verbatim.

---

## Key Terminology

| Term | Meaning |
|------|---------|
| **Angle** | The creative approach to the concept — HOW you attack it (was "Hook Move") |
| **Concept** | The idea itself — WHAT the piece is about (was "Hook") |
| **Play** | A specific creative pattern within a format — a move you can make |
| **Mechanic** | A structural driver of virality — WHY it spreads |

---

## Announce Block

> **Activating IP Engine — SHORT-FORM.**
> **Input:** [spark title or IP name]
> **Mode:** [Standalone / Post-Pipeline]
> **Output:** [Loop / Punch / Carousel / Micro-Trailer / Character Intro]

---

## Downstream

Short-form content is terminal — it produces generation-ready prompts, not material for further stages. But it can:
- Feed back into the full pipeline if a short-form hit reveals franchise potential ("this went viral — build the world")
- Generate series (multiple character intros, carousel series, punch series)
- Produce platform-specific variants of the same concept
