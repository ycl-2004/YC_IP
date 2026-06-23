# YC_IP Illustrations

> 用 YC 的 IP 角色为任何内容生成配图。默认对齐当前 examples/images 的 Sample 成品风格；只有明确点名 Minimal / Sticker / 贴图纸 / 贴纸 / 极简时才做最小贴纸，只有明确点名 Rich 时才做完整海报 / IP 设定页。
>
> 三种模式（Sample / Minimal / Rich）| 多比例支持 | YC chibi 角色（红发透明眼镜）| 必带参考图工作流 | Codex Skill

---

## ⚠️ 最高优先级铁律（先读这一段）

无论用户怎么措辞——哪怕明确说"**结构图 / 架构图 / 解释图 / 流程图 / diagram**"——本 skill 永远**不画方框 + 箭头的论文式结构图**。必须把抽象结构**重新翻译成一个 YC 正在亲手操作的手绘场景/低科技装置**：把概念变成机器、织机、桥、分拣台、传送带、过滤器等,YC 转动曲柄 / 拉网 / 测试新输入,信息沿一条主流向走完"例子 → YC 操作 → 可见中间结构 → 新输入 → 具体判断"。

- 看到"结构图/架构图"= 触发**改写**,不是触发画框图。先在脑内完成 [`yc-ip/references/concept-director.md`](yc-ip/references/concept-director.md) 的"不是 A,而是 B"机制判断 + 物理动词 + 低科技装置,再生图。**抽象/知识主题强制先读 concept-director。**
- 纯白底、单个 YC(红发 + 透明圆框眼镜)、温暖手绘、3-5 个中文短标注、大量留白。
- 标志性失败信号(出现即重画):方框 + 箭头的架构图、encoder/decoder 方块、PPT 信息图、多面板、顶部大标题、定义段落、底部总结条、深色/霓虹背景、两个以上 YC。
- 每次先扫描 `yc-ip/assets/examples/`，按 topic、比例、情绪和信息密度选择真实 primary reference；它只锁定画面语言，不复制构图。`07-noise-filter.png` 是单角色机制图 fallback，不是固定默认。正式产物必须把选中的 asset 作为真实 image input。

> 一句话:用户要的"Transformer 结构图"= 一台 YC 正在操作的"注意力织机/装配机",不是论文里的方框图。

---

## 这个仓库是什么

YC_IP Illustrations 是一个 Codex Skill，用来指导 AI Agent 用 YC 的固定 IP 角色生成个人品牌配图。

它不是通用插画 prompt，也不是 PPT 模板。核心目标是：把任何内容（YC 的5大主题方向，或任意知识主题）用 YC 的视觉风格和角色呈现出来，生成一张有 YC 品牌识别度的图。

默认视觉 IP 是「YC」：一个红发蓬松、戴透明圆框眼镜、chibi 比例的年轻人角色。YC 不是吉祥物，不是装饰，而是正在认真探索世界、build 东西、创作音乐、持续学习的真实年轻人缩影。

一句话：**让每一张图都有 YC 的识别度，让内容和角色浑然一体。**

---

## 最短用法规则

用户不需要写长 prompt。只要说：

```text
用这个 skill 的风格解释 Machine Learning
```

默认就应该生成 **Sample / Standard Broad Concept Explainer**：

- 不是百科信息图，不是课程卡片，不是 PPT。
- 只画一个连续场景：具体例子 → 一个 YC 操作 → 可见中间结构 → 新输入 → 具体判断。
- 只保留 3-5 个中文短标注；解释句只用于内部构思，不写进图里。
- 不要定义段落、分类列表、真实公司案例、底部总结条、section header。
- 必须实际调用图像工具并附 canonical Sample 参考图；不能停在分析或 final prompt。
- 只有明确说“贴图纸 / 贴纸 / Sticker / Minimal / 极简”才做 Minimal。
- 只有明确说“Rich / 完整海报 / IP 设定页 / 品牌全景”才做 Rich。

