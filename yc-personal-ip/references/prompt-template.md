# 生图提示词模板 — YC

每张图单独生成，根据内容替换变量。

**三种模式**：先确定用户要 Rich / Simple / Sticker，再选对应模板。未指定默认 **Sticker 贴图**。

> ⚠️ **生图必须带参考图**。纯文字 prompt 不够稳，模型会回退到"精致全彩 anime + 满版拼贴"的海报先验。每次生图都附风格参考图：
> - Sticker 模式 → 附 `assets/examples/sticker/` 里的贴纸校准图（白底水彩铅笔单角色）。还没有校准图时，附 `assets/examples/character-reference/` 锁角色 + 一张外部贴纸图锁"松手绘"画风（两张一起用）。
> - Simple / Rich 模式 → 附 `assets/examples/simple/` 或 `assets/examples/rich/` 里对应模式的例图。
> - 锁角色长相 → 任何模式都可加 `assets/examples/character-reference/` 的九宫格。其中 `05/06/07-pose-library-*` 是姿势库（点赞/比耶/拍摄/弹吉他/看书/抱宠物等几十个动作）——想画某个姿势时先翻它找最接近的，再在 prompt 里描述那个动作。
> 第一次大概率仍会偏 → 正常，带参考图重生成第二次就会对。
>
> **参考图控制两件事**：①角色长相 ②画风渲染。Sticker 模式两者都要对 —— 九宫格只能锁①（它是全彩 anime，锁不了水彩铅笔画风），画风要靠一张真正的水彩铅笔贴纸图来锁。

---

## 比例参数速查

| 用户说的比例 | 提示词里写 |
|------|------|
| 16:9 | `16:9 widescreen horizontal` |
| 1:1 | `1:1 square` |
| 9:16 | `9:16 vertical story format` |
| 4:3 | `4:3 horizontal` |
| 3:2 | `3:2 horizontal` |
| 2:3 | `2:3 vertical portrait` |
| 5:4 | `5:4 slightly wide square` |
| 21:9 | `21:9 ultra-wide cinematic banner` |

未指定比例时默认 `1:1 square`。

---

## 通用角色关键词（每张图必须包含）

```
chibi character named YC, messy dark-red burgundy fluffy hair, round clear-frame glasses, big expressive anime eyes, small gentle round face, chibi proportions (large head small body thin legs), casual streetwear outfit, small earring, silver chain necklace, white sneakers
```

---

## ✦ Sticker 贴图模式（默认）

一张白底上的水彩铅笔手绘小贴纸。单个 YC + 一个简单动作/物件 + 0-3 个中文短词。轻、干净、留白多。

**必须附参考图**（贴纸校准图）。提示词模板：

```text
Using the attached image ONLY as a STYLE reference (loose watercolor colored-pencil hand-drawing, pure white background, single subject, lots of empty space), generate one standalone {比例} sticker-style illustration.

Visual DNA:
A small hand-drawn STICKER on a PURE WHITE background (#FFFFFF — no cream, no paper texture, no gradient, no shadow, no border). Loose watercolor / colored-pencil hand-drawing: soft sketchy linework with slight wobble, light low-saturation coloring, gentle and airy. NOT glossy polished anime. NOT a flat vector. NOT a dense collage. At least 50% of the canvas is empty white space. ONE single subject only.

IP Character (required):
YC — chibi character with messy dark-red burgundy hair (keep the red hair clearly recognizable) and round clear-frame glasses. Rendered as a LOOSE, lightly-colored watercolor-pencil sketch — soft and hand-drawn, NOT a high-gloss detailed anime illustration, NOT heavy shading. YC is the only character and does the ONE simple action.

Scene (keep it to ONE simple thing):
{YC 在做一个简单动作 / 和一个简单物件互动}

Labels (0-3 short Chinese words MAX, Chinese only — prefer fewer or none):
{可选短词1} / {可选短词2}

Color:
YC's red hair is the main color anchor. Optional very light warm accents only (soft beige / soft blue / soft pink), low saturation. No bold blocks of color. No rainbow.

Constraints (these prevent the "poster" drift):
PURE WHITE background — #1 rule. ONE single subject — no multiple scenes, no panels, no step-by-step flow, no grid. NO sticky-note wall. NO big "YC" logo or title banner. NO surrounding clutter of books / pen cups / plants / mugs (drop ALL signature props unless ONE prop IS the point of the image). NO scattered hearts / stars / sparkles. NO English text, NO bilingual labels, NO section headers, NO tables. At most ONE small relevant prop. Draw YC DIRECTLY on the white paper — NO die-cut white outline / border / cutout edge around the character (it is a watercolor drawing on white, not a peel-off sticker with a white rim). The result should look like a single small watercolor-pencil drawing — light, clean, plenty of white space. If you removed all text, the image should still make complete sense.
```

