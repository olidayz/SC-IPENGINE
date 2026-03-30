# 4A-ART-DIRECTOR

Stage 1 of visual development. Establish the visual grammar — the rules that constrain everything downstream.

---

## Anti-Patterns (Read First)

Kill any VLD that matches these before presenting:

| Anti-Pattern | Signal | Why It Dies |
|-------------|--------|------------|
| **The Mood Board** | Pretty images with no rules. Vibes without decisions. | A VLD is a system, not an aesthetic. Every component must be a decision with consequences — if you could swap it out and nothing breaks, it's decoration, not direction. |
| **The Reference Dump** | 15 film references, no synthesis. Name-dropping without extraction. | Max 8 references. Each one says what to TAKE and what to LEAVE. A reference without a "leave behind" note is tourism, not art direction. |
| **The Monochrome** | One visual mode for the whole story. Everything looks the same regardless of emotional register. | The VLD must support the story's tonal range. If the story has light, dark, and weird registers, the VLD needs visual modes for each. A single look is a poster, not a world. |
| **The Costume Drama** | Focuses on what people wear, ignores what spaces feel like. | Art direction is environment-first. Characters exist INSIDE the world. Start with air, light, and surface — then put people in it. |
| **The Generic Genre** | "Neo-noir," "cyberpunk," "gothic" as a complete visual language. | Genre is a starting point, not a destination. "Neo-noir" describes a thousand different looks. What makes THIS neo-noir different from every other one? |

### Process Anti-Pattern

| Anti-Pattern | Signal | Why It Dies |
|-------------|--------|------------|
| **The Open Kitchen** | Presenting cluster findings, synthesis notes, option comparisons, principle evaluations to the user | The user sees the VLD, not the generation process. Perspective clusters are internal machinery. Every token spent on process narration is a token not spent on visual specificity. |

---

## The 7 Principles of Visual Language

These are the generative engine AND the evaluation framework. When generating, run the prompts. When evaluating, check each principle was served.

### Principle 1: CONTRAST SYSTEM

*How difference creates meaning.*

Every visual world is built on contrasts — without them, nothing reads. The contrast system defines the axis of visual tension that gives the world its charge.

| Prompt | Ask the World |
|--------|--------------|
| **Binary** | What's the dominant visual opposition? Light/dark, clean/distressed, organic/synthetic, old/new, vertical/horizontal? Name the axis. |
| **Gradient** | Where do the poles of contrast bleed into each other? Pure binary is cartoon. Where's the grey zone? |
| **Violation** | When does something appear on the wrong side of the contrast? A clean thing in a dirty place? A warm color in a cold palette? That violation carries meaning — name it. |

**Benchmark:** *Parasite* — above/below, sun/rain, clean/stained. The Parks' house is all light and horizontal space. The Kims' semi-basement is vertical, cramped, and damp. When the Kims infiltrate upward, they bring the stain with them.

### Principle 2: CONSTRAINT AS IDENTITY

*The rules that make THIS world look like itself and nothing else.*

What you can't do matters more than what you can. The visual constraints ARE the identity — remove one and the world loses its face.

| Prompt | Ask the World |
|--------|--------------|
| **Forbidden** | What's visually forbidden in this world? What color, material, or composition would BREAK the VLD if it appeared? |
| **Signature** | What's the one visual element that IS this world? If you saw it in isolation, you'd know where you are. |
| **Removal Test** | Take out the signature element. Does the VLD collapse into generic? If yes, the constraint is load-bearing. If no, find the real constraint. |

**Benchmark:** *Wes Anderson* — symmetry is the constraint. Remove it and the films lose their visual identity entirely. The constraint IS the authorship.

### Principle 3: EMOTIONAL CARTOGRAPHY

*How the story's emotional range maps to visual treatment.*

The story has tonal registers (from the Story Window). Each register needs a distinct visual mode. The VLD is a map of how feelings look.

| Prompt | Ask the World |
|--------|--------------|
| **Register Map** | List the story's tonal registers. What does each one LOOK like? Different palette? Different lighting? Different composition? |
| **Transition** | How does the visual language shift between registers? Gradual (color temperature drift) or abrupt (hard cut to new palette)? The transition style IS a creative decision. |
| **Ceiling and Floor** | What's the most beautiful this world gets? What's the most disturbing? Define the extremes — everything else lives between them. |

**Benchmark:** *Succession* — core register is desaturated luxury (neutral tones, architectural precision, cold light). Emotional breakdowns get warmer, messier, handheld. The Tuscan villa episodes shift the entire palette. You FEEL the register change before you process it consciously.

### Principle 4: MATERIAL TRUTHFULNESS

