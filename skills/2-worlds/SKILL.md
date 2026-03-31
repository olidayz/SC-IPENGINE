---
name: 2-worlds
description: "Expand a selected spark from 1-IDEAS into a complete franchise-scale world package. Three stages: Core Identity (2 directions from 5-7), World Infrastructure (world texture, history, factions, conflicts, objects), Franchise Architecture (tonal range, formats, participation). Evaluated against world-references.md benchmarks."
---

# 2-WORLDS

Expand a selected spark from 1-IDEAS into a complete franchise-scale world package.

---

## Summary

- **Expand** a selected spark from 1-IDEAS
- **Develop** a complete franchise-scale world package
- **Containing** Core Identity (2 surviving directions from 5-7 generated), World Infrastructure, Franchise Architecture
- **Evaluated** against gates, Independence Test, Anti-Marvel Guards, Reference Calibration in `world-references.md`

---

## Integration

- **Load:** `daniel-taste-profile/SKILL.md` → PASS/FAIL criteria + reference tags (REQUIRED)
- **Reference:** `world-references.md` → gates, benchmarks, anti-patterns, verification checklist (REQUIRED)
- **Reference:** `spacecadet-brand/SKILL.md` → brand dimensions at ~25% weight. Light reference for territory, not a filter. (OPTIONAL at Stage 1, checked silently at Stage 2)
- **Reference:** `speculative-tech-seeds/SEEDS.md` → optional enrichment at Stage 2 only. Do not load at Stage 1.

---

## Spark Type Detection

Before generating, identify the spark type. This determines how the world gets built.

| Type | Signal | Approach |
|------|--------|----------|
| **IP-Referenced** | Spark names or clearly riffs on existing characters, settings, franchises, or cultural properties | Build FROM the existing IP's bones — keep its characters, settings, recognizable elements, internal logic. Expand, reinterpret, deepen. Don't replace with original worldbuilding. |
| **Original** | Spark is a concept, collision, or premise with no existing IP anchor | Build a new world from scratch using the full Core Identity process. |
| **Hybrid** | Spark mashes existing IP with a new concept or another IP | Preserve what's recognizable from the source IP. Let the new concept reshape it, not replace it. |

If IP-Referenced or Hybrid: the existing IP's world, characters, and logic are *material*, not inspiration. The skill builds on top of them, not alongside them.

**Hard routing for Hybrid/IP-Referenced:** Before generating any directions in Stage 1 (Core), explicitly identify the source IP elements that MUST appear in every surviving direction: characters, settings, objects, visual language, cultural catchphrases, and real-world origin story. These are non-negotiable building material. The IP DNA Gate in `2a-core.md` enforces their presence — any direction that fails the Swap Test (could you replace this source IP with a different one and get the same world?) is rewritten, not killed.

---

## Staged Expansion

Three stages. Each reviewable before proceeding.

### Stage 1: Core (load `2a-core.md`)

The spark becomes a world with an identity.

**Generate** 5-7 core identities internally → **Filter** through infrastructure check → **Integrate** best cutting room floor material into survivors → **Present** 2 enriched directions. Cutting room floor shows only what wasn't absorbed.

No speculative tech seeds at this stage. No explicit Spacecadet dimension tagging in output. The World Premise should be social, cultural, or allegorical first — speculative mechanisms enter at Stage 2 if needed.

**Exit:** User picks a direction (or hybridizes) before Stage 2. **→ Save approved direction to IP Bible (Stage 2: World > Core Identity).**

### Stage 2: World (load `2b-world.md`)

The identity becomes an inhabitable place.

**Contains:** Speculative Layer (optional enrichment — tech seeds load here if needed), World Texture, History, Factions (with territory, contested rivals, and character archetypes integrated), Conflicts, Objects & Artifacts

**Exit:** User confirms world before scaling to franchise. **→ Save approved world to IP Bible (Stage 2: World > World Build).**

### Stage 3: Franchise (load `2c-franchise.md`)

The world becomes a multi-format, multi-decade IP.

**Contains:** Tonal Range, Expansion Vectors (3 films, series, game, VV), How Fans Join (merged participation + physical objects)

Re-introduce key world elements with brief reminders — don't assume the user remembers Stage 1/2 terminology. Final verification runs invisibly; surface only specific concerns.

**Exit:** Complete expansion passes internal verification against `world-references.md`. World is ready for Stage 3 — Renders. **→ Save approved franchise architecture to IP Bible (Stage 2: World > Franchise).**

---

## Announce Block

> **Activating IP Engine — 2-WORLDS.**
> **Spark type:** [IP-Referenced / Original / Hybrid]
> **Expanding:** [spark title]
> **Context loading:** Tech seeds [OFF until Stage 2]. Spacecadet brand [~25%, light reference].
> **Stage 1:** Core (2 directions) → **Stage 2:** World → **Stage 3:** Franchise

---

## Internal Verification (After All Stages)

Silently run the complete expansion against `world-references.md`. Don't display as a table.

**If all pass:** "This world is ready for Stage 3 — [one sentence on strongest quality]."

**If any fail:** Surface the specific concern in prose with a suggested fix. Don't list full gate results.
