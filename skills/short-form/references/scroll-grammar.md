# Scroll Grammar — Visual Language of the Feed

Short-form is not cinema shrunk down. It has its own visual grammar — rules for how images and video behave INSIDE A FEED. A frame that works on a cinema screen dies in a scroll. A frame that stops a scroll would be invisible on a cinema screen.

This reference defines the visual language specific to feed-native content.

---

## The Feed as Context

Every piece of short-form content has TWO compositions:
1. **The content itself** — what's inside the frame
2. **The content inside the feed** — what surrounds it (other posts, UI chrome, text overlays, profile pics)

A still image competes with the post above it and below it. A video competes with the impulse to swipe. The feed is an ADVERSARIAL environment. Your content must fight for attention against an infinite scroll of alternatives.

**Implication:** Every visual decision must account for the feed context. High contrast beats subtle. Faces beat landscapes. Wrong beats normal. The content that survives the scroll is the content that violates the scroll's visual rhythm.

---

## The First Frame

The most important frame in any piece of short-form content. This is where the algorithm and the human both make their decision.

### First Frame Taxonomy — 18 Opening Moves

#### FACE OPENERS
The highest-performing category. Faces stop thumbs.

| # | Opener | Description | When to Use |
|---|--------|-------------|-------------|
| 1 | **The Stare** | Direct eye contact with camera. Uncomfortably close. The viewer is SEEN. | Character intros. Confrontational content. "I need to tell you something" energy. |
| 2 | **The Reaction** | A face mid-reaction to something unseen. The expression is so extreme it demands context. | Hooks where the reveal comes after the reaction. Comedy. Horror. |
| 3 | **The Wrong Face** | A calm face where panic should be. A smile where grief should be. The mismatch between expression and context. | Subversion content. Deadpan comedy. Unsettling world-building. |
| 4 | **The Macro Face** | Extreme close-up. Pores visible. One eye fills the frame. Skin texture IS content. | Beauty/horror. Character reveals. Emotional intensity. |
| 5 | **The Face in Context** | A face occupying 30-40% of frame with the environment visible around it. The relationship between face and space. | Character intros. Establishing tone. POV content. |

#### OBJECT OPENERS
The second-highest category. Objects that shouldn't exist demand explanation.

| # | Opener | Description | When to Use |
|---|--------|-------------|-------------|
| 6 | **The Impossible Object** | A physical thing that can't exist but looks real. Presented matter-of-factly. | World-building stills. Artifact reveals. "What is this?" hooks. |
| 7 | **The Familiar Wrong** | A recognizable everyday object with ONE wrong detail. | Subtle world-building. The wrongness IS the hook. |
| 8 | **The Scale Object** | Something at the wrong size. A tiny thing held massive. A massive thing held small. | Awe content. Scale-break hooks. |
| 9 | **The Evidence** | An object photographed like crime scene evidence. Flat lay, clinical lighting, forensic framing. | Mystery content. Artifact reveals. In-world documents. |
| 10 | **The Texture** | Extreme macro of a surface. The material IS the content. What is this made of? | ASMR-adjacent. Craft content. World texture reveals. |

#### ENVIRONMENT OPENERS
Third category. Spaces that pull you in.

| # | Opener | Description | When to Use |
|---|--------|-------------|-------------|
| 11 | **The Threshold** | The frame IS a doorway, window, or passage into another space. The viewer is about to cross. | World reveals. Micro-trailers. "Enter this world" energy. |
| 12 | **The Wrong Place** | A familiar environment with something impossible in it. A living room with a dinosaur. A subway with wrong signage. | World-building. Comedy. Horror. |
| 13 | **The Aerial** | Overhead/drone perspective of a landscape or space. The scale pulls you in before you understand what you're seeing. | Micro-trailers. World reveals. Establishing grandeur. |
| 14 | **The Empty** | A space that SHOULD have someone in it but doesn't. Absence as presence. The vacancy demands explanation. | Horror. Mystery. Post-apocalyptic. Emotional content. |

