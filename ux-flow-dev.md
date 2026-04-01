# IP Engine — Dev Spec

Every screen, every API call, every state, every edge case. Implementation notes in **`DEV:`** blocks.

---

## Architecture

```
Frontend (Next.js / React)
    │
    ├── API Layer (your backend)
    │     │
    │     ├── Claude API ──── all creative text generation
    │     ├── Image Gen API ── image generation (user picks provider)
    │     └── Video Gen API ── video generation from stills/prompts
    │
    └── Database (Postgres / Supabase)
          └── IP Bible (one record per project, JSONB)
```

> **DEV: API layer abstraction is critical.** The Image Gen and Video Gen APIs must be provider-agnostic — the user picks Midjourney, DALL-E, Flux, etc. in settings, and your backend routes to the right provider. Same interface, different backends. Claude API is always Anthropic.

> **DEV: The IP Bible is the single source of truth.** Every screen reads from it, every approval writes to it. It's a JSONB column on the project record. When context is needed for a Claude call, you read the relevant bible sections and pass them as input. The bible IS the context window.

> **DEV: Claude calls use structured output.** Every Claude call should return JSON, not prose. The skill files (`.md` files in the `skills/` directory) are the system prompts. Your backend constructs the Claude call by: (1) loading the relevant skill file as system prompt, (2) injecting bible context as user message, (3) requesting structured JSON output. Parse the JSON and render as UI components.

---

## 0. DASHBOARD

**Screen:** Project grid/list.

| Element | Detail |
|---------|--------|
| Project card | Title, thumbnail image (from Stage 1b if exists), current stage badge, last edited date |
| Progress indicator | Dots or progress bar showing which stages are complete |
| [+ New Project] | Routes to Session Config |
| Click existing project | Routes to Project Home at last active stage |

> **DEV: The thumbnail on the project card comes from `bible.stage1.thumbnails[0].image_url` (first selected thumbnail). If no thumbnails yet, show a placeholder with the project seed text. The current stage comes from `bible.current_stage`.**

---

## 0.1 SESSION CONFIG

**Screen:** New project setup form. Single page.

| # | Control | UI Component | Default | DB Field | Conditional |
|---|---------|-------------|---------|----------|-------------|
| 1 | **Pipeline** | 3-button toggle: Full / Short-Form / Both | Full | `config.pipeline` | **This is first.** Selection changes which fields below are visible. |
| 2 | **Seed** | Text input (large, prominent). Placeholder: "What's your idea?" | Required | `seed` | Always visible |
| 3 | **Alien Dial** | Slider 1-10. Show description label that updates as slider moves (e.g. "7 — Uncomfortable territory") | 7 | `config.alien` | Always visible |
| 4 | **SC Dimensions** | 4 toggle chips: Sci-Fi, Surreal, Spiritual, Satiraverse. Toggled = emphasized (highlighted). Min 2 must be on. | All on | `config.dimensions[]` | Always visible |
| 5 | **Tech Seeds** | Multi-select dropdown. Options: Body & Life, Mind, Space & Time, World & Environment, Society & Control, Transport & Movement, Machines & Weapons, None. | None | `config.seeds[]` | **Hidden when pipeline = Short-Form** |
| 6 | **Modifiers** | Checkbox group: Violation Mode, Satiraverse, Anti-Taste. Plus: Emotional Register dropdown (WOW/NAH/HMM/NSFW/LOL/WTF/UGH). Plus: Contrast Mode toggle (enables second emotion dropdown). | None | `config.modifiers` | Always visible. Contrast Mode only shows second dropdown when toggled. |
| 7 | **Taste Filter** | Toggle: On / Off | On | `config.taste_filter` | Always visible |

**Action:** [Start Project →] — creates project record in DB, writes config to bible, routes to Stage 1.

> **DEV: The pipeline toggle is the first interaction. Implement conditional rendering — when user picks "Short-Form", hide the Tech Seeds control and simplify the modifier options. When "Both" is selected, show everything. Store as enum: `"full" | "short_form" | "both"`.**

> **DEV: Alien dial — use a range input. On change, update a label next to it. Labels: 1-2 "Safe", 3-4 "Subtly off", 5-6 "Breaking conventions", 7-8 "Uncomfortable territory" (bold this one as default), 9-10 "Parallel universe".**

> **DEV: SC Dimensions — implement as toggle chips, not checkboxes. Validation: at least 2 must be active. If user tries to deactivate a third, show inline error "Minimum 2 dimensions required."**

> **DEV: Modifiers — these are Stage 1 only. They're sent to Claude with the ideas prompt. They don't affect any other stage. But they're stored in the bible config so we know how the ideas were generated.**