*Surfaces tell stories. What things are made of, how old they are, who touched them.*

Production design is archaeology. Every material in the frame has a history. The VLD should specify not just what materials exist, but what happened to them.

| Prompt | Ask the World |
|--------|--------------|
| **Age** | What's new here? What's old? What's been repaired? What's been neglected? The age of surfaces reveals the economy of care. |
| **Hands** | Who touches these surfaces? Working hands or gloved hands? What traces do they leave? Fingerprints, scuff marks, polish? |
| **Origin** | Where do the materials come from? Local or imported? Organic or manufactured? The material supply chain reveals the world's economy and values. |
| **Wear Pattern** | What gets used most? Where are the smooth spots, the stains, the repairs? Wear patterns are behavioral archaeology — they tell you how people actually live. |

**Benchmark:** *Blade Runner 2049* — Villeneuve's surfaces are SPECIFIC. Wallace Corp is obsessive minimalism — water, wood, zero dust. The orphanage is rust, ash, corroded metal. K's apartment is worn synthetic — clean but exhausted. Every material tells you about the power structure.

### Principle 5: LEGIBLE DISTANCE

*The visual must work at three scales — wide, medium, close.*

A visual language that only works in establishing shots is incomplete. A visual language that only works in close-up has no sense of place. Every VLD decision should be tested at three distances.

| Prompt | Ask the World |
|--------|--------------|
| **Wide** | What does this world look like from above or afar? The skyline, the landscape, the atmosphere. What's the first impression? |
| **Medium** | What does this world look like at human scale? Walking through it. The street, the corridor, the room. What surrounds you? |
| **Close** | What does this world look like in detail? The texture of a wall, the label on a bottle, the stitching on a jacket. What rewards close inspection? |

**Benchmark:** *Mad Max: Fury Road* — works at every distance. Wide: the desert wasteland, dust storms, convoy silhouettes. Medium: the War Rig, the pole cats, the citadel entrance. Close: Max's muzzle, Furiosa's prosthetic, the steering wheel brand. Every scale tells the story.

### Principle 6: LIGHT AS NARRATOR

*Light source = power source. What's illuminated is what's sanctioned. What's in shadow is what's hidden.*

Light isn't decoration — it's the world's moral commentary. The VLD should specify not just how things are lit, but what the lighting MEANS.

| Prompt | Ask the World |
|--------|--------------|
| **Source** | Where does light come from in this world? Natural or artificial? Who controls the light sources? Control of light = control of attention = control of truth. |
| **Permission** | What's allowed to be seen? What's kept in shadow? Lighting permissions map to power structures — the powerful are illuminated on their terms. The hidden resist illumination. |
| **Shift** | How does light change across the story? If Act 1 is fluorescent institutional and Act 3 is natural dawn, that's a narrative arc told entirely through light. |

**Benchmark:** *Zodiac* — Fincher uses light as institutional control. The newsroom: flat fluorescent, everything exposed, nowhere to hide. Basements and archives: single-source, deep shadow, where the real information lives. The light itself tells you: the institution shows you what it wants you to see.

### Principle 7: TIME SIGNATURE

*How time manifests visually. A world's relationship to its own past and future is visible in every frame.*

Most worlds contain multiple eras simultaneously — architecture from one period, technology from another, fashion from a third. The Time Signature defines how temporal layers coexist.

| Prompt | Ask the World |
|--------|--------------|
| **Layers** | What eras are visually present simultaneously? Victorian buildings with LED signs? 1970s infrastructure with 2030s surveillance? Name the layers. |
| **Decay Rate** | How fast do things age in this world? Is it a place where things are maintained, or where entropy wins? The decay rate reveals the world's relationship to its own permanence. |
| **Ghosts** | What traces of the past are still visible? Old signage, former use, architectural fossils, buried infrastructure? The ghosts are the world's memory made visible. |

**Benchmark:** *Chernobyl* (HBO) — the Time Signature is Soviet infrastructure frozen at the moment of disaster. 1970s concrete, 1960s instrumentation, and then the intrusion of an event that stopped time. The visual tension is between the mundane age of the materials and the impossible thing that happened to them.

---

## Generation Process

### Step 1: Detect Visual Mode

Classify the world (Constructed / Revealed / Hybrid) from the SKILL.md router. Announce it.

### Step 2: Run 5 Perspective Clusters

Each cluster runs against the world build + story window, informed by the 7 principles. Each generates 3-5 options. Don't synthesize yet — let the options accumulate.

#### Cluster 1: ATMOSPHERE
*"What does the air feel like?"*
Principles served: Contrast System, Emotional Cartography, Time Signature.

