# 3B-ARCS

Stage 2 of story development. Selected seeds become full narrative blueprints.

---

## Anti-Patterns (Read First)

These are arc-development failures, not seed failures. A seed can pass all gates and still produce a bad arc.

| Anti-Pattern | Signal | Fix |
|-------------|--------|-----|
| **The Symmetrical Opponent** | Opponent is a mirror of the protagonist with no independent claim | Give the opponent a VALID position. They should be right about something the protagonist is wrong about. |
| **The Inert Collision** | The hinge moment is something that happens TO the protagonist | The discovery must come FROM the protagonist's own actions — they create the conditions for their own revelation. |
| **The Clean Resolution** | Protagonist gains everything, loses nothing | Cost must be real. If nothing is surrendered, the audience feels cheated. |
| **The Drift** | Arc stops using the world's systems and becomes a generic story | Stress-test: are the faction names, system mechanics, and world rules actively shaping events? |
| **The Lecture** | Resolution delivers a moral instead of demonstrating a consequence | O'Connor: show what happens. Don't tell us what it means. The audience does that work. |

---

## Story Window Format

Every arc produces one Story Window. This is the exit artifact — the blueprint that renders and scenes build from.

### Formatting Principles

1. **Setup before premise.** The reader should be oriented cold — logline, world summary, key characters — before encountering story structure.
2. **Every section opens with a 1-2 line italic summary.** The summary layer is the story. The detail layer is the craft. A reader scanning only the italics should understand the full arc.
3. **Scannable density.** Pressure Cooker and other long sections use numbered sub-elements. No walls of text — high-level understanding first, details underneath.
4. **No Tags section.** Genre engine, emotional register, Booker shape, tonal register, and source prompts are internal generation infrastructure. They do not appear in the Story Window.
5. **No Stress Tests or Diagnostic in output.** Run stress tests silently. If a test fails, fix the window. The user sees the result, not the QA process.

### Template

```
# [STORY TITLE] — Story Window

---

## Logline

[One sentence — the hook before you know any characters.]

---

## Setup

[1-2 paragraphs orienting a cold reader. What is this world? What's the situation? Written as prose, not structure.]

**Key characters:**

- **[Name]** — [role + defining quality, one line]
  [What they're performing + what they're hiding, one line. Enough for downstream visual design to infer psychology.]
- **[Name]** — [role + defining quality, one line]
  [Performance + secret, one line.]
- **[Name]** — [role + defining quality, one line]
  [Performance + secret, one line.]
[3-6 characters. Only characters who appear in this Story Window. The second line per character feeds 4-vis-dev — it's the psych hook the visual designer builds from.]

---

## The Premise

*[Egri machine in italic: Trait → Action → Consequence. 1-2 sentences max.]*

[1-2 sentences expanding: how the premise functions as a causal engine for the story.]

---

## The Protagonist

*[1-2 line summary: the need/want gap and why it's unbearable.]*

[The wound elaborated. The defining choice — the decision that reveals character under pressure. What they choose, why, and what it says about someone shaped by this system.]

---

## The Opponent

*[1-2 line summary: why their position is valid and how they apply pressure.]*

[Valid claim. Method of pressure. The mirror — what they share with the protagonist that makes the conflict personal.]

---

## The Pressure Cooker

*[1-2 line summary: the arc of escalation in plain language.]*

**Inciting Event:** [What disrupts equilibrium. 2-3 sentences.]

**Clock:** [What makes delay impossible. 2-3 sentences.]

**Three complications, each caused by the last:**

**1. [Short label.]** [One paragraph. The complication, its cause, its consequence.]

**2. [Short label.]** [One paragraph.]

**3. [Short label.]** [One paragraph.]

---

## The Collision

*[1-2 line summary: the discovery and what it means.]*

[The discovery elaborated — how it emerges from the protagonist's own actions. The reversal — what they were moving toward vs. what they're now moving toward.]

**Before:** "[Worldview sentence.]"
**After:** "[Worldview sentence.]"

[Optional: one calibration reference in italic.]

---

## The Cost

*[1-2 line summary: what's gained, what's lost, stated plainly.]*

[What the audience understands — the felt clarification. Sacred Question response — how this story embodies the world's central question, lived through consequence.]

---
```

---

## Integration

- **Load:** `daniel-taste-profile/SKILL.md` → Full profile (REQUIRED)
- **Input:** Selected seeds from 3a + complete world build (REQUIRED)
- **Reference:** `story-references.md` → Sauce Mother film examples for calibration (REQUIRED)

---

## Development Process

For each selected seed, work through 5 stages. Each stage corresponds to a Sauce Mother — applied with full rigor, not the light touch from 3a.

### Stage 1: The Premise (Egri + McKee)

Expand the seed's one-sentence premise into the story's causal engine.

**Test:** Can you trace every major story event back to this sentence? If an event doesn't connect to the premise, it doesn't belong in this story.

