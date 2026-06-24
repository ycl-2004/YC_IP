---
name: yc-ip
description: 生成 YC 风格的中文个人 IP 配图。调用本 skill、要求“用 YC 解释 X”或“做一张 X 的图”时，默认必须走本地 imagegen CLI/API 的 reference-locked edit 路线生成并交付图片，不能优先使用 prompt-only image_gen，也不能只输出分析、画面方案或生图 prompt；只有用户明确说只分析、只要 prompt、shot list 或不要生成时才停在文字。默认使用 Sample/Standard 成品风格：纯白底、YC 红发透明眼镜 chibi、手绘线条、中文短标注、中等信息密度。只有用户明确点名 Minimal/Sticker/贴图纸/贴纸/极简/最小贴纸时才启用 Minimal；只有明确点名 Rich、完整海报、IP 设定页或品牌全景时才启用 Rich。默认比例：文章 16:9 / 社媒 1:1。
---

# YC 个人 IP 配图

## 核心定位

用 YC 的视觉 IP 为任何内容生成配图。主题不限（AI/成长/音乐/设计/生活是常见场景，但讲数学、科学、历史、任何知识文章都适用）——只要是"YC 来给你解释"就行。

YC 角色：男性，深红凌乱短发 + 圆框透明眼镜 + chibi 比例。**红发和眼镜是识别命脉，必须有。**

## 反图表铁律 + 隐喻铁律（与交付物闸门并列最高优先级）

**永远不要画方框 + 箭头的论文式结构图 / 架构图 / PPT 信息图。** 哪怕用户明确说"结构图 / 架构图 / 解释图 / 流程图 / diagram",这都是**改写信号**,不是画框图信号：把抽象结构翻译成**一个 YC 正在亲手操作的手绘物理隐喻场景**。场景可以是装置、桥、路径、循环、桌面、保护伞、倾听记录、情绪转译等；不要默认每次都是机器、箱子或曲柄。

即使你没读 `concept-director.md`，生图前也必须在脑内走完这四步（它们是 concept-director 的精华，内联在此，防止浅读漏掉）：

1. **机制判断**：用一句"不是 A，而是 B"锁定这件事真正怎么工作。
2. **物理动词**：把认知动作(分类/匹配/预测/编码…)变成可被 YC 执行的可见动作(倒入/摇动/拉网/织/测试/盖戳…)。
3. **场景原型**：先读 `references/explanation-variation.md`，从工作台装置 / 桥 / 分拣 / 一源多出 / 循环 / 接力 / 桌面 / 保护 / 倾听 / 情绪转换 / 小胜利里选一个。只有主题真的需要内部转换时才用机器装置。
4. **单场景因果**：例子/起点 → YC 操作 → 可见变化或结构 → 新输入/回应/结果；不是四格漫画，也不是固定左中右机器流程。

抽象 / 知识 / 系统机制主题（如"什么是 Transformer / 注意力 / 机器学习"）**强制先读** `references/concept-director.md` 和 `references/explanation-variation.md` 再生图。

> 示例：用户要"Transformer 结构图" → 画一台 YC 正在操作的"注意力织机/装配机"：词元进来加位置刻度，YC 拉多根注意力线把相关词连起来，经前馈小工坊后吐出"下一个词"；只放 `词元`/`位置`/`注意力`/`前馈`/`输出` 这类 3-5 个短标注。**不是** encoder/decoder 方块 + 箭头。

**正式产物必须 reference-locked**：在 Codex 本地环境里，正式 YC 图片默认必须走 `imagegen` skill 的 CLI/API edit 路线，把本地 examples PNG 作为真实 input image 传入。当前聊天内置的 prompt-only `image_gen` 不能传 `image` / `reference_image` / `input_image`，只能作为 CLI/API 不可用时的 fallback 草稿；fallback 结果必须标记为 `style draft / 未 reference locked`，不得当作正式 YC locked asset。

## 交付物闸门（最高优先级）

本 skill 的默认交付物是**生成完成的图片**，不是文字解释、构图方案或最终 prompt。

- 用户调用本 skill，或说“用 YC 解释 X / 什么是 X / 做一张 X 的配图 / 跟这个风格一样”时：完成内部构思后，必须在同一轮使用本地 `imagegen` CLI/API 生成图片。
- 正式产物不得优先使用当前聊天内置的 prompt-only `image_gen`，因为它不能传入本地参考图。
- “概念解释、画面隐喻、短标注、最终 illustration prompt”都只是内部中间产物；不要把它们当作任务完成状态。
- 只有用户明确说“只分析 / 先分析 / 只要方案 / 只要 prompt / shot list / 不要生成图片”时，才输出文字并停止。
- 如果本地 CLI/API 不可用或调用失败，可以降级到 prompt-only `image_gen`，但必须明确说明失败原因，并把结果标记为 `style draft / 未 reference locked`；不要把 fallback 草稿当成正式交付图片。

