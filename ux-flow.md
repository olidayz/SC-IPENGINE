# IP Engine — Web App UX Flow

Developer spec. Every screen, every user action, every API call, every data state.

The app wraps the IP Engine skill system into a product. Claude generates the creative output. Image/video generation APIs are integrated — the user generates inline, not copy-paste. The IP Bible is the database.

---

## Architecture Overview

```
┌──────────────────────────────────────────────────────────┐
│                        FRONTEND                          │
│  Dashboard → Project → Stage Screens → Generation View   │
└────────────────────────┬─────────────────────────────────┘
                         │
                    ┌────┴────┐
                    │   API   │
                    └────┬────┘
                         │
         ┌───────────────┼───────────────┐
         │               │               │
    ┌────┴────┐    ┌─────┴─────┐   ┌─────┴─────┐
    │  Claude  │    │  Image Gen │   │ Video Gen  │
    │   API    │    │    API     │   │    API     │
    │          │    │            │   │            │
    │ Creative │    │ Midjourney │   │  Runway    │
    │ Engine   │    │ DALL-E     │   │  Kling     │
    │          │    │ Flux       │   │  Sora      │
    │          │    │ Ideogram   │   │            │
    └──────────┘    └────────────┘   └────────────┘
         │               │               │
         └───────────────┼───────────────┘
                         │
                    ┌────┴────┐
                    │   DB    │
                    │ IP Bible│
                    │ (per    │
                    │ project)│
                    └─────────┘
```

**Claude API** — generates all creative text (ideas, worlds, stories, VLD, scene hooks, prompts)
**Image Gen API** — generates images from prompts inline (user picks provider)
**Video Gen API** — generates video from prompts/images inline
**DB / IP Bible** — persistent store per project. Every approval writes here.

---

## Screen Flow

```
DASHBOARD
    │
    ├── [+ New Project] → SESSION CONFIG → STAGE 1: IDEAS
    │
    └── [Existing Project] → PROJECT HOME → resume at last stage
                                │
                                ├── Stage 1: Ideas
                                ├── Stage 1b: Thumbnails
                                ├── Stage 2: World
                                ├── Stage 3: Stories
                                ├── Stage 4.0: Style Lock
                                ├── Stage 4.1: Art Direction
                                ├── Stage 4.2: Characters + Locations
                                ├── Stage 4.3: Casting
                                ├── Stage 5: Scenes
                                ├── Stage 6.0: Settings
                                ├── Stage 6.1: Shots
                                ├── Stage 6.2: Motion
                                ├── Short-Form
                                └── IP Bible (viewable/editable at any time)
```

---

## 0. DASHBOARD

**What the user sees:**
- Grid/list of existing projects, each showing: title, thumbnail (if generated), current stage, last edited date
- [+ New Project] button
- Each project card shows progress indicator (which stages are complete)

**Data:** List of projects from DB. Each project = one IP Bible.

---

## 0.1 SESSION CONFIG (New Project)

**What the user sees:**
A single setup screen with the following controls:

| Control | UI Element | Default | Saves To |
|---------|-----------|---------|----------|
| **Pipeline** | Radio: Full Pipeline / Short-Form / Both. **This is the first choice.** Controls which other fields are visible. Short-Form hides Tech Seeds and simplifies modifiers. | Full | `bible.config.pipeline` |
| **Project seed** | Text input — "What's your idea?" (subject, IP, concept, anything) | Empty (required) | `bible.seed` |
| **Alien dial** | Slider, 1-10, with label descriptions at each level | 7 | `bible.config.alien` |
| **Spacecadet dimensions** | 4 toggles (Sci-Fi, Surreal, Spiritual, Satiraverse) — toggle emphasis on/off, at least 2 must be on | All on (balanced) | `bible.config.dimensions` |
| **Tech seeds** | Dropdown multi-select from 7 territories, or "None" | None | `bible.config.seeds` |
| **Reference anchors** | Searchable picker with category tabs (Directors, Films, TV, Movements, Music, Brands) + free-text custom entry. Autocomplete from `anchor-library.md` (500+ entries with default take/leave). Each selected anchor shows: name, category badge, editable "Take" field (pre-filled from library, user can override), editable "Leave" field (pre-filled, user can override). Max 3. | Empty (optional but recommended) | `bible.config.anchors[]` |
| **Idea modifiers** | Checkbox group: Violation Mode, Satiraverse, Anti-Taste, Emotional Register (dropdown: WOW/NAH/HMM/NSFW/LOL/WTF/UGH), Contrast Mode (two emotion dropdowns) | None | `bible.config.modifiers` |
| ~~**Pipeline**~~ | ~~Moved to top of form — see first row~~ | — | — |