例：解释 Machine Learning 时，画一个 YC 把分好类的水果例子倒进手摇学习机，机器把特征织成规则网，再用一个新水果测试并输出“苹果？”预测。

---

## 三种输出模式（核心）

这个 skill 不是单一风格，而是一个**从轻到重的密度光谱**。默认走当前 samples 的中等密度，避免平时输出太轻，也避免做成满版海报。

默认模式是 **Sample / Standard**：对齐 `examples/images` 和 `yc-ip/assets/examples/simple/current-showcase/` 的成品风格，适合日常文章配图、社媒单图、标题图、知识讲解和方法类图。Minimal 和 Rich 都不自动启用，只有用户明确说“Minimal / Sticker / 贴图纸 / 贴纸 / 极简 / 最小贴纸”或“Rich / 完整海报 / IP 设定页 / 品牌全景”才启动。

| | Minimal / Sticker（仅显式点名） | Sample / Standard（默认） | Rich 丰富（仅显式点名） |
|---|---|---|---|
| **样子** | 白底水彩铅笔小贴纸，单角色 | 当前 examples/images 的成品图 | 满版 editorial，多面板 |
| **画风** | 水彩铅笔轻涂松手绘 | 温暖手绘 chibi 插画 | 精致 editorial 插画 |
| **背景** | 纯白 | 纯白 | 奶油白 |
| **文字** | 0-3 个中文短词 | 中文短标注，中等密度 | 中英混排，多标注 |
| **何时用** | 仅显式点名：贴图纸、贴纸、极简、minimum | 默认：文章正文配图、社媒单图、封面/标题、流程、知识讲解 | 仅显式点名：完整海报、IP 自我介绍、品牌全景、整页设定图 |

**模式口诀**：

- 用户没指定 → **Sample / Standard**
- 用户明确说 **Minimal / Sticker / 贴图纸 / 贴纸 / 极简 / 最小贴纸** → Minimal
- 用户明确说 **Rich / 完整海报 / IP 设定页 / 品牌全景** → Rich

> **Minimal 和 Rich 都是显式模式，不参与自动判断。** 日常文章、正文配图、社媒和封面默认都走 Sample / Standard。

想手动指定时直接说模式词即可：「用 minimal/sticker 画…」「默认 sample 风格…」「来个 rich 的 IP 介绍」。

---

## 生图必须带参考图（最重要的稳定性技巧）

纯文字 prompt 不稳，模型会回退到"精致全彩 anime + 满版拼贴"的海报先验。**每次生图都附一张参考图。**

参考图同时锁三件事：**①YC 长相 ②画风渲染 ③信息密度**。

- Sample / Standard → 先按 `yc-ip/references/reference-routing.md` 扫描并选择 topic-matched primary reference；`07-noise-filter.png` 只在没有更贴切主题图时作为单角色机制图 fallback。
- Minimal / Sticker 模式 → 固定附 `yc-ip/assets/examples/sticker/00-reference-sheet-watercolor.png` 作为 canonical 画风锁；动作图只作构思参考。
- Rich 模式 → 仅用户显式点名时，附 `yc-ip/assets/examples/rich/` 里最接近的整页例图。
- 只想锁角色长相 → 附 `character-reference/` 里的九宫格（注意：九宫格是全彩，只能锁长相、锁不了水彩画风）。

Broad Concept 不要使用 `05-concept-explainer.png`、多角色图、Rich 图或九宫格作为默认参考。第一次仍可能偏；如果出现深色背景、霓虹、多 YC、标题段、面板、UI 或底部总结条，直接判失败并用 canonical 参考重生成，最多自动重试两次。

---

## 适合什么场景

**最适合：**

- 为 YC 的原创文章、知识帖、小红书/B站内容生成干净的正文配图与封面
- 想要统一视觉风格、固定 IP 角色的个人品牌内容创作者
- 需要多比例配图（16:9 文章 / 1:1 社媒 / 9:16 竖版 Story 等）
- 想要统一、留白干净、像当前 examples 那样的手绘个人 IP 配图（而不是信息塞满的海报）

**不适合：**