**发送最终回复前强制检查**：用户是否明确要求只要文字？如果没有，当前轮是否已经成功走过 reference-locked CLI/API edit？若没有，只能生成 fallback 草稿并显式标记，或报告无法正式交付。

## Quick Intent Router（短 prompt 也要这样理解）

用户不需要写长 prompt。只要用户说“用这个 skill / 跟这个风格一样 / same style / 解释 X / 什么是 X”，默认就按 **Sample / Standard Broad Concept Explainer** 执行：

- 先把 X 压成一个核心隐喻，而不是百科页。
- 先选一个场景原型，不要自动套“左输入-中机器-右输出”。需要内部机制时才画装置；信任用桥，反馈用循环，协作用接力，专注用桌面/保护，情绪用转译。
- 画一个中心场景：具体起点、YC 的核心动作、可见变化或结构、最后的验证/回应/结果。
- 默认保留 3-5 个中文短标注，只标因果节点。
- 不要定义段落、分类列表、真实公司案例、底部总结条、section header 或教学卡片排版。
- 完成构思后立即调用本地 `imagegen` CLI/API edit；不要先把构思长篇输出给用户，也不要停在“最终提示词”。
- 只有用户明确说 Minimal / Sticker / 贴图纸 / 贴纸 / 极简时才变成 Minimal；只有明确说 Rich / 完整海报 / IP 设定页时才变成 Rich。

例：用户只说“跟这个 skill 一样的风格解释 machine learning”，也应生成：YC 把分好类的水果例子倒进手摇学习机，机器把可见特征织成规则网，再用一个新水果测试并输出“苹果？”预测。

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

**所有实际生图先读四个文件**（角色关键词已并进模板，别一次塞满上下文）：
- `references/prompt-template.md`：生图提示词模板（含三模式角色关键词、约束、参考图指令）
- `references/qa-checklist.md`：生成后检查
- `references/style-gate.md`：实际生成时必读；规定 reference-locked CLI/API 路径、canonical reference、preflight、失败条件和自动重试
- `references/reference-routing.md`：按主题、比例与情绪扫描真实 examples 并选择 primary reference；它是 reference 选择的唯一来源
- `references/concept-director.md`：解释抽象概念、方法或系统机制时必读；先完成视觉推理，再写生图 prompt
- `references/explanation-variation.md`：解释类图片的场景原型库；用于避免固定机器/箱子流程，先选原型再写 prompt

按需再读：
- `references/style-dna.md`：三模式画风细节、色板、禁忌（拿不准画风时）
- `references/yc-character.md`：服装/道具库、表情库（要换装或定姿势时）
- `references/yc-brand-identity.md`：5大内容支柱、性格、价值观（讲品牌/自我介绍时）
- `references/composition-patterns.md`：Rich 的 IP 设定页、品牌全景、完整海报布局

> Minimal 和 Rich 仅在用户明确点名时才进入对应流程；默认流程不要读 Rich 布局，也不要自动降到 Minimal。

## 工作流

### 1. 消化内容

读用户给的内容，提炼核心观点和"认知锚点"（核心判断/转折/对比/闭环）。**不要每段都配图**——只给锚点配，够用就好，别做成画册。文章默认 3-6 张；单条社媒 1-2 张。

如果用户问的是“什么是 X / explain X / 解释某个大概念”，默认不要做百科课件或整页教学卡片。读取 `references/concept-director.md` 和 `references/explanation-variation.md`，先写出“不是 A，而是 B”的机制判断，再选择最贴切的场景原型，把认知动作变成 YC 可执行的物理动作。只讲这个概念最重要的一层，但要画完整因果：**具体起点 → YC 操作 → 可见变化/结构 → 验证/回应/结果**。这个因果可以发生在桥、循环、桌面、保护、倾听、情绪转换等场景中，不必每次都是机器。

不要把“一个核心隐喻”误解成只有三个泛化节点。Sample 默认可包含 1 个主场景物件或场景锚点、2-3 个具体样本/声音/干扰/证据、1 个可见变化或中间结构、1 个验证结果和 3-5 个中文短标注；增加语义细节，不增加装饰、面板或长文。

### 2. 先出配图策略（仅限用户明确要求只分析时）

只有用户明确说“只分析 / 先分析 / 只要方案 / 只要 prompt / shot list / 不要生成”时才停在这里。每张写：放在哪段后、主题+核心意思、用哪个模式、YC 在做什么、建议比例、建议元素和标注词。简短即可。

### 3. 单张生成（reference-locked CLI/API）

