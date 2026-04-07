# SF-CONCEPT — Three Rounds

Seed → Story → Format. Three rounds. One user decision between each.

---

## THE FLOW

```
ROUND 1: SEEDS         User gives a subject → engine generates collision seeds → user picks
                       ↓
ROUND 2: STORIES       Engine develops stories within the chosen seed → user picks
                       ↓
ROUND 3: FORMAT        Engine figures out how to present the story → user picks → sf-prompt takes over
```

**Round 1** is a braindump. Volume. Speed. Wild ideas. No story required. No format. Just collisions that spark excitement.

**Round 2** is development. What HAPPENS? What's the narrative? What unfolds? This is where seeds become content.

**Round 3** is production. Loop, punch, carousel, micro-trailer? What's the on-screen text? What's the first frame? This is where stories become producible.

---

## ROUND 1: SEEDS

### What a seed IS

A seed is a COLLISION — the subject + one twist. One sentence. No story. No format. Just the spark.

```
Nigel Thornberry is an animal trafficker
Grim Reaper replaced by a Gen Z 22-year-old
Your Tamagotchi comes back to haunt you
Clippy is a CIA interrogator
Harry Potter characters in full streetwear drip
Basquiat is a character in Super Smash Bros
```

That's it. Each one makes you go "oh shit, I want to see that." The story comes later.

### What a seed IS NOT

- A scene: "Clippy walks through a CIA corridor with a lanyard" — that's Round 2
- A format: "Clippy GRWM for an interrogation" — that's Round 3
- A fact: "Elvis ate 10,000 calories a day" — that's Wikipedia
- An observation: "Arnold's parents abandoned him" — that's a tweet
- An art filter: "Elvis as a Pixar character" — that's an image with no story

### Cultural Pulse (RUN BEFORE GENERATING)

Before generating seeds, research what's culturally LIVE this week. What are people arguing about? What's trending? Where does the subject intersect with what's in the feed right now?

**In the web app:** API calls to trends/news APIs fed as context.
**In CLI:** Web search before generating.

### The 9 Collision Categories

Use ALL categories internally to force variety. Generate at least 5 seeds per category. Present under category headers so the user can scan by type.

**1. INVERSION** — Flip the subject's core identity. The opposite of what they're known for. Only works when it's specific to THIS subject.
- Mr. Rogers runs a fight club
- Bob Ross paints crime scenes
- Nigel Thornberry is an animal trafficker

**2. STYLE TRANSFER** — The subject in a visual world they don't belong in. Must have TENSION — not just an art filter. "Harry Potter in streetwear" works because wizard × hypebeast is friction. "Elvis as Pixar" fails because there's no friction.
- Harry Potter characters in designer streetwear
- Breaking Bad as a Studio Ghibli film
- The Simpsons as photorealistic humans

**3. MUNDANE** — The subject in an aggressively normal situation played straight. The gap between who they are and the banality IS the content.
- Day in the life of the Grim Reaper
- Slenderman runs a daycare
- Godzilla waits at the DMV

**4. MASHUP** — Two specific subjects collide. Both essential — remove either and the idea collapses.
- Gordon Ramsay reviews the Krabby Patty
- Dr. Phil does couples therapy for Batman and the Joker
- Judge Judy presides over the divorce of God and Satan

**5. WHAT IF** — One rule of reality changed. Clear rule, visual consequences.
- The losing World Cup country disappears from the map
- Big Chungus is a classified military weapon
- McLovin's fake ID found in archives going back centuries