**Actions:**
- [Start] → creates project in DB, saves config to IP Bible, routes to Stage 1

---

## 1. STAGE 1: IDEAS

### 1.1 Generation

**Trigger:** User hits [Generate Ideas] or arrives from Session Config.

**API call:** Claude API
- **Input:** Seed from config + Session Config (dials, modifiers, anchors)
- **Prompt:** Load `1-ideas.md` + relevant context files
- **Output:** 30-50 sparks, each as `{ title, logline }` — structured JSON

**What the user sees:**
- Grid of spark cards. Each card shows:
  - Title (large, bold)
  - 2-sentence logline (smaller)
  - Action buttons: ♥ Select | ✎ Develop | ↻ Modify | ⚡ Collide
- Top bar: count of sparks, [Regenerate] button, modifier toggles (can change and re-run)
- Selected sparks highlighted, collected in a sidebar tray

**User actions:**

| Action | What happens |
|--------|-------------|
| **♥ Select** | Spark added to selection tray. Can select multiple. |
| **✎ Develop** | Claude API call: expand logline into full paragraph. Inline update on card — logline expands beneath title. |
| **↻ Modify** | Opens text input: "How should this change?" → Claude API call → returns modified spark, replaces card. |
| **⚡ Collide** | Opens modal: pick a second spark (or type a concept) → Claude API call → returns new collision spark. |
| **→ Thumbnails** | Available once 1+ sparks selected. Routes to 1b. |
| **→ Short-Form** | Available per spark. Routes to Short-Form pipeline with this spark. |
| **→ Build World** | Skip thumbnails, go straight to Stage 2. |

**Saves to Bible:** Selected spark(s) — `bible.stage1.sparks[]`

### 1.2 Thumbnails

**Trigger:** User selects sparks and hits [Generate Thumbnails].

**For each selected spark:**

**API call 1:** Claude API
- **Input:** Selected spark + Session Config
- **Prompt:** Load `1b-thumbnails.md`
- **Output:** 5 thumbnail concepts, each as `{ name, visual_description, prompt }` — structured JSON

**API call 2:** Image Gen API (runs automatically after prompt generation)
- **Input:** Each prompt from Claude
- **Output:** 5 generated images (9:16 vertical)

**What the user sees:**
- Spark title at top
- 5 images in a row (or 2×3 grid on mobile), each with:
  - Generated image (9:16 vertical)
  - Concept name beneath
  - ♥ Select | ↻ Regenerate (reruns image gen with same prompt) | ✎ Edit Prompt (opens prompt editor, regenerate with edited version)
- Below the grid: [Generate 5 More] (new concepts, new prompts, new images)

**User actions:**

| Action | What happens |
|--------|-------------|
| **♥ Select** | Thumbnail marked as selected. Can select multiple. |
| **↻ Regenerate** | Same prompt → re-run image gen API → new image replaces old. |
| **✎ Edit Prompt** | Opens the raw prompt in a text editor. User edits → [Generate] → image gen API → new image. |
| **→ Build World** | Routes to Stage 2 with selected spark + thumbnail direction. |

**Saves to Bible:** Selected thumbnail concept(s) + prompt + generated image URL — `bible.stage1.thumbnails[]`

---

## 2. STAGE 2: WORLD

### 2.1 Core (2 Directions)

**API call:** Claude API
- **Input:** Selected spark + Session Config
- **Prompt:** Load `2a-core.md`
- **Output:** 2 directions, each as structured JSON: `{ sacred_question, premise, tension, allegory, myth, rules[] }`

**What the user sees:**
- Two side-by-side panels, each showing one direction:
  - Sacred Question (highlighted)
  - World Premise
  - Tension
  - Allegory
  - Myth
  - Rules table
- Below: action row

**User actions:**

