# SESSION — Configure Before You Start

Pick your pipeline, set the dials, configure the run. Do this ONCE at the start. The session config carries forward through all stages.

---

## Step 1: Choose Your Pipeline

This is the first decision. Everything downstream adapts to it.

| Pipeline | What You're Making | What You'll Configure |
|----------|-------------------|----------------------|
| **Full Pipeline** | Franchise-scale IP: Ideas → Worlds → Stories → Vis-Dev → Scenes → Shots | All dials + modifiers + anchors + seeds |
| **Short-Form** | Viral content: Ideas → Concept Lock → Production Prompts | Dials + anchors. No seeds, no world modifiers. |
| **Full → Short-Form** | Build the world, THEN produce viral content from it | Full config — short-form inherits later. |

**Command:** `run full pipeline` / `run short-form` / `run both`

The config screen adapts:
- **Full Pipeline** → shows all controls
- **Short-Form** → hides Tech Seeds, simplifies modifiers, keeps dials + anchors
- **Both** → shows all controls (short-form inherits what's relevant)

---

## Step 2: Set the Dials

Three dials (two for short-form). Set each before generating.

### Alien Dial (1-10)

How strange should this get?

| Level | Feel |
|-------|------|
| 1-2 | Safe. Recognizable. Category-normal. |
| 3-4 | Subtly off. Something's different but you can't name it. |
| 5-6 | Noticeably breaking conventions. Clients get nervous. |
| **7-8** | **Uncomfortable territory. Feels risky. (IP Engine default)** |
| 9-10 | Parallel universe. Impossible until it lands. |

**Command:** `set alien [1-10]` — or accept default 7.

### Spacecadet Dimensions (select emphasis)

Four dimensions. All always present as background radiation. But you can EMPHASIZE 1-2 to steer the output.

| Dimension | What It Pushes |
|-----------|---------------|
| **Sci-Fi** | Speculative technology, futurism, infrastructure, systems |
| **Surreal** | Dream logic, visual strangeness, impossible geometry, glitches |
| **Spiritual** | Consciousness, mythology, transcendence, sacred questions |
| **Satiraverse** | Cultural critique, dark humor, systemic exposure, teeth |

**Command:** `emphasize [dimension]` — or `emphasize [dim1] + [dim2]`. Or leave balanced (all four equal weight).

**Minimum:** At least 2 dimensions present in final output.

### Tech Seeds (territory)

2,452 speculative technologies across 7 libraries. Don't load all of them. Select the territory that matches your concept.

| Territory | Seeds | Loads When |
|-----------|-------|-----------|
| Body & Life | 503 | Body, enhancement, death, biology |
| Mind | 170 | Intelligence, identity, memory, consciousness |
| Space & Time | 44 | Dimensions, time, stasis, reality |
| World & Environment | 431 | Infrastructure, materials, cities, ecology |
| Society & Control | 344 | Governance, surveillance, economy, law |
| Transport & Movement | 500 | Vehicles, teleportation, flight |
| Machines & Weapons | 460 | Robots, AI, weapons, defense |

**Command:** `load seeds [territory]` — or `no seeds` for concepts that don't need speculative tech. Seeds activate at Stage 2 (Worlds), not Stage 1.

### Reference Anchors (2-3 touchstones)

Lock 2-3 films, shows, artists, or works that define the north star for this IP. These aren't casual references — they're the persistent creative compass. Every stage checks against them.

**What anchors do:**
- **Stage 1 (Ideas):** "Would this spark feel at home in the world of [anchor]?"
- **Stage 2 (Worlds):** "Does this world's texture/tone sit in the neighborhood of [anchor]?"
- **Stage 3 (Stories):** "Would this story's emotional register work in a double feature with [anchor]?"
- **Stage 4 (Vis-Dev):** Anchors feed directly into VLD references. Style Lock, palette, lighting, composition all triangulate from the anchors.
- **Stage 5 (Scenes):** "Would this scene feel native in a trailer for [anchor]?"
- **Stage 6 (Shots):** Anchors inform prompt language — "the lighting of [anchor], the framing of [anchor]."
- **Short-Form:** "Would this piece sit in the same feed as content from [anchor]?"

**How to pick anchors:**

| Rule | Why |
|------|-----|
| **Max 3** | More than 3 and they cancel each other out. The triangulation needs precision. |
| **At least 1 visual, 1 tonal** | One anchor should define how it LOOKS. One should define how it FEELS. The third (if used) can be wild card — a music artist, a brand, a game, a photographer. |
| **Name what you TAKE and what you LEAVE** | "Coen Brothers — take the landscape-as-moral-commentary, leave the nihilism." "Miyazaki — take the world-as-character, leave the pastoral pace." Every anchor has a take and a leave. |
| **They don't have to be similar** | The most interesting IPs come from anchors that shouldn't coexist. "Wes Anderson meets Bong Joon-ho" creates a specific, productive tension. "Wes Anderson meets Wes Anderson" creates nothing. |

**Command:** `anchor [work] — take [X], leave [Y]`

**Examples:**
```
anchor Coen Brothers — take dry landscape morality, leave nihilism
anchor Miyazaki — take living worlds, leave slow pacing
anchor Kanye (production) — take maximalist layering, leave ego
```

---

## Step 3: Select Idea Modifiers (Stage 1 only)

Optional. These constrain HOW ideas are generated. Stack multiple.

| Modifier | What It Locks | When to Use |
|----------|--------------|-------------|
| **Violation Mode** | All ideas must use Promise Break title move. No other moves. | When you want pure violation energy — break every assumption. |
| **Satiraverse** | All ideas locked to satire/critique register. | When the concept is cultural commentary first. |
| **Anti-Taste** | Inverts the taste filter. PASS becomes FAIL. FAIL becomes PASS. | When you want to explore what the taste profile rejects. Deliberately transgressive. |
| **Emotional Register** | Lock to a specific emotion (WOW / NAH / HMM / NSFW / LOL / WTF / UGH). | When you want ideas that hit one feeling. |
| **Contrast Mode** | Stack two emotional registers. The collision is the constraint. | When you want internal contradiction in every spark. |

**Command:** `modifier [name]` — or `no modifiers` for unconstrained generation.

---

## Session Config Output

After setup, confirm the session:

```
═══════════════════════════════════════════
SESSION CONFIG
═══════════════════════════════════════════
Pipeline:         [Full / Short-Form / Both]
Alien Dial:       [N] / 10
SC Dimensions:    [emphasized dimensions or "balanced"]
Tech Seeds:       [territory or "none"] (Full pipeline only)
Reference Anchors:
  1. [work] — take [X], leave [Y]
  2. [work] — take [X], leave [Y]
  3. [work] — take [X], leave [Y] (optional)
Modifiers:        [list or "none"]
Taste Profile:    [On / Off]
═══════════════════════════════════════════
```

This config is referenced at every stage. If context compresses or a new session starts, reload from the saved IP Bible.

---

## Changing Dials Mid-Pipeline

Dials can be adjusted at any stage. But changes must be noted in the IP Bible so the record is accurate.

| What | Can Change? | Notes |
|------|------------|-------|
| Alien dial | Yes, at any stage | Common to lower at vis-dev (production constraints) or raise at scenes (push weird territory). |
| Dimension emphasis | Yes, at any stage | The world may reveal which dimensions are strongest. |
| Tech seeds | Add territory at Stage 2+ | Don't remove seeds already integrated into the world. |
| Reference anchors | Yes, but rarely | Anchors usually hold. If you swap one, note it in the IP Bible Change Log — it may shift everything downstream. |
| Modifiers | Stage 1 only | Modifiers are ideation tools. They don't apply past spark generation. |
| Taste filter | Yes, any stage | On by default. Turn off when you want to explore without the quality floor. Turn back on before locking. |
| Pipeline | Can switch to short-form at any point | Any approved material carries forward. |

---

## Persistent Actions (Available at Every Stage)

These actions are always available — not locked to a specific stage.

| Action | What It Does | When to Use |
|--------|-------------|-------------|
| **Spacecadetify** | Run the Spacecadet Brand dimensions against current output. Amplify Sci-Fi, Surreal, Spiritual, or Satiraverse presence. Returns amplification suggestions with specific options. | Any time output feels too conventional, too safe, not weird enough. Works on sparks, worlds, stories, scenes, prompts — anything. |
| **Edit** | Inline edit any approved output. Change names, rewrite descriptions, adjust details. Saves updated version to IP Bible with Change Log entry. | Anytime. The user is always in control. Approvals aren't permanent — they're the current best version. |
| **→ Short-Form** | Branch current concept/spark/scene to the short-form pipeline. | Any spark in Stage 1. Any scene in Stage 5. Any moment from any stage that has viral energy. |
| **→ Build World** | Send a spark or concept into the full pipeline (Stage 2). | Any spark in Stage 1 that deserves franchise depth. Can also be triggered from short-form if a concept reveals world potential. |
| **Toggle Taste Filter** | Turn the 12-principle quality filter on or off. | On = quality floor enforced. Off = explore freely, no gates. |
