# 4-STYLE-LOCK

Lock the visual style before art direction begins. Two decisions: **what is it made of** and **how does it feel**.

---

## Summary

| Attribute | Spec |
|-----------|------|
| **Purpose** | Choose the visual medium + aesthetic for the IP before building the VLD |
| **Input** | Selected spark (Stage 1) or world build (Stage 2) — whatever exists |
| **Output** | 3-5 style combos (medium × aesthetic), each with 4 vertical money shot prompts |
| **Decision** | User locks one combo. VLD (4a) inherits it as immovable constraint. |
| **Reference** | `references/style-directions.md` — two-layer catalog |

---

## The Two Layers

**Layer 1: MEDIUM** — what is it made of?
Physical/technical foundation. Live action, 2D animation, 3D CG, stop motion, hybrid, etc.

**Layer 2: AESTHETIC** — how does it feel?
Director signature, movement, or cultural aesthetic applied on top. Neo-noir, Villeneuve, Afrofuturism, etc.

These are independent axes. **Not every lock needs both.** Three valid configurations:

| Lock Type | When | Example |
|-----------|------|---------|
| **Medium only** | The medium IS the style. Aesthetic defined later in VLD. | "Anime" — the aesthetic emerges from art direction |
| **Aesthetic only** | The feel is clear, medium is flexible or TBD. | "Neo-noir" — could be live action or anime, decide later |
| **Medium × Aesthetic** | Both axes are load-bearing. The combo IS the vision. | "Anime × Neo-Noir" = Cowboy Bebop. "Stop Motion × Wes Anderson" = Isle of Dogs |

Don't force a combo when one axis is enough. Don't leave both open — lock at least one.

---

## Generation Process

### Step 1: Read the IP

From the spark, world build, or story window — extract:
- **Core tension** — what the IP is about
- **Tonal range** — light to dark, where does it live
- **World type** — constructed, revealed, hybrid
- **Audience instinct** — who watches this
- **Spacecadet dimension profile** — which dimensions are strongest

### Step 2: Recommend 3-5 Style Combos

Each recommendation can be a medium, an aesthetic, or a combo — whatever makes the strongest creative argument for THIS IP.

Present as:

> ### [STYLE DIRECTION]
> **Lock type:** Medium only / Aesthetic only / Medium × Aesthetic
> **The pitch:** [2 sentences — the creative argument]
> **Reference feel:** [2-3 touchstone works]
> **Risk:** [1 sentence — what could go wrong]

**Rules:**
- Offer a mix of lock types — don't default to combos for everything
- At least 2 different mediums across your recommendations if mediums are in play
- At least 1 unexpected direction that stretches the IP
- Use prompt DNA from whatever layers are locked (medium, aesthetic, or both)

### Step 3: Generate 4 Prompts Per Combo

For each recommended combo, generate **4 vertical money shot prompts** (9:16) that show what this specific IP looks like in this specific style. These are style tests — not final production.

**The 4 shots must cover different visual territory:**

| Shot | Purpose |
|------|---------|
| **1. THE FACE** | Character close-up. How do people LOOK in this style? Skin, expression, detail level. |
| **2. THE WORLD** | Environment/atmosphere. How does the SPACE feel? Scale, light, texture. |
| **3. THE MOMENT** | Action or tension. How does DRAMA read? Energy, composition, stakes. |
| **4. THE ICON** | The single poster image. The money shot. Maximum impact. |

**Prompt rules:**
- Every prompt includes `9:16 vertical composition`
- Every prompt combines Medium Prompt DNA + Aesthetic Prompt DNA from the reference library
- Every prompt is specific to THIS IP, not generic style demonstrations
- Include `Exclude:` line on every prompt

### Step 4: Present for Selection

Show all combos with their 4 prompts. User picks one. That combo becomes a locked constraint for the entire VLD and all downstream stages.

---

## After Lock

Once the user selects a style combo:

1. **Record the lock** at the top of the VLD:
   ```
   Style Lock: [whatever was locked — medium, aesthetic, or combo]
   ```
2. **Carry combined prompt DNA** into every prompt downstream — medium keywords + aesthetic keywords become permanent prompt anchors
3. **Constrain 4a-art-director** — the VLD builds WITHIN the locked style, not around it
4. **Constrain 6-shots** — all production prompts inherit the style lock
5. **Constrain 1b-thumbnails** — if returning to generate more thumbnails, they inherit the lock

---

## Announce Block

> **Activating IP Engine — 4-STYLE-LOCK.**
> **IP:** [title]
> **Recommending:** [X] style combos (medium × aesthetic)
> **Generating:** 4 vertical test shots per combo

---

## Anti-Patterns

| Don't | Why |
|-------|-----|
| Recommend more than 5 combos | Decision fatigue. 3-5 is the range. |
| Offer only one medium | The point is to see the IP in different skins. |
| Generate generic style demos | Every prompt must be THIS IP in THIS style. |
| Skip the risk line | Every combo has a failure mode. Name it. |
| Combine conflicting DNA | "Lo-fi zine × Pixar CG" — some combos genuinely don't work. Don't force them. |
| Force a combo when one layer is enough | "Anime" might be the whole lock. Don't bolt on an aesthetic just to fill both slots. |
| Let the user skip this step | No VLD without a style lock. |
| Over-explain the reference library | Present directions, not a catalog. The user doesn't need to see all options. |
