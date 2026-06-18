---
name: YC_IP
description: 生成 YC 风格的中文个人 IP 配图。默认使用 Sample/Standard 成品风格，对齐 assets/examples/simple/current-showcase/ 和 README examples/images：纯白底、YC 红发透明眼镜 chibi、手绘线条、中文短标注、中等信息密度。只有用户明确点名 Minimal/Sticker/贴图纸/贴纸/极简/最小贴纸时才启用 Minimal 贴纸模式；只有明确点名 Rich、完整海报、IP 设定页或品牌全景时才启用 Rich 丰富模式。用于文章正文配图、文章封面/标题、社媒单图、知识讲解、自我介绍等。默认比例：文章 16:9 / 社媒 1:1；其余比例仅在用户点名时使用。
---

# YC 个人 IP 配图

## 核心定位

用 YC 的视觉 IP 为任何内容生成配图。主题不限（AI/成长/音乐/设计/生活是常见场景，但讲数学、科学、历史、任何知识文章都适用）——只要是"YC 来给你解释"就行。

YC 角色：深红凌乱短发 + 圆框透明眼镜 + chibi 比例。**红发和眼镜是识别命脉，必须有。**

## Quick Intent Router（短 prompt 也要这样理解）

用户不需要写长 prompt。只要用户说“用这个 skill / 跟这个风格一样 / same style / 解释 X / 什么是 X”，默认就按 **Sample / Standard Broad Concept Explainer** 执行：

- 先把 X 压成一个核心隐喻，而不是百科页。
- 画一个中心场景：左边输入材料，中间 YC 操作/学习/处理，右边输出结果。
- 只保留 3-4 个中文短标注。
- 不要定义段落、分类列表、真实公司案例、底部总结条、section header 或教学卡片排版。
- 只有用户明确说 Minimal / Sticker / 贴图纸 / 贴纸 / 极简时才变成 Minimal；只有明确说 Rich / 完整海报 / IP 设定页时才变成 Rich。

例：用户只说“跟这个 skill 一样的风格解释 machine learning”，也应生成：YC 把许多“数据”卡片放进“学习机器”，机器找规律，输出“预测”卡片。

## 三种模式（默认 Sample / Standard）

默认密度 = **Sample / Standard**。不指定模式时，所有普通文章配图、知识讲解、社媒单图、封面/标题图都先对齐 `assets/examples/simple/current-showcase/` 和 README `examples/images/` 的成品风格：纯白底、手绘线条、YC 参与核心动作、中文短标注、中等信息密度。

**最极简和最多信息都需要显式点名**：用户明确说 Minimal / Sticker / 贴图纸 / 贴纸 / 极简 / 最小贴纸，才启用 Minimal；用户明确说 Rich / 完整海报 / IP 设定页 / 品牌全景，才启用 Rich。

| | Minimal / Sticker（仅显式点名） | Sample / Standard（默认） | Rich 丰富（仅显式点名） |
|---|---|---|---|
| 画风 | 水彩铅笔轻涂松手绘（非全彩 anime，非黑线稿） | 当前 samples 的温暖手绘 chibi 插画 | 满版 editorial / IP 设定页 |
| 背景 | **纯白 #FFFFFF**，无纹理 | **纯白 #FFFFFF**，只允许轻接触阴影 | 奶油白，信息密度更高 |
| 主体 | 单角色 + 一个动作/物件 | 单场景隐喻或紧凑流程，YC 参与核心动作 | 多区块、多场景、完整视觉体系 |
| 文字 | 0-3 个中文短词（能不写就不写） | 中文短标注，克制但能解释清楚 | 中英混排，多标注，但仍要克制 |
| 信息密度 | 极低，巨量留白 | 中：一张图讲清一个核心意思 | 高：整页成品 |
| 适合 | 用户明确要求极简、轻贴纸、最小表达 | 默认文章配图、封面/标题、社媒单图、知识讲解、流程/对比 | 用户明确要求 Rich、完整海报、IP 自我介绍、品牌全景、整页设定图 |

**怎么选**：
- 用户没指定密度 → **Sample / Standard**
- 用户明确说 Minimal / Sticker / 贴图纸 / 贴纸 / 极简 / 最小贴纸 → **Minimal**
- 用户明确说 Rich / 完整海报 / IP 设定页 / 品牌全景 / 整页成品 → **Rich**

> ⚠️ Minimal 和 Rich 都不参与自动判断。普通文章、正文配图、社媒单图和封面图默认走 Sample / Standard。模型容易跑成"全彩 anime + 满版拼贴"= 海报，三档都必须主动压制：白底、手绘线条、YC 参与核心动作、中文标注克制、**带参考图**。

