# 生图提示词模板 — YC

每张图单独生成，按内容替换 `{变量}`。**默认 Sample / Standard 成品风格**，对齐 `assets/examples/simple/current-showcase/`；只有用户明确点名 Minimal / Sticker / 贴图纸 / 贴纸 / 极简 / 最小贴纸时才用 Minimal；只有用户明确点名 Rich、完整海报、IP 设定页或品牌全景时才用 Rich。

> **执行要求**：本文件中的构思和 prompt 是给 Codex native `image_gen` 或用户明确选择的 CLI/API fallback 使用的内部材料。除非用户明确要求只要 prompt 或不要生成，否则写完 prompt 后必须立即调用 Codex native `image_gen`，不能把 prompt 当作最终交付。`OPENAI_API_KEY` 只属于 CLI/API fallback，不是 Codex 默认路线的前置条件。

> ⚠️ **正式生图必须让参考图真实进入生成上下文**，纯文字 prompt 会回退到"全彩 anime + 满版拼贴"的海报先验。Codex native route 先用 `view_image` / image attachment 载入 selected primary reference，再调用 built-in `image_gen`；CLI/API fallback 才使用 `--image`。先读 `reference-routing.md` 与 `assets/examples/README.md`，扫描 topic-matched assets 后选择一张 primary reference。
> - Sample / Standard → 根据主题、比例、情绪与信息密度选择 `assets/examples/simple/current-showcase/` 或 `simple/` 中最贴切的真实 asset；`07-noise-filter.png` 只在没有更贴切主题图时作为机制图 fallback。
> - Minimal / Sticker（仅显式点名）→ 带 `assets/examples/sticker/00-reference-sheet-watercolor.png`。
> - 长相锁（红发眼镜不稳时加）→ `assets/examples/character-reference/` 九宫格。注意它是全彩 anime，只能锁长相；Minimal 要 00 + 九宫格两张一起带。
> - Cover → 看 `assets/examples/cover/01-sticker-cover-tiny-win.png` 的密度：16:9，一个 YC hero + 一行中文标题 + 白底。
> - Social → 看 `assets/examples/social/01-social-1x1-tiny-win.png` 的密度：1:1，沿用当前 samples 视觉语言。
> - Rich → 仅用户显式点名时，带 `assets/examples/rich/` 对应整页例图。
> - 第一次仍可能偏 → 正常，带参考图重生一次就对。

参考图只锁"长相+画风+密度"，**不照抄构图**，每次从当前内容重想画面。`reference-routing.md` 决定哪个 example 是 primary reference；不要因为方便而固定使用同一张。`sticker/01-08` 是 Minimal 动作姿势库，`sticker/outfit-0x` 是服装变体——都只作构思参考，不当默认画风锁。

## Reference Context Prompt Block（Codex native + CLI/API fallback 共用）

正式生成时，把这段放在 prompt 开头。Codex native route 中，Image 2 指已经通过 `view_image` / image attachment 进入上下文的 selected reference；CLI/API fallback 中，Image 2 指 `--image <canonical-reference>`：

```text
Input image 1 is only the blank output canvas. It is a pure white canvas for creating a new illustration. Do not treat it as style or content.

Input image 2 is the canonical YC reference for this mode. Use image 2 only for character identity, line quality, white background, color restraint, visual density, and handwritten Chinese label style. Do not copy its composition, objects, device, layout, or specific story.

Create a new scene for the requested topic. The output must be a fresh YC illustration, not an edit or copy of the reference image's composition, objects, layout, or story.
```

Codex native route 必须先让 selected reference 在上下文中可见，再调用 built-in `image_gen`。只有用户明确选择 CLI/API fallback，或 native route 不可用时，才使用 `image_gen.py edit --image <blank-canvas> --image <canonical-reference> ...`。如果只能走无参考图的 prompt-only 草稿，必须在交付时标记 `style draft / 未 reference locked`。

## 短 prompt 路由

用户只说“跟这个 skill 一样的风格解释 X / 什么是 X / explain X”时，不要要求用户补长 prompt。直接按默认 Sample / Standard 生成一张 Broad Concept Explainer：

- 把 X 压成一个核心隐喻。
- 先读 `concept-director.md`，写清“不是 A，而是 B”的机制判断。
- 先读 `explanation-variation.md` 选择场景原型，不要自动套机器。构图为一个连续场景：具体起点 → YC 操作 → 可见变化或结构 → 验证/回应/结果。
- 标注默认 3-5 个中文短词；每个词都要推进因果，不要写装饰性口号。
- 禁止百科页、课程卡片、定义段落、分类列表、真实案例列表、底部总结条。
- 以上步骤在内部完成；随后立即调用 Codex native `image_gen`。禁止只回复概念解释、画面方案或 final illustration prompt。