| Action | What happens |
|--------|-------------|
| **Pick Direction A** | Direction A locked, B discarded. |
| **Pick Direction B** | Direction B locked, A discarded. |
| **Hybridize** | Opens text input: "What to take from each?" → Claude API call → returns hybrid. Shown as a third panel. User approves or iterates. |
| **→ Next** | Routes to 2.2 World Build. |

**Saves to Bible:** Approved direction — `bible.stage2.core`

### 2.2 World Build

**API call:** Claude API
- **Input:** Approved core + Session Config (tech seeds load here if configured)
- **Prompt:** Load `2b-world.md`
- **Output:** Structured JSON: `{ speculative_layer, world_texture, history[], factions[], conflicts[], objects[] }`

**What the user sees:**
- Scrollable document-style page with collapsible sections:
  - Speculative Layer
  - World Texture (prose)
  - History (timeline/table)
  - Factions (cards with territory, values, rivals)
  - Conflicts
  - Objects & Artifacts
- Each section has: [✓ Approve] [✎ Edit] [↻ Regenerate Section]

**User actions:**
- Approve entire build or request edits per section
- [✎ Edit] → inline text editing, user modifies directly
- [↻ Regenerate Section] → Claude API call with feedback → replaces section

**Saves to Bible:** Approved world build — `bible.stage2.world`

### 2.3 Franchise

**API call:** Claude API
- **Input:** Approved world
- **Prompt:** Load `2c-franchise.md`
- **Output:** `{ tonal_range, expansion_vectors[], how_fans_join[] }`

**Same UI pattern** — collapsible sections, approve/edit/regenerate per section.

**Saves to Bible:** `bible.stage2.franchise`

---

## 3. STAGE 3: STORIES

### 3.1 Seeds

**API call:** Claude API
- **Input:** Full world bible
- **Prompt:** Load `3a-seeds.md`
- **Output:** 3-5 stories, each as: `{ title, logline, protagonist: { name, position, premise, wound, hook }, ensemble[] }`

**What the user sees:**
- Story cards (expandable). Each shows:
  - Title + logline (collapsed view)
  - Expand → protagonist, premise, wound, hook, ensemble list
  - ♥ Select for development

**User selects 1-3 seeds.**

**Saves to Bible:** `bible.stage3.selected_seeds[]`

### 3.2 Story Windows

**API call:** Claude API (per selected seed)
- **Input:** Selected seed + full world bible
- **Prompt:** Load `3b-arcs.md`
- **Output:** Full Story Window as structured JSON

**What the user sees:**
- Document-style page per story: Setup, Characters, Premise, Protagonist, Opponent, Pressure Cooker, Collision, Cost
- Approve / Edit / Regenerate per section

**Saves to Bible:** `bible.stage3.story_windows[]`

---

## 4. STAGE 4: VISUAL DEVELOPMENT

### 4.0 Style Lock

**API call 1:** Claude API
- **Input:** Spark + world + story + Session Config (anchors especially important here)
- **Prompt:** Load `4-style-lock.md` + `references/style-directions.md`
- **Output:** 3-5 style recommendations, each as: `{ name, lock_type, pitch, reference_feel, risk, prompts[4] }`

**API call 2:** Image Gen API (batch — 4 images per direction, 12-20 total)
- **Input:** 4 prompts per direction
- **Output:** Generated test images

**What the user sees:**
- Style direction cards in a row. Each card shows:
  - Direction name + lock type (Medium / Aesthetic / Combo)
  - 2-line pitch
  - 4 generated test images in a 2×2 grid (The Face, The World, The Moment, The Icon)
  - Risk line in smaller text
- Radio select: pick one direction

**User actions:**
- Select a style direction → [Lock Style]
- [↻ Regenerate Images] per direction (same prompts, new gen)
- [More Directions] → Claude API generates 3-5 more options

**Saves to Bible:** `bible.stage4.style_lock` — locked style name + prompt DNA keywords

### 4.1 Art Direction (VLD)

**API call:** Claude API
- **Input:** All prior stages + Style Lock
- **Prompt:** Load `4a-art-director.md`
- **Output:** Full VLD as structured JSON (visual signature, palette×light×material table, composition×register table, time layers, motifs, references, downstream translation)

