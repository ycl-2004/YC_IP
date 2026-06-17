# 生图提示词模板 — YC

每张图单独生成，根据内容替换变量。

**三种模式**：先确定用户要 Rich / Simple / Minimal，再选对应模板。未指定默认 Simple。

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

## ✦ Minimal 极简模式

极致干净。纯白底 + YC + 一个核心隐喻 + 最多 2-5 个词。图本身就是全部内容。

```text
Generate one standalone {比例} illustration in MINIMAL ultra-clean style.

Visual DNA:
PURE WHITE background — no cream, no texture, no paper grain, no warmth tint. Black hand-drawn line art with slightly wobbly pen lines. Massive white space — at least 50% of canvas is completely empty. ONE visual metaphor, ONE flow, ONE action. The drawing itself explains the idea — text is almost unnecessary.

IP Character (required):
YC — chibi character with messy dark-red burgundy hair, round clear-frame glasses, big expressive anime eyes, chibi proportions. Drawn in simple black line art style (not full-color detailed illustration). YC performs the ONE core action that IS the metaphor. YC should feel like a quick but expressive sketch, not a polished anime character.

Scene:
{一个核心隐喻画面：YC 和什么物件在做什么动作}

Labels (STRICT MAXIMUM 2-5 short words, Chinese only):
{极短词1} / {极短词2} / {可选词3}

Color:
Black line art for everything. ONLY ONE accent color — orange for directional arrows/flow, OR red for key emphasis. No blue. No pink. No hearts. No sparkles. No decorative elements.

Constraints:
PURE WHITE background — this is the #1 rule. No cream, no off-white. Drawing style is loose hand-sketch, NOT polished anime illustration. No section headers. No English text. No title banners. No panels. No frames. No tables. No numbered steps. No signature props (no MacBook, no smiley mug — unless they ARE the metaphor). No decorative hearts/stars/sparkles. The image should look like someone quickly sketched an idea on blank white paper to explain ONE thing. Maximum 2-5 Chinese words total on the entire image. If you remove ALL text, the image should still make complete sense.
```

### Minimal 模式的隐喻构思法

每次从内容重新发明一个视觉隐喻：

1. 把抽象概念换成一个物理动作：搬运、卡住、漏掉、变重、过滤、连接、断开
2. 把系统/结构换成一个低科技物件：传送带、纸箱、漏斗、秤、梯子、井、门、桥
3. 让 YC 成为动作的执行者 — 拉、扛、塞、撑、推、接、拆

**例子：学习流程 Minimal 版**
- 画面：YC 站在一条简单的传送带旁边，左边是散乱的纸片（输入），YC 在中间把纸片压进一个小盒子里（消化），右边盒子里整齐放着几本小册子（输出）
- 只标注：「输入」→「消化」→「输出」
- 纯白底，黑色线稿，橙色箭头表示方向
- 没有步骤编号，没有装饰，没有 section

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
