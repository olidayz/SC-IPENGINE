# 3A-SEEDS

Stage 1 of story development. The world becomes a set of story doors.

---

## Anti-Patterns (Read First)

Kill any seed that matches these before presenting:

| Anti-Pattern | Signal | Why It Dies |
|-------------|--------|------------|
| **The Thesis Paper** | Premise is a theme ("it's about identity") not a causal chain | No engine. Egri: trait → action → consequence or nothing. |
| **The Tour Guide** | Protagonist walks through the world experiencing it | No wound, no pressure, no collision. A travel brochure. |
| **The Explainer** | Story exists to deliver worldbuilding exposition | Mamet: if it doesn't advance the objective, cut it. |
| **The Good Guy** | Protagonist has no wound, just obstacles | No internal contradiction = no character. |
| **The Message** | Resolution argues a position instead of demonstrating consequence | O'Connor: fiction that becomes argument dies. |
| **The One-Trick** | Remove the world's signature mechanic and the story collapses | A demo, not a story. Independence test failure. |
| **The Chosen One** | Protagonist is special because the plot says so | No agency. The crisis should come FROM the character's flaw. |
| **Villain-Dependent** | Remove the villain and no tension remains | Structural conflict > personal antagonism. |

### Process Anti-Pattern

| Anti-Pattern | Signal | Why It Dies |
|-------------|--------|------------|
| **The Open Kitchen** | Presenting prompt family findings, evaluation tables, coverage matrices, bundling rationale to the user | The user sees **stories**, not process. Prompt families are generation infrastructure — internal only. Every token spent displaying machinery is a token not spent on craft. If a hook reads as a description instead of a scene, the kitchen door was open. |

---

## Output: Stories, Not Seeds

The prompt families generate raw character-level findings. But the user doesn't see those — they see **stories**. A story is a core protagonist surrounded by supporting arcs that collide with each other.

**Present 3-5 stories.** Each story is scannable: protagonist + premise first, then wound + hook + ensemble underneath.

### Story Format

**[TITLE]**
[Logline: One sentence — the world-level hook. What is this story about before we know the character?]

**[Protagonist name]** — [position in world, one phrase]
[Premise: Trait → Action → Consequence, one sentence]

**Wound:** [Need vs. Want]

**Hook:** [The image or moment that IS this story]

**Ensemble:**
- [Name — role in this story, one line]
- [Name — role in this story, one line]
- [Name — role in this story, one line]

---

## Integration

- **Load:** `daniel-taste-profile/SKILL.md` → PASS/FAIL criteria + reference tags (REQUIRED)
- **Input:** Complete world build from 2-worlds (REQUIRED)
- **Reference:** `story-references.md` → genre engine examples, emotional register examples, anti-patterns (REQUIRED)

---

## Generation Process

### Step 1: Read the World

Before any generation, establish the world's material:
- 6 systems (Power, Economy, Biology, Technology, Culture, Geography)
- Factions and their claims
- Named characters and their positions
- Objects and artifacts
- Sacred Question
- Existing franchise vectors

Announce what you're working with:

> **World material loaded.**
> **Systems:** [list]
> **Factions:** [count] with [brief tension summary]
> **Named characters:** [count]
> **Sacred Question:** [question]
> **Running 5 prompt families.**

### Step 2: Run Prompt Families (Internal — Not Presented)

**Do not display prompt family findings, tables, or evaluation matrices. The user sees stories (Step 5), not generation infrastructure. Spend tokens on hook craft and ensemble precision, not process narration.**

Run all 5 families against the world. Not every prompt will have energy — note which ones fire and which don't. This step produces raw character-level findings — protagonist candidates, wound sketches, collision points, pressure mechanisms. These are working material, not the output.

---

#### Family 1: WORLD PRESSURE
*"What does this world do to people?"*

| Prompt | Ask the World |
|--------|--------------|
| **Monster** | What threat lives here? What confines people with it? What sin created it? |
| **Institution** | What group demands loyalty? What does joining cost? What does leaving destroy? |
| **Cage** | What traps people? What would escape cost everyone left behind? |
| **Clock** | What's running out? What happens when it does? |

Every answer should name a specific character position where the pressure is unbearable.

#### Family 2: CHARACTER WOUND
*"Who is broken here, and how?"*

| Prompt | Ask the World |
|--------|--------------|
| **Need vs. Want** | Who needs one thing but wants another? Where does that gap become unbearable? |
| **Blind Spot** | Who can't see what everyone else sees about them? What would force them to look? |
| **The Fool** | Who sees truth that everyone else misses? Why does nobody listen? |
| **Secret Keeper** | Who is hiding something? What would exposure cost — and who benefits from the lie? |

Every answer should identify a specific wound, not just a character.

#### Family 3: GENRE ENGINE
*"What structural machine drives this story?"*

| Prompt | Ask the World |
|--------|--------------|
| **Quest** | Who's searching for something the world says doesn't exist? What does finding it cost? |
| **Mystery / Whydunit** | What doesn't add up? — OR — Why did this person do this terrible thing? |
| **Horror** | What violation of natural order haunts this world? What does confronting it reveal? |
| **Wish / Consequence** | If someone got exactly what they wanted, what would go wrong? |
| **Forbidden** | What connection does this world forbid? What makes two people pursue it anyway? |