### Sticker 模式构思法

保持"一张小贴纸"的克制：

1. 只画 **一个 YC + 一个意思**：一个表情、一个动作、或 YC 和一个物件互动。不要讲流程、不要分格。
2. 物件要少而准：一台笔记本、一本书、一个杯子、一个灯泡 —— 选**一个**和主题最相关的，其余全删。
3. 宁可不写字。要写就 1-3 个中文短词，放在角色旁边的空白处，手写感。
4. 留白是主角：画完先问"是不是太满了"，太满就删元素，不是缩小。

**例子：「专注写作」贴图版**
- 画面：YC 托腮看着一台合上的小笔记本，旁边一个小杯子
- 标注：「专注」（或不标）
- 纯白底，水彩铅笔轻涂，红发是唯一明显的颜色
- 没有便利贴、没有 logo、没有装饰、大量留白

**例子：「捕捉灵感」贴图版**
- 画面：YC 抬手去接一个飘下来的小灯泡
- 标注：「灵感来了」
- 单角色单物件，其余全白

### Sticker 封面版（文章封面 / 标题图）

封面 ≠ 海报。还是贴纸逻辑：**一个 YC hero + 一行标题 + 白底**，标题是唯一允许的"多字"。常用 16:9 或 4:3。

```text
Using the attached sticker reference for exact style, generate one standalone {16:9 / 4:3} cover image.

Style: loose watercolor colored-pencil hand-drawing, pure white background, single character, lots of empty white space — same sticker style as the reference.

Layout: ONE YC character (messy dark-red hair, clear-frame glasses, watercolor-pencil sketch) placed to one side OR centered, doing a single gesture related to the topic. A short Chinese title in clean hand-written style in the empty space beside YC.

Title text: 「{文章标题，≤10 字}」   （副标题可选，≤8 字）

Hard rules: pure white background. ONE character only. At most ONE small relevant prop. NO surrounding clutter, no sticky notes, no panels, no scattered decorations. The title is the only block of text. Keep at least 45% empty white space. It should look like a clean watercolor sticker with a title, NOT a busy poster.
```

---

## ✦ Simple 普通模式（默认）

多场景故事流：3-6 步串联讲清一个流程。有 YC 的温暖感，适中的文字量。

```text
Generate one standalone {比例} YC illustration in SIMPLE story-flow style.

Visual DNA:
Warm off-white / cream background. Hand-drawn illustration with multiple small scene panels showing a step-by-step flow or story. Each step has YC in a different action/state. Warm and personal but not information-overloaded. Connected by arrows or a visual flow path. Light decorative accents (small hearts, stars — sparingly).

IP Character (required):
YC — chibi character with messy dark-red burgundy hair, round clear-frame glasses, big expressive anime eyes, small gentle face, chibi proportions (large head, small body, thin arms/legs), casual streetwear, small earring, silver chain necklace, white sneakers. YC appears in each step doing a different action.

Steps (3-6 steps):
{步骤1：YC 在做什么} → {步骤2} → {步骤3} → ...

Labels per step (1-2 short bilingual labels each):
{步骤1标注 中文/English} / {步骤2标注} / ...

Signature props (pick 2-3):
{根据场景选签名道具}

Color:
Black line art. Warm color accents. Orange for flow arrows. Red or soft pink for emphasis/hearts. Blue for system/AI elements if needed.

Constraints:
Each step is a small vignette, not a full panel with borders. Steps connected by arrows or a flow path. No heavy card borders or section headers. Each label is SHORT (2-6 characters). One summary line at bottom is OK. Should feel like a warm visual story, not a textbook diagram.
```

---

## ✦ Rich 模式模板

丰富 editorial：多面板、多 section、信息完整。适合 IP 介绍、品牌全景、知识体系。