#### TEXT OPENERS
Text as visual element, not caption.

| # | Opener | Description | When to Use |
|---|--------|-------------|-------------|
| 15 | **The Statement** | Bold text on screen. One sentence. The text IS the hook. Image supports. | Hot takes. World facts. Provocative claims. |
| 16 | **The Question** | A question on screen that the viewer can't scroll past without wanting answered. | Curiosity-gap content. Debate bait. |
| 17 | **The Document** | In-world text presented as real — a form, a sign, a warning, a notification. | World-building. Format hijacks. Found media. |
| 18 | **The Counter** | A number. Day 1. Attempt 47. 3 remaining. Numbers imply story without telling it. | Series content. Countdown hooks. Progress content. |

### First Frame Rules

| Rule | Why |
|------|-----|
| **Readable in 0.3 seconds** | The thumb makes its decision in 300ms. If the first frame can't communicate its hook in that window, it loses. |
| **Maximum contrast with feed** | The feed is visually noisy. Your first frame must break the pattern — different color, different scale, different texture than what surrounds it. |
| **No logos, no titles, no credits** | These signal "ad" or "brand content." The algorithm deprioritizes. The thumb scrolls past. |
| **The hook is IN the frame, not after it** | Don't "build to" the hook. The first frame IS the hook. Everything after keeps the promise the first frame made. |
| **Faces beat everything** | When in doubt, open with a face. Faces outperform objects outperform environments outperform text — universally, across platforms. |

---

## Vertical Composition for Feed

Short-form vertical (9:16) has different rules than cinematic vertical.

### The Three Zones

The 9:16 frame has three critical zones driven by platform UI:

```
┌─────────────────────┐
│   SAFE ZONE (top)   │  ← Username, follow button, platform chrome
│                     │
│   HERO ZONE (mid)   │  ← Primary content lives here
│                     │
│   TEXT ZONE (bottom) │  ← Caption, hashtags, sound attribution
└─────────────────────┘
```

| Zone | Position | Rule |
|------|----------|------|
| **Top 15%** | Platform chrome territory | Don't put critical content here — username, follow button, and platform UI overlay this area. |
| **Middle 60%** | The hero zone | This is where your hook lives. Primary subject, key detail, the thing that stops the scroll. |
| **Bottom 25%** | Caption/text territory | Text overlays, caption, sound attribution, and engagement buttons live here. If your content HAS text, layer it above this zone so it doesn't compete with captions. |

### Feed-Native Composition Patterns

| Pattern | How It Works | Scroll Effect |
|---------|-------------|---------------|
| **Center Punch** | Subject dead-center in the hero zone. Maximum visual weight at the frame's center of gravity. | Immediate recognition. No eye-searching. The brain processes it in one fixation. |
| **The Interrupt** | Subject breaks the expected visual rhythm of a feed. Extremely saturated in a muted feed. Black-and-white in a color feed. Massive negative space. | Pattern interrupt. The thumb hesitates because the brain detected anomaly. |
| **The Bleed** | Subject extends beyond frame edges. Cropped tight. The world is bigger than the container. | Curiosity gap. What's beyond the frame? The incompleteness pulls attention. |
| **Top-Heavy** | Subject weighted to the top third. The eye enters from the top (where the previous post ends) and immediately hits content. | Optimized for scroll direction. Content hits the eye the moment it enters the viewport. |
| **The Split** | Frame divided horizontally. Top half and bottom half are different worlds, states, or subjects. The dividing line IS the content. | Juxtaposition. Two things compared without explanation. The viewer's brain does the work. |
| **The Tunnel** | Depth composition — the frame pulls the eye INTO the screen through converging lines, doorways, or corridors. | Immersion. The viewer feels pulled into the space. Higher dwell time. |

---

## Color in the Feed

Color behaves differently in a scroll than in a theater.

### Feed Color Rules

