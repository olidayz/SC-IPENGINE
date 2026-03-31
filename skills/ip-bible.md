# IP BIBLE — Persistent Output

The IP Bible is a single file that accumulates ALL approved decisions across the pipeline. It saves to disk so nothing is lost between sessions or context compressions.

**File location:** Saved as `[IP-TITLE]-bible.md` in the working directory.

**When to write:** After every approval/lock point. Not at the end — INCREMENTALLY. Each time the user approves something, it gets appended to the bible immediately.

**When to read:** At the start of any new session, or after context compression. The bible IS the persistent context.

---

## Structure

The IP Bible grows stage by stage. Each section is written ONLY when that stage is completed and approved. Empty sections mean the pipeline hasn't reached that stage yet.

```markdown
# [IP TITLE] — IP Bible
Generated: [date]
Last updated: [date + stage]

---

## Session Config

Alien Dial: [N] / 10
SC Dimensions: [emphasized or balanced]
Tech Seeds: [territory or none]
Reference Anchors:
  1. [work] — take [X], leave [Y]
  2. [work] — take [X], leave [Y]
  3. [work] — take [X], leave [Y] (if set)
Modifiers: [list or none]
Pipeline: [Full / Short-Form / Both]

---

## Stage 1: Spark

**Title:** [locked title]
**Logline:** [2-sentence logline]
**Thumbnail Direction:** [selected thumbnail concept, if generated]

---

## Stage 2: World

### Core Identity (2a — approved direction)
**Sacred Question:** [1-2 sentences]
**World Premise:** [2-3 sentences]
**Tension:** [1-2 sentences]
**Allegory:** [1-2 sentences]
**Myth:** [2-3 sentences]
**Rules:**
| Rule | How It Works |
|------|-------------|
| ... | ... |

### World Build (2b — approved)
**Speculative Layer:** [if applicable]
**World Texture:** [First Encounter + Lived Experience]
**History:**
| Era | Period | Force | What Haunts |
|-----|--------|-------|-------------|
| ... | ... | ... | ... |

**Factions:**
[summary of each faction — territory, values, visual identity]

**Objects & Artifacts:**
[key world objects]

### Franchise (2c — approved)
**Tonal Range:** Core / Light / Dark / Weird
**Expansion Vectors:** Film 1, Films 2-3, Series, Game, Short-Form
**How Fans Join:** [participation paths]

---

## Stage 3: Story

### Selected Seed(s)
**Title:** [story title]
**Logline:** [one sentence]
**Protagonist:** [name] — [position in world]
**Premise:** [Trait → Action → Consequence]
**Wound:** [need vs want]
**Hook:** [the image/moment]

### Story Window (3b — approved)
[Full story window content — setup, characters, premise, protagonist, opponent, pressure cooker, collision, cost]

---

## Stage 4: Visual Development

### Style Lock (4-style-lock — approved)
**Lock Type:** [Medium only / Aesthetic only / Medium × Aesthetic]
**Medium:** [if locked]
**Aesthetic:** [if locked]
**Prompt DNA:** [combined keywords from style-directions.md]

### VLD (4a — approved)
[Full Visual Language Document — visual signature, palette × light × material table, composition × tonal register table, time layers, visual motifs, references, downstream translation notes]

### Name Registry

#### Characters (post-casting)
| Name | Role | Visual Shorthand | Prompt Anchor |
|------|------|-----------------|---------------|
| ... | ... | ... | [30-50 words — paste verbatim] |

#### Locations
| Name | Territory | Visual Shorthand | Prompt Anchor |
|------|-----------|-----------------|---------------|
| ... | ... | ... | [30-50 words — paste verbatim] |

### Character Visual Packages (4b — approved)
[One section per character — silhouette, palette, costume logic, signature detail, body in space, visual arc]

### Location Visual Packages (4c — approved)
[One section per location — history layer, lived-in, scale, faction signature, threshold, sensory depth]

### Locked Cast (4d — approved)
[One section per character — selected variation description, locked sheet reference, Prompt Anchor]

---

## Stage 5: Scenes (curated)

### Curated Scene List
[Only the scenes the user selected from all 5 invocations — title + hook line for each]

### Spine Report
[Top 2-3 spines with density and quality notes]

---

## Stage 6: Production

### Set Sheets (6-settings — approved)
[One section per location — architecture, furniture, props, surfaces, signage, light sources, time-of-day variants, Set Sheet Prompt Block]

### Prop Registry
| Prop | Owner | Description | Signature? |
|------|-------|-------------|-----------|
| ... | ... | ... | ... |

### Generated Shots
[Scene title → shot table → selected prompt IDs for each scene that has been shot]

---

## Short-Form (if applicable)

### Concept Locks
[One entry per short-form concept — title, concept, angle, output type, play, viral mechanics, copy, tone]

### Series (if applicable)
[Series structure, locked format, episode log]

---

## Change Log

| Date | Stage | What Changed | Why |
|------|-------|-------------|-----|
| ... | ... | ... | ... |
```

---

## Rules

### Writing the Bible

| Rule | Why |
|------|-----|
| **Write after every approval** | Don't batch. If the user approves the VLD, write the VLD section immediately. |
| **Verbatim for Prompt Anchors** | Prompt Anchors and Set Sheet Prompt Blocks are copy-paste sources. They must be EXACT in the bible — no summarizing, no paraphrasing. |
| **Include the Session Config** | Dial settings are decisions. They must be recorded so a new session can restore them. |
| **Note rejected options** | In the Change Log, briefly note what was rejected and why. This prevents re-proposing killed ideas in future sessions. |
| **Update, don't duplicate** | If a Prompt Anchor changes (recasting), UPDATE the existing entry. Don't add a second one. |

### Reading the Bible

| Situation | What to Do |
|-----------|-----------|
| **New session, continuing an IP** | Read the full bible before doing anything. Restore Session Config. Resume at the next uncompleted stage. |
| **Context compressed mid-session** | Re-read the bible sections relevant to the current stage + Session Config. |
| **User asks "where are we?"** | Reference the bible. The last completed section tells you the current state. |
| **User wants to change an approved decision** | Update the bible entry + add to Change Log. Note what changed and why. |

### File Naming

```
[IP-TITLE]-bible.md

Examples:
YEAR-ONE-bible.md
SADDLESAUR-bible.md
COLD-BLOOD-CODE-bible.md
```

Saved in the working directory alongside the skills folder.

---

## Anti-Patterns

| Don't | Why |
|-------|-----|
| Wait until the end to write the bible | Context may compress. Sessions may end. Write incrementally. |
| Summarize Prompt Anchors | They're verbatim paste sources. Summaries break downstream prompt consistency. |
| Skip the Change Log | Without it, you'll re-propose killed ideas or forget why something was changed. |
| Put generation process notes in the bible | The bible stores DECISIONS and APPROVED OUTPUT. Not drafts, not rejected options (except brief Change Log notes), not internal reasoning. |
| Let the bible grow without structure | Follow the template. Every section maps to a pipeline stage. Don't add freeform notes — they become noise. |