---

## 比例参数速查

| 用户说 | 提示词里写 |
|------|------|
| 16:9 | `16:9 widescreen horizontal` |
| 1:1 | `1:1 square` |
| 9:16 | `9:16 vertical story format` |
| 4:3 | `4:3 horizontal` |
| 3:2 | `3:2 horizontal` |
| 2:3 | `2:3 vertical portrait` |
| 5:4 | `5:4 slightly wide square` |
| 21:9 | `21:9 ultra-wide cinematic banner` |

默认：文章 `16:9`，社媒 `1:1`。

---

## 角色关键词

**Sample / Standard（默认，当前 samples 风格）**：
```
young adult male chibi character YC, short messy dark-red burgundy hair, round clear-frame glasses, gentle masculine brows and face, simple gentle eyes without glossy anime highlights, chibi proportions (large head small body thin legs), casual streetwear, warm hand-drawn sketchbook illustration, slightly wobbly pencil-like linework, lightly colored, low saturation, personal creator-content style, not corporate, not glossy anime, not a commercial poster
```

**Minimal / Sticker（仅显式点名，水彩铅笔轻渲染）**：
```
young adult male chibi character YC, short messy dark-red burgundy hair (red hair clearly recognizable), round clear-frame glasses, gentle masculine face, chibi proportions, drawn as a LOOSE watercolor colored-pencil sketch — soft sketchy linework with slight wobble, light low-saturation coloring, hand-drawn and airy, NOT glossy polished anime, NOT heavy shading, simple soft eyes (no high-gloss highlights), single subject on pure white background
```

**Rich（完整 editorial / IP 设定页）**：
```
young adult male chibi character YC, short messy dark-red burgundy hair, round clear-frame glasses, gentle masculine face, expressive but gentle anime eyes, chibi proportions, casual creative streetwear, silver accessories, warm hand-drawn editorial illustration, polished but still personal and sketchbook-like, not corporate, not glossy commercial poster
```

服装库见 `yc-character.md`（默认 Denim Casual）。

---

## ✦ Sample / Standard 默认模式

当前 samples 风格。纯白底，温暖手绘 chibi，YC 参与核心动作，中文短标注，中等信息密度。默认文章配图、知识讲解、封面、社媒都先用这一档。参考 `assets/examples/simple/current-showcase/`。

> **填写前先确认改写铁律**：哪怕主题是"结构图/架构图/解释图/diagram"，输出必须是 YC 亲手操作的连续手绘物理隐喻场景，**绝不是方框+箭头的论文式架构图**。先在脑内完成"不是 A 而是 B"机制判断 + 物理动词 + `explanation-variation.md` 场景原型选择，再填下面的变量。正式产物默认走 Codex native image route；CLI/API 仅为 fallback。无参考图草稿必须标记为未 reference locked。