---

## 1. STAGE 1: IDEAS

### 1.1 Spark Generation

**Trigger:** User arrives from Session Config, or hits [Regenerate].

**API Flow:**
1. Backend reads `bible.config` + `bible.seed`
2. Backend loads `skills/1-ideas-titles-thumbs/1-ideas.md` as system prompt
3. Backend loads context files: `CTX-taste-profile.md`, `CTX-spacecadet-brand.md`, `CTX-alien.md`
4. If modifiers active: also load `1z-idea-modifiers.md`
5. Send to Claude API with instruction to return JSON array: `[{ title, logline }]`
6. Parse response, write to `bible.stage1.sparks[]`

**UI:** Grid of spark cards (responsive — 2 col mobile, 3-4 col desktop).

| Card Element | Detail |
|-------------|--------|
| Title | Large, bold. 1-5 words. |
| Logline | 2 sentences beneath title. Smaller, lighter color. |
| Action row | 4 buttons: ♥ Select, ✎ Develop, ↻ Modify, ⚡ Collide |
| Selected state | Card border highlight + added to sidebar selection tray |

**Top bar:** Spark count ("38 sparks"), [Regenerate All] button, active modifier badges.

**Sidebar tray:** Shows selected sparks. Actions: [→ Thumbnails], [→ Build World], [→ Short-Form].

> **DEV: Each action button triggers a different Claude call:**
> - **♥ Select** — client-side only. Toggle `selected: true` on the spark object. Add to sidebar tray.
> - **✎ Develop** — Claude call: "Expand this logline into a full paragraph." Returns `{ developed_text }`. Append to card inline (accordion expand). Write to `bible.stage1.sparks[i].developed_text`.
> - **↻ Modify** — Opens small modal with text input: "How should this change?" Claude call with spark + user instruction. Returns replacement `{ title, logline }`. Replace card in place.
> - **⚡ Collide** — Opens modal: either pick another spark from the grid, or type a freeform concept. Claude call with both inputs. Returns new `{ title, logline }`. Add as new card to the grid.

> **DEV: [Regenerate All] re-runs the full Claude call. It does NOT delete existing sparks — it appends a new batch. User can scroll through multiple generations. Store a `generation_batch` field on each spark so UI can group them.**

> **DEV: Routing from selection tray:**
> - [→ Thumbnails] — requires 1+ selected. Routes to Stage 1b.
> - [→ Build World] — requires exactly 1 selected. Routes to Stage 2 (skips thumbnails).
> - [→ Short-Form] — available per-spark (not just selected). Routes to Stage 7 with that spark as seed.

---

### 1.2 Thumbnails

**Trigger:** User selects sparks and hits [→ Thumbnails].

**API Flow (per selected spark):**
1. Claude call: load `1b-thumbnails.md` as system prompt + spark + config. Return `[{ name, visual_description, prompt }]` (5 items).
2. **Immediately** fire Image Gen API for each prompt. 5 parallel image gen calls.
3. Write prompts + image URLs to `bible.stage1.thumbnails[]`

**UI:** One spark at a time (or tabbed if multiple selected). 5 image cards in a row.

| Card Element | Detail |
|-------------|--------|
| Image | 9:16 vertical. Loading spinner until gen completes. |
| Concept name | Below image |
| Actions | ♥ Select, ↻ Regen (same prompt, new image), ✎ Edit Prompt |

Below grid: [Generate 5 More] — new Claude call for 5 more concepts + 5 more image gen calls.

> **DEV: Image Gen is the first place you hit external APIs. Key implementation:**
> - Fire all 5 image gen calls in parallel (Promise.all).
> - Show placeholder cards with loading spinners immediately.
> - As each image resolves, swap spinner for image. Don't wait for all 5.
> - Store: `{ spark_id, concept_name, prompt_text, image_url, image_gen_provider, selected: false }`
> - **↻ Regen** re-fires the image gen API with the SAME prompt. Different seed/randomization produces a different image. Replaces the image URL on the same record.
> - **✎ Edit Prompt** opens a modal with the raw prompt text in a textarea. User edits → [Generate] → image gen API → new image. Creates a NEW thumbnail record (preserves the original).

> **DEV: The prompts from Claude are plain text strings, NOT JSON at this stage. They're written in natural language optimized for image gen tools. Store the raw prompt string.**

---

## 2. STAGE 2: WORLD

**Pattern: Card Grid with Progressive Disclosure.** Used for all 2.x stages.

> **DEV: All world sub-stages (2a, 2b, 2c) follow the same UI pattern. Build a reusable `<CardGrid>` component that takes structured JSON and renders cards. Each card needs: title, summary (always visible), full content (expandable), and an action row (approve/edit/regen/spacecadetify). The card component is reused in Stage 3 too.**

