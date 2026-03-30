# 6C-MOTION

Turn selected still images into video/motion prompts. Takes your approved selects from 6a, assigns camera movement + subject action + environmental motion, sequences into an edit, outputs JSON.

---

## Purpose

You've generated stills (6a), picked your selects. Now each select becomes a video clip. The motion skill specifies: what the camera does, what moves in the frame, how long it runs, and how it connects to the next clip.

---

## Anti-Patterns

| Anti-Pattern | Signal | Why It Dies |
|-------------|--------|------------|
| **The Music Video** | Every shot has dramatic, complex camera movement | Not every moment needs to move. Static holds, breathing cameras, and slow drifts are often more powerful than sweeping cranes. Story drives movement. |
| **The Abstract Action** | Subject motion described psychologically ("she processes the information," "grief washes over him") | Video generators render physical action. "Eyes close slowly, jaw tightens" not "she absorbs the weight of what she's heard." Renderability rule applies to motion too. |
| **The Overloaded Frame** | Camera movement + subject motion + environmental motion all happening simultaneously at high intensity | One dominant motion per clip. A slow dolly-in with a character turning their head — yes. A crane + whip pan + character running + wind + light shift — chaos. |
| **The Disconnected Cut** | Two consecutive clips with no visual or temporal logic connecting them | Every cut needs motivation: a match cut (same shape, different subject), a movement continuation (camera was moving left, next shot continues left), or a tonal bridge (same light, same pace). |
| **The Even Edit** | Every clip is the same duration | Rhythm needs variation. A 6-second hold followed by a 2-second cut followed by a 4-second drift. The pattern of long-short IS the rhythm. |

---

## Input