```text
Input image 1 is only the blank output canvas. It is a pure white canvas for creating a new illustration. Do not treat it as style or content.

Input image 2 is the selected YC Sample / Standard primary reference (`{selected-reference.png}`), chosen from the real example assets for this topic. Use image 2 ONLY for character identity, line quality, white background, color restraint, visual density, and handwritten Chinese label style. Do not copy its composition, objects, layout, or story.

Generate one standalone {比例} YC illustration in the same SAMPLE / STANDARD style. Create a fresh scene for the requested topic; preserve only the reference's white canvas, single-character staging, pencil line quality, light coloring, sparse labels, and whitespace.

Reframing rule (highest priority):
Even if the topic is described as a "structure / architecture / explainer diagram", DO NOT draw a boxes-and-arrows architecture diagram, encoder/decoder blocks, a PPT infographic, or a formal flowchart. Reframe the structure into ONE continuous hand-drawn physical metaphor scene where YC performs the action that makes the idea work. The scene may be a workbench device, bridge/path, sorter, one-source-many-outputs desk, feedback loop, human-AI relay, focused desk, protection umbrella, listening notebook, emotion-to-melody setup, or small-win scene. Use a machine only when internal transformation/filtering/prediction is truly the best metaphor.

Visual DNA:
STYLE IS THE HIGHEST PRIORITY; reduce content before violating it. PURE WHITE background (#FFFFFF) across the entire canvas, no cream paper tint, no full-page gray/off-white wash, no black or dark area, no paper texture, no gradient, no neon, no glow. Warm hand-drawn chibi illustration with slightly wobbly pencil-like sketch lines and light low-saturation coloring. EXACTLY ONE YC character, integrated into ONE continuous scene and performing the core action. No duplicate YC, no panels, no card grid, no numbered steps, no UI screens, no photoreal images. Medium information density: one clear visual metaphor, a few physical objects, 3-5 short handwritten Chinese labels, and 35%-45% empty white space.

IP Character (required):
{Sample 角色关键词}. YC must have clearly recognizable messy dark-red burgundy hair and round clear-frame glasses.

Theme:
{这张图的主题}

Core idea:
{这张图要表达的核心意思}

Mechanism statement:
{用“不是 A，而是 B”写出概念真正怎样工作}

Scene archetype:
{从 explanation-variation.md 选择：工作台装置 / 桥路径 / 分拣收纳 / 一源多出 / 循环迭代 / 接力校准 / 桌面专注 / 保护边界 / 倾听采样 / 情绪转换 / 小胜利}

Why this archetype:
{一句话说明为什么这个场景比默认机器/箱子更适合；如果选择机器，也说明为什么必须展示内部转换}

Cognitive action and physical verb:
{分类/匹配/预测等一个认知动作} expressed as {倒入/摇动/分拣/织网/测试等可见物理动作}

Composition:
{具体画面：YC 在哪里、正在做什么、核心物件/隐喻是什么、信息如何流动}

Causal beats in one continuous scene (not panels):
1. Starting evidence/input: {2-3 组具体、可区分的输入 / 声音 / 证据 / 干扰 / 原料}
2. YC's core action: {YC 亲手做的明确动作；去掉 YC 后结果不能成立}
3. Visible change/structure: {网/筛/轨道/刻度/模板/桥板/伞面/笔记/旋律线/反馈箱等}
4. Causal proof: {一个新输入 / 回应 / 被保护的产出 / 小成果如何证明这个机制}

Semantic micro-details:
{只列 2-4 个能解释机制的细节；不要列装饰}

Suggested elements:
{元素1} / {元素2} / {元素3} / {可选元素4}

Chinese handwritten labels:
{标注词1} / {标注词2} / {标注词3} / {可选标注词4} / {可选标注词5}

Text rendering rule:
Render ONLY the selected 3-5 short Chinese labels above. The mechanism statement, causal beats, semantic micro-details, and user explanation are private art-direction notes and MUST NOT appear as titles, paragraphs, captions, speech bubbles, numbered steps, or a bottom summary strip.

Color:
YC's red hair is the main color anchor. Black line art, warm beige/gray object shading, orange for flow arrows or movement, red/pink for emphasis, blue only for system/AI/secondary notes.

Constraints:
One image explains one core mechanism, with enough semantic detail to make its causality visible. Use exactly one YC and one primary scene archetype. Use a main device only when it is the selected archetype; otherwise use the chosen bridge, loop, desk, umbrella, listening notebook, relay, melody, or small-win scene as the causal anchor. Include 2-3 small hand-drawn inputs/voices/evidence/interferences/materials, one visible change or structure, and one proof/result when the concept needs them. Samples must be simple hand-drawn icons or objects, never photos, screens, cards grid, or a side UI column. Every secondary object must explain the mechanism; remove decorative clutter. Keep the background pure white and preserve 35%-45% blank space. Show only 3-5 short Chinese labels. No title banner, no definition paragraph, no speech-bubble paragraph, no type/category list, no bottom process strip, no summary strip, no dense table, no heavy card borders, no section headers, no PPT infographic, no formal flowchart, no numbered steps, no dark background, no neon, no glow, no photoreal imagery. Keep all beats in one continuous hand-drawn scene, not separate panels. Do not use a full poster layout. Avoid repeating a wooden crank machine or box silhouette unless the topic requires internal transformation. Do not make it Minimal unless the user explicitly asked for Minimal/Sticker/贴图纸/贴纸. Do not make it Rich unless the user explicitly asked for Rich. Invent a fresh scene for this content while matching the attached selected reference's style and restraint.
```

### Broad Concept Explainer 构思法