### 2a — Core (2 Directions)

**API Flow:**
1. Claude call: `2a-core.md` + spark + config. Returns 2 direction objects, each with `_summary` fields for every section.

**UI:** Two side-by-side card columns. Each column is one direction, rendered as a vertical stack of cards (Sacred Question, Premise, Tension, Allegory, Myth, Rules).

**Key interaction:** User picks A, B, or Hybridize. 
- Pick A/B: write selected direction to `bible.stage2.core`, discard other.
- Hybridize: opens modal with text input ("What to take from each?"). Claude call with both directions + user instruction. Returns hybrid direction. Shown as third column. User approves or iterates.

> **DEV: Each card in the direction column has a `_summary` field (1-2 sentences) and a `_full` field (complete content). Default state: collapsed (show summary only). Click/tap expands to full. The card grid must support this progressive disclosure — don't render full content until expanded (performance).**

> **DEV: Hybridize is an iterative loop. The modal stays open, the hybrid appears as a new column. User can say "more of A's tension, less of B's myth" — Claude re-generates. Track hybridize iterations in `bible.stage2.core.hybridize_history[]` for the change log.**

### 2b — World Build

**API Flow:**
1. Claude call: `2b-world.md` + approved core + config (tech seeds load here). Returns structured JSON with all sections + summaries.
2. **Auto-fire Image Gen** for each faction: Claude's output includes a `faction_image_prompt` per faction. Fire image gen calls in parallel.

**UI:** Card grid. Top row: Speculative Layer, World Texture, History (rendered as mini-timeline). Below: Faction cards (special — see below). Bottom: Conflicts, Objects & Artifacts.

**Faction cards are special:**

| Element | Detail |
|---------|--------|
| Color indicator | Left border color per faction (auto-assigned from VLD palette later, placeholder now) |
| Concept image | Generated inline. Loading spinner → image. 1:1 aspect. |
| Summary | 2 lines, always visible |
| Expandable sub-sections | Territory, Values, Rivals, Character Archetypes, Visual Identity |
| Action row | ✓ ✎ ↻ 🛸 + [→ Short-Form] |

> **DEV: Faction images fire automatically when the world build loads. Don't wait for user to click. The Claude output includes a `faction_image_prompt` field per faction — route this to image gen API. Show spinner in the image area until complete. Store URL in `bible.stage2.world.factions[i].concept_image_url`.**

> **DEV: [→ Short-Form] on a faction card creates a new short-form entry in `bible.short_form[]` with the faction as the seed concept. Routes to Stage 7 (short-form). The faction name, summary, and concept image carry over as context.**

> **DEV: Bottom of the card grid: [Approve All Remaining] button. This bulk-approves every card that hasn't been individually addressed. It writes `approved: true` on each card. Only appears when at least half the cards are already approved individually (prevent lazy bulk-approve of everything).**

### 2c — Franchise

**API Flow:** Claude call: `2c-franchise.md` + approved world. Returns structured JSON.

**UI:** Same card grid. Specific card types:
- **Tonal Range** — rendered as 4 tabs or side-by-side mini-cards (Core, Light, Dark, Weird) within one container card.
- **Expansion Vectors** — one card per format (Film 1, Films 2-3, Series, Game, Short-Form). Each is a mini-pitch.
- **How Fans Join** — single card with expandable participation paths.

> **DEV: Tonal Range card is a compound component — it contains 4 sub-sections that can each be edited independently. Implement as tabs within the card, or as 4 horizontal mini-cards. Each sub-section writes to `bible.stage2.franchise.tonal_range[register]`.**

---

## 3. STAGE 3: STORIES

### 3a — Seeds

**API Flow:** Claude call: `3a-seeds.md` + full bible (world). Returns 3-5 story objects.

**UI:** Story cards. Each card:

| Element | Detail |
|---------|--------|
| Title + logline | Always visible |
| Expand | Protagonist (name, position, premise, wound, hook), ensemble list |
| Actions | ♥ Select for development, [→ Short-Form] |

> **DEV: Selection is multi-select, 1-3 seeds. When user hits [Develop Selected →], fire one Claude call per selected seed for Stage 3b. These can run in parallel — each is independent. Show a stepper/tab UI for multiple story windows.**

### 3b — Story Windows

**API Flow (per seed):** Claude call: `3b-arcs.md` + selected seed + full bible. Returns structured JSON with per-section summaries.

**UI:** Card grid with special layouts:

| Section | UI Component | Notes |
|---------|-------------|-------|
| **Setup** | Standard card | Summary + expandable prose. |
| **Protagonist ↔ Opponent** | **Split card** — two cards side by side with "VS" divider in the middle | Both independently editable. The visual opposition IS the point. |
| **Premise** | Standard card | Shows Trait → Action → Consequence as a chain/flow. |
| **Pressure Cooker** | **Timeline component** — horizontal line with 5 nodes: Inciting Event, Comp 1, Comp 2, Comp 3, Clock | Each node has a label + 1-sentence summary. Click node to expand detail. Entire timeline has its own action row. |
| **Collision** | Standard card | "The discovery" + expandable Before/After worldview shift. |
| **Cost** | Standard card | Gained / Lost + Sacred Question response. |

> **DEV: The Protagonist/Opponent split card is a custom component. Two `<Card>` components in a flexbox with a vertical divider. The divider shows "VS" centered. Each side is independently editable — if user edits the Protagonist, it doesn't regenerate the Opponent. But if user hits ↻ Regen on either side, the Claude call includes BOTH sides as context (they're a pair).**

> **DEV: The Pressure Cooker timeline is a custom component. Horizontal flex layout with circles (nodes) connected by lines. Each node: colored circle → label below → 1-line summary. Click/tap a node to expand its detail in a popover or inline expansion. The whole timeline has an action row below it. When user hits ↻ Regen on the timeline, Claude regenerates ALL nodes (they're a sequence — can't regenerate one in isolation).**

> **DEV: Collision and Cost cards are a pair — render them side by side at the same width, at the bottom of the grid. They're the story's payoff — visually they should feel like the destination everything above was building toward.**

---

## 4. STAGE 4: VISUAL DEVELOPMENT

### 4.0 — Style Lock

**Two-part screen:** Anchor picker at top, style recommendations below.

#### Part 1: Reference Anchors

| Element | Detail |
|---------|--------|
| Search input | Autocomplete. Searches `anchor-library.md` entries (500+ records). |
| Category tabs | Directors, Films, TV, Movements, Music, Brands. Filter search results. |
| Selected anchors (max 3) | Cards below search. Each shows: category badge, name, editable Take input, editable Leave input, × remove. |
| Pre-fills | When user selects from library, Take/Leave fields auto-fill from `anchor-library.md` defaults. User can override. |
| Free text | If typed text doesn't match library, create custom anchor. Take/Leave fields are blank. |

> **DEV: The anchor library (`anchor-library.md`) should be parsed at build time into a searchable JSON index. Structure: `[{ name, category, default_take, default_leave }]`. Fuzzy search on name. Filter by category. Store selected anchors in `bible.stage4.style_lock.anchors[]`.**

> **DEV: The anchor picker MUST be completed before [Generate Recommendations] is available. Minimum 1 anchor, max 3. If user tries to generate without anchors, show inline prompt "Set at least 1 reference anchor."**

#### Part 2: Style Recommendations

**API Flow:**
1. Claude call: `4-style-lock.md` + `style-directions.md` + anchors + spark + world + story. Returns 3-5 style directions with 4 prompts each.
2. Image Gen API: 4 images per direction (batch, parallel). 12-20 total.

**UI:** Style direction cards. Each card:

| Element | Detail |
|---------|--------|
| Direction name | Bold. e.g. "Anime × Western" |
| Lock type badge | "Medium", "Aesthetic", or "Medium × Aesthetic" |
| Pitch | 2 lines — why this style fits the IP |
| Anchor connection | 1 line — how this connects to the user's reference anchors |
| 4 test images | 2×2 grid. Labels: Face, World, Moment, Icon. Each with ↻ Regen. |
| Risk | 1 line, smaller text, muted color |
| Radio select | Only one direction can be selected |

**Actions:** [Lock Style] (active when one direction selected), [More Directions] (new Claude call), [Change Anchors] (scrolls back to picker, clears recommendations).

> **DEV: The 4 test images per direction should render as a 2×2 grid with labels. Fire all image gen calls for all directions in parallel (12-20 concurrent calls). Show spinners. Stagger completion is fine — each image appears as its own gen completes.**

> **DEV: [Lock Style] writes to `bible.stage4.style_lock`: `{ lock_type, medium, aesthetic, prompt_dna, anchors[] }`. The `prompt_dna` field is a string of keywords extracted from `style-directions.md` for the selected style — these keywords get injected into EVERY downstream image/video prompt. This is the most important persistence field in the whole system.**

> **DEV: After locking, the user CANNOT change the style without an explicit "Unlock" action that triggers a confirmation dialog: "Changing the style will affect all downstream visuals. Continue?" Changes are logged in `bible.change_log[]`.**