Mystery = hidden information (what happened?). Whydunit = hidden character (why did they do it?). Different engines — don't conflate.

#### Family 4: AUDIENCE FEELING
*"What does the viewer experience?"*

| Prompt | Ask the World |
|--------|--------------|
| **Revenge** | Who's been wronged beyond forgiveness? What does pursuing justice cost them? |
| **Obsession** | Who has a hole they keep trying to fill? What's never enough? |
| **Fall** | Who seems to have everything? What's the crack? When does it all come apart? |
| **Escape** | Who is trapped? What makes staying finally unbearable? What's on the other side? |
| **Sacrifice** | What can only be saved by giving something irreplaceable? Who makes that choice? |

Start from the gut. Name the feeling first, then find the character.

#### Family 5: THE COLLISION
*"Where do incompatible things meet?"*

| Prompt | Ask the World |
|--------|--------------|
| **System × System** | Where do world systems produce irreconcilable demands on one person? Map all 15 pairwise from 6 systems. Identify which 5-8 create genuine pressure. |
| **Faction × Faction** | Which factions have the most personal reason for conflict? Where are two valid worldviews irreconcilable? |
| **Perception × Reality** | What does everyone assume this world is about? How is it actually about the opposite? |
| **Past × Present** | What buried history is about to surface? What old wound is reopening now? |
| **Self × Self** | Where is a character at war with themselves? Two identities that can't coexist? |

The Collision family often produces the strongest seeds. Don't rush it. The System × System prompt alone can generate 5-8 viable seeds.

---

### Step 3: Bundle Into Stories

The prompt families produce character-level findings — protagonist candidates, wounds, collision points, pressure sources. Many of these will cluster naturally into the SAME story told from different angles. An Alfred finding, a Tim finding, and a Bruce finding might all be threads in one story.

**Bundling process:**
1. Identify which character findings share the same central collision or pressure source
2. For each cluster, choose the **core protagonist** — the character whose wound drives the story
3. Slot remaining characters as **ensemble** — supporting arcs that orbit, pressure, or mirror the protagonist
4. Write the premise from the protagonist's perspective (trait → action → consequence)
5. Kill clusters that don't cohere into a single premise — if you can't state it in one sentence, it's not one story

**Target: 3-5 stories.** A rich world might produce 5. A focused world might produce 3. More than 5 means you haven't bundled tightly enough.

### Step 4: Evaluate

Run each story (not each character finding) against the gates.

#### Sauce Mothers (Light Standard)

| Mother | Story Must Have |
|--------|---------------|
| **Premise** | One-sentence causal chain from the protagonist's trait |
| **Wound** | Protagonist's need/want gap is identifiable |
| **Pressure Cooker** | Named forcing function — world makes inaction impossible |
| **Collision** | Describable turn — what breaks, what can't be un-known |
| **Cost** | Something at stake — what could be lost |

#### Kill Gates (Binary — Pass or Die)

| Gate | Test | Kill If |
|------|------|---------|
| **Mamet** | Protagonist's objective is a verb phrase | Objective is a feeling, not an action |
| **Egri** | Premise is a causal chain, not a theme | "It's about X" instead of "X leads to Y which results in Z" |
| **Independence** | Story survives without the world's signature mechanic | Remove the trick and the story collapses |
| **Sympathy** | Protagonist tries, fails, tries again under constraint | Protagonist is passive or already knows the answer |
| **Faction** | 2+ factions with incompatible valid positions | Clear good guy vs. bad guy |

### Step 5: Present

Present 3-5 stories in the story format. Protagonist + premise first (the scan line), then wound + hook + ensemble underneath (the detail layer).

After presenting, note:
- Which stories overlap (characters appearing in multiple stories = franchise signal)
- Which prompt families drove the strongest stories
- Any characters that didn't fit into a story (interesting loners worth flagging)

Ask user to select 1-3 for arc development.

---

## Notes on Bundling

The best stories often emerge when character findings from different prompt families land in the same cluster. A World Pressure finding (the institution), a Character Wound finding (the blind spot), and a Collision finding (past × present) might all describe the same story from different angles. That convergence is signal — the story is real.

Characters that appear in multiple story bundles are franchise connective tissue. Flag them.

Characters that fit nowhere might be interesting standalone VV concepts or anthology entries. Note them separately.

---

## Coverage Check (Internal)

After generation, verify you've searched broadly enough. Not for the user — for yourself.

| Family | Prompts Asked | Findings | Stories Fed |
|--------|:------------:|:--------:|:-----------:|
| World Pressure | /4 | | |
| Character Wound | /4 | | |
| Genre Engine | /5 | | |
| Audience Feeling | /5 | | |
| The Collision | /5 | | |

If any family produced 0 findings, note it — that's information about the world's story-nature.

---

**Exit:** User selects 1-3 stories. Proceed to Stage 2 — `3b-arcs.md`.