**Required:**
- Selected still prompts from 6a (your picks — the JSON prompts for the images you've approved)
- Scene Template from 6a (locked fields carry forward)
- Camera movement library (`references/camera-movements.md`)

**The still image IS the starting frame.** The motion prompt describes what happens to that image over time — how the camera moves, what the subject does, what shifts in the environment.

---

## Motion Prompt JSON Format

Each selected still becomes a motion prompt. The still IS the starting frame — the AI already has it. The motion prompt only describes what CHANGES.

```json
{
  "source_still": "[prompt ID from 6a — e.g. '3a']",
  "format": "vertical 9:16 portrait",
  "duration": "[seconds]",

  "camera_movement": {
    "primary": {
      "tag": "[movement tag from camera-movements.md]",
      "speed": "[slow/med/fast]",
      "description": "[specific execution — direction, distance, what changes in the frame]"
    },
    "secondary": {
      "tag": "[optional — must be subordinate to primary]",
      "speed": "[slow/med/fast]",
      "description": "[how it layers with primary]"
    }
  },

  "subject_motion": {
    "action": "[physical action — only renderable movements, no psychology]",
    "timing": "[when — 'throughout', 'first 2 seconds', 'final second', 'at 3 seconds']"
  },

  "environmental_motion": {
    "elements": "[what moves — dust, light shift, candle flicker, wind, shadows]",
    "intensity": "[subtle/moderate/prominent]"
  },

  "landing_state": "[1 sentence — what the frame resolves to in the final 0.5-1 second. The resting point. Used to design visual rhymes with the next clip's reference still.]"
}
```

**What's NOT in the prompt:** No `starting_frame` (the AI has the reference still). No `negative` (the still already has the right look). No `style` (inherited from the still). No `ending_frame` narrative (replaced by `landing_state` — one sentence, the visual resting point, nothing more).

---

## The Three Motion Layers

### Layer 1: Camera Movement (Primary)

What the camera does. Pull from `references/camera-movements.md` using tags. Every clip has exactly ONE primary camera movement (or `STATIC-LOCK` / `BREATHE` for no movement — which is a deliberate choice, not a default).

**Selection principle:** The camera movement must serve the story beat. Ask: what does the audience need to FEEL during this clip?

| Story Need | Movement |
|------------|----------|
| Building tension | `DOLLY-IN-SLOW`, `ZOOM-CREEP` |
| Revealing context | `DOLLY-OUT-SLOW`, `TILT-REVEAL`, `CRANE-UP` |
| Following action | `TRACK-FOLLOW`, `PAN-FOLLOW` |
| Holding emotion | `STATIC-HOLD`, `BREATHE` |
| Shocking / punctuating | `WHIP-PAN`, `DOLLY-IN-FAST`, `ZOOM-IN-FAST` |
| Transitioning between zones | `PASS-THROUGH`, `CRANE-UP-REVEAL` |

### Layer 2: Subject Motion

What the person or object in the frame does. Must be physically renderable — no psychology, no abstractions.

**The renderability test for motion:** Can you direct an actor to do this in one sentence? "Close your eyes slowly" = yes. "Process what you've heard" = no.

| Don't Write | Write Instead |
|-------------|--------------|
| "She realizes the truth" | "Her eyes widen, mouth opens slightly" |
| "He absorbs the grief" | "His head drops two inches, shoulders lower" |
| "Tension rises between them" | "He leans forward one inch, she leans back one inch" |
| "She decides" | "Her right fist tightens around the stone" |
| "He breaks down" | "His jaw clenches, he blinks rapidly, his chin drops" |
| "She withdraws" | "She pulls her hands from the table into her lap" |
| No motion needed | "Still — no subject motion" (this is valid and often powerful) |

### Layer 3: Environmental Motion

What moves in the world around the subject. These are atmospheric details that make the frame feel alive.

| Element | What It Looks Like | When to Use |
|---------|-------------------|-------------|
| **Dust motes** | Particles floating in a light beam, slowly drifting | Any scene with visible light shafts — the strip-mall window, the seminary |
| **Candle flicker** | Flame movement, light dancing on surrounding surfaces | The vigil, the enclosure at night, any candlelit scene |
| **Light shift** | Golden hour light slowly moving across a surface or face — the sun continues setting | Any golden-hour scene — the light IS a clock |
| **Fabric movement** | Slight movement in clothing from breathing, from a fan, from opening a door | Adds life to static character shots |
| **Shadow movement** | Shadows shifting as light source moves or flickers | Candle scenes, cloud movement, passing cars |
| **Breath visible** | Condensation in cold air, rhythmic | The vigil, outdoor night scenes |
| **Screen flicker** | Laptop/monitor light pulsing subtly | Dex's apartment, any screen-lit scene |
| **Wind** | Hair movement, paper rustling, candle flame bending | Outdoor scenes, threshold crossings |
| **Rain/condensation** | Drops on surfaces, condensation forming on glass | Weather-dependent, adds texture |
| **Ambient human movement** | Congregation shifting slightly, background figures breathing | Any crowd scene — the group is alive even when still |

**Intensity rule:** Environmental motion should be SUBTLE by default. It's atmospheric, not the subject. If it's the first thing the audience notices, it's too prominent (unless the environment IS the subject — a light shift scene, a wind scene).

---

## Sequencing: Ordering Standalone Clips

Each clip is a self-contained 5-10 second generated video. There is no editing software. No cuts, no dissolves, no match cuts. Clips play back-to-back. The "edit" is the ORDER you place them in and how each clip is designed to flow into the next.

### 1. Rhythm Pattern

The duration pattern across clips. Design this before assigning movements.

| Pattern | Feel | Example |
|---------|------|---------|
| **Long-short-long-short** | Breathing rhythm, tension and release | 8s — 4s — 7s — 3s — 9s |
| **Escalating compression** | Building urgency, clips get shorter | 10s — 8s — 6s — 5s — 4s |
| **Hold-hold-hold-snap** | Sustained tension, sudden short clip | 8s — 8s — 8s — 3s |
| **Even sustained** | Meditative, observational, no rush | 7s — 7s — 7s — 7s |

### 2. Each Clip Is a Complete Arc

Every clip must have its own internal beginning → middle → end within its duration. It can't rely on the next clip to resolve anything. Think of each clip as a complete sentence, not a fragment:

| Clip Element | What It Does | Example |
|-------------|-------------|---------|
| **Entry state** | What the frame looks like at second 0. This IS the reference still. | The open hand, golden-hour-lit, fingers extended |
| **Motion** | What changes during the clip — camera, subject, environment. This is the verb. | Fingers slowly curl inward, shadow deepens between them |
| **Landing state** | What the frame looks like at the final second. The clip resolves to this. | The loose fist, knuckles catching light, the offering closed |

The landing state should feel like a resting point — not a cliffhanger. The viewer should feel "that was complete" before the next clip begins.

### 3. Sequencing Logic (No Cuts — Just Order)

Since clips play back-to-back without editorial control, the flow between them depends entirely on how you design the ENDING of clip N and the BEGINNING of clip N+1.

| Principle | How It Works |
|-----------|-------------|
| **Visual rhyme** | The landing state of clip N and the reference still of clip N+1 should share something — a color, a shape, a spatial position, a light quality. Not identical — rhyming. A closing hand (end of clip 1) followed by a close-up of a stone in a fist (start of clip 2). The hand rhymes. |
| **Energy continuity** | If clip N ends in stillness, clip N+1 should begin in stillness (then introduce motion). If clip N ends in motion, clip N+1 should begin with motion (same or contrasting direction). Avoid: clip N ends still, clip N+1 starts with fast motion. The jump is jarring without a cut to smooth it. |
| **Scale progression** | Design the clip order so the framing progresses: wide → medium → close → detail. Or the reverse. Or alternating. The point is: the progression IS the storytelling. Getting closer = getting more intimate. Pulling back = seeing more context. |
| **Movement diversity** | Don't repeat the same camera movement in consecutive clips. If clip 1 is a slow dolly in, clip 2 should be a static hold, a tilt, or a different movement. Two dolly-ins in a row feels like the same clip twice. |
| **Landing = breathing room** | Every clip should land on a resting state for at least the final 0.5-1 second. The camera settles. The motion completes. This gives the viewer a beat before the next clip starts. Without this, the sequence feels like one continuous rush. |

### 4. What NOT to Design For

| Don't | Why |
|-------|-----|
| Match cuts | There's no cut. You can't match-cut between generated clips. Design visual rhymes instead. |
| Cross-dissolves | No editing tools. Each clip is a hard start. |
| Split-second timing between clips | You don't control the gap. The clips just play in order. Design each one to be self-sufficient. |
| Clip N ending mid-action with clip N+1 completing it | The action won't line up across two separately generated clips. Each clip completes its own action. |
| Relying on audio continuity | There is no audio track connecting clips. Each clip is visually self-contained. |

---

## Output Format

One JSON prompt per selected still. Listed in sequence order.

```
### MOTION SEQUENCE: [SCENE TITLE]

Rhythm: [the duration pattern]
Total duration: [sum]
Sequence logic: [1-2 sentences — what the clip order does narratively]

**Clip 1** (from still [ID])
```json
{ complete motion JSON prompt }
```

**Clip 2** (from still [ID])
Visual rhyme from Clip 1: [what connects the landing of clip 1 to the start of clip 2]
```json
{ complete motion JSON prompt }
```

**Clip 3** (from still [ID])
Visual rhyme from Clip 2: [connection]
```json
{ complete motion JSON prompt }
```
```

---

## Quality Gates (Run Silently)

| Gate | Test | Kill If |
|------|------|---------|
| **Renderability** | Is every subject motion physically described? No psychology, no abstractions? | "She realizes" instead of "her eyes widen" |
| **Movement Motivation** | Does every camera movement serve the story beat? | Movement chosen for variety, not narrative purpose |
| **Single Primary** | Does each clip have exactly one primary camera movement? | Two competing primary movements in one clip |
| **Complete Arc** | Does each clip have entry state → motion → landing state? Does it resolve on its own? | Clip ends mid-action or requires the next clip to make sense |
| **Landing Beat** | Does each clip settle/resolve in its final 0.5-1 second? | Clip ends abruptly with no resting point |
| **Rhythm Variation** | Does the duration pattern vary? Not all clips the same length? | Five 7-second clips in a row |
| **Movement Diversity** | Are consecutive clips using different movements? | Two dolly-ins in a row, two static holds in a row |
| **Visual Rhyme** | Does the landing state of clip N share a visual element with the start of clip N+1? | Consecutive clips with no visual connection — jarring sequence |
| **Energy Continuity** | Does the energy level flow between consecutive clips? No stillness-to-fast-motion jumps? | Clip N ends still, clip N+1 starts with fast movement (no cut to smooth the transition) |
| **Environmental Restraint** | Is environmental motion subtle/atmospheric, not competing with subject? | Prominent environmental motion in a clip about the character's face |
| **No Editorial Assumptions** | Does the prompt avoid assuming editing tools — no match cuts, dissolves, split-second timing between clips? | Prompt designed for capabilities that don't exist in the pipeline |

---

## Invocation

- "Build motion for [scene]" → Takes your selects, assigns motion, sequences edit
- "Animate my selects" → Same
- "Motion sequence for [list of prompt IDs]" → Takes specific selects
- "Adjust clip [N] movement" → Modify a single clip's motion
- "Resequence" → Change the edit order or rhythm