### 4.1 — VLD (Art Direction)

**API Flow:** Claude call: `4a-art-director.md` + all prior stages + style lock. Returns full VLD as structured JSON.

**UI:** Styled document with card-like sections. Each section collapsible with action row.

| Section | Render As |
|---------|----------|
| Visual Signature | Prose paragraph |
| Palette × Light × Material | Table (rows = zones/factions) |
| Composition × Tonal Register | Table (rows = registers) |
| Time Layers | Table (rows = eras) |
| Visual Motifs | Table (rows = motifs) |
| References / Anti-References | Tables |
| Downstream Translation | **Code block** (highlighted, read-only by default, editable on click) |

> **DEV: The Downstream Translation section is the most operationally important part of the VLD. It contains keyword strings that flow into every prompt. Render it as a highlighted code block. Store as `bible.stage4.vld.downstream_translation` — a flat object with keys like `palette_anchors`, `lighting_keywords`, `texture_keywords`, `composition_cues`, `negative_prompts`. These get injected into every Scene Template and every shot prompt downstream.**

> **DEV: Each table in the VLD should be rendered as an editable data grid. User can click a cell to edit. Changes save immediately to bible. No need to "approve" individual cells — the VLD is approved as a whole unit.**

### 4.2 — Characters + Locations

**API Flow:**
1. Claude call: `4b-characters.md` + `4c-locations.md` + VLD + story window. Returns characters[] + locations[], each with image prompts.
2. Image Gen API: 1 concept image per character + 1 establishing shot per location. Fire in parallel.

**UI:** Two tabs: Characters | Locations.

**Characters tab:**

| Element | Detail |
|---------|--------|
| Summary table | One row per character. Columns: Name, Role, Silhouette (brief), Palette, Signature Detail. |
| Concept image | Generated inline per character. Shows character in environment — the design direction, NOT the final cast face. |
| Expandable package | Full 6-principle visual package below each row. |
| Actions per character | ✓ Approve design, ✎ Edit (opens package for inline editing), ↻ Regen (new Claude call for this character only), 🛸 Spacecadetify, [→ Short-Form] |

**Locations tab:** Same pattern — summary table + establishing shot image + expandable package + Prompt Anchor visible.

> **DEV: Concept images are NOT the cast. They show the design direction — costume, signature detail, body in environment. The face/features may be generic or stylized. Make this clear in the UI: add a label beneath each concept image: "Design preview — casting finds the face." This prevents user confusion about why the character looks different after casting.**

> **DEV: The Name Registry is auto-populated from this stage. Build it as a sidebar component that updates in real-time as characters and locations are created/renamed. Structure: `bible.name_registry.characters[]` and `bible.name_registry.locations[]`. Each entry has `name`, `role/territory`, `visual_shorthand`. Locations also get `prompt_anchor` written here.**

> **DEV: Editing a character's visual package → [Regenerate Concept Image] should be a single button that: (1) sends the edited package to Claude to generate a new image prompt, (2) fires image gen with the new prompt, (3) replaces the concept image. The old image is kept in a version history: `bible.stage4.characters[i].concept_image_history[]`.**

### 4.3 — Casting

**UI:** Stepper — one character at a time. Progress indicator shows which characters are done.

**Per character:**

**API Flow:**
1. Claude call: casting prompts. Returns 5 variation prompts.
2. Image Gen: 5 landscape (16:9) portraits. Parallel.
3. After user selects: Claude call to write Prompt Anchor (30-50 words).
4. Image Gen: 1 turnaround sheet (front, 3/4, profile).

**UI for each character:**

| Element | Detail |
|---------|--------|
| Character info | Name + visual shorthand at top |
| 5 portraits | 16:9 landscape cards in a row. Radio select (only one). Each has ↻ Regen and ✎ Edit Prompt. |
| Confirmation | After selection: "This is [Name]" confirmation message + displayed Prompt Anchor text (editable) |
| Turnaround sheet | Generated after confirmation. Full reference sheet shown below. |

**After all characters cast:** Cast overview page — all locked sheets in a grid. Name Registry updated with Prompt Anchors. [Approve Cast →] proceeds.

> **DEV: Prompt Anchors are the MOST CRITICAL text in the entire system. The 30-50 word description for each character gets copy-pasted VERBATIM into every downstream prompt. Store as `bible.stage4.cast[i].prompt_anchor_text`. This field must be: (1) editable by the user, (2) never auto-truncated, (3) never modified by any downstream process. It's a copy-paste source.**