**What the user sees:**
- Styled document. Tables render as tables. Prose renders as prose.
- Collapsible sections with approve/edit/regenerate per section
- Downstream Translation section shown as a code block (these are the keywords that flow into every prompt)

**Saves to Bible:** `bible.stage4.vld`

### 4.2 Characters + Locations

**API call 1:** Claude API
- **Input:** VLD + Story Window
- **Prompt:** Load `4b-characters.md` + `4c-locations.md`
- **Output:** Characters and locations as structured JSON, each with proper names, visual packages, image prompts, and Prompt Anchors (locations)

**API call 2:** Image Gen API (per character + per location)
- **Input:** Image prompts from Claude output
- **Output:** 1 concept image per character (character in environment) + 1 establishing shot per location

**What the user sees:**
- Two tabs: Characters | Locations
- **Characters tab:** Summary table at top. Each character row shows its **generated concept image** — the design direction before casting. Below: expandable full visual packages.
- **Locations tab:** Summary table + generated establishing shots per location. Expandable packages. Each location has its Prompt Anchor visible.
- Name Registry auto-populated in sidebar

**User actions on character concept images:**
- **Approve** → design confirmed, move to casting
- **Edit** → adjust costume, detail, palette → Claude regenerates prompt → Image Gen regenerates concept image
- **Spacecadetify** → amplify brand dimensions on this character → regenerate
- **→ Short-Form** → branch this character to a Character Intro in short-form pipeline

**Saves to Bible:** `bible.stage4.characters[]`, `bible.stage4.locations[]`, `bible.name_registry`, concept image URLs

### 4.3 Casting

**For each character:**

**API call 1:** Claude API
- **Input:** Character package + VLD + Style Lock
- **Prompt:** Load `4d-casting.md` (Phase 1)
- **Output:** 5 casting variation prompts as JSON

**API call 2:** Image Gen API (batch — 5 images per character)
- **Input:** 5 prompts
- **Output:** 5 landscape (16:9) portrait images

**What the user sees:**
- One character at a time (stepper UI)
- Character name + visual shorthand at top
- 5 generated landscape portraits in a row
- Each has: radio select + [↻ Regenerate] + [✎ Edit Prompt]
- Below selected image: "This is [Name]" confirmation

**After selection:**

**API call 3:** Claude API
- Writes the Prompt Anchor (30-50 words) based on selected variation
- Displayed beneath the selected image for review

**API call 4:** Image Gen API (locked turnaround sheet)
- **Input:** Full turnaround prompt (front, 3/4, profile) using selected variation
- **Output:** 1 landscape character reference sheet

**What the user sees after all characters cast:**
- Cast page: all locked character sheets in a grid
- Name Registry updated with Prompt Anchors
- [Approve Cast] → proceed

**Saves to Bible:** `bible.stage4.cast[]` — each with locked sheet image URL + Prompt Anchor text

---

## 5. STAGE 5: SCENES

### 5 invocations, same UI pattern:

**API call:** Claude API (per invocation)
- **Input:** Full bible + exclusion list from prior invocations
- **Prompt:** Load `5a` through `5e` sequentially
- **Output:** ~50 scenes per invocation as `{ number, title, hook_line }`

**What the user sees:**
- Scene list. Each scene is a card: number + title + hook line
- Invocation tabs at top (1: Extract, 2: Invent, 3: Weird, 4: Participation, 5: Counter)
- Each card has: ♥ Select | 🗑 Skip
- Curated scenes collected in a sidebar tray
- After all 5 invocations: Spine Report shown as a summary panel

**User actions:**
- Scan and select across all invocations
- [Curate] → finalize selection
- Curated scenes reorderable via drag-and-drop

**Saves to Bible:** `bible.stage5.curated_scenes[]`, `bible.stage5.spine_report`

---

## 6. STAGE 6: PRODUCTION

### 6.0 Settings (Set Sheets)

**API call:** Claude API
- **Input:** Curated scenes + location packages + VLD
- **Prompt:** Load `6-settings.md`
- **Output:** Set Sheet per location + Prop Registry as structured JSON

**What the user sees:**
- Location tabs. Each tab = one Set Sheet:
  - Architecture, Furniture, Props, Surfaces, Signage, Light Sources, Time-of-Day Variants
  - Set Sheet Prompt Block shown in a highlighted code block