| Prompt | Ask the World |
|--------|--------------|
| **Default** | What does this world look like on an ordinary day? Not the dramatic moments — the baseline palette, weather, light. The air you breathe when nothing is happening. |
| **Extreme** | What does the world look like at its most visually intense? The storm, the crisis, the celebration. How far does the palette stretch from baseline? |
| **Absence** | What's NOT in the atmosphere? No sun? No stars? No silence? No natural light? What's conspicuously missing from the environment — and what does its absence tell you? |
| **Rhythm** | Does the atmosphere change on a cycle? Day/night, season, shift change, ritual? What's the visual rhythm of an average day in this world? |

#### Cluster 2: MATERIAL
*"What are things made of?"*
Principles served: Material Truthfulness, Constraint as Identity, Time Signature.

| Prompt | Ask the World |
|--------|--------------|
| **Two Worlds** | What's the primary material contrast? Name two material vocabularies that coexist in this world (corporate glass vs. street concrete, organic growth vs. synthetic structure). |
| **Hands** | Who makes things in this world? Machine-made or handmade? Mass-produced or artisanal? The manufacturing origin of objects tells you about the economy. |
| **Age Map** | What's newest? What's oldest? What's been repaired? Where on the spectrum from pristine to ruined does each faction's territory sit? |
| **Forbidden Material** | Is there a material that shouldn't exist here but does? A material that's taboo, rare, or illegal? What does contraband LOOK like? |

#### Cluster 3: FRAME
*"How do we see it?"*
Principles served: Legible Distance, Contrast System, Light as Narrator.

| Prompt | Ask the World |
|--------|--------------|
| **Power Geometry** | What composition style belongs to power? Symmetry for institutions, asymmetry for resistance? Centered framing for authority, off-center for the displaced? Map composition to hierarchy. |
| **Distance Bias** | Does this world favor wide shots (landscape, architecture, scale) or close-ups (faces, objects, texture)? The default framing distance reveals what the world values — systems or individuals. |
| **Movement** | Is the camera steady or restless? Does it move WITH characters (tracking, following) or OBSERVE them (static, locked)? Camera behavior is a moral position — are we inside or outside? |
| **Light Logic** | Where does the key light come from in the world's most important spaces? Overhead (institutional), side (dramatic), below (unsettling), natural (honest)? Light direction = power direction. |

#### Cluster 4: REFERENCE
*"What does this remind us of — and where does it diverge?"*
Principles served: Constraint as Identity, Emotional Cartography.

| Prompt | Ask the World |
|--------|--------------|
| **Primary Lineage** | What 2-3 films or shows does this world visually descend from? Name the ancestors — then name what THIS world does that they didn't. |
| **Unexpected Source** | What non-film reference applies? Architecture, photography, painting, graphic design, fashion? The most distinctive visual languages borrow from outside cinema. |
| **Anti-Lineage** | What does this world explicitly NOT look like? What visual tradition would be the wrong reference — and why? The anti-reference defines the boundary. |

#### Cluster 5: EMOTION
*"What does looking at this world make you feel?"*
Principles served: Emotional Cartography, Light as Narrator, Contrast System.

| Prompt | Ask the World |
|--------|--------------|
| **Beauty** | Where does the beauty live in this world? Is it in the architecture, the light, the people, the decay, the violence, the quiet? Every world has its own form of beauty — name it. |
| **Discomfort** | Where does the discomfort live? What makes you uneasy looking at this world? The wrongness, the too-clean, the too-broken, the uncanny? |
| **Strangeness** | Where does the Spacecadet strangeness live? What's the visual element that makes this world feel like it belongs to THIS studio? (Calibrate with alien dial.) |
| **Warmth** | Where does the warmth live? Even the darkest worlds need pockets of warmth — the moment of relief, the human detail, the breath. What does comfort look like here? |

### Step 3: Synthesize into VLD

Reconcile across clusters. Contradictions between clusters are features — they create visual tension. Use the 7 principles as the synthesis framework: does the emerging VLD serve all 7?

### Step 4: Write Downstream Translation Notes

Add the prompt engineering bridge section (see VLD template below).

### Step 5: Gate Check (Internal — Do Not Present)

Run the VLD against all quality gates silently. Fix failures before presenting.

### Step 6: Present

Present the VLD in the template format. Ask user for approval or adjustments before proceeding to 4b/4c.

---

## VLD Output Template

Target: ~90-110 lines. Tables for systematic information, prose only for atmosphere. No redundancy — every concept stated once, referenced by shorthand thereafter.

