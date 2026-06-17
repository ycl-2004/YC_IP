# 生图提示词模板 — YC

每张图单独生成，根据内容替换变量。

**两种模式**：先确定用户要 Rich 还是 Simple，再选对应模板。未指定默认 Simple。

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

## ✦ Simple 模式模板（默认）

极简图说：一张图 = 一个画面 + 一个核心隐喻。让图本身说故事，文字只是点睛。

```text
Generate one standalone {比例} YC illustration in SIMPLE minimal style.

Visual DNA:
Warm off-white / cream background. Clean, minimal, hand-drawn illustration. ONE clear scene with generous white space. Very few text labels — the image tells the story, not the words. Cozy and personal but NOT information-dense. No multi-panel layouts, no section headers, no cards, no grids, no tables. Think: one beautiful sketch in a notebook page with tons of breathing room.

IP Character (required):
YC — chibi character with messy dark-red burgundy hair, round clear-frame glasses, big expressive anime eyes, small gentle face, chibi proportions (large head, small body, thin arms/legs), casual streetwear, small earring, silver chain necklace, white sneakers. YC performs ONE clear action that IS the core visual metaphor.

Scene:
{一个清晰的核心画面：YC 在做什么、核心视觉隐喻是什么}

Signature props (pick 1-2 only):
{根据场景选最核心的 1-2 个道具}

Labels (MAXIMUM 2-4 short labels, each 2-6 characters):
{极短标注1} / {极短标注2} / {可选极短标注3}

Color:
Black line art. One accent color only (orange for paths/flow, OR red for emphasis, OR blue for system/AI). Do not use all three.

Constraints:
MINIMAL TEXT — the image should be understandable even without reading any labels. YC must be the core action subject. At least 40% of the canvas should be empty white/cream space. No section headers, no title banners, no panels, no cards, no grids, no tables, no numbered lists. No multi-panel layout. ONE scene, ONE metaphor, ONE action. Should feel like a single thoughtful sketch, not an infographic page.
```

### Simple 模式的隐喻构思法

每次从内容重新发明一个视觉隐喻：

1. 把抽象概念换成一个物理动作：连接、攀爬、浇灌、拼图、开门、过桥、称重
2. 把系统/结构换成一个低科技物件：黑板、梯子、天平、种子、桥、门、容器
3. 让 YC 成为动作的执行者，不是旁观者

**例子：三角函数 Simple 版**
- YC 站在一个巨大的单位圆旁边，手指指向圆上的一个点
- 只标注 3 个词：sin / cos / θ
- 没有表格、没有多个 section、没有公式列表
- 图本身就是"YC 在探索单位圆"的画面

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