- 想要商业品牌 KV 或精修商业插画的人
- 想要严格可编辑矢量源文件的人
- 想要大量文字塞满画面的信息图的人

---

## 它会产出什么

- 指定比例的 YC IP 配图（支持 8 种比例）
- 文章/内容的 shot list（每张图的主题、模式、YC 动作、标注建议）
- 最终 PNG，统一保存到 `/Users/yichenlin/Desktop/AI Agent/Personal IP/YC_Img_Out/`

**支持的图片比例：**

| 比例 | 用途 |
|------|------|
| `16:9` | 文章配图、博客 banner、B站封面 |
| `1:1` | Instagram、小红书方图、通用社媒 |
| `9:16` | Story、抖音竖版、朋友圈竖图 |
| `4:3` | 传统横版、部分平台帖子 |
| `3:2` | 横版照片风格、博客图 |
| `2:3` | Pinterest、竖版海报 |
| `5:4` | 微博/部分平台方形偏横 |
| `21:9` | 超宽 banner、网站 header |

**不输出：** PPTX / PDF / 可编辑源文件、商业插画 KV、无 YC 角色的通用插画。

---

## 示例效果

这组是当前默认 Sample 成品样例：方法不是旁边的流程线，而是被画成 YC 正在操作的真实场景物件。安装后的 skill 内部也同步了一份到 `yc-ip/assets/examples/simple/current-showcase/`，作为最终成品风格基准。

### 找回上下文
![找回上下文](examples/images/01-context-back.png)

### 信任桥
![信任桥](examples/images/02-trust-bridge.png)

### 按用途分拣
![按用途分拣](examples/images/03-purpose-sort.png)

### 一份素材，多种表达
![一份素材，多种表达](examples/images/04-one-source-many-outputs.png)

这些图片是成品展示样例。使用时优先学习它们的处理方式：YC 参与核心动作，方法变成桥、机器、分拣装置或输出装置；不要做成 PPT 流程图，也不要把角色贴在白色小方块里。

### 封面版
![封面版](yc-ip/assets/examples/cover/01-sticker-cover-tiny-win.png)

### 社媒 1:1
![社媒 1:1](yc-ip/assets/examples/social/01-social-1x1-tiny-win.png)

---

## 安装

```bash
git clone https://github.com/<your-github>/YC_IP.git
cd YC_IP
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R ./yc-ip "${CODEX_HOME:-$HOME/.codex}/skills/"
```

安装后，在 Codex 里使用：

```text
Use $yc-ip 为这篇内容生成 YC 风格配图。
```

如果你的客户端支持 slash skill，也可以直接呼叫 `/yc-ip`。

---

## 怎么用

### 配图策略（先不生图）

```text
Use $yc-ip 先不要生图。
分析下面这篇文章哪里值得配图，输出 shot list。
每张图写清楚：段落位置、主题、核心意思、用哪个模式、YC 在做什么、建议比例、建议标注词。

<粘贴文章>
```

### 文章正文配图（默认 Sample）

```text
Use $yc-ip 为下面这篇文章配几张图（默认 Sample 风格，对齐当前 examples）。

<粘贴文章>
```

### 单个概念 / 情绪（默认 Sample）

```text
Use $yc-ip 画一张 1:1 图，主题「专注写作」，YC 正在把注意力收回到笔记本上。
```

### Minimal / Sticker 极简图（显式点名）

```text
Use $yc-ip 明确使用 Minimal / Sticker，画一张「专注写作」的极简贴纸图，1:1。
```

### 文章封面 / 标题图（默认 Sample 封面版）

```text
Use $yc-ip 给这篇文章做个 16:9 封面，标题「我是怎么搭出个人 IP 的」。
一个 YC hero + 一行标题 + 白底，干净不堆元素。
```

### 流程 / 步骤（默认 Sample）

```text
Use $yc-ip 把这个学习方法画成 16:9 场景图：把方法变成可操作的物件，YC 正在里面操作，纯白背景，对齐当前 examples。
```

### IP 自我介绍（Rich）