| Rule | Why |
|------|-----|
| **Saturated beats muted** | The feed is a competitive visual environment. Muted, desaturated content gets LOST in the scroll. Saturation is a survival mechanism. |
| **One dominant color** | A frame with one dominant color reads faster than a multi-colored frame. The single color becomes a visual anchor. |
| **Contrast with platform** | Instagram is warm and bright. TikTok is higher-contrast with more neon. LinkedIn is muted and corporate. Content should contrast with the platform's default aesthetic. |
| **Color as branding** | If your IP has a signature color (from VLD), use it as the dominant color in short-form. Consistency across pieces builds recognition. |
| **Skin tones outperform** | Warm skin tones in the frame trigger face-recognition processing even when the face isn't the focus. Subconscious attention boost. |
| **Red stops scrolls** | Red triggers the highest involuntary attention response across all colors. Use strategically, not constantly. |

---

## Text on Screen

Text in short-form is a visual element, not a caption. It occupies screen space, competes with the image, and has its own rules.

### Text Rules

| Rule | Why |
|------|-----|
| **Max 7 words on screen at any time** | More than 7 words and the viewer reads instead of watches. Reading mode kills the visual experience. |
| **Text appears WITH the beat** | Text timing must align with visual or audio beats. Text that appears at arbitrary moments feels amateur. |
| **Text is always in the hero zone** | Never in the top 15% (platform chrome) or bottom 25% (caption zone). Always in the middle 60%. |
| **High contrast against the image** | White text with black outline is the universal default for a reason. Text must be readable on ANY background frame. |
| **Text reveals, not repeats** | On-screen text should add information the image doesn't contain. Text that describes what's already visible is waste. |
| **World-native typography when possible** | If the IP has a visual language, the text should feel like it belongs to that world, not to Instagram's default font. |

### Text Timing (for video)

| Duration | Rule |
|----------|------|
| **1-3 words** | Can flash (0.5-1 second). Impact. Punch. |
| **4-7 words** | Needs 1.5-2 seconds on screen. Quick read. |
| **Full sentence** | Needs 2-3 seconds. But ask: should this be on screen at all? |
| **Two lines stacked** | Maximum. If you need three lines, you need fewer words. |

---

## Motion Grammar (for Video Formats)

How movement behaves in a feed — different from cinematic motion.

### Speed Rules

| Rule | Why |
|------|-----|
| **Movement in the first 0.5 seconds** | Static openings get scrolled. Something must MOVE immediately — camera, subject, text appearing, a particle, ANYTHING. The eye tracks motion. |
| **Fast cuts beat slow cuts** | The average TikTok cut is 1.5-3 seconds. Cinema is 4-8 seconds. Short-form viewers process faster. Honor their speed. |
| **Slow motion is earned** | Slow-mo in short-form must follow fast content. The deceleration IS the impact. Opening with slow-mo gets scrolled — there's no speed contrast yet. |
| **Camera movement > static** | Even subtle drift (a slow push-in, a gentle handheld wobble) outperforms static frames. Movement signals "this is alive." |
| **Vertical motion > horizontal motion** | In a 9:16 frame, up-down movement uses the full canvas. Left-right motion crosses the frame too quickly. Falling, rising, tilting — all stronger in vertical. |

### Transition Grammar

| Transition | Feel | When to Use |
|------------|------|-------------|
| **Hard cut** | Energy. Speed. Collision. | Between contrasting shots. Tonal shifts. Beat drops. |
| **Whip pan** | Momentum. "Let me show you." | Between related subjects. Tours. Escalation. |
| **Match cut** | Intelligence. Connection. | Shape/color/movement continues across the cut. The edit itself IS content. |
| **Zoom punch** | Impact. Arrival. | Zooming into a detail. "Look at THIS." |
| **Morph/dissolve** | Transformation. Dream. | Before/after. Time passage. Identity shifts. |
| **Swipe wipe** | Native. Platform-born. | Mimics the scroll gesture. Feels like the viewer swiped into the content. |
| **Freeze frame** | "Wait." | Stopping motion for text overlay, detail highlight, or comedic timing. |
