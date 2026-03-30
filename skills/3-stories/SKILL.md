---
name: 3-stories
description: "Find stories inside a completed world build. Unified generation engine runs 5 prompt families (~23 prompts) against the world bible, produces 10-12 story seeds, then develops user-selected seeds into full Story Windows via 5 Sauce Mothers. Optional stage — some worlds arrive with obvious stories. Router runs Quick Scan to surface existing entry points before committing to generation."
---

# 3-STORIES

Find stories inside a world. Produce narrative blueprints that renders and scenes build from.

---

## Summary

- **Find** stories inside a completed world build
- **Generate** 3-5 stories (core protagonist + ensemble) via unified prompt engine
- **Develop** 1-3 user-selected stories into full Story Windows
- **Evaluated** against 5 Sauce Mothers + 5 Kill Gates + Sacred Question Check

---

## Integration

- **Load:** `daniel-taste-profile/SKILL.md` → Full profile — emotional specificity needed for character work (REQUIRED)
- **Input:** Complete world build from 2-worlds — all stages (REQUIRED)
- **Reference:** `story-references.md` → Principle buckets, genre engine examples, anti-patterns (REQUIRED)
- **Reference:** `spacecadet-brand/SKILL.md` → Brand dimensions. Light check, not filter. (OPTIONAL)
- **Reference:** `universal-contexts/CTX-alien.md` → If alien dial adjustment needed (OPTIONAL)

---

## Quick Scan

Before generating, scan the world build for story entry points that already exist. Many worlds arrive from 2-worlds with characters, conflicts, and franchise vectors that ARE stories — they just haven't been named as such.

**Scan for:**
1. Characters with explicit need/want gaps
2. Faction conflicts that are already personal (not just systemic)
3. Franchise vectors that imply character arcs (not just format pitches)
4. The Sacred Question — does it already point at a specific character?

**Use them in conjunction with the seed stage ideation if applicable, but don't overindex on them.**

---

## Staged Development

Two stages. Each reviewable before proceeding.

### Stage 1: Seeds (load `3a-seeds.md`)

The world becomes a set of story doors.

**Run** 5 prompt families → **Bundle** character findings into story clusters → **Evaluate** against Sauce Mothers (light) + Kill Gates → **Present** 3-5 stories (protagonist + premise + ensemble).

**Exit:** User selects 1-3 stories for development.

### Stage 2: Arcs (load `3b-arcs.md`)

Selected seeds become full narrative blueprints.

**Develop** each selected story into a complete Story Window → **Apply** 5 Sauce Mothers with full rigor → **Stress-test** against world bible → **Sacred Question Check** → **Present** 1-3 Story Windows.

**Exit:** Story Windows ready for 4-vis-dev or 5-scenes.

---

## Announce Block

> **Activating IP Engine — 3-STORIES.**
> **World:** [world title]
> **Sacred Question:** [the world's Sacred Question]
> **Systems loaded:** [list active world systems]
> **Taste filter:** Active — full profile.
> **Stage 1:** Seeds (3-5 stories from prompt engine) → **Stage 2:** Arcs (1-3 Story Windows)

---

## Internal Verification (After Stage 2)

Silently check each Story Window against `story-references.md` anti-patterns.

**If all pass:** "These Story Windows are ready for renders — [one sentence on strongest quality]."

**If any concern:** Surface it in prose with a suggested fix. Don't display full gate results.

---

## Downstream

- **4-vis-dev** expects: protagonist + ensemble characters, key locations, emotional register, tonal registers (from Story Window)
- **5-scenes** expects: full Story Window as primary input
- **6-shots** expects: Hook image from seeds → money-shots
