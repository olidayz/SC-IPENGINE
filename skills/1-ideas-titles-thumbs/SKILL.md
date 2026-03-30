---
name: ip-ideas-titles-thumbs
description: "IP Engine Stage 1: Generate original IP concepts at scale. Three sub-skills in sequence: (1) IDEAS generates 30-50+ divergent IP sparks using 8 ideation families with 73 lenses + 12 title construction moves, each spark as Title + Paragraph; (2) user selects favorites; (3) THUMBNAILS generates visual hook concepts for selected sparks using 17 perspectives across 5 clusters, filtering through 7 quality gates and 5 spreadability principles. Use when creating IP concepts, generating world seeds, brainstorming franchise premises, developing visual hooks for content, or any creative ideation for entertainment IP. Triggers: 'generate IP', 'IP concepts', 'world ideas', 'break this IP', 'thumbnail concepts', 'visual hooks', 'what does this look like', 'IP Engine', 'spark generation', 'premise ideas'."
---

# Stage 1: Ideas, Titles, Thumbs

Generate IP sparks, name them, visualize them.

## Workflow

```
Input → 1-IDEAS (divergent, 30-50+ sparks) → User Selection → 1B-THUMBNAILS (visual hooks for selected sparks) → 2-WORLDS
```

## What This Stage Does

Three things happen here, in sequence:

1. **Ideas** — Generate 30-50+ IP sparks using 8 ideation families (73 lenses) + 12 title moves. Each spark is a Title + Paragraph. Volume over depth. → `1-ideas.md`
2. **Selection** — User scans, marks favorites. Expand | Modify | Reject | More | Riff | Collide.
3. **Thumbnails** — Selected sparks get visual hooks. 100+ concepts internally, present Top 3 + 10-15 survivors. → `1b-thumbnails.md`

## Files

| File | Purpose | Load When |
|------|---------|-----------|
| `1-ideas.md` | Core generation engine — 8 ideation families, 12 title moves, 7 gates. Title construction patterns integrated. | Always (this is the main skill) |
| `1b-thumbnails.md` | Visual hook generator — 17 perspectives (5 clusters), 5 spreadability principles, 7 gates | After user selects sparks |
| `1-idea-modifiers.md` | Toggleable generation constraints — Violation Mode, Satiraverse, Anti-Taste. Lock one axis per modifier. Stack multiple. | When user requests a modifier |

## Dependencies

**Always load:**
- `daniel-taste-profile/SKILL.md` — taste filtering (REQUIRED)
- `1-ideas.md` — core generation (includes title construction)

**Load after selection:**
- `1b-thumbnails.md` — visual hooks for selected sparks

## Context Rule

Taste > Spacecadet Brand > Spec-Tech — involved but NOT over-influencing ideas. Tech seeds inform world expansion (Stage 2), not spark generation. Worlds informed but not overindexing ideas.

## Invocation

- "Generate IP concepts" → Load 1-ideas.md, run generation
- "Run the IP Engine" → Same as above
- "I need world concepts for [input]" → Same as above
- "Take [IP] and break it" → Same as above
- "Generate thumbnails for these" → Load 1b-thumbnails, run against selected sparks
- "Show me what these look like" → Same as above
- "Run in Violation Mode" → Load 1-idea-modifiers.md, apply Violation Mode constraint
- "Satiraverse mode" → Load 1-idea-modifiers.md, apply Satiraverse constraint
- "Anti-Taste" / "Invert taste" → Load 1-idea-modifiers.md, apply Anti-Taste constraint