## 比例

默认：**文章配图 `16:9`，社媒单图 `1:1`**。其余（`9:16` `4:3` `3:2` `2:3` `5:4` `21:9`）只在用户明确点名时用，不要每次都让用户选。

## 先读这些参考

**默认 Sample 路径只需两个文件**（角色关键词已并进模板，别一次塞满上下文）：
- `references/prompt-template.md`：生图提示词模板（含三模式角色关键词、约束、参考图指令）
- `references/qa-checklist.md`：生成后检查

按需再读：
- `references/style-dna.md`：三模式画风细节、色板、禁忌（拿不准画风时）
- `references/yc-character.md`：服装/道具库、表情库（要换装或定姿势时）
- `references/yc-brand-identity.md`：5大内容支柱、性格、价值观（讲品牌/自我介绍时）
- `references/composition-patterns.md`：Rich 的 IP 设定页、品牌全景、完整海报布局

> Minimal 和 Rich 仅在用户明确点名时才进入对应流程；默认流程不要读 Rich 布局，也不要自动降到 Minimal。

## 工作流

### 1. 消化内容

读用户给的内容，提炼核心观点和"认知锚点"（核心判断/转折/对比/闭环）。**不要每段都配图**——只给锚点配，够用就好，别做成画册。文章默认 3-6 张；单条社媒 1-2 张。

如果用户问的是“什么是 X / explain X / 解释某个大概念”，默认不要做百科课件或整页教学卡片。先压成一个核心隐喻：输入什么、YC 怎么操作、输出什么。只讲这个概念最重要的一层，不要同时塞定义、分类、流程、例子和总结。

### 2. 先出配图策略（用户说"分析/shot list/帮我想"时）

每张写：放在哪段后、主题+核心意思、用哪个模式、YC 在做什么、建议比例、建议元素和标注词。简短即可。

### 3. 单张生成（必须带参考图）

用户说"生成/出图/帮我做"时，用 `image_gen` **每张单独生成**，不要拼一起。纯文字 prompt 会跑成海报，每张都附参考图：

- Sample / Standard → 优先看 `assets/examples/simple/current-showcase/`；方法类图可额外参考 `08-idea-press-machine.png`、`09-trust-bridge.png`、`10-purpose-sort-machine.png`、`11-one-source-many-outputs.png`
- Minimal / Sticker → 仅用户显式点名时，固定带 `assets/examples/sticker/00-reference-sheet-watercolor.png`（canonical 画风锁）；长相不稳再加 character-reference
- Cover → `assets/examples/cover/01-sticker-cover-tiny-win.png` 可作 16:9 封面版布局/密度参考，但默认仍保持 Sample 风格，不自动变 Rich
- Social → `assets/examples/social/01-social-1x1-tiny-win.png` 可作 1:1 社媒单图布局/密度参考
- Rich → `assets/examples/rich/`（仅用户显式点名 Rich 时）
- 角色长相不稳时额外加 `assets/examples/character-reference/`

每张提示词必含：明确比例 + YC 关键词（红发 + 透明眼镜 + chibi）+ 模式画风要点。第一次仍偏属正常，带参考图重生一次即对。

`assets/examples/` 只校准画风+角色，**不照抄构图**——每次从当前内容重新想画面。

Sample 的方法类图要把“方法”变成画面里的场景物件：压缩机、桥、分拣机、传送带、输出装置、过滤器等。YC 必须正在操作这个物件或参与核心动作。不要画成 PPT 线框图，不要把 YC 当贴纸贴在流程图旁边，不要让角色周围出现白色矩形边框。

知识解释图也按 Sample 处理：例如“什么是 Machine Learning”应画成 YC 把一堆数据卡片喂进学习机器，机器根据模式吐出预测卡片；最多 3-4 个中文短标注。不要生成包含大标题、定义段落、类型列表、真实公司例子和总结条的 textbook infographic。

### 4. 检查与迭代

过 `qa-checklist.md`。常见问题：
- YC 没红发/眼镜 → 角色失败，重生成
- Sample：背景不是纯白、方法没有变成场景物件、YC 没参与核心动作、太像 PPT/信息图 → 重生成或补回
- Minimal：只有显式点名才可用；若没点名却生成得过轻，升回 Sample
- Rich：只有显式点名才可用；若用户没点名却生成了 Rich，降级到 Sample
- 拿不准回看对应模式例图对齐

### 5. 保存

```
assets/<content-slug>/01-topic-name.png
```

## 输出口径

策略输出简洁。交付含：生成张数、每张用途、保存路径、哪张最稳。不解释风格理论，让图说话。
