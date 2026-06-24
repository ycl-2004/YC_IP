# YC Reference Routing

This file is the source of truth for selecting real YC image references. Read it, `assets/examples/README.md`, and for explainers `explanation-variation.md` before every YC image generation.

## Non-negotiable workflow

1. Classify the request by mode, deliverable ratio, topic, and emotional tone.
2. Scan the corresponding real assets under `assets/examples/`. When working from the source repo, also scan `/Users/yichenlin/Desktop/AI Agent/Personal IP/YC_IP/examples/images/`; these are the same canonical Sample showcase assets and can be used to reason about scene language.
3. Choose the closest **primary reference** and pass it as an actual image input to the image-generation or edit route. A text prompt that merely names an asset is not compliant.
4. Add at most one **secondary reference** only when it solves a separate need: a specific approved pose, outfit, or a character-identity correction. Do not stack references for decoration.
5. Use the references for YC identity, line quality, palette restraint, whitespace, and information density. Build a new scene; never copy the reference composition.

`07-noise-filter.png` is a safe fallback for a one-character, one-device mechanism illustration. It is **not** the blanket default. For explainers, first choose a scene archetype in `explanation-variation.md`; only choose `07-noise-filter.png` when the topic truly needs compact filtering/noise removal or no better archetype fits.

## Primary-reference routing

| Topic or deliverable | Primary reference |
| --- | --- |
| Find or recover context | `simple/current-showcase/01-context-back.png` |
| Trust, proof, feedback, or relationship building | `simple/current-showcase/02-trust-bridge.png` |
| Sort, prioritize, or classify inputs | `simple/current-showcase/03-purpose-sort.png` |
| Repurpose one source into multiple outputs | `simple/current-showcase/04-one-source-many-outputs.png` |
| Broad concept with an explanatory sequence | `simple/current-showcase/05-concept-explainer.png` |
| Before/after contrast | `simple/current-showcase/06-before-after-contrast.png` |
| Signal versus noise, filtering, or a compact one-character mechanism | `simple/current-showcase/07-noise-filter.png` |
| Habit, feedback loop, or a small repeatable system | `simple/current-showcase/08-minimum-loop.png` |
| Human–AI collaboration or hand-off | `simple/current-showcase/09-human-ai-relay.png` |
| Emotion, music, songwriting, or mood | `simple/current-showcase/10-emotion-to-melody.png` |
| Deep work, coding, writing, or intentional creation | `simple/current-showcase/11-deep-work-corner.png` |
| Boundaries, distraction protection, or focus | `simple/current-showcase/12-protect-focus.png` |
| Audience empathy, listening, community, or support | `simple/current-showcase/13-audience-listening.png` |
| Encouragement, progress, celebration, or a tiny win | `simple/current-showcase/14-tiny-win.png` |
| 16:9 title-led cover | `cover/01-sticker-cover-tiny-win.png` |
| 1:1 social post | `social/01-social-1x1-tiny-win.png` |
| Explicit Minimal / Sticker | `sticker/00-reference-sheet-watercolor.png` |
| Explicit Rich character, brand, workspace, music, or transformation page | the closest `rich/01-05-*.png` asset |

For Sample method scenes, also inspect `simple/08-idea-press-machine.png`, `simple/09-trust-bridge.png`, `simple/10-purpose-sort-machine.png`, and `simple/11-one-source-many-outputs.png`. Use one when its scene metaphor fits the request better than a current-showcase asset.

## Explainer scene variation

For "explain X / what is X" requests, do **not** automatically route to a machine or box. First choose one of these scene languages, then choose the corresponding primary reference:

- Internal transformation / filtering / prediction: `05-concept-explainer.png` or `07-noise-filter.png`
- Trust / connection / migration: `02-trust-bridge.png`
- Classification / prioritization: `03-purpose-sort.png`
- Repurposing / multi-output: `04-one-source-many-outputs.png`
- Feedback / optimization / habit loop: `08-minimum-loop.png`
- Human judgment / AI handoff / review: `09-human-ai-relay.png`
- Emotional or creative translation: `10-emotion-to-melody.png`
- Focus / writing / coding / creation state: `11-deep-work-corner.png`
- Boundary / distraction protection: `12-protect-focus.png`
- Listening / audience research / empathy: `13-audience-listening.png`
- Small win / progress / encouragement: `14-tiny-win.png`

If two valid references fit, choose the one that changes the scene language away from the most recent output. Avoid consecutive explainers that share the same "wooden machine with crank" silhouette unless the user asked for a series with visual continuity.

## Character, outfit, and copy

YC is a young adult **male** character: short messy deep-burgundy hair, round clear-frame glasses, chibi proportions, gentle masculine face, and casual streetwear. Red hair and clear glasses are mandatory.

Choose clothing from the topic rather than reusing one look:

- Denim Casual: everyday, support, outdoor, and general-purpose scenes.
- Black Workwear: engineering, late-night building, and deep work.
- Varsity Playful: learning, campus, travel, and lighter social subjects.
- Clean Cream: music, emotion, intimate creative work, and café/content creation.

Use concise Chinese copy only when it adds meaning to the scene. Select its wording from the request; never reuse a fixed slogan by default.

## Reference quality gate

Reject and regenerate if the output is text-only-reference-based, copies the reference layout, turns YC into a female character, omits his red hair or clear-frame glasses, drifts into generic glossy anime, or violates the selected asset’s white-space and density language.
