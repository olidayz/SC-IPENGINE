# Camera Movement Taxonomy — Expanded

160+ tagged camera movements. Organized by category. Each has a tag, speed variants, emotional function, 9:16 notes, and film reference.

---

## Tags & Speed

**Tags:** CAPS (e.g. `DOLLY-IN`, `CRANE-UP`). Used in motion prompts.
**Speed:** Append `-SLOW`, `-MED`, `-FAST`. Or specify in the prompt. Slow = 4-8s. Med = 2-4s. Fast = 0.5-2s.

---

## Category 1: PAN (Horizontal Rotation)
*Camera in place, rotates horizontally.*

| Tag | Name | Motion | Emotional Function | 9:16 Notes | Reference |
|-----|------|--------|-------------------|------------|-----------|
| `PAN-L` | Pan Left | Rotates left | Discovery, following gaze, revealing context | Narrow width = fast reveal. Less distance to cover. | Standard coverage |
| `PAN-R` | Pan Right | Rotates right | Same. L-to-R reads as "forward" in Western grammar. | Same compression. | Standard coverage |
| `PAN-FOLLOW` | Follow Pan | Pans tracking moving subject | Connection, attachment. Subject centered, world moves. | Subject stays in narrow frame. Background slides. | *Birdman* — continuous pans |
| `PAN-REVEAL` | Reveal Pan | Starts on A, pans to reveal B | The reveal. Off-screen changes everything. Speed = drama. | Fast in narrow frame. Every degree counts. | *The Shining* — room reveals |
| `PAN-SURVEY` | Survey Pan | Slow continuous scan of a space | Establishing, surveying. Camera looks at everything. | Slow drift. Narrow frame means each degree shows less. | *Barry Lyndon* — room surveys |
| `PAN-WHIP` | Whip Pan | Extremely fast, motion blur | Shock, energy, time jump. Blur IS the transition. | Disorienting — blur fills width instantly. Sparingly. | *Evil Dead* — Raimi whip pans |
| `PAN-SEARCH` | Searching Pan | Irregular, slightly jerky — the camera is looking for something | Anxiety, urgency, the camera doesn't know where to look | The search is more visible in the narrow frame — each adjustment is noticeable. | *The Hurt Locker* — searching for threats |
| `PAN-RECOIL` | Recoil Pan | Fast pan away from something — the camera flinches | Shock, revulsion, the camera refuses to look | The narrow frame amplifies the flinch — the subject vanishes instantly. | *Irreversible* — camera recoiling |
| `PAN-RETURN` | Return Pan | Pans away, then pans back to the original subject | Second look, reconsideration, "wait, what?" | The return reveals the subject has changed (or hasn't — which is worse). | Documentary convention |
| `PAN-180` | 180 Pan | Full semicircle pan — starts on subject, rotates 180° to show what's behind the camera | Complete reversal of perspective. What was behind you. | In vertical: the 180 is disorienting. The narrow frame makes the rotation feel faster. | *Goodfellas* — Copacabana entrance |

---

## Category 2: TILT (Vertical Rotation)
*Camera in place, rotates vertically. The native 9:16 movement.*

| Tag | Name | Motion | Emotional Function | 9:16 Notes | Reference |
|-----|------|--------|-------------------|------------|-----------|
| `TILT-UP` | Tilt Up | Rotates upward | Revelation, awe, scale, ascent. Power builds up. | The STRONGEST native 9:16 movement. Enormous vertical reveal. | *Citizen Kane* — tilting up at Xanadu |
| `TILT-DOWN` | Tilt Down | Rotates downward | Discovery below, grounding, descent, detail at the base | Long descent. Hands, objects, the ground. | *Psycho* — tilt down to the drain |
| `TILT-FOLLOW` | Follow Tilt | Tracks vertical motion — standing up, falling | Connection to vertical action | Perfectly native. Subject moves through strongest axis. | Standard coverage |
| `TILT-REVEAL` | Reveal Tilt | Starts on one zone, tilts to reveal another | Vertical reveal. What's above/below changes meaning. | 78% more vertical space than 16:9. Massive potential. | *2001* — monolith reveal |
| `TILT-WHIP` | Whip Tilt | Extremely fast vertical rotation | Shock, temporal jump. Vertical whip pan. | Blur fills the height. Extremely disorienting. | *Scott Pilgrim* — vertical whips |
| `TILT-NOD` | Nodding Tilt | Small up-down-up oscillation — the camera nods | Acknowledgment, agreement, the camera confirming something | Subtle. The camera says "yes" without words. | Documentary convention |
| `TILT-SCAN` | Body Scan Tilt | Slow tilt from feet to face or face to feet — scanning a person | Assessment, objectification, introduction. We read the person head-to-toe or toe-to-head. | The body fills the vertical frame at every point of the scan. Native movement. | *Goodfellas* — character introductions |
| `TILT-PENDULUM` | Pendulum Tilt | The camera tilts back and forth like a pendulum — slow oscillation | Disorientation, seasickness, time distortion, dreaming | The vertical oscillation in 9:16 is hypnotic. | *Enter the Void* — floating camera |

---

## Category 3: DOLLY (Camera Moves Through Space)
*Physical movement toward/away/alongside subject.*

| Tag | Name | Motion | Emotional Function | 9:16 Notes | Reference |
|-----|------|--------|-------------------|------------|-----------|
| `DOLLY-IN-SLOW` | Slow Dolly In | Creeps forward | Intensification, intimacy building, dread. The slow speed IS the tension. | Subject grows in narrow frame. More claustrophobic than widescreen. | *The Shining* — approaching Room 237 |
| `DOLLY-IN-MED` | Medium Dolly In | Moderate forward | Standard approach. Building focus. | Frame narrows around subject. Environment falls away. | Standard coverage |
| `DOLLY-IN-FAST` | Fast Push In | Quick forward | Urgency, impact, realization. The fast approach IS punctuation. | Aggressive in narrow frame. Feels like falling forward. | *Jaws* — Brody on the beach |
| `DOLLY-OUT-SLOW` | Slow Dolly Out | Creeps backward | Abandonment, isolation. The world expanding around a shrinking person. | Subject shrinks in tall frame. Negative space opens above/below. Devastating. | *The 400 Blows* — final shot |
| `DOLLY-OUT-MED` | Medium Dolly Out | Moderate backward | Revealing context. Showing what surrounds. | Reveals above and below more than beside. | Standard coverage |
| `DOLLY-OUT-FAST` | Fast Pull Out | Quick backward | Shock reveal of scope. The "oh shit" scale moment. | Subject becomes tiny fast. Vertical space dominates. | *Dark Knight* — Joker reveal |
| `DOLLY-LATERAL` | Lateral Dolly | Sideways, parallel to subject | Observation, following. Neither approaching nor retreating. | Background changes rapidly in narrow frame. | *Oldboy* — corridor fight |
| `DOLLY-ARC` | Arc / Orbit | Curved path around subject | Examination, circling, reverence or threat. Slow = study. Fast = frenzy. | Reveals different vertical slices of environment during orbit. | *The Matrix* — bullet time orbit |
| `DOLLY-CONVERGE` | Converging Dolly | Camera approaches subject who is simultaneously approaching camera | Collision course. Two forces meeting. The distance closes twice as fast. | The approach is accelerated. The subject fills the narrow frame rapidly. | *Raging Bull* — ring approaches |
| `DOLLY-DIVERGE` | Diverging Dolly | Camera retreats while subject also retreats | Growing distance. Two forces separating. The gap opens. | Both figures shrink. The space between expands vertically. | *The Conformist* — separation |
| `DOLLY-THROUGH` | Dolly Through | Camera passes through subject's space — enters, passes, exits | The camera has its own trajectory. It's not attached to the subject. It passes through their world. | The pass-through in narrow frame feels like brushing past someone. | *Children of Men* — car scene continuous |
| `DOLLY-PROBE` | Probe / Snorkel | Camera moves into a tight space — into a gap, through a hole, between objects | Discovery of hidden space. Penetrating a barrier. | The probe into tight vertical spaces (between shelves, through fence gaps) is native to 9:16. | *Requiem for a Dream* — refrigerator probe |

---

## Category 4: ZOOM (Optical)
*Camera stays, lens changes focal length.*

| Tag | Name | Motion | Emotional Function | 9:16 Notes | Reference |
|-----|------|--------|-------------------|------------|-----------|
| `ZOOM-IN-SLOW` | Slow Zoom In | Lens tightens slowly | Psychological intensification. Background doesn't move. Subject is trapped. | Compression intense in narrow frame. Claustrophobic. | *Zodiac* — interrogation zooms |
| `ZOOM-IN-FAST` | Snap Zoom In | Lens tightens rapidly | Shock, discovery, focus. Retro/documentary energy. | Subject fills narrow frame instantly. Very aggressive. | *The Office* — reaction zooms |
| `ZOOM-OUT-SLOW` | Slow Zoom Out | Lens widens slowly | Release, context. Background appears without camera moving. | Vertical environment opens. Ceiling/floor appear. | *Barry Lyndon* — slow zoom outs |
| `ZOOM-OUT-FAST` | Snap Zoom Out | Lens widens rapidly | Shock reveal of scope. | Sudden vertical context — architecture, sky, ceiling. | *Goodfellas* — diner snap zoom |
| `ZOOM-CREEP` | Imperceptible Zoom | 1-2% change over full duration. Audience doesn't notice. | Subliminal intensification. Pressure without identification. Fincher signature. | Works same in any format. The key is the audience doesn't notice. | *Mindhunter* — interview creep zooms |
| `ZOOM-CRASH` | Crash Zoom | Extremely rapid zoom to a specific detail — from wide to ECU in under 1 second | Maximum shock. The camera ATTACKS a detail. Exploitative but powerful. | In narrow frame: the detail goes from tiny to frame-filling in a heartbeat. | *Kill Bill* — crash zooms to eyes |
| `ZOOM-PULSE` | Zoom Pulse | Tiny, rhythmic in-out zoom — 2-3% oscillation | Heartbeat, breathing, alive. The frame pulses. Subliminal but felt. | The pulse is more visible in narrow frame. Subtle discomfort. | *Uncut Gems* — anxiety zooms |
| `ZOOM-RACK` | Rack Zoom | Zoom changes what's in focus — foreground to background or reverse, via focal length change | Shift of attention, recontextualization, "look at THIS instead" | The foreground/background hierarchy shifts vertically in 9:16 — bottom to top. | *The Departed* — focus shifts |

---

## Category 5: CRANE / JIB (Vertical Spatial Movement)
*Camera physically rises or descends.*

| Tag | Name | Motion | Emotional Function | 9:16 Notes | Reference |
|-----|------|--------|-------------------|------------|-----------|
| `CRANE-UP` | Crane Up | Rises vertically | Ascension, liberation, overview. Rising above to see bigger. | Camera rises through frame's natural axis. Subject drops below. Sky appears. The MOST powerful 9:16 crane. | *The Shawshank Redemption* — final crane |
| `CRANE-DOWN` | Crane Down | Descends vertically | Descent, grounding, closing in, arriving | Frame fills with ground, floor, detail. Sky disappears. | *Vertigo* — bell tower descent |
| `CRANE-UP-REVEAL` | Crane Up Reveal | Rises to reveal beyond an obstruction | Over-the-top reveal. Hidden by scale, exposed by altitude. | Rising over vertical obstruction (wall, fence, crowd). | *Atonement* — beach reveal crane |
| `CRANE-DOWN-LAND` | Crane Down Landing | Descends from high to land on specific subject | Arrival, selection, choosing this person from above | Descending through tall frame to settle on target. Deliberate selection. | *Spielberg* — crane landing on faces |
| `CRANE-UP-ABANDON` | Crane Up Abandon | Rises and keeps rising — leaving the subject behind below | Abandonment, the divine withdrawing. The camera ascends and doesn't return. | The subject shrinks. The vertical height grows. The camera leaves. | *The Truman Show* — final ascent |
| `CRANE-SWOOP` | Swoop | Rapid descent from high to low — the camera dives | Energy, arrival, the camera attacks the scene from above | The swoop in vertical fills the frame with ground rapidly. Impact. | *Spielberg* — swooping into action |
| `BOOM-UP` | Boom Up | Small rise, inches to feet | Subtle elevation. Camera breathes up. Following standing. | Small rise adjusts framing — waist to head, detail to face. | Standard coverage |
| `BOOM-DOWN` | Boom Down | Small descent | Settling, grounding. Camera exhales down. Following sitting. | Descends from face to hands, standing to seated. | Standard coverage |
| `CRANE-LATERAL` | Lateral Crane | Rises/descends while moving sideways — a diagonal through space | The most cinematic combined crane. Sweeping, grand, survey-in-motion. | The diagonal path through the vertical frame changes both what's above/below AND what's beside. | *Atonement* — Dunkirk beach lateral crane |

---

## Category 6: TRACKING
*Camera follows subject through space.*

| Tag | Name | Motion | Emotional Function | 9:16 Notes | Reference |
|-----|------|--------|-------------------|------------|-----------|
| `TRACK-LEAD` | Leading | Ahead of subject, facing back | Anticipation, approach, confrontation. They advance. | Subject walks into the camera's face. Intense in narrow frame. | *Goodfellas* — Henry walking |
| `TRACK-FOLLOW` | Following | Behind subject | Journey, accompaniment, voyeurism. We go where they go. | Back and shoulders lower frame. Environment ahead fills upper. | *Elephant* — following through hallways |
| `TRACK-SIDE` | Side Track | Alongside at same speed, profile | Companionship, observation, interview position | Profile fills one side. Moving background fills other. | *Before Sunrise* — walking conversations |
| `TRACK-CIRCLE` | Circling | Orbits stationary/moving subject | Examination, tension, reverence, frenzy. Speed determines. | Orbit reveals different vertical slices behind subject. | *The Matrix* — bullet time |
| `TRACK-APPROACH` | Approach | Toward stationary subject from distance | Arrival, convergence, focusing | Subject grows from small to dominant in tall frame. | *Lawrence of Arabia* — Omar Sharif approach |
| `TRACK-RETREAT` | Retreat | Backward as subject advances | Pursuit tension. Distance maintained. | Distance maintained. Narrow frame makes pursuit compressed. | *The Shining* — Danny's Big Wheel |
| `TRACK-PARALLEL` | Parallel Track | Two subjects moving in the same direction, camera tracking both | Parallel lives, shared journey, convergence | Both figures in the narrow frame, one above/behind the other. | *Heat* — parallel tracking |
| `TRACK-CONTRA` | Contra Track | Camera moves opposite direction to subject — they go right, camera goes left | Passing, missed connection, ships in the night | The cross-movement in narrow frame is disorienting. The subject sweeps through and is gone. | *Wong Kar-wai* — passing in corridors |
| `TRACK-STALK` | Stalking Track | Following from further back than normal, partially obscured | Predatory, surveillance, the camera shouldn't be here | Distance + obstructions (columns, people, furniture) between camera and subject. | *Zodiac* — following suspects |
| `TRACK-DRIFT-OFF` | Drift Off | Camera starts tracking a subject, then slowly drifts away to follow something else — or nothing | Distraction, a more interesting subject, the camera has its own agenda | The camera abandons the original subject in the narrow frame. Unsettling. | *Magnolia* — camera drifts |
| `TRACK-CAROUSEL` | Carousel / 360° | Full 360° orbit around subject | Complete examination, hypnotic, timeless, the subject as monument | In vertical: the full rotation reveals the entire vertical environment behind the subject. | *Carlito's Way* — Grand Central station |

---

## Category 7: STATIC & MICRO
*The camera barely moves or doesn't. Stillness as choice.*

| Tag | Name | Motion | Emotional Function | 9:16 Notes | Reference |
|-----|------|--------|-------------------|------------|-----------|
| `STATIC-LOCK` | Locked | No movement. Tripod. | Observation, surveillance, formality. World moves, camera doesn't. | Locked vertical frame. Everything happens within. | *Ozu* — pillow shots |
| `STATIC-HOLD` | Extended Hold | No movement, holds longer than comfortable (5+ seconds same frame) | Duration as pressure. Audience wants it to end. It doesn't. | Tall frame holds. Eye searches for something to happen. | *Chantal Akerman* — *Jeanne Dielman* holds |
| `BREATHE` | Breathing | 1-2% drift, as if held by a breathing person | Presence, humanity. A person is watching. | More noticeable in narrow frame — 1% of width is proportionally larger. | *The Dardenne Brothers* — handheld breathing |
| `DRIFT-SLOW` | Slow Drift | Glacial movement in one direction. Almost imperceptible. | Subliminal motion. Time passing. | Through the tall frame, the composition changes so gradually it's almost still. | *Tarkovsky* — glacial drifts |
| `DRIFT-CIRCULAR` | Circular Drift | Very slow circular/orbital drift — the camera is drifting, not tracking | Dream state, untethered, the world slowly rotating | In narrow frame the drift shows vertical slices changing slowly. Meditative. | *Enter the Void* — floating above Tokyo |
| `SETTLE` | Settle | Small adjustment from off-center to locked | The camera finding position. Composition crystallizes. End of a movement chain. | Snaps vertical alignment into final position. Arrival. | Standard — often after a pan or dolly |
| `FLOAT` | Float | Moves smoothly through space without fixed path — weightless, exploratory | Dream, disembodied, the wandering eye. Not attached to anyone. | Floating through tall-frame spaces feels like a ghost in architecture. | *The Shining* — Steadicam through Overlook |
| `HANDHELD-ENERGY` | Energetic Handheld | Visible handheld motion — not subtle breathing but active, responsive movement | Urgency, chaos, the camera is a person in the scene, reacting in real time | The narrow frame amplifies the shaking — more perceived movement per pixel. | *The Bourne Identity* — action handheld |
| `HANDHELD-NERVOUS` | Nervous Handheld | Subtle but irregular handheld — micro-adjustments, searching, unsettled | Anxiety, the camera is uncomfortable. It doesn't know where to rest. | The nervousness reads clearly in the narrow frame. Every micro-adjustment is visible. | *Uncut Gems* — anxious camera |
| `LOCKED-VIBRATION` | Locked with Vibration | Tripod-locked but with subtle vibration — from a passing truck, from bass, from machinery | The stillness is being disturbed by the world. Something shakes the frame. | The vibration is visible against the rigid vertical edges. | *Sicario* — tunnel sequence vibrations |

---

## Category 8: COMBINED MOVEMENTS
*Two+ basic movements simultaneous. The most cinematic options.*

| Tag | Name | Combination | Emotional Function | 9:16 Notes | Reference |
|-----|------|------------|-------------------|------------|-----------|
| `DOLLY-ZOOM` | Vertigo Effect | Dolly in + zoom out (or reverse) | Disorientation, dread, world shifting around fixed point | Background compression/expansion in tall frame. Extremely unsettling. | *Jaws* — Brody on beach |
| `CRANE-PAN` | Crane + Pan | Rise/descend while panning | Sweeping revelation, combined vertical and horizontal discovery | Crane vertical + pan horizontal = two axes of discovery. | *Gone with the Wind* — pullback crane-pan |
| `DOLLY-TILT` | Dolly + Tilt | Forward/backward while tilting | Following the eye — approaching while looking up/down | Dolly changes proximity, tilt changes vertical zone visible. | *Spielberg* — approaching monuments |
| `TRACK-BOOM` | Track + Boom | Lateral movement while rising/descending | Elevated follow. Walking alongside while changing altitude. | Subject stays in frame while camera's vertical position changes. | *Atonement* — beach track-boom |
| `ARC-CRANE` | Arc + Crane | Orbits while rising/descending | Spiral. Most complex combined movement. Reveals subject from every angle at changing height. | Orbit shows vertical slices while crane shows changing height. Maximally dynamic. | *The Revenant* — battle sequences |
| `PAN-ZOOM` | Pan + Zoom | Pans while zooming | Focus shift within survey. Wide on crowd, tightening on one face. | Pan horizontal, zoom changes what fills narrow frame. | *Altman* — zooming while panning through crowds |
| `DOLLY-ARC` | Dolly + Arc | Approaches while orbiting | Spiral approach. Not straight but curved. Angle changes during approach. | Approach reveals different vertical compositions as angle shifts. | *The Revenant* — approaching subjects |
| `CRANE-ZOOM` | Crane + Zoom | Rising while zooming in (or descending while zooming out) | Maintaining subject size while changing altitude. The world changes but the subject doesn't. | The subject stays the same size in the narrow frame while everything around them transforms. | *Hitchcock* variations |
| `TRACK-PAN` | Track + Pan | Moving laterally while panning in the same direction | Acceleration of the survey. The camera moves AND rotates, covering ground faster. | In narrow frame: the combined movement makes the background move very fast. | *Kubrick* — war film tracking |
| `DOLLY-DRIFT` | Dolly + Drift | Moving forward while drifting slightly left or right | The imperfect approach. The camera is heading toward something but its path isn't straight. | The slight lateral drift in narrow frame creates an off-center approach. | *PTA* — imperfect approaches |
| `CRANE-ROTATE` | Crane + 360° | Rising while doing a full rotation | Ascending spiral. Total environmental survey from rising altitude. | The spiral in vertical reveals everything — every direction at every height. | *Hugo* — clock tower ascent |

---

## Category 9: SPECIALIZED
*Movements defined by narrative purpose or visual effect.*

| Tag | Name | Motion | Emotional Function | 9:16 Notes | Reference |
|-----|------|--------|-------------------|------------|-----------|
| `REVEAL-PULL` | Pull-Back Reveal | Starts tight, pulls back to context | Scope reveal. Intimate was part of something larger. | Pulling back reveals enormous vertical context. | *Touch of Evil* — opening crane |
| `REVEAL-PUSH` | Push-In Reveal | Starts wide, pushes in to discover detail | Discovery. Something in the wide deserves attention. | Push eliminates vertical context, isolates detail. | *Zodiac* — pushing into evidence |
| `PEEK` | Peek | Lateral to see past obstruction | Discovery, voyeurism, what's around the corner | Peeking past vertical obstruction native to tall frame. | *The Shining* — peeking around corners |
| `PASS-THROUGH` | Pass Through | Camera moves through narrow space into new zone | Threshold crossing. Camera physically crosses boundary. | Through doorway, gap, window. Frame shape matches gap. | *Children of Men* — continuous through spaces |
| `OVERHEAD-DROP` | Overhead Drop | Starts overhead, drops to eye level | God's-eye to human-eye. Detachment to presence. | Overhead fills with ground, descent reveals horizontal world. | *Fight Club* — overhead drops |
| `FLOOR-RISE` | Floor Rise | Starts ground level, rises to eye level or above | Emergence, waking, standing up | Rising from ground reveals vertical layers — floor, body, face, ceiling. | *Requiem for a Dream* — floor-level rises |
| `LOCK-OFF` | Lock-Off | Moving camera stops abruptly — locks static | Arrival, decision, punctuation. The stop IS the moment. | After movement, the rigid vertical frame is confrontational. | *PTA* — dolly to lock-off |
| `UNMOTIVATED-DRIFT` | Unmotivated Drift | Camera drifts unrelated to any subject | Unease, another intelligence behind the lens. Camera has its own agenda. | The drift in narrow frame feels like scanning, searching. | *Kubrick* — the Overlook's own camera |
| `SWAY` | Sway | Camera sways gently side to side — as if on a boat or pendulum | Disorientation, dreaminess, intoxication, the world off-balance | The sway in narrow frame is amplified — the vertical edges rock. | *Moonlight* — ocean sequences |
| `STUTTER` | Stutter Step | Camera moves, stops, moves, stops — irregular rhythm | Hesitation, indecision, the camera is uncertain | The stutter is mechanical uncertainty. Each stop is a decision point. | Documentary convention |
| `SNAP-TO` | Snap To | Camera rapidly repositions — not a smooth movement but a jump cut in position | Disorientation, time skip, violence of reframing | The snap in narrow frame is jarring — the composition changes completely in one frame. | *Mr. Robot* — jump reframings |
| `ROLL` | Roll | Camera rotates on its own axis — the horizon tilts | Maximum disorientation. The world turns upside down. Use almost never. | The vertical frame rotating makes ALL lines diagonal. Total spatial collapse. | *Inception* — hallway fight |
| `PUSH-PULL` | Push-Pull | Camera alternates forward-backward — approaching and retreating rhythmically | Ambivalence, approach-avoidance, the camera can't decide | The subject grows and shrinks in the narrow frame. Breathing toward and away. | *Eternal Sunshine* — memory instability |
| `FLOAT-UP` | Float Up | Weightless ascent — not a crane but a drift upward, as if gravity released the camera | Transcendence, death, the soul departing, elevation without machinery | The camera lifts. Slow. Inevitable. The subject below gets smaller. | *American Beauty* — floating sequences |
| `FLOAT-DOWN` | Float Down | Weightless descent | Arrival from above, the divine descending, landing | The camera lowers. The world below grows. Arrival. | *Wings of Desire* — angel descending |
| `STRAFE` | Strafe | Camera moves laterally while maintaining facing — like a crab walk | Surveillance, assessment, the camera evaluates from the side without committing to approach | The subject stays in profile while the camera repositions. | *Heat* — tactical camera movements |

---

## Category 10: TRANSITIONAL MOVEMENTS
*Movements designed to create or serve as transitions between scenes/clips.*

| Tag | Name | Motion | Emotional Function | 9:16 Notes | Reference |
|-----|------|--------|-------------------|------------|-----------|
| `TRANS-WHIP` | Whip Transition | Fast whip pan/tilt that motion-blurs into the next shot | Time jump, location change, energy continuation | Blur fills frame, next image resolves from blur. | *Whiplash* — practice transitions |
| `TRANS-OBJECT` | Object Transition | Camera pushes into an object until it fills the frame black, next shot emerges | Into darkness, through a surface, into a different world | Object fills narrow frame = total black. Next shot emerges from black. | *2001* — monolith transitions |
| `TRANS-MATCH-MOVE` | Match Movement | End of clip A is moving in a direction, start of clip B continues same direction | Continuity of motion across cut. One movement, two spaces. | The directional continuity IS the bridge. | *2001* — bone to satellite |
| `TRANS-SETTLE-START` | Settle to Start | Clip A settles to static, clip B begins static — a beat of stillness between motions | The breath between sentences. Rest before the next movement. | Both clips bookend a moment of vertical stillness. | Standard editorial |
| `TRANS-LIGHT` | Light Transition | Camera moves into or out of a light source — flare, brightness, or darkness as transition | Through light into the next scene. Through darkness into the next scene. | The light fills the narrow frame = white. Or darkness = black. The next world emerges. | *The Tree of Life* — light transitions |
| `TRANS-FOCUS` | Focus Transition | Image goes fully out of focus, next image resolves from blur | Soft dissolve through optical means. The blur IS the bridge. | The blur fills the frame. No content. Just texture. Then the next image resolves. | *Wong Kar-wai* — blur transitions |
| `TRANS-FALL` | Fall Transition | Camera tilts/drops rapidly downward — the world falls away | The ground opens. Falling into the next scene. | The downward rush in vertical is a plunge. | *Requiem for a Dream* — falling transitions |
| `TRANS-RISE` | Rise Transition | Camera tilts/rises rapidly upward — ascending into the next scene | Rising out of one world into another | The upward rush in vertical is an ascent. | *The Tree of Life* — ascending transitions |

---

## Quick Reference: Movements by Emotional Need

| I need to convey... | Primary | Supporting |
|---|---|---|
| **Tension building** | `DOLLY-IN-SLOW`, `ZOOM-CREEP`, `ZOOM-PULSE` | `STATIC-HOLD`, `BREATHE`, `HANDHELD-NERVOUS` |
| **Revelation** | `TILT-REVEAL`, `PAN-REVEAL`, `REVEAL-PULL`, `CRANE-UP-REVEAL` | `PEEK`, `PASS-THROUGH`, `DOLLY-OUT-SLOW` |
| **Isolation** | `DOLLY-OUT-SLOW`, `CRANE-UP-ABANDON`, `STATIC-HOLD` | `FLOAT`, `DRIFT-SLOW`, `UNMOTIVATED-DRIFT` |
| **Intimacy** | `DOLLY-IN-SLOW`, `BREATHE`, `BOOM-DOWN` | `SETTLE`, `TRACK-APPROACH`, `ZOOM-CREEP` |
| **Surveillance** | `STATIC-LOCK`, `PAN-SURVEY`, `TRACK-STALK` | `UNMOTIVATED-DRIFT`, `CRANE-UP`, `STRAFE` |
| **Energy / urgency** | `PAN-WHIP`, `DOLLY-IN-FAST`, `TRACK-LEAD`, `ZOOM-CRASH` | `TILT-WHIP`, `HANDHELD-ENERGY`, `SNAP-TO` |
| **Devotion** | `DOLLY-IN-SLOW`, `CRANE-DOWN-LAND`, `STATIC-HOLD` | `TILT-UP`, `ARC-CRANE`, `FLOAT-DOWN` |
| **Disorientation** | `DOLLY-ZOOM`, `PAN-WHIP`, `ROLL`, `SWAY` | `DOLLY-ARC`, `TRACK-CIRCLE`, `TILT-PENDULUM` |
| **Journey** | `TRACK-FOLLOW`, `TRACK-SIDE`, `PASS-THROUGH` | `DOLLY-LATERAL`, `CRANE-PAN`, `TRACK-PARALLEL` |
| **Scale / grandeur** | `CRANE-UP`, `TILT-UP`, `DOLLY-OUT-FAST`, `WS-AERIAL` | `REVEAL-PULL`, `OVERHEAD-DROP`, `CRANE-LATERAL` |
| **Time passing** | `STATIC-HOLD`, `DRIFT-SLOW`, `PAN-SURVEY` | `ZOOM-CREEP`, `FLOAT`, `DRIFT-CIRCULAR` |
| **Arrival** | `TRACK-APPROACH`, `CRANE-DOWN-LAND`, `SETTLE`, `FLOAT-DOWN` | `DOLLY-IN-MED`, `LOCK-OFF`, `CRANE-SWOOP` |
| **Departure** | `DOLLY-OUT-SLOW`, `CRANE-UP-ABANDON`, `TRACK-RETREAT` | `TILT-UP`, `PAN-SURVEY`, `FLOAT-UP` |
| **Confrontation** | `DOLLY-IN-FAST`, `TRACK-LEAD`, `STATIC-LOCK`, `DOLLY-CONVERGE` | `ZOOM-CRASH`, `LOCK-OFF`, `PAN-RECOIL` |
| **Dream** | `FLOAT`, `DRIFT-CIRCULAR`, `SWAY`, `DOLLY-ZOOM` | `DRIFT-SLOW`, `ARC-CRANE`, `TILT-PENDULUM` |
| **Anxiety** | `HANDHELD-NERVOUS`, `ZOOM-PULSE`, `PAN-SEARCH` | `STUTTER`, `PUSH-PULL`, `SNAP-TO` |
| **Transcendence** | `FLOAT-UP`, `CRANE-UP-ABANDON`, `TILT-UP` | `DRIFT-CIRCULAR`, `CRANE-ROTATE`, `TRANS-LIGHT` |

---

## Quick Reference: Movements by Shot Type

| Starting Shot Tag | Best Movements | Why |
|---|---|---|
| `ECU-*` | `STATIC-HOLD`, `BREATHE`, `DOLLY-OUT-SLOW`, `ZOOM-CREEP` | ECU is powerful still or slowly retreating. Movement competes with detail. |
| `CU-FACE` | `DOLLY-IN-SLOW`, `BREATHE`, `ZOOM-CREEP`, `STATIC-HOLD` | Face builds intensity through approach or stillness. |
| `CU-HANDS-LAP` | `TILT-UP`, `STATIC-HOLD`, `BOOM-UP` | Hands-to-face is natural vertical reveal. |
| `MS-*` | `DOLLY-IN-SLOW`, `DOLLY-OUT-SLOW`, `TRACK-SIDE`, `BREATHE` | Medium shots are versatile. |
| `WS-*` | `PAN-SURVEY`, `CRANE-UP`, `TILT-UP`, `DOLLY-IN-MED` | Wides establish, then find subject. |
| `WS-NEGATIVE` | `STATIC-HOLD`, `DOLLY-OUT-SLOW`, `CRANE-UP-ABANDON` | Let emptiness breathe. Movement emphasizes void. |
| `ARCH-THROUGH-DOOR` | `PASS-THROUGH`, `DOLLY-IN-MED`, `PEEK` | Doorways are thresholds. Cross them. |
| `ARCH-CORRIDOR` | `TRACK-FOLLOW`, `DOLLY-IN-SLOW`, `TRACK-LEAD` | Corridors are built for forward motion. |
| `SURF-*` | `STATIC-HOLD`, `DRIFT-SLOW`, `DOLLY-IN-SLOW` | Surfaces reward stillness. Texture is the event. |
| `LIGHT-*` | `STATIC-HOLD`, `BREATHE`, `DRIFT-SLOW` | Light-defined shots are about light, not movement. |
| `NAR-SACRED` | `STATIC-HOLD`, `DOLLY-IN-SLOW`, `CRANE-DOWN-LAND` | Sacred demands stillness or reverent approach. |
| `NAR-REVEAL` | `PAN-REVEAL`, `TILT-REVEAL`, `REVEAL-PULL` | Match reveal direction to movement. |
| `REL-OTS-*` | `BREATHE`, `STATIC-LOCK`, `DOLLY-IN-SLOW` | Conversation shots breathe or hold. |
| `REL-FACE-TO-FACE` | `STATIC-HOLD`, `ZOOM-CREEP`, `DOLLY-IN-SLOW` | Two faces. Let tension build. |
