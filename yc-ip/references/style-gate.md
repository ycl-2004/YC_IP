# Style Gate：生成前后硬闸门

所有实际生图任务都先确认模式。本文件的严格单角色/单场景 gate 适用于默认 **Sample / Standard Broad Concept Explainer** 和普通单场景方法图；用户明确要求 Legacy Story-flow、Minimal 或 Rich 时，改用对应模式的构图规则，但仍必须保持该模式的背景、角色和渲染风格。风格优先级高于内容细节：

1. YC 角色识别与 Sample 画风
2. 纯白背景与单场景构图
3. 核心机制的因果可读性
4. 次要信息和装饰

如果内容细节与风格冲突，删内容，不牺牲风格。

## Topic-matched primary reference

Before generating, read `reference-routing.md` and `assets/examples/README.md`, then scan the real examples to select the closest primary reference. For explainers, also read `explanation-variation.md` and choose a scene archetype before choosing the image reference. Choose for topic, deliverable ratio, emotional tone, scene language, and information density—not convenience. `07-noise-filter.png` is only the fallback for a compact one-character mechanism scene; it is not a blanket default.

Pass exactly one selected primary reference as the normal style lock. A character-reference grid may be added only after two character-identity failures, and the prompt must explicitly prohibit copying its grid or multi-character layout.

## Codex Native Generation Path（正式默认路径）

正式 YC 图片在 Codex 里默认使用系统 `imagegen` skill 的 built-in `image_gen`，不要求 `OPENAI_API_KEY`。本地参考图仍必须真实进入生成上下文：先用 `view_image` 打开 blank canvas（如需要）、selected primary reference，以及必要的 continuity anchor，再调用 built-in `image_gen`。生成后从 `$CODEX_HOME/generated_images/...` 复制最终 PNG 到 `YC_Img_Out/`。

只有用户明确要求 CLI/API fallback，或 built-in route 不可用时，才使用 `image_gen.py`。fallback 命令形态：

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

Native route 下，selected primary reference 必须通过 `view_image` 或 Codex image attachment 进入上下文，只锁角色身份、线条、白底、克制配色、信息密度和手写中文标注风格。prompt 必须明确禁止复制该参考图的原始构图。CLI/API fallback 下，Input image 1 是纯白 blank canvas，Input image 2 是 selected primary reference。

空白画布尺寸必须与 `--size` 一致：16:9 用 `1536x1024`，1:1 用 `1024x1024`，竖图用 `1024x1536`。画布只是纯白 PNG，不要包含任何内容、文字、水印或透明背景。

参考路径：

- Sample / Standard: use the topic-matched asset selected by `reference-routing.md`; `07-noise-filter.png` is fallback only
- Minimal / Sticker: `assets/examples/sticker/00-reference-sheet-watercolor.png`
- Rich: `assets/examples/rich/<chosen>.png`

如果当前 native 工具无法接收或看见参考图，先用 `view_image` 把本地参考图载入上下文；仍不可用时才说明 CLI/API fallback。无参考图的 prompt-only 草稿必须标记为 `style draft / 未 reference locked`，不能宣称它是正式 YC locked asset。

## Sample Broad Concept 生图前 Preflight

调用 Codex native `image_gen` 或 CLI/API fallback 前必须确认最终 prompt 与实际生成上下文同时满足：

- `PURE WHITE #FFFFFF background across the entire canvas`
- `ONE YC character only`
- `one continuous hand-drawn scene, no panels`
- `warm pencil-like sketch lines, light low-saturation coloring`
- `no dark background, no black background, no neon, no glow`
- `no title, no paragraph, no definition, no summary strip`
- `no cards grid, no numbered steps, no UI screens, no photoreal images`
- `render only the listed short Chinese labels; never render the explanatory brief`
- selected primary reference 已经真实进入生成上下文：native route 用 `view_image` / image attachment，CLI/API fallback 用 `--image` / input_images；不能只在文字里说“using attached reference”
- CLI/API fallback 时，第一张 input image 是 blank white canvas，第二张 input image 是 topic-matched primary reference
- prompt 已声明不得复制 selected primary reference 的原构图，只能使用角色、线条、白底、配色克制、密度和手写标注风格

Broad Concept 额外确认：

- 已从 `explanation-variation.md` 选择一个场景原型；不是无脑复用机器/箱子。
- 一个 YC 正在执行核心动作；动作可能是操作装置、铺桥、分拣、校准、撑伞、记录、调音、复盘或展示小成果。
- 2-3 组样本/声音/证据/干扰/原料用小型手绘物件或图标表示，不用照片、显示器或卡片墙。
- 中间变化是场景的一部分，不拆成多个说明面板。
- 验证/回应/结果是同一场景里的收尾，不另做右侧 UI 栏。
- 全图只显示 3-5 个短标注；机制说明、百分比和长句默认不写进图里。

## 视觉预算

- 1 个 YC
- 1 个主场景物件或场景锚点
- 2-3 组小型输入物件 / 声音 / 证据 / 干扰 / 原料
- 1 个可见中间结构或变化
- 1 个新输入 / 回应 / 被保护的产出 / 输出结果
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