除非用户明确要求只要文字，否则用本地 `imagegen` CLI/API **每张单独生成**，不要拼一起。调用 skill、说“解释 X / 什么是 X / 跟这个风格一样”本身就视为生成意图，不需要用户再次说“生成”。纯文字 prompt 会跑成海报，每张正式产物都必须把参考图作为 `edit --image` 的真实输入。

正式 YC 图片默认命令形态：

```bash
python /Users/yichenlin/.codex/skills/imagegen/scripts/image_gen.py edit \
  --image <blank-canvas.png> \
  --image <canonical-reference.png> \
  --prompt-file <prompt.txt> \
  --size <1536x1024|1024x1024|1024x1536> \
  --quality high \
  --input-fidelity high \
  --out "/Users/yichenlin/Desktop/AI Agent/Personal IP/YC_Img_Out/YYYY-MM-DD-<content-slug>-<topic-name>.png"
```

`<blank-canvas.png>` 是纯白输出画布，只用来承载新画面；`<canonical-reference.png>` 才是风格/IP reference。不要只把参考图当第一张 input，否则模型容易复制旧图构图。空白画布可用任意本地图片工具生成，尺寸必须和目标 `--size` 一致。

参考图选择：先读取 `references/reference-routing.md` 与 `assets/examples/README.md`，扫描真实 examples 后按主题、比例与情绪选一张 primary reference。`07-noise-filter.png` 仅在没有更贴切主题 reference 时作为单角色机制图 fallback，不得作为通用默认。角色连续两次识别失败时，才可额外加入一张 `assets/examples/character-reference/`；必须声明不得复制九宫格或多角色。

每张提示词必含：明确比例 + YC 关键词（红发 + 透明眼镜 + chibi）+ 模式画风要点 + `style-gate.md` 的全部 Sample preflight 约束。参考图必须出现在 CLI/API 的 `--image` / input_images 里，不能只在 prompt 里声称“attached”。

`assets/examples/` 只校准画风+角色，**不照抄构图**——每次从当前内容重新想画面。

Sample 的方法类图要把“方法”变成画面里的场景物件或情境动作：压缩机、桥、分拣台、传送带、输出装置、过滤器、反馈回路、桌面专注角落、保护伞、倾听笔记、音乐转译等。YC 必须正在操作这个物件或参与核心动作。不要画成 PPT 线框图，不要把 YC 当贴纸贴在流程图旁边，不要让角色周围出现白色矩形边框。

知识解释图也按 Sample 处理：例如“什么是 Machine Learning”不要只画“数据 → 机器 → 预测”。应画 YC 把分好类的水果例子倒进手摇学习机，机器把颜色/形状/纹理织成可见的规则网，再让一个没有标签的新水果落入网中，输出“苹果？”预测；默认 3-5 个中文短标注。不要生成包含大标题、定义段落、类型列表、真实公司例子和总结条的 textbook infographic。

### 4. 检查与迭代

先过 `style-gate.md` 的视觉 Pass / Fail，再过 `qa-checklist.md`。Sample 出现任一硬失败信号时，不交付，自动重生成，最多 2 次。常见问题：
- YC 没红发/眼镜 → 角色失败，重生成
- Sample：背景不是纯白、方法没有变成场景物件、YC 没参与核心动作、太像 PPT/信息图 → 重生成或补回
- Minimal：只有显式点名才可用；若没点名却生成得过轻，升回 Sample
- Rich：只有显式点名才可用；若用户没点名却生成了 Rich，降级到 Sample
- 拿不准回看对应模式例图对齐

### 5. 保存

所有最终 YC 图片统一保存到：

```
/Users/yichenlin/Desktop/AI Agent/Personal IP/YC_Img_Out/YYYY-MM-DD-<content-slug>-<topic-name>.png
```

本地 CLI/API 生成时直接把这个路径传给 `--out`。如果图像工具先写入自身默认 generated-images 目录，必须在交付前把完成的 PNG 原样复制到 `YC_Img_Out/`，并把副本作为唯一 final output path 报告；不得把工具临时路径当作最终交付路径。

## 输出口径

默认先生成再交付。策略输出仅用于用户明确要求的只分析模式。图片生成成功后，交付含：生成张数、每张用途、保存路径、哪张最稳；不要再附上大段概念分析或完整 prompt，让图说话。

正式交付前必须报告生成闸门四项：

- `mode`: Sample / Standard、Minimal / Sticker、Rich 中的实际模式
- `reference_image`: 实际传入 CLI/API 的参考图路径
- `generation_route`: `API edit` / `prompt-only fallback`
- `output_path`: 最终图片路径

如果 `generation_route = prompt-only fallback`，必须标记为 `style draft / 未 reference locked`，不算正式 YC locked asset。
