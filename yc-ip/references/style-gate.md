# Style Gate：生成前后硬闸门

所有实际生图任务都先确认模式。本文件的严格单角色/单场景 gate 适用于默认 **Sample / Standard Broad Concept Explainer** 和普通单场景方法图；用户明确要求 Legacy Story-flow、Minimal 或 Rich 时，改用对应模式的构图规则，但仍必须保持该模式的背景、角色和渲染风格。风格优先级高于内容细节：

1. YC 角色识别与 Sample 画风
2. 纯白背景与单场景构图
3. 核心机制的因果可读性
4. 次要信息和装饰

如果内容细节与风格冲突，删内容，不牺牲风格。

## Sample Broad Concept Canonical Reference

Broad Concept Explainer 和普通 Sample 方法图默认只附这一张风格锁：

`assets/examples/simple/current-showcase/07-noise-filter.png`

它负责锁定：纯白背景、单个 YC、温暖铅笔手绘、轻上色、一个核心动作、少量中文标注和足够留白。

**不要**把以下图片用于 Broad Concept 的生图参考：

- `05-concept-explainer.png`：多个 YC 和分步场景会诱导模型复制成流程拼贴。
- `09-human-ai-relay.png` 或其他多角色/多场景图：会诱导重复角色。
- `character-reference/` 九宫格：全彩 anime 和网格构图会污染 Sample 画风；仅在角色长相严重漂移时作为第二张参考，并再次强调不得复制网格。
- `rich/`、封面或社媒参考：不属于正文概念图。

每次只附一张 canonical reference。只有角色连续两次识别失败，才允许追加一张 character reference。

## Sample Broad Concept 生图前 Preflight

调用 `image_gen` 前必须确认最终 prompt 同时包含：

- `PURE WHITE #FFFFFF background across the entire canvas`
- `ONE YC character only`
- `one continuous hand-drawn scene, no panels`
- `warm pencil-like sketch lines, light low-saturation coloring`
- `no dark background, no black background, no neon, no glow`
- `no title, no paragraph, no definition, no summary strip`
- `no cards grid, no numbered steps, no UI screens, no photoreal images`
- `render only the listed short Chinese labels; never render the explanatory brief`
- canonical reference 的具体路径已经传给图像工具，而不是只在文字里说“using attached reference”

Broad Concept 额外确认：

- 一个 YC 正在操作一件主装置。
- 2-3 组样本用小型手绘物件或图标表示，不用照片、显示器或卡片墙。
- 中间结构是装置的一部分，不拆成多个说明面板。
- 新输入和预测是同一场景里的收尾，不另做右侧 UI 栏。
- 全图只显示 3-5 个短标注；机制说明、百分比和长句默认不写进图里。

## 视觉预算

- 1 个 YC
- 1 件主装置
- 2-3 组小型输入物件
- 1 个可见中间结构
- 1 个新输入或输出结果
- 3-5 个中文短标注
- 35%-45% 纯白留白

元素不够时优先补机制；元素超出时先删解释框、编号、装饰和重复角色。

## Sample Broad Concept 生成后 Pass / Fail

以下任一项出现，Sample 直接判失败，不向用户交付：

- 深色、黑色、灰色或整张米色背景
- 霓虹、发光、赛博机器、黑板或夜景
- 两个或更多 YC
- 顶部大标题、解释段落、定义框、speech bubble 长文
- 多面板、卡片网格、编号步骤、底部流程条或总结条
- 照片、真实猫狗图片、显示器 UI、仪表盘
- 大面积高饱和色块、厚重阴影、商业 anime 海报质感
- 文字超过 5 处或出现非指定长句
- YC 没有红发或透明圆眼镜

失败后立即用下面的纠偏语句重新生成，最多自动重试 2 次：

```text
Regenerate from scratch and prioritize the attached canonical YC Sample style over content density. The previous result failed the style gate. Use a pure white canvas, exactly one YC, one continuous pencil-sketched scene, light low-saturation color, and only 3-5 short Chinese labels. Remove all titles, paragraphs, panels, numbered steps, bottom summary strips, photoreal images, UI screens, dark areas, neon, glow, and duplicate characters. Keep only the single core action and the minimum objects needed to show causality.
```

两次仍失败时，报告风格锁失败，不要把不合格图片当成最终结果。