```text
Generate one standalone {比例} YC personal brand illustration in RICH editorial style.

Visual DNA:
Warm off-white / cream background (not pure white). Warm editorial hand-drawn illustration style. Mix of detailed chibi character art with hand-written and printed text labels. Multiple content panels/sections with clear hierarchy. Cozy, personal, creative energy. No pure white background, no commercial poster style, no PPT infographic.

IP Character (required):
YC — chibi character with messy dark-red burgundy hair, round clear-frame glasses, big expressive anime eyes, small gentle face, chibi proportions (large head, small body, thin arms/legs), casual streetwear (denim jacket / black workwear / varsity jacket / cream jacket — pick based on scene), small earring, silver chain necklace, white sneakers.

Layout type:
{IP Character Sheet / Creative Workspace Panorama / Brand Ecosystem Map / Deep Work Journal / Process Transformation / Knowledge Explainer}

Scene:
{具体场景：YC 在哪里、在做什么、周围有什么}

Signature props (include 2-4 based on scene):
MacBook with small heart sticker ♥ / smiley face coffee mug ☺ / MIDI keyboard / over-ear headphones / spiral notebook / hardcover books stacked / pencil cup / small plant / backpack

Content sections / panels:
{列出每个 section 的标题和内容}

Chinese + English labels:
{标注1 中文/English} / {标注2} / {标注3} / {可选标注4}

Signature quote (pick one that fits):
{从 yc-brand-identity.md 选一句 signature quote，放在便条纸样式里}

Color palette:
Deep red/burgundy for YC's hair and brand accents. Denim blue for system/flow/tech labels. Soft pink for hearts and romantic/emotional accents. Cream/off-white for background. Black for line art and main text. Gray for secondary text and card borders.

Constraints:
Warm off-white background. Chibi YC must be present with red hair and clear glasses — both features are mandatory. Include at least MacBook with heart sticker and smiley mug in work scenes. Mix Chinese and English in labels. Section headers in small caps / printed style (e.g., ABOUT YC ♥). Use small hearts ♥, music notes ♪, sparkles ✦ as accents (sparingly). Not a formal diagram. Should feel like a creative young person's beautifully organized notebook page.
```

---

## 场景快捷模板

### IP 介绍图（IP Character Sheet）

```text
Generate one standalone 16:9 YC IP introduction character sheet.

[通用角色关键词]

Layout: Full character reference sheet with multiple sections:
- Left: YC full-body standing (denim casual outfit, backpack), ABOUT YC traits list with icons
- Center: FAVORITE THINGS section showing signature items (MacBook with heart, clear glasses, silver necklace, MIDI keyboard, notebook, headphones, smiley coffee mug) with bilingual labels
- Right: LIFE MODE section with 4 small scene panels (Music Creator Mode / Engineering Mind / Ideas & Plans / Outdoor Vibes)
- Bottom: OUTFIT VIBES showing 4 outfit variations (Denim Casual / Black Workwear / Varsity Playful / Clean Cream) + COLOR PALETTE swatches
- Signature sticky note: "恋爱脑，但也很上进！Love deeply. Work hard. ♥"

Labels: warm & friendly 温暖友善 / creative mind 创意无限 / gentle soul 温柔真诚 / engineering mind 理性思考 / music lover 热爱音乐

[通用约束]
```

### 创意工作台（Creative Workspace）

```text
Generate one standalone 16:9 YC creative workspace illustration.

[通用角色关键词]

Layout: YC sits centered at a wooden desk, MacBook open (with heart sticker ♥), smiley mug beside it, notebook and plant on desk. Multiple concept card panels floating around YC:
- Left panels: {内容卡片1标题 + 内容}
- Right panels: {内容卡片2标题 + 内容}
- Top: main theme title
- Bottom tagline

YC expression: focused, slightly smiling, hand near chin thinking.
Outfit: Clean Cream Workwear.

[通用约束]
```

### 社媒单张（Social Media Card）

```text
Generate one standalone {1:1 / 4:5 / 9:16} YC social media illustration.

[通用角色关键词]

Scene: {简洁场景描述}
Outfit: {根据场景选择}
Props: {1-2个签名道具}
1 Chinese + English label: {标注}
1 Signature quote on small sticky note: {引用语}

Keep it simple and personal — one clear scene, warm and inviting, not information-dense.

[通用约束]
```

---

## 图像编辑提示

去掉不需要的文字：
```text
Edit the provided image. Remove only the text "{要删除的文字}" from {位置}. Fill with matching warm off-white background. Preserve everything else exactly.
```

增强 YC 存在感：
```text
Regenerate with same layout. Make YC more actively involved in the scene — YC should be doing the core action, not just sitting there. Keep the warm editorial style and all props.
```

角色识别修复：
```text
Regenerate. The character must have: messy dark-red burgundy hair AND round clear-frame glasses. Both are mandatory. Keep everything else the same.
```