大概念不要画百科页。只画一个核心隐喻：
1. 机制：先写“不是 A，而是 B”。
2. 原型：读 `explanation-variation.md`，先决定是装置、桥、循环、接力、桌面、保护、倾听、情绪转换还是小胜利。
3. 例子：输入/声音/证据/干扰要具体、可区分。
4. 操作：YC 用一个可见物理动作改变结果。
5. 结构：画出学习/处理/保护/连接/归纳/转译后留下的可见变化。
6. 验证：让一个新输入、回应、产出或小成果证明这个变化有用。
7. 标注：默认 3-5 个中文短词，只标因果节点；机制说明只用于构思，不写进图里。

例：「什么是 Machine Learning」→ 左侧苹果/香蕉/西瓜例子篮，中间 YC 流汗摇动“学习”曲柄，机器把颜色、形状、纹理织成“模型”规则网；右侧一个没标签的新水果落入网中，机器吐出“预测：苹果？”票据。标注从这些节点中选 3-5 个：`例子` / `学习` / `特征` / `模型` / `新问题` / `预测：苹果？`。

---

## ✦ Minimal / Sticker 贴图模式（仅显式点名）

白底上一张水彩铅笔小贴纸。单个 YC + 一个动作/物件 + 0-3 中文短词。轻、干净、留白多。**只有用户明确点名 Minimal / Sticker / 贴图纸 / 贴纸 / 极简 / 最小贴纸时使用，必带 `00-reference-sheet-watercolor.png`。**

```text
Input image 1 is only the blank output canvas. It is a pure white canvas for creating a new sticker-style illustration. Do not treat it as style or content.

Input image 2 is the canonical YC Minimal / Sticker reference (`00-reference-sheet-watercolor.png`). Use image 2 ONLY for loose watercolor colored-pencil hand-drawing, pure white background, single subject restraint, red-hair clear-glasses identity, and airy whitespace. Do not copy its sheet layout or poses unless the user explicitly requested that pose.

Generate one standalone {比例} sticker-style illustration.

Visual DNA:
A small hand-drawn STICKER on a PURE WHITE background (#FFFFFF — no cream, no paper texture, no gradient, no shadow, no border). Loose watercolor / colored-pencil hand-drawing: soft sketchy linework with slight wobble, light low-saturation coloring, gentle and airy. NOT glossy polished anime. NOT a flat vector. NOT a dense collage. At least 50% of the canvas is empty white space. ONE single subject only.

IP Character (required):
{Minimal 角色关键词}. YC is the only character and does the ONE simple action.

Scene (ONE simple thing):
{YC 在做一个简单动作 / 和一个简单物件互动}

Labels (0-3 short Chinese words MAX, Chinese only — prefer fewer or none):
{可选短词1} / {可选短词2}

Color:
YC's red hair is the main color anchor. Optional very light warm accents only (soft beige / soft blue / soft pink), low saturation. No bold color blocks, no rainbow.

{通用约束 · Minimal}
```

### Minimal 约束块（通用）

```text
Constraints (prevent the "poster" drift):
PURE WHITE background — #1 rule. ONE single subject — no multiple scenes, no panels, no step flow, no grid. NO sticky-note wall. NO big "YC" logo or title banner. NO surrounding clutter of books / pen cups / plants / mugs — drop ALL signature props unless ONE prop IS the point. NO scattered hearts / stars / sparkles. NO English, NO bilingual labels, NO section headers, NO tables. At most ONE small relevant prop. Draw YC DIRECTLY on white paper — NO die-cut white outline around the character. Result = one small light watercolor-pencil drawing, plenty of white space. If you removed all text, the image should still make complete sense.
```

### Minimal 构思法
1. 一个 YC + 一个意思（一个表情 / 一个动作 / 和一个物件互动）。不讲流程、不分格。
2. 物件少而准：选**一个**和主题最相关的，其余全删。
3. 宁可不写字；要写就 1-3 个中文短词放角色旁空白处。
4. 留白是主角：画完先问"是不是太满"，太满就删元素，不是缩小。

**例**：「专注写作」→ YC 托腮看着合上的小笔记本，旁边一个小杯子，标注「专注」（或不标），纯白底，红发是唯一明显颜色，无装饰、大量留白。

### Sample 封面版（文章封面 / 标题图）

封面 ≠ 海报，仍然默认走 Sample 逻辑：**一个 YC hero + 一行标题 + 白底**，标题是唯一允许的"多字"。常用 16:9 / 4:3。布局密度参考 `assets/examples/cover/01-sticker-cover-tiny-win.png`。