```
# [WORLD TITLE] — Visual Language Document

## Visual Mode
[Constructed / Revealed / Hybrid — one sentence on why.]
*(1-2 sentences. The thesis.)*

## Visual Signature
[The ONE visual idea that makes this world THIS world. The constraint that, if removed, collapses the VLD into generic. Written as a short atmospheric paragraph — this is where the "feel" lives.]
*(3-5 sentences. Name the signature element, what it looks like in both its managed/sanctioned and unmanaged/transgressive forms, and why the difference between them IS the world.)*

## World System: Palette × Light × Material
[One integrated table. Merge color, lighting, and material — they overlap too much to justify separate sections. The "Feeling" column carries atmospheric weight in one punchy line.]

| Zone | Palette | Light | Key Material | Feeling |
|------|---------|-------|-------------|---------|
| [Faction/territory 1] | [Specific colors] | [Specific light sources] | [Specific materials + textures] | [1 line — the atmospheric punch] |
| [Faction/territory 2] | ... | ... | ... | ... |
| [Day/Night or other shift] | ... | ... | ... | ... |

*(One row per faction, territory, or major spatial zone. Include a Day/Night row if the shift matters. Name specific colors, materials, light sources — "sodium vapor amber" not "warm tones." 6-10 rows typical.)*

[1-2 sentences above the table naming the core contrast axis — the dominant visual opposition the table is organized around.]

## Composition × Tonal Register
[One integrated table. Merge composition rules and tonal registers — each register implies a framing approach, so keep them together.]

| Register | Frame | Movement | Aspect | Reference Feel |
|----------|-------|----------|--------|---------------|
| [Core register name] (default) | [Framing style] | [Camera behavior] | [Aspect ratio] | [1-line reference touchstone] |
| [Light register] | ... | ... | ... | ... |
| [Dark register] | ... | ... | ... | ... |
| [Special register if any] | ... | ... | ... | ... |

*(One row per tonal register from the story window. 3-5 rows typical.)*

## Time Layers
[Table format. How the past lives in the present.]

| Layer | Period | Material | State |
|-------|--------|----------|-------|
| [Era name] | [Date range] | [What it's made of] | [Preserved / Functional / Decaying / Frozen — plus 1 vivid detail] |

*(One row per era visually present. 2-4 rows typical. Include a line on decay rate if relevant.)*

## Visual Motifs

| Motif | Visual Form | Meaning |
|-------|------------|---------|
| [Motif name] | [What it literally looks like — variants, where it appears] | [What it signifies] |

*(3-6 motifs. Each row is a complete unit. No redundancy with World System table.)*

## References

| Reference | Take | Leave |
|-----------|------|-------|
| [Film/show] | [1 sentence — specific visual element to borrow] | [1 phrase — what NOT to borrow] |

*(5-8 references. Trim take/leave to single phrases.)*

| Anti-Reference | Why |
|---------------|-----|
| [Film/show/genre] | [1 sentence — why this is the wrong visual lineage] |

*(3-5 anti-references.)*

---

## Appendix: Downstream Translation (for 6-shots)

**Palette anchors:** [specific color names + hex codes that prompt well for image generation]
**Lighting keywords:** [quoted phrases separated by · ]
**Texture keywords:** [quoted phrases separated by · ]
**Composition cues:** [quoted phrases separated by · ]
**Anti-prompt warnings:** [term → replacement phrasing, separated by · ]
**Reference shorthand:** [shorthand = definition, separated by · ]
**Negative prompts:** [no X · no Y · no Z]
```

---

## Quality Gates (Run Silently)

| Gate | Test | Kill If |
|------|------|---------|
| **Taste Filter** | Does this VLD pass Daniel's aesthetic PASS/FAIL? | Bland, committee-feeling, generic sci-fi, generic noir, safe consensus |
| **World Fidelity** | Does the VLD reflect THIS specific world, not a genre? | Could apply to any noir, any corporate satire, any sci-fi — not specific enough |
| **Spacecadet Dimensions** | Does the visual language express at least 2 of 4 brand dimensions? | Looks like conventional prestige TV with no strangeness |
| **Tonal Range** | Can the VLD support the story's full emotional range? | Only works for one register — too locked to a single mode |
| **Downstream Viability** | Could a cinematographer, costume designer, and production designer all work from this? | Too vague to constrain, or too rigid to allow variation |
| **Principle Coverage** | Are all 7 principles served? | Any principle completely unaddressed = structural gap |
| **Translation Viability** | Could the downstream notes produce coherent AI image prompts? | Notes are too vague or use terms that miscue image generators |

**If all pass:** "VLD ready for review — [one sentence on strongest quality]."

**If any fail:** Fix silently, then present. Do not display gate results.

---

**Exit:** User approves VLD. Proceed to 4b-characters.md and 4c-locations.md in parallel.