```text
Use $yc-ip 生成一张 16:9 的 YC IP 介绍图，展示 YC 是谁、关注什么、在做什么。明确使用 Rich 模式。
```

更多示例见 [examples/prompts.md](examples/prompts.md)。

---

## 工作流程

1. 读取用户给的内容（文章/帖子/想法/知识主题）
2. 先提"认知锚点"——只给核心判断/转折/对比/闭环配图，够用就好，不做画册
3. 默认使用 Sample / Standard；Minimal 和 Rich 只有用户明确点名才启用
4. 读取 `yc-ip/references/reference-routing.md`，扫描 examples 后取 topic-matched primary reference；`07-noise-filter.png` 仅作 fallback
5. 每张图单独调用图像模型生成（带参考图）
6. 先过 `references/style-gate.md`：白底、一个 YC、单场景、无海报/UI/长文；失败自动重生成。再做角色和密度 QA
7. 保存 PNG 到 `/Users/yichenlin/Desktop/AI Agent/Personal IP/YC_Img_Out/`，报告用途、模式和最终路径

---

## 目录结构

```text
.
├── README.md
├── LICENSE
├── examples/
│   ├── images/                  # README 成品展示图
│   └── prompts.md               # 更多使用示例
└── yc-ip/                       # Codex Skill 主体（需要安装的就是这个）
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    ├── assets/
    │   └── examples/            # 风格校准 + 参考图，按模式分文件夹
    │       ├── sticker/         # Minimal/贴图纸：白底水彩贴纸（含动作 + 穿搭变体）
    │       ├── simple/          # 多步场景流 / 干净标题图
    │       │   └── current-showcase/  # 当前 examples/images 成品风格基准
    │       ├── cover/           # 16:9 Sample 封面版样例
    │       ├── social/          # 1:1 社媒单图样例
    │       ├── rich/            # 满版 editorial（IP/品牌）
    │       └── character-reference/  # 九宫格：锁角色长相 + 姿势库（浏览挑姿势）
    └── references/
        ├── style-dna.md         # 三模式风格 DNA、防海报护栏
        ├── style-gate.md        # 生图前后硬闸门、canonical 参考与失败重试
        ├── yc-character.md      # YC 角色外形、服装、生图关键词（含贴图轻渲染版）
        ├── yc-brand-identity.md # 5大内容支柱、人设、signature quotes
        ├── composition-patterns.md
        ├── prompt-template.md   # 三模式 prompt + 封面版 + 参考图工作流
        └── qa-checklist.md      # 按模式的生成后检查
```

---

## 注意事项

- YC 必须有**红发**和**透明圆框眼镜**，缺一不可，否则角色识别失败需重生成
- **每次生图都带参考图**，这是稳定性的关键
- 每张图都先选 topic-matched primary reference；`07-noise-filter.png` 仅在没有更贴切主题图时作为机制图 fallback。九宫格只在角色连续两次漂移时作为第二张修复参考
- Sample 的 style gate 是硬标准：纯白底、一个 YC、一个连续场景、无标题段/面板/UI/底部总结条；失败不交付
- 一张图只讲一件事，宁可多出几张轻图，也不要一张塞满
- 背景按模式：**Minimal / Sample 都用纯白**；Rich 才允许奶油白或轻纸感。别套错（文章配图一旦变成整张暖色纸底，会显得不够干净）
- **Rich 必须显式点名才启用**；普通文章封面、正文配图、社媒图不要自动升级到 Rich
- `assets/examples/` 只用来锁画风和角色，不要照抄具体构图
- AI 图像模型可能出现角色漂移（发色不对/眼镜丢失），生成后需检查
- 中文标注越短越稳定

---

## 关于 YC

**YC (Yichen)** — AI Builder / Music Creator / Always Learning

用创意和技术 build 有意思的东西。

- 内容方向：AI 工具 × 个人成长 × 音乐创作 × 设计创意 × 留学生活
- 平台：小红书 / B站 / YouTube / Instagram
- Motto：认真生活，浪漫创作。♥

---

## License

MIT License. See [LICENSE](LICENSE).