**Calibration:** The premise of *Chinatown* — "Obsessive pursuit of truth in a corrupt system leads to exposing the powerful, which results in the powerful winning anyway." Every scene in the film either advances or resists this machine.

### Stage 2: The Wound (Truby + Egri)

Build the full character web from the seed's need/want gap.

**The Protagonist:** What do they need (internal, psychological, often invisible to them) vs. what do they want (external, concrete, actively pursued)? The gap between these IS the character.

**The Opponent:** Not a villain. The opponent holds a valid counter-position — a different answer to the same moral question the protagonist is asking. They apply pressure that forces the wound to surface.

**The Character Web:** Every named character in the Story Window should represent a different possible answer to the story's central question. If two characters hold the same position, merge them or cut one.

**Calibration:** In *Moonlight*, every major character — Juan, Paula, Kevin, Terrel — represents a different answer to "how do you survive as a Black queer man in this world?" No two occupy the same position.

### Stage 3: The Pressure Cooker (Mamet + McKee + Aristotle)

Build the escalation structure from the seed's forcing function.

**Inciting Event:** What disrupts equilibrium? Must connect to the world's systems, not just personal circumstance.

**Clock:** What makes delay impossible? Name the specific mechanism — ticking clock, narrowing options, rising stakes.

**Progressive Complications:** Three escalations, each narrowing the protagonist's options. Each complication should be causally connected to the previous one — not random obstacles but consequences of the protagonist's own choices.

**World Systems Check:** Which of the world's 6 systems are actively generating pressure? If fewer than 2, the story may have drifted from the world. If more than 4, it may be unfocused.

**Calibration:** In *Get Out*, the progressive complications are Chris noticing increasingly wrong things — each "reasonable explanation" he accepts takes him deeper. The social pressure system and the power system are both generating the trap. Every complication narrows his exit options.

### Stage 4: The Collision (Truby + O'Connor)

Build the hinge from the seed's described turn.

**Discovery:** What does the protagonist learn that cannot be un-known? This must emerge from their own actions — not delivered by exposition or coincidence.

**Reversal:** How does this knowledge flip the story's trajectory? What was the protagonist moving toward, and what are they now moving toward instead?

**Before/After:** State the worldview shift in one sentence each. Before the collision, the protagonist believed X. After, they understand Y. The gap between X and Y IS the story's meaning.

**Test:** If you remove the Collision, does the story still have a shape? If yes, the Collision isn't strong enough. It should be the hinge the entire structure turns on.

**Calibration:** In *The Truman Show*, Truman reaches the wall. The sky is painted. Everything he knew was manufactured. Before: "My life is real." After: "My life was constructed." The only remaining action is to leave.

### Stage 5: The Cost (Aristotle + O'Connor + Saunders)

Build the resolution from the seed's stakes.

**What's Gained:** Be specific. Not "understanding" — what specifically does the protagonist now have or know?

**What's Lost:** Be specific. Not "innocence" — what specifically can they never get back?

**What the Audience Understands:** This is catharsis — not emotional release but emotional *clarification*. The audience now understands something about the premise that they didn't before. State it.

**Sacred Question Response:** How does this specific story embody the world's Sacred Question? The protagonist's journey should be the question made personal. Not answered didactically — lived through consequence.

**Test:** Does the resolution demonstrate or argue? If it argues a position, rewrite. The world answers honestly through consequence, not through messaging.

**Calibration:** In *Eternal Sunshine*, Joel gains Clementine back. Loses the certainty that it'll work. The audience understands: love is choosing someone knowing exactly how it ends. The film doesn't argue this — it demonstrates it through the decision Joel makes.

---

## Stress Tests (Run Silently — Do Not Present)

Run these on each completed Story Window. If a test fails, fix the window before presenting. The user sees the result, not the QA.

| Test | Question | If Fail |
|------|----------|---------|
| **World Fidelity** | Does this story use the world's actual systems, factions, rules, and characters? Or has it drifted into generic narrative? | Reground in world material. Name specific factions, systems, locations. |
| **Character Web** | Does every named character represent a different answer to the same moral question? | Merge or cut redundant positions. |
| **O'Connor** | Does the resolution show consequences or argue a position? | Rewrite resolution. World answers honestly. |
| **Saunders** | At every major beat, what does the audience expect? Does the story productively violate that expectation? | Find the predictable beats and twist them. |
| **Independence** | Does this story survive if you remove the world's signature mechanic? | If not, find the human story underneath the mechanic. |
| **Taste Filter** | Does this Story Window pass Daniel's taste profile PASS/FAIL criteria? | Flag specific failure points. |

---

## Presentation

Present each Story Window in the template format above. The italic summary layer should tell the full story on its own — a reader scanning only italics understands the arc.

Do not present: Tags, Stress Test results, Diagnostic notes, Sauce Mother analysis, or any other generation infrastructure. These are internal. The output is the story.

---

**Exit:** Story Windows ready for 4-vis-dev (visual development) or 5-scenes (scene writing). User decides which path.