- Prop Registry as a separate tab/table
- Approve / edit per section

**Saves to Bible:** `bible.stage6.set_sheets[]`, `bible.stage6.prop_registry[]`

### 6.1 Shots

**For each curated scene:**

**API call 1:** Claude API
- **Input:** Scene hook + Name Registry + Prompt Anchors + Set Sheet + VLD + Style Lock
- **Prompt:** Load `6a-shots.md`
- **Output:** Scene Template (locked blocks) + Shot Table + 10 JSON prompts per shot

**What the user sees — two-panel layout:**

**Left panel: Shot Table**
- Scene title + hook at top
- Shot table: rows with shot name, angle, description, register
- Clicking a shot row → shows its 10 prompt variations in right panel

**Right panel: Generation Grid**
- 10 prompt cards per shot
- Each card: [Generate] button → image gen API call → image appears in card
- Can batch-generate all 10: [Generate All]
- Each generated image has: ♥ Select | ↻ Regenerate | ✎ Edit Prompt | 🔍 Zoom

**User actions:**
- Generate images per prompt (or batch)
- Select best per shot
- Mix and match across shots (1a + 2c + 3f)
- [Complete Scene] → selected images locked

**API calls per scene:**
- Claude: 1 call (scene template + shot table + all prompts)
- Image Gen: 10 × number of shots (e.g., 5 shots = 50 image gen calls)

**Saves to Bible:** `bible.stage6.shots[]` — per scene: shot table + selected prompt IDs + generated image URLs

### 6.2 Motion

**For each selected still:**

**API call 1:** Claude API
- **Input:** Selected still's prompt + shot context
- **Prompt:** Load `6c-motion.md`
- **Output:** Video prompt JSON: `{ camera_movement, subject_action, environmental_motion, duration }`

**API call 2:** Video Gen API
- **Input:** Selected still image + video prompt
- **Output:** Generated video (3-5 seconds)

**What the user sees:**
- Selected stills in a filmstrip at top
- Below each still: generated video playback + video prompt details
- [↻ Regenerate] | [✎ Edit Motion] per video
- Sequence view: drag to reorder stills/videos into an edit sequence

**Saves to Bible:** `bible.stage6.motion[]` — video URLs + prompts + sequence order

---

## 7. SHORT-FORM (branches from any stage)

**Entry points:**
- From Stage 1: [→ Short-Form] on any spark
- From Project Home: [Short-Form] tab (uses full IP if pipeline is further along)

### 7.1 Concept Lock

**API call:** Claude API
- **Input:** Spark or IP context + Session Config
- **Prompt:** Load `sf-concept.md`
- **Output:** 5-8 concept locks, each as: `{ title, concept, angle, output_type, play, viral_mechanics[], copy, duration, aspect, tone }`

**What the user sees:**
- Concept cards. Each shows:
  - Title (bold)
  - 2-line concept description
  - Format badge (Loop / Punch / Carousel / Micro-Trailer / Character Intro)
  - Angle + viral mechanics as tags
  - Copy (if applicable)
- ♥ Select | ✎ Modify

### 7.2 Production

**API call 1:** Claude API
- **Input:** Locked concept
- **Prompt:** Load `sf-prompt.md`
- **Output:** Format-specific prompts (varies by format — see sf-prompt.md for structure)

**API call 2:** Video Gen API (batch)
- **Input:** Prompts + any reference images (Prompt Anchors if post-pipeline)
- **Output:** Generated video(s)

**What the user sees — varies by format:**

| Format | UI |
|--------|-----|
| **Loop** | 3 video variations side by side. Play/pause. Select best. |
| **Punch** | Shot sequence timeline. Generate per shot. Preview assembled edit. |
| **Carousel** | Frame grid (3-7). Generate each frame. Reorder via drag. Preview as swipe. |
| **Micro-Trailer** | Full timeline editor. 8-15 shots. Generate each. Preview assembled. |
| **Character Intro** | 3-5 shot sequence. Generate. Preview as assembled edit. |

**Saves to Bible:** `bible.short_form[]` — concept lock + prompt + generated asset URLs

---

## IP BIBLE (accessible at any time)

