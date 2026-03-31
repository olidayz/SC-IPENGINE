# SF-PROMPT — Production Prompts

Take a locked concept from sf-concept and produce generation-ready prompts. Format-specific output.

---

## Input

- Locked concept from sf-concept (format, hook, viral mechanics, copy, tone)
- Style Lock (if post-pipeline — inherited medium/aesthetic)
- Prompt Anchors (if post-pipeline — characters and locations from Name Registry)
- Set Sheets (if post-pipeline — locked environment descriptions)
- Taste profile (always on)

---

## Output by Format

Everything is motion. No stills. If a concept feels like "one frame" — make it a loop or a punch.

### LOOP

One video prompt. 3-5 seconds. The loop point must be designed.

```json
{
  "format": "vertical 9:16 video, 3-5 seconds, seamless loop",
  "style": "[Style Lock or declared medium]",
  "subject": "[what's in frame]",
  "action": "[the subject's movement — must return to starting position by end]",
  "camera": "[camera movement — static or subtle drift that resets]",
  "environment": "[setting + environmental motion that loops: smoke, light shift, particle drift]",
  "loop_point": "[describe how end connects to beginning — what visual element bridges the cut]",
  "lighting": "[specific light source and how it behaves across the loop]",
  "negative": ["[anti-prompts]"],
  "viral_note": "[mechanic served]"
}
```

**Generate 3 variations** — different loop strategies for the same concept.

### PUNCH

3-5 shot prompts sequenced as a micro-edit. Setup → escalation → payoff.

```
HOOK SEQUENCE: [TITLE]
Duration: [X] seconds
Rhythm: [describe the pacing — slow build → snap, or constant escalation, or steady → break]

SHOT 1: [name] — [X seconds]
```
```json
{
  "format": "vertical 9:16 video",
  "style": "[locked medium]",
  "duration": "[seconds for this shot]",
  "subject": "[what's in frame]",
  "action": "[subject movement]",
  "camera": "[camera behavior]",
  "environment": "[setting]",
  "lighting": "[light]",
  "text_overlay": "[on-screen text if any — exact words, timing, placement]",
  "transition_to_next": "[how this shot ends / connects to next — cut, whip pan, match cut, etc.]",
  "negative": ["[anti-prompts]"]
}
```

```
SHOT 2: [name] — [X seconds]
...

SHOT [final]: [name] — [X seconds] — PAYOFF
[The last shot carries the punchline / reveal / emotional spike]
```

**Generate 2 variations** of the full sequence — different edit rhythms for the same concept.

### CAROUSEL

3-7 frame prompts. Each frame is a single image or short clip. Sequenced for swipe tension.

```
CAROUSEL: [TITLE]
Frames: [X]
Swipe logic: [what drives the swipe — reveal, escalation, contrast, narrative]

FRAME 1: [the scroll-stop — this is the cover image]
```
```json
{
  "format": "[1:1 or 4:5]",
  "style": "[locked medium]",
  "subject": "[what's in frame]",
  "composition": "[framing]",
  "environment": "[setting]",
  "lighting": "[light]",
  "text_overlay": "[on-frame text — the incomplete thought that drives the swipe]",
  "negative": ["[anti-prompts]"]
}
```

```
FRAME 2: [the first reveal]
...

FRAME [final]: [the payoff + share trigger]
[This frame must make the viewer want to SEND the carousel to someone]
```

### MICRO-TRAILER

8-15 shot prompts + motion directives. A compressed Transmission.

**Load** `5-scene-builder/references/trailer-logic.md` for Transmission modes.

```
MICRO-TRAILER: [TITLE]
Duration: [X] seconds
Mode: [Fever Dream / Speed Myth / Hybrid / Channel]
Spine: [the one thread holding it together — a sound, a visual motif, a voice]
Rhythm: [describe the pacing arc]

SHOT 1: [name] — [X seconds]
```
```json
{
  "format": "vertical 9:16 video",
  "style": "[locked medium]",
  "duration": "[seconds]",
  "subject": "[what's in frame]",
  "action": "[movement]",
  "camera": "[camera behavior]",
  "environment": "[setting]",
  "lighting": "[light]",
  "sound_note": "[what this moment SOUNDS like — for downstream audio]",
  "transition_to_next": "[edit logic — emotional association, hard cut, match cut, whip]",
  "negative": ["[anti-prompts]"]
}
```