> **DEV: The Prompt Anchor is initially written by Claude based on the selected variation. Show it to the user in an editable text field. If they modify it, that modified version becomes the locked anchor. Important: the user might want to add details Claude missed ("she has a scar on her left temple") or remove details that aren't rendering well. Let them.**

> **DEV: Stepper navigation: [← Previous Character] and [Next Character →]. User can go back and re-cast a character. Re-casting overwrites the previous selection but old images are kept in history. Also support [Skip to Cast Overview] for users who want to see all characters at once before approving.**

---

## 5. STAGE 5: SCENES

**API Flow:** 5 sequential Claude calls (one per invocation). Each call includes the exclusion list from prior invocations to prevent duplicates.

**UI:** Tabbed interface (5 tabs: Extract, Invent, Weird, Participation, Counter). Each tab shows ~50 scene cards.

| Card Element | Detail |
|-------------|--------|
| Scene number | e.g. [047] |
| Title | Bold |
| Hook line | 1 sentence, uses character/location names |
| Actions | ♥ Select, 🗑 Skip (greys out the card) |

**Sidebar tray:** Curated scenes. Shows count, reorderable via drag-and-drop. Persists across all 5 tabs.

**After all 5 invocations:** Spine Report shown as a summary panel below the tabs.

**Bottom bar:** [Finalize Curation →] locks the curated scene list.

> **DEV: Scenes are generated in sequence — don't fire all 5 Claude calls at once. After invocation 1 completes, construct an exclusion list (territories covered + scene titles) and pass it to invocation 2. This prevents duplicate scenes across invocations. Store each invocation's output separately: `bible.stage5.scenes_by_invocation[0..4]`.**

> **DEV: The sidebar tray persists across tabs. User selects scenes from any invocation — the tray shows all selections. Drag-and-drop reordering in the tray determines the final curated order. On [Finalize], write ordered scene IDs to `bible.stage5.curated_scenes[]`.**

> **DEV: Scene cards should have a [→ Short-Form] action too (not shown in the card by default — accessible via right-click or overflow menu). Any scene with viral energy can branch to the short-form pipeline.**

> **DEV: Spine Report is generated by Claude AFTER all 5 invocations. It's a single call that takes all ~250 scenes and identifies recurring threads. It's informational, not interactive — render as a read-only summary panel. Store in `bible.stage5.spine_report`.**

---

## 6. STAGE 6: PRODUCTION

### 6.0 — Settings (Set Sheets)

**API Flow:** Claude call: `6-settings.md` + curated scenes + location packages + VLD. Returns structured JSON: set sheets per location + prop registry.

**UI:** Location tabs (one tab per named location that appears in curated scenes). Each tab is a Set Sheet:

| Section | Render As |
|---------|----------|
| Architecture | Bullet list (editable) |
| Furniture & Fixtures | Editable data table: Item, Description, Position, Condition |
| Props & Objects | Editable data table: Item, Description, Position, Story Weight |
| Surfaces & Textures | Bullet list |
| Signage & Text | Editable data table |
| Light Sources | Editable data table: Source, Type, Color, Position, State |
| Time-of-Day Variants | Table: Time, What Changes |
| **Set Sheet Prompt Block** | **Highlighted code block** (60-100 words) — this is the paste-ready text for 6a |

**Separate tab/page:** Prop Registry (portable objects across scenes).

> **DEV: The Set Sheet Prompt Block is the second most critical text field (after Prompt Anchors). It's a 60-100 word condensed description of the location that gets pasted into every shot prompt. Render it as a highlighted, editable code block. Store as `bible.stage6.set_sheets[i].prompt_block`. Same rules as Prompt Anchors: never auto-truncate, always editable, never modified by downstream processes.**

> **DEV: All tables in Set Sheets should be editable data grids. User can add rows, edit cells, delete rows. Changes save immediately to bible. This is where production designers would make specific choices — "change the coffee pot from tin to copper" — and those changes propagate into all shot prompts for that location.**

### 6.1 — Shots (HEAVIEST GENERATION STAGE)

**This is where most images are generated.** Per scene: 3-8 shots × 10 prompts per shot = 30-80 image gen calls.

**API Flow (per curated scene):**
1. Claude call: `6a-shots.md` + scene hook + Name Registry + Prompt Anchors + Set Sheet Prompt Block + VLD + Style Lock. Returns: Scene Template + Shot Table + 10 JSON prompt objects per shot.
2. Image Gen: user triggers per-prompt or batch.

**UI:** Two-panel layout.

**Left panel (fixed):** Scene info + Shot Table.

| Element | Detail |
|---------|--------|
| Scene title + hook | At top |
| Scene Template | Collapsible section showing locked blocks (Environment, Character, Negative). Read-only unless user opens editor. |
| Shot table | Vertical list of shots. Each row: shot name, angle, description, register. Clicking a row loads its prompts in the right panel. Active row highlighted. |

