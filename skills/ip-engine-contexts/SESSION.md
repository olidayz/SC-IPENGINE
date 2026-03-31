# SESSION — Configure Before You Start

Set the dials, pick your modifiers, configure the pipeline. Do this ONCE at the start of any IP Engine run. The session config carries forward through all stages.

---

## Step 1: Set the Dials

Three dials. Set each before generating.

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

---

## Step 2: Select Idea Modifiers (Stage 1 only)

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

## Step 3: Select Pipeline

| Pipeline | When | Command |
|----------|------|---------|
| **Full** | Franchise-scale IP: Ideas → Worlds → Stories → Vis-Dev → Scenes → Shots | `run full pipeline` |
| **Short-Form** | Viral content: Ideas → Concept Lock → Production Prompts | `run short-form` |
| **Full → Short-Form** | Build the world, THEN produce viral content from it | `run full pipeline` then `run short-form` on completed IP |

---

## Session Config Output

After setup, confirm the session:

```
═══════════════════════════════════════════
SESSION CONFIG
═══════════════════════════════════════════
Alien Dial:       [N] / 10
SC Dimensions:    [emphasized dimensions or "balanced"]
Tech Seeds:       [territory or "none"]
Modifiers:        [list or "none"]
Pipeline:         [Full / Short-Form]
Taste Profile:    Always on
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
| Modifiers | Stage 1 only | Modifiers are ideation tools. They don't apply past spark generation. |
| Pipeline | Can switch to short-form at any point | Any approved material carries forward. |