**What the user sees:**
- Sidebar or dedicated page, always accessible
- Structured document matching the bible template
- Every section shows its approval state: ✓ Approved | ⏳ In Progress | — Not Started
- Sections are viewable and editable
- Change Log at bottom
- [Export] → downloads as `.md` file or JSON

**Data:**
- This IS the database. Every API response that gets approved writes here.
- Session Config lives here
- Prompt Anchors are shown in full (not truncated) — these are copy-paste sources
- Generated image/video URLs stored with their prompts

---

## Data Model (simplified)

```
Project {
  id
  title
  created_at
  updated_at
  current_stage          // "stage1" | "stage2" | ... | "complete"

  config {
    alien_dial           // 1-10
    dimensions[]         // ["sci-fi", "satiraverse"]
    tech_seeds[]         // ["society_control"]
    anchors[] {
      work               // "Coen Brothers"
      take               // "dry landscape morality"
      leave              // "nihilism"
    }
    modifiers[]          // ["violation_mode"]
    pipeline             // "full" | "short-form" | "both"
  }

  stage1 {
    sparks[] {
      id, title, logline, selected, developed_text
    }
    thumbnails[] {
      spark_id, concept_name, prompt, image_url, selected
    }
  }

  stage2 {
    core {
      direction_chosen    // "a" | "b" | "hybrid"
      sacred_question, premise, tension, allegory, myth
      rules[]
    }
    world {
      speculative_layer, world_texture, history[], factions[], conflicts[], objects[]
    }
    franchise {
      tonal_range, expansion_vectors[], how_fans_join[]
    }
  }

  stage3 {
    selected_seeds[] {
      title, logline, protagonist, premise, wound, hook, ensemble[]
    }
    story_windows[] {
      // full story window structure
    }
  }

  stage4 {
    style_lock {
      lock_type, medium, aesthetic, prompt_dna
    }
    vld {
      // full VLD structure
    }
    characters[] {
      name, role, visual_shorthand, prompt_anchor,
      visual_package {}, // full 6-principle package
      cast {
        selected_variation, locked_sheet_image_url, prompt_anchor_text
      }
    }
    locations[] {
      name, territory, visual_shorthand, prompt_anchor,
      visual_package {}  // full 6-principle package
    }
  }

  stage5 {
    scenes_by_invocation[] {
      invocation, scenes[] { number, title, hook_line, selected }
    }
    curated_scenes[]     // selected scene IDs in order
    spine_report {}
  }

  stage6 {
    set_sheets[] {
      location_name, architecture, furniture[], props[], surfaces,
      signage[], light_sources[], time_variants, prompt_block
    }
    prop_registry[] {
      name, owner, description, is_signature
    }
    shots_by_scene[] {
      scene_id, scene_template {},
      shot_table[] { name, angle, description, register },
      prompts_by_shot[] {
        shot_id, prompts[] {
          id, json_prompt, image_url, selected
        }
      }
    }
    motion[] {
      source_image_id, video_prompt, video_url, sequence_order
    }
  }

  short_form[] {
    concept_lock {
      title, concept, angle, output_type, play,
      viral_mechanics[], copy, duration, aspect, tone
    }
    prompts[]           // format-specific
    generated_assets[]  // video/image URLs
  }

  change_log[] {
    timestamp, stage, what_changed, why
  }
}
```

---

## API Integration Points

| Where | Claude API | Image Gen API | Video Gen API |
|-------|-----------|--------------|--------------|
| **Ideas** | Generate 30-50 sparks | — | — |
| **Develop/Modify/Collide** | Per-action calls | — | — |
| **Thumbnails** | 5 prompts per spark | 5 images per spark | — |
| **World (2a-2c)** | 3 calls (core, world, franchise) | — | — |
| **Stories (3a-3b)** | 2 calls (seeds, windows) | — | — |
| **Style Lock** | 3-5 directions + 4 prompts each | 12-20 test images | — |
| **VLD** | 1 call | — | — |
| **Characters + Locations** | 1 call | — | — |
| **Casting** | 5 prompts per character + Prompt Anchor | 5 portraits + 1 turnaround per character | — |
| **Scenes (×5)** | 5 calls (~50 scenes each) | — | — |
| **Settings** | 1 call | — | — |
| **Shots** | 1 call per scene (template + all prompts) | 10 × shots per scene (heaviest usage) | — |
| **Motion** | 1 prompt per selected still | — | 1 video per selected still |
| **Short-Form** | Concept lock + format prompts | Per-format | Per-format (all video) |