**Right panel (dynamic):** Generation grid for the selected shot.

| Element | Detail |
|---------|--------|
| 10 prompt cards | Grid (2×5 or scrollable). Each card shows prompt ID (1a, 1b...1j). |
| Card states | Empty → [Generate] button → Generating (spinner) → Generated (image shown) → Selected (green border) |
| Per-card actions | ♥ Select, ↻ Regen, ✎ Edit Prompt, 🔍 Full-screen zoom |
| Batch action | [Generate All 10] fires all 10 image gen calls in parallel |

**Bottom bar:** [Complete Scene →] locks selected images for this scene.

> **DEV: This is the most API-intensive stage. Optimizations needed:**
> - **Batch generation:** [Generate All 10] fires 10 parallel image gen calls. Show progress indicator (3/10 complete...).
> - **Lazy generation:** Don't auto-generate. Let user click [Generate] per card or [Generate All]. Some users will only generate a few before selecting.
> - **Scene Template persistence:** The Scene Template is the same for all 10 prompts in a shot. It's generated by Claude once and stored. The 10 prompts only differ in the `camera`, `lens`, and `lighting` fields. Store the template as `bible.stage6.shots[scene_id].scene_template` and the 10 prompts as separate records referencing it.
> - **Cross-shot mixing:** User must be able to select 1a + 2c + 3f (one prompt from each shot). The selection is stored as `bible.stage6.shots[scene_id].selected_prompts[]` — an array of prompt IDs, one per shot.

> **DEV: The Scene Template contains Prompt Anchors (character descriptions) and Set Sheet Prompt Blocks (location descriptions) pasted verbatim. When constructing the Claude call, your backend reads these from the bible and passes them as context. Claude does NOT regenerate them — it copies them into the template. Verify in the response that the locked blocks match the bible. If they drift (Claude paraphrased), use the bible version, not Claude's.**

> **DEV: Edit Prompt (✎) opens the full JSON prompt in a code editor modal. User can modify any field. [Generate with Edits] fires image gen with the modified prompt. The edit creates a NEW prompt record (preserves original). Track as `bible.stage6.shots[scene_id].prompts[shot_id].edited_prompts[]`.**

### 6.2 — Motion

**API Flow (per selected still):**
1. Claude call: `6c-motion.md` + selected still's prompt. Returns `{ camera_movement, subject_action, environmental_motion, duration }`.
2. Video Gen API: selected still image + motion prompt. Returns video.

**UI:** Filmstrip at top (selected stills from 6.1). Below each: video playback + motion prompt details.

| Element | Detail |
|---------|--------|
| Still → Video pair | Side by side: original still on left, generated video on right |
| Motion prompt | Shown as editable text fields: Camera, Subject, Environment, Duration |
| Actions | ↻ Regen (same prompt, new video), ✎ Edit Motion (edit prompt → regen) |
| Sequence editor | Below: drag-and-drop timeline of all video clips. Reorder to build edit sequence. |

> **DEV: Video Gen takes an image + text prompt as input. The image is the selected still from 6.1 — pass its URL. The text prompt is the motion description from Claude. This is image-to-video generation, not text-to-video. Make sure your Video Gen API integration supports image input.**

> **DEV: The sequence editor is a drag-and-drop horizontal timeline. Each clip shows thumbnail + duration. Reordering updates `bible.stage6.motion[].sequence_order`. Add a [Preview Sequence] button that plays all clips in order — just sequential video playback, no transitions. Export the sequence as ordered video URLs.**

---

## 7. SHORT-FORM

**Entry points:** [→ Short-Form] button from: Stage 1 sparks, faction cards, character cards, scene cards, or Project Home.

### 7.1 — Concept Lock

**API Flow:** Claude call: `sf-concept.md` + seed (spark, faction, scene, or character) + config + bible context (if post-pipeline). Returns 5-8 concept lock options.

**UI:** Concept cards.

| Card Element | Detail |
|-------------|--------|
| Title | Bold |
| Concept | 2 lines — the idea |
| Format badge | Chip: Loop / Punch / Carousel / Micro-Trailer / Character Intro |
| Tags | Angle + viral mechanics as small chips |
| Copy | If applicable, shown in quotes |
| Actions | ♥ Select, ✎ Modify (Claude regen with notes) |

> **DEV: Format badge determines which production UI loads in 7.2. Store as `output_type` enum: `"loop" | "punch" | "carousel" | "micro_trailer" | "character_intro"`. Route to the appropriate production view based on this.**

