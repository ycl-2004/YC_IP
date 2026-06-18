# 生图提示词模板 — YC

每张图单独生成，按内容替换 `{变量}`。**默认 Sample / Standard 成品风格**，对齐 `assets/examples/simple/current-showcase/`；只有用户明确点名 Minimal / Sticker / 贴图纸 / 贴纸 / 极简 / 最小贴纸时才用 Minimal；只有用户明确点名 Rich、完整海报、IP 设定页或品牌全景时才用 Rich。

> ⚠️ **生图必须带参考图**，纯文字 prompt 会回退到"全彩 anime + 满版拼贴"的海报先验。
> - Sample / Standard（默认）→ 带 `assets/examples/simple/current-showcase/` 中最接近的例图。
> - Minimal / Sticker（仅显式点名）→ 带 `assets/examples/sticker/00-reference-sheet-watercolor.png`。
> - 长相锁（红发眼镜不稳时加）→ `assets/examples/character-reference/` 九宫格。注意它是全彩 anime，只能锁长相；Minimal 要 00 + 九宫格两张一起带。
> - Cover → 看 `assets/examples/cover/01-sticker-cover-tiny-win.png` 的密度：16:9，一个 YC hero + 一行中文标题 + 白底。
> - Social → 看 `assets/examples/social/01-social-1x1-tiny-win.png` 的密度：1:1，沿用当前 samples 视觉语言。
> - Rich → 仅用户显式点名时，带 `assets/examples/rich/` 对应整页例图。
> - 第一次仍可能偏 → 正常，带参考图重生一次就对。

参考图只锁"长相+画风+密度"，**不照抄构图**，每次从当前内容重想画面。`sticker/01-08` 是 Minimal 动作姿势库（想画某动作先翻它找最接近的），`sticker/outfit-0x` 是服装变体——都只作构思参考，不当默认画风锁。

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
chibi character YC, messy dark-red burgundy hair, round clear-frame glasses, expressive gentle eyes, small gentle round face, chibi proportions (large head small body thin legs), casual streetwear, small earring, silver chain necklace, white sneakers, warm hand-drawn sketchbook illustration, pencil-like linework, lightly colored, personal creator-content style, not corporate, not glossy commercial poster
```

**Minimal / Sticker（仅显式点名，水彩铅笔轻渲染）**：
```
chibi character YC, messy dark-red burgundy hair (red hair clearly recognizable), round clear-frame glasses, chibi proportions, drawn as a LOOSE watercolor colored-pencil sketch — soft sketchy linework with slight wobble, light low-saturation coloring, hand-drawn and airy, NOT glossy polished anime, NOT heavy shading, simple soft eyes (no high-gloss highlights), single subject on pure white background
```

**Rich（完整 editorial / IP 设定页）**：
```
chibi character YC, messy dark-red burgundy hair, round clear-frame glasses, expressive but gentle anime eyes, small round face, chibi proportions, casual creative streetwear, silver accessories, warm hand-drawn editorial illustration, polished but still personal and sketchbook-like, not corporate, not glossy commercial poster
```

服装库见 `yc-character.md`（默认 Denim Casual）。

---

## ✦ Sample / Standard 默认模式

当前 samples 风格。纯白底，温暖手绘 chibi，YC 参与核心动作，中文短标注，中等信息密度。默认文章配图、知识讲解、封面、社媒都先用这一档。参考 `assets/examples/simple/current-showcase/`。

```text
Using the attached current-showcase image ONLY as a STYLE and DENSITY reference, generate one standalone {比例} YC illustration in the same SAMPLE / STANDARD style.

Visual DNA:
PURE WHITE background (#FFFFFF), no cream paper tint, no full-page gray/off-white wash, no paper texture, no gradient. Warm hand-drawn chibi illustration with pencil-like sketch lines and light coloring. YC is part of the core conceptual action, not a mascot pasted beside a diagram. Medium information density, similar to the current examples: clear visual metaphor, a few objects, short handwritten Chinese labels, plenty of white space.

IP Character (required):
{Sample 角色关键词}. YC must have clearly recognizable messy dark-red burgundy hair and round clear-frame glasses.

Theme:
{这张图的主题}

Core idea:
{这张图要表达的核心意思}

Composition:
{具体画面：YC 在哪里、正在做什么、核心物件/隐喻是什么、信息如何流动}

Suggested elements:
{元素1} / {元素2} / {元素3} / {可选元素4}

Chinese handwritten labels:
{标注词1} / {标注词2} / {标注词3} / {可选标注词4}

Color:
YC's red hair is the main color anchor. Black line art, warm beige/gray object shading, orange for flow arrows or movement, red/pink for emphasis, blue only for system/AI/secondary notes.

Constraints:
One image explains one core idea. Keep the background pure white. Keep labels short, Chinese-first, and readable. No long paragraphs, no dense table, no heavy card borders, no section headers, no PPT infographic, no formal flowchart. Do not use a full poster layout. Do not make it Minimal unless the user explicitly asked for Minimal/Sticker/贴图纸/贴纸. Do not make it Rich unless the user explicitly asked for Rich. Invent a fresh scene for this content while matching the current examples' density and finish.
```

---

## ✦ Minimal / Sticker 贴图模式（仅显式点名）

白底上一张水彩铅笔小贴纸。单个 YC + 一个动作/物件 + 0-3 中文短词。轻、干净、留白多。**只有用户明确点名 Minimal / Sticker / 贴图纸 / 贴纸 / 极简 / 最小贴纸时使用，必带 `00-reference-sheet-watercolor.png`。**

```text
Using the attached image ONLY as a STYLE reference (loose watercolor colored-pencil hand-drawing, pure white background, single subject, lots of empty space), generate one standalone {比例} sticker-style illustration.

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
Using the attached Rich reference image ONLY as a density and layout reference, generate one standalone {比例} YC RICH editorial poster / character-system page.

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