### Estimated API Usage Per Full IP Run

| API | Calls | Notes |
|-----|-------|-------|
| **Claude** | ~25-40 | Text generation across all stages |
| **Image Gen** | ~800-3,500 | Bulk is at Stage 6 shots (10 per shot × 3-8 shots × 20-40 scenes). Casting + style lock add ~40-60. |
| **Video Gen** | ~20-100 | Selected stills → motion. Plus short-form content. |

---

## Global Actions (Available at Every Stage)

These actions persist in the UI at all times — toolbar or contextual menu.

| Action | UI Element | What It Does |
|--------|-----------|-------------|
| **Spacecadetify** | Button on any output card/section | Runs Spacecadet Brand dimensions against the selected output. Returns amplification options (which dimensions to push, specific suggestions). User picks, output regenerates with amplified strangeness. |
| **Edit** | Inline on any approved content | Opens any text/description for direct editing. User modifies → saves → IP Bible updated with Change Log entry. No re-approval needed for minor edits. |
| **→ Short-Form** | Button on any spark, scene, character, or moment | Branches the selected item into the short-form pipeline. Opens sf-concept with this item as the seed. Available from Stage 1 sparks, Stage 5 scenes, character cards, or any moment with viral energy. |
| **→ Build World** | Button on any spark or concept | Sends the item into Stage 2 (World). Available from Stage 1 sparks and from short-form concepts that reveal franchise depth. |
| **Taste Filter toggle** | Toggle in top toolbar | On (default) = 12-principle quality floor enforced at every generation and gate check. Off = generate freely with no quality filtering. Visual indicator shows current state. Can be toggled at any time. |
| **Spacecadet Dimensions** | Quick-access in toolbar | Adjust dimension emphasis (Sci-Fi, Surreal, Spiritual, Satiraverse) at any point. Changes apply to next generation. |
| **Alien Dial** | Quick-access in toolbar | Adjust 1-10 strangeness at any point. |

---

## Key UI Patterns

### The Generation Card
Used everywhere images are generated: thumbnails, style lock, casting, shots.

```
┌──────────────────────────┐
│                          │
│    [Generated Image]     │
│                          │
│    or                    │
│    [Generate] button     │
│    (before generation)   │
│                          │
├──────────────────────────┤
│ ♥ Select  ↻ Regen  ✎ Edit│
└──────────────────────────┘
```

States: Empty → Generating (spinner) → Generated → Selected → Locked

### The Approval Bar
Used at every stage exit.

```
┌──────────────────────────────────────────────────────┐
│ ✓ Approve & Continue    ✎ Request Changes    ↻ Redo  │
└──────────────────────────────────────────────────────┘
```

[Approve] → saves to bible, unlocks next stage
[Request Changes] → opens feedback input → Claude API re-generates with notes
[Redo] → full regeneration of current stage

### The Prompt Editor
Available on any generated image via [✎ Edit Prompt].

```
┌──────────────────────────────────────────────────────┐
│ Raw JSON prompt (editable)                           │
│                                                      │
│ {                                                    │
│   "format": "vertical 9:16",                        │
│   "style": "...",                                    │
│   "subject": { ... },                                │
│   ...                                                │
│ }                                                    │
│                                                      │
├──────────────────────────────────────────────────────┤
│ [Generate with Edits]    [Reset to Original]         │
└──────────────────────────────────────────────────────┘
```

### The Bible Sidebar
Always accessible. Shows current project state.

```
┌─────────────────────┐
│ 📖 IP BIBLE          │
│                     │
│ ✓ Config            │
│ ✓ Spark             │
│ ✓ Thumbnails        │
│ ✓ World             │
│ ✓ Stories           │
│ ● Style Lock ← YOU  │
│ ○ VLD               │
│ ○ Characters        │
│ ○ Casting           │
│ ○ Scenes            │
│ ○ Settings          │
│ ○ Shots             │
│ ○ Motion            │
│                     │
│ [View Full Bible]   │
│ [Export]            │
└─────────────────────┘
```

✓ = completed + approved
● = current stage
○ = not started