### 7.2 — Production (varies by format)

**API Flow:** Claude call: `sf-prompt.md` + locked concept. Returns format-specific prompts. Then Video Gen API.

| Format | UI | Generation |
|--------|-----|-----------|
| **Loop** | 3 video cards side by side. Play/pause. Select best. | 3 video gen calls (parallel). Each is a full 3-5s looping video. |
| **Punch** | Vertical timeline: 3-5 shot cards. Each generates independently. [Preview Edit] plays them in sequence. | Video gen per shot (3-5 calls). Preview assembles in-browser. |
| **Carousel** | Grid of 3-7 frame cards. Each generates as image or short clip. Drag to reorder. [Preview Swipe] simulates swipe. | Image or video gen per frame (3-7 calls). |
| **Micro-Trailer** | Full timeline: 8-15 shot cards in horizontal scroll. Generate each. [Preview] plays sequence. | Video gen per shot (8-15 calls). Heavy. |
| **Character Intro** | 3-5 shot timeline. Generate each. [Preview] plays sequence. | Video gen per shot (3-5 calls). |

> **DEV: Preview functionality is client-side only — just play the generated videos in sequence. No server-side stitching. For carousels, preview as a swipe animation using CSS transitions. For timelines, sequential video playback with the HTML5 video API (play next on ended event).**

> **DEV: If this is a post-pipeline short-form (the full IP exists), Claude's prompt will include Prompt Anchors for characters and Set Sheet Prompt Blocks for locations. The same consistency system applies. If standalone (just a spark), these fields are empty and Claude invents the visual descriptions.**

---

## GLOBAL: IP BIBLE

**UI:** Always-accessible sidebar (collapsed by default) + dedicated full page.

**Sidebar (collapsed):**

| Element | Detail |
|---------|--------|
| Stage list | Vertical list with status icons: ✓ complete, ● current, ○ not started |
| Click any stage | Navigates to that stage's screen |
| [View Full Bible] | Opens full page |
| [Export] | Downloads as `.md` or `.json` |

**Full page:** Rendered document matching the bible template. Every section is viewable and editable. Change Log at the bottom.

> **DEV: The bible sidebar is a persistent UI element — it stays visible (or accessible via toggle) across all stage screens. It's the project's progress tracker AND navigation. Implement as a fixed sidebar that can collapse to just icons on smaller screens.**

> **DEV: Export formats:**
> - `.md` — render the bible JSONB as a markdown document matching the template in `ip-bible.md`
> - `.json` — raw dump of the bible JSONB
> - Both should include image/video URLs as links, not embedded media.

> **DEV: Change Log is append-only. Every time a bible field is modified after initial approval, append: `{ timestamp, stage, field_path, old_value_summary, new_value_summary, reason }`. The `reason` field is optional — prompt the user with "Why this change?" but allow skipping.**

---

## GLOBAL: Action Toolbar

Persistent across all screens. Renders in the top nav or as a floating bar.

| Button | Behavior | Implementation |
|--------|----------|---------------|
| 🛸 **Spacecadetify** | Context-dependent. If user has a card/section focused, runs on that. Otherwise, shows "Select something to Spacecadetify." | Claude call: `CTX-spacecadet-brand.md` + selected content. Returns amplification suggestions. User picks → content regenerates with amplification. |
| ✎ **Edit** | Enables inline editing on whatever content is visible. | Client-side: makes text fields editable. On blur/save, writes to bible + change log. |
| **Taste Filter: ON/OFF** | Toggle. Visual indicator (green = on, grey = off). | Stored in `bible.config.taste_filter`. When ON, Claude calls include taste profile as context. When OFF, taste profile is omitted from the system prompt. |
| **Alien: 7** | Click to open quick slider. Adjust 1-10. | Updates `bible.config.alien`. Next Claude call uses new value. Shows current value always. |
| **Dimensions** | Click to open 4-chip toggles. | Updates `bible.config.dimensions[]`. Same real-time update pattern. |

> **DEV: The toolbar reads from `bible.config` and writes to it in real-time. Changes to dials don't retroactively change approved content — they only affect the NEXT Claude call. This is by design. If user wants to re-generate previous content with new settings, they need to explicitly ↻ Regen that content.**

> **DEV: Spacecadetify is the most complex toolbar action. It needs context awareness — what is the user looking at right now? Implement as: (1) user clicks 🛸, (2) UI enters "select mode" where clickable items get highlighted, (3) user clicks a card/section, (4) that content + the Spacecadet Brand context gets sent to Claude, (5) Claude returns 2-3 amplification options, (6) user picks one, (7) content regenerates with the amplification baked in.**