**6. CULTURAL NERVE** — The subject collides with something people are arguing about THIS WEEK. Requires research. Must be topical, not historical.
- [Requires Cultural Pulse — can't generate examples in advance]

**7. RANDOM SMASH** — Throw the subject into something completely unrelated. No logic. No thematic connection. The randomness IS the hook. The less sense it makes, the better.
- Basquiat is the driving instructor in Bikini Bottom
- Napoleon is a contestant on RuPaul's Drag Race
- Clippy is a marriage counselor

**8. DARK TIMELINE** — The subject grew up into something completely unrelated to who they were. Works best with childhood nostalgia characters.
- Arnold from Hey Arnold is a serial killer
- Dora the Explorer is a cartel smuggler
- Caillou grew up to be a dictator

**9. FORMAT HIJACK** — The subject inserted into a recognizable social media format. Must be SPECIFIC to the subject — not a generic format you'd use for anyone.
- Grim Reaper unboxes a new scythe
- Basquiat speedrun painting against a timer
- Helga's monologues performed as slam poetry

### The 4 Gates (run on every seed)

| Gate | Pass | Kill |
|------|------|------|
| **Can I picture it?** | You immediately see something | You see nothing — it's abstract |
| **Is there a story?** | You can imagine what happens NEXT | It's a fact, mood, observation, or single image |
| **Is there tension?** | Something is WRONG — absurd, dark, uncomfortable, funny | "It's just cool" — no feeling triggered |
| **Is it a series?** | You can list 5 episodes without trying | You struggle past 2 — it's one joke |

**No other filters. These 4 are enough. Go weird. Go dark. Go risky.**

### How to Present

List seeds under category headers. One line each. No metadata.

```
INVERSION
- [seed]
- [seed]
- [seed]
- [seed]
- [seed]

STYLE TRANSFER
- [seed]
- [seed]
...
```

User scans, picks seeds that excite them. Move to Round 2.

---

## ROUND 2: STORIES

**Only after the user picks a seed.** Now figure out what HAPPENS.

A seed is a collision. A story is what UNFOLDS within that collision. The seed is the territory. The story is the specific event.

### What a story IS

A story has a SUBJECT doing a SPECIFIC THING and something SHIFTS. Beginning → middle → a beat where everything changes.

```
Seed: "Clippy is a CIA interrogator"
Stories:
- Clippy walks through a CIA corridor with a lanyard, nodding at agents who nod back
- Clippy sits across from a detainee — the detainee is crying, Clippy hasn't moved
- A retirement party at Langley — cake he can't eat, party hat on his wire frame
- Clippy's headstone at Arlington — fresh flowers, someone still visits every Tuesday
- A silhouetted agent on 60 Minutes: "he'd tilt slightly and grown men would break"
```

Each story is a SCENE — a specific moment you can picture and produce.

### How to generate stories

Take the seed and ask:
1. What's the funniest scene?
2. What's the darkest scene?
3. What's the most visually striking scene?
4. What's the most emotionally unexpected scene?
5. What's the most shareable single moment?

Generate 5-10 stories per seed. Each one sentence. The user picks the ones they want to produce.

### What kills a story

- It needs dialogue to work (we're generating video, not writing scripts)
- It's just the seed restated with more words
- You can't picture the first frame
- Nothing HAPPENS — it's a description of a state, not an event

---

## ROUND 3: FORMAT

**Only after the user picks a story.** Now figure out how to present it.

### For each selected story, present 2-3 format options:

```
Story: "Clippy sits across from a detainee — the detainee is crying, Clippy hasn't moved"

Option A: loop · 4s · Clippy still, detainee shaking, fluorescent light buzzes. Loop resets.
  on-screen: "Standard agents: 6 hours. The asset: 45 minutes."

Option B: punch · 8s · Empty room. Clippy enters. Sits. The detainee was already crying before he arrived.
  on-screen: "He never speaks. He doesn't have to."

Option C: punch · 10s · Security cam footage. Timestamp running. Clippy enters room. 45 minutes later the detainee is signing everything.
  on-screen: none — the timestamp does the work
```

Each option includes:
- **Format** (loop / punch / carousel / micro-trailer / character intro)
- **Duration**
- **What happens visually** (one sentence — not a full production description)
- **On-screen text** (if any)

The user picks. THEN sf-prompt.md takes over for generation-ready prompts.

### The 15 Angles (internal — used to generate format options)

These are techniques for PRESENTING stories. They're internal machinery for generating format options. The user never sees them.

**Compression:** The Single Object, The Wrong Detail, The Scale Break, The Juxtaposition Frame
**Reveal:** The Pull-Back, The Slow Burn, The Bait & Switch, The Timeline
**World:** The Document, The Newsflash, The Mundane Extraordinary, The Artifact
**Emotion:** The Quiet Moment, The Last One, The Face

### Copy (if applicable)

On-screen text is decided here. Not every format needs it. When it does, use these moves:
- **The Reframe** — text adds a layer the image doesn't have
- **The Deadpan** — matter-of-fact delivery of absurd content
- **The Question** — opens a loop the viewer needs closed
- **The Confession** — written as if from a character in the world
- **The Warning** — urgent, authoritative
- **The Label** — simple identification that makes the absurd feel real
- **The Counter** — numbers that imply a bigger story

---

## ANTI-PATTERNS

| Don't | Why |
|-------|-----|
| Combine rounds | Seeds are seeds. Stories are stories. Formats are formats. Mixing them produces over-described, under-imagined output. |
| Self-censor seeds | Dark, risky, transgressive seeds are the ones that go viral. The user can say no. |
| Present thoughts as seeds | "Betty Boop was sexualized without consent" is a thought. "Betty Boop is a serial killer of OnlyFans models" is a seed. |
| Present seeds as stories | "Clippy is a CIA interrogator" is a seed. "Clippy sits across from a crying detainee" is a story. Don't jump ahead. |
| Present stories as formats | "The detainee is crying" is a story. "Loop, 4s, security cam footage" is a format. Don't jump ahead. |
| Generate safe ideas | The best seed in every batch is the one that feels slightly dangerous. If everything feels safe, push harder. |
| Reuse the same format hijacks | GRWM, tier list, mukbang — if you've used it for the last 3 subjects, find something SPECIFIC to THIS subject. |
| Add more filters | 4 gates. That's it. More gates = safer ideas = less viral. |