**Rules for micro-trailers:**
- Hook in frame 1 — no logos, no titles, no setup
- Every frame must be independently iconic (pause-worthy)
- Density over clarity — move faster than comprehension
- End incomplete — the audience should feel the world is bigger than the container
- Design for rewatch — background details that reward second viewing

### CHARACTER INTRO

3-5 shot prompts + motion. One character. Pure presence.

**Requires:** Character Prompt Anchor (from Name Registry or invented for standalone).

```
CHARACTER INTRO: [CHARACTER NAME]
Duration: [X] seconds
Environment: [where we find them — the space IS the introduction]
Signature detail: [the one thing]
Contradiction: [what's surprising about this moment]

SHOT 1: [name] — [X seconds]
```
```json
{
  "format": "vertical 9:16 video",
  "style": "[locked medium]",
  "duration": "[seconds]",
  "subject": "[Prompt Anchor — pasted verbatim if post-pipeline]",
  "action": "[what the character is DOING — caught mid-life, not posed]",
  "camera": "[camera behavior — how we approach/discover this person]",
  "environment": "[Set Sheet Prompt Block if post-pipeline, or invented]",
  "lighting": "[light — environment-specific, reveals character]",
  "sound_note": "[ambient sound of WHERE we find them]",
  "signature_moment": "[the frame where the signature detail is revealed]",
  "transition_to_next": "[edit logic]",
  "negative": ["[anti-prompts]"]
}
```

**Rules for character intros:**
- No dialogue. Presence only.
- Environment first, character revealed within it
- The body tells the story — posture, gesture, spatial relationship
- Signature detail gets one clear moment
- End on contradiction — the thing about this person that doesn't fit

---

## Viral Quality Gates

Run on every piece before presenting.

| Gate | Test | Kill If |
|------|------|---------|
| **3-Second Test** | Would someone stop scrolling in 3 seconds? | Opens slow, generic, or requires context |
| **Zero-Context Test** | Does this work for someone who knows nothing about the IP? | Requires lore, backstory, or explanation |
| **Screenshot Test** | Would someone screenshot / screen-record this? | Not visually distinctive enough to save |
| **Share Test** | Would someone send this to a specific person? | Generic — no "you need to see this" energy |
| **Rewatch Test** | Is there a reason to watch again? | Everything lands on first view, nothing hidden |
| **Mute Test** | Does this work without sound? | Relies on audio for comprehension |
| **Taste Test** | Does this pass the taste profile? | Generic, stock, committee energy |
| **Completion Test** (video only) | Would someone watch to the end? | Front-loaded — no reason to stay past second 3 |
| **Loop Test** (loops only) | Is the loop seamless and hypnotic? | Visible loop point, jarring reset |

---

## Anti-Patterns

| Don't | Why |
|-------|-----|
| Over-produce variations | 3 variations per loop/punch is enough. Not 15 of the same angle. |
| Write hooks longer than 15 seconds | If it takes 15+ seconds, it's not a hook — it's a micro-trailer. Use the right format. |
| Design carousels longer than 7 frames | Swipe fatigue. 3-5 is the sweet spot. 7 is the ceiling. |
| Open micro-trailers with titles or logos | Hook in frame 1. Always. Branding lives at the end or in the world itself. |
| Pose character intros | Characters are caught, not presented. Found in action, not standing for a portrait. |
| Describe sound in image prompts | Sound notes are for downstream audio. Image/video prompts describe what you SEE. |
| Generate before concept is locked | The concept lock is not optional. Format, hook, mechanic, copy — all decided before any prompts. |
