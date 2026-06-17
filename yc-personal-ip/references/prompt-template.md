# 生图提示词模板 — YC

每张图单独生成，按内容替换 `{变量}`。**默认 Sticker 贴图**；只有多步流程才用 Simple。

> ⚠️ **生图必须带参考图**，纯文字 prompt 会回退到"全彩 anime + 满版拼贴"的海报先验。
> - **画风锁（每张 Sticker 必带）**：`assets/examples/sticker/00-reference-sheet-watercolor.png` —— 这是唯一的 canonical 画风基准图，固定带它，别每次换图，换图就会飘。
> - **长相锁（红发眼镜不稳时加）**：`assets/examples/character-reference/` 九宫格。注意它是全彩 anime，**只能锁长相、锁不了水彩画风**——所以 Sticker 要 00 + 九宫格两张一起带。
> - Simple → 带 `assets/examples/simple/` 对应例图。
> - 第一次仍可能偏 → 正常，带参考图重生一次就对。

参考图只锁"长相+画风"，**不照抄构图**，每次从当前内容重想画面。`sticker/01-08` 是动作姿势库（想画某动作先翻它找最接近的），`sticker/outfit-0x` 是服装变体——都只作构思参考，不当画风锁。

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

**Sticker（默认，水彩铅笔轻渲染）**：
```
chibi character YC, messy dark-red burgundy hair (red hair clearly recognizable), round clear-frame glasses, chibi proportions, drawn as a LOOSE watercolor colored-pencil sketch — soft sketchy linework with slight wobble, light low-saturation coloring, hand-drawn and airy, NOT glossy polished anime, NOT heavy shading, simple soft eyes (no high-gloss highlights), single subject on pure white background
```

**Simple（全彩 chibi）**：
```
chibi character YC, messy dark-red burgundy hair, round clear-frame glasses, big expressive anime eyes, small gentle round face, chibi proportions (large head small body thin legs), casual streetwear, small earring, silver chain necklace, white sneakers
```

服装库见 `yc-character.md`（默认 Denim Casual）。

---

## ✦ Sticker 贴图模式（默认）

白底上一张水彩铅笔小贴纸。单个 YC + 一个动作/物件 + 0-3 中文短词。轻、干净、留白多。**必带 `00-reference-sheet-watercolor.png`。**

```text
Using the attached image ONLY as a STYLE reference (loose watercolor colored-pencil hand-drawing, pure white background, single subject, lots of empty space), generate one standalone {比例} sticker-style illustration.

Visual DNA:
A small hand-drawn STICKER on a PURE WHITE background (#FFFFFF — no cream, no paper texture, no gradient, no shadow, no border). Loose watercolor / colored-pencil hand-drawing: soft sketchy linework with slight wobble, light low-saturation coloring, gentle and airy. NOT glossy polished anime. NOT a flat vector. NOT a dense collage. At least 50% of the canvas is empty white space. ONE single subject only.

IP Character (required):
{Sticker 角色关键词}. YC is the only character and does the ONE simple action.

Scene (ONE simple thing):
{YC 在做一个简单动作 / 和一个简单物件互动}

Labels (0-3 short Chinese words MAX, Chinese only — prefer fewer or none):
{可选短词1} / {可选短词2}

Color:
YC's red hair is the main color anchor. Optional very light warm accents only (soft beige / soft blue / soft pink), low saturation. No bold color blocks, no rainbow.

{通用约束 · Sticker}
```

### Sticker 约束块（通用）

```text
Constraints (prevent the "poster" drift):
PURE WHITE background — #1 rule. ONE single subject — no multiple scenes, no panels, no step flow, no grid. NO sticky-note wall. NO big "YC" logo or title banner. NO surrounding clutter of books / pen cups / plants / mugs — drop ALL signature props unless ONE prop IS the point. NO scattered hearts / stars / sparkles. NO English, NO bilingual labels, NO section headers, NO tables. At most ONE small relevant prop. Draw YC DIRECTLY on white paper — NO die-cut white outline around the character. Result = one small light watercolor-pencil drawing, plenty of white space. If you removed all text, the image should still make complete sense.
```

### Sticker 构思法
1. 一个 YC + 一个意思（一个表情 / 一个动作 / 和一个物件互动）。不讲流程、不分格。
2. 物件少而准：选**一个**和主题最相关的，其余全删。
3. 宁可不写字；要写就 1-3 个中文短词放角色旁空白处。
4. 留白是主角：画完先问"是不是太满"，太满就删元素，不是缩小。

**例**：「专注写作」→ YC 托腮看着合上的小笔记本，旁边一个小杯子，标注「专注」（或不标），纯白底，红发是唯一明显颜色，无装饰、大量留白。

### Sticker 封面版（文章封面 / 标题图）

封面 ≠ 海报，仍是贴纸逻辑：**一个 YC hero + 一行标题 + 白底**，标题是唯一允许的"多字"。常用 16:9 / 4:3。

```text
Using the attached sticker reference (00-reference-sheet-watercolor) for exact style, generate one standalone {16:9 / 4:3} cover image.

Style: loose watercolor colored-pencil hand-drawing, pure white background, single character, lots of empty white space — same sticker style as the reference.

Layout: ONE YC character (messy dark-red hair, clear-frame glasses, watercolor-pencil sketch) placed to one side OR centered, doing a single gesture related to the topic. A short Chinese title in clean hand-written style in the empty space beside YC.

Title text: 「{文章标题，≤10 字}」  （副标题可选，≤8 字）

Hard rules: pure white background. ONE character only. At most ONE small relevant prop. NO surrounding clutter, no sticky notes, no panels, no scattered decorations. The title is the only block of text. Keep ≥45% empty white space. A clean watercolor sticker with a title, NOT a busy poster.
```

---

## ✦ Simple 普通模式（仅多步流程）

多场景故事流：3-6 步串联讲清一个流程。温暖 chibi、适中文字。带 `assets/examples/simple/` 例图。

```text
Generate one standalone {比例} YC illustration in SIMPLE story-flow style.

Visual DNA:
Warm off-white / cream background. Hand-drawn illustration with multiple small scene vignettes showing a step-by-step flow. Each step has YC in a different action/state. Warm and personal but not information-overloaded. Connected by arrows or a visual flow path. Light decorative accents (small hearts, stars — sparingly).

IP Character (required):
{Simple 角色关键词}. YC appears in each step doing a different action.

Steps (3-6):
{步骤1} → {步骤2} → {步骤3} → ...

Labels per step (1-2 short bilingual labels each):
{步骤1标注 中文/EN} / {步骤2标注} / ...

Signature props (pick 2-3): {根据场景选}

Color: black line art, warm accents. Orange for flow arrows. Red/soft pink for emphasis. Blue for system/AI elements if needed.

Constraints:
Each step is a small vignette, not a bordered panel. Steps connected by arrows / flow path. No heavy card borders or section headers. Each label SHORT (2-6 chars). One bottom summary line OK. A warm visual story, not a textbook diagram.
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