```text
Using the attached cover reference for density and layout, generate one standalone {16:9 / 4:3} YC cover image.

Style: current YC sample style, pure white background, hand-drawn chibi, clear red hair and round clear-frame glasses, clean creator-content illustration.

Layout: ONE YC character (messy dark-red hair, clear-frame glasses, watercolor-pencil sketch) placed to one side OR centered, doing a single gesture related to the topic. A short Chinese title in clean hand-written style in the empty space beside YC.

Title text: 「{文章标题，≤10 字}」  （副标题可选，≤8 字）

Hard rules: pure white background. ONE main YC hero. At most 1-2 relevant props. No panels, no section headers, no scattered decorations. The title is the only block of text. Keep generous empty white space. A clean YC cover, NOT a busy poster and NOT Rich.
```

---

## ✦ Legacy Simple / Story-flow prompt（按需）

这段保留给明确需要 3-6 步流程串联的场景，但它仍属于默认 Sample / Standard 密度，不是单独自动模式。最终成品风格以 `assets/examples/simple/current-showcase/` 为准。

```text
Generate one standalone {比例} YC illustration in SIMPLE story-flow style.

Visual DNA:
PURE WHITE background (#FFFFFF), no cream paper tint, no full-page gray/off-white wash. Hand-drawn illustration with multiple small scene vignettes showing a step-by-step flow. Each step has YC in a different action/state. Warm and personal but not information-overloaded. Connected by arrows or a visual flow path. Light contact shadows under objects are okay; keep the overall canvas white and clean. Light decorative accents (small hearts, stars — sparingly).

IP Character (required):
{Sample 角色关键词}. YC appears in each step doing a different action.

Steps (3-6):
{步骤1} → {步骤2} → {步骤3} → ...

Labels per step (1-2 short Chinese labels each):
{步骤1中文短标注} / {步骤2中文短标注} / ...

Signature props (pick 2-3): {根据场景选}

Color: black line art, warm accents. Orange for flow arrows. Red/soft pink for emphasis. Blue for system/AI elements if needed.

Constraints:
Each step is a small vignette, not a bordered panel. Steps connected by arrows / flow path. No heavy card borders or section headers. Each label SHORT (2-6 chars). One bottom summary line OK. A warm visual story, not a textbook diagram.
```

---

## ✦ Rich 丰富模式（仅显式点名）

完整海报 / IP 设定页 / 品牌全景。**不要自动使用**。只有用户明确说 Rich、完整海报、IP 介绍、品牌全景、整页设定图时才用。

```text
Input image 1 is only the blank output canvas. It is a pure white or warm off-white canvas for creating a new Rich illustration. Do not treat it as style or content.

Input image 2 is the chosen YC Rich reference. Use image 2 ONLY for YC identity, editorial density, warm hand-drawn system-page feeling, and short-label treatment. Do not copy its exact sections, objects, or layout unless explicitly requested.

Generate one standalone {比例} YC RICH editorial poster / character-system page.

Visual DNA:
Warm off-white / cream background with a refined hand-drawn editorial feeling. Full-page composition with multiple organized sections. Rich but still breathable. Personal creator brand energy, not a corporate key visual, not a generic anime poster.

IP Character (required):
{Rich 角色关键词}. YC must have clearly recognizable messy dark-red burgundy hair and round clear-frame glasses.

Purpose:
{完整海报 / IP 自我介绍 / 品牌生态地图 / 个人设定页 / 内容体系}

Page structure:
Main YC hero area: {主视觉动作或姿态}
Supporting sections: {ABOUT / LIFE MODE / CONTENT PILLARS / FAVORITE THINGS / WORKFLOW / SIGNATURE MOOD 等，按任务选择 3-6 个}
Small scenes or icons: {根据主题选择}

Text:
Short bilingual labels are allowed. Keep each label brief. No long paragraphs. Use handwritten-style headings and short notes only.

Color:
YC red hair is the anchor. Use denim blue, soft pink, warm beige, black linework, and muted gray. Keep it warm, personal, and cohesive.

Constraints:
Rich mode is full-page, but not cluttered. Avoid tiny unreadable text. Avoid corporate brochure style. Avoid heavy glossy anime rendering. Avoid generic poster effects. Every section should explain YC or the user's requested complete theme.
```

---

## 图像编辑提示

去掉文字：
```text
Edit the provided image. Remove only the text "{要删除的文字}" from {位置}. Fill with matching background. Preserve everything else exactly.
```

增强 YC 存在感：
```text
Regenerate with same layout. Make YC do the core action, not just sit there. Keep the style and all props.
```

角色识别修复：
```text
Regenerate. The character must have: messy dark-red burgundy hair AND round clear-frame glasses. Both mandatory. Keep everything else the same.
```
