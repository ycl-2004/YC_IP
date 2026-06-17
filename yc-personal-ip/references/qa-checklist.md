# QA Checklist — YC

## 必过项

**所有模式通用**：
- [ ] YC 有红发（深红/酒红色）
- [ ] YC 有透明/细框圆眼镜
- [ ] YC 参与了核心动作，不只是装饰
- [ ] 比例符合用户需求
- [ ] 没有复刻旧图的具体布局

**仅 Simple / Rich**（Sticker 模式不要套这些，否则又变海报）：
- [ ] 背景是奶油白/米白（不是纯白）
- [ ] 包含 MacBook（带心形贴纸）或笑脸杯（工作/创意场景）
- [ ] 有中英混排标注
- [ ] 布局类型与内容匹配

**Sticker 模式的必过项见下方专项检查**（纯白底 + 水彩铅笔 + 单主体 + 极少字）。

## 失败信号 → 重生成

| 问题 | 解决方式 |
|------|------|
| YC 没有红发 | 重生成，在提示词里强调 `dark-red burgundy hair — mandatory` |
| YC 戴黑框眼镜而不是透明眼镜 | 重生成，强调 `round clear-frame glasses, NOT black frames` |
| 背景是纯白 | 重生成，强调 `warm off-white cream background, NOT pure white` |
| 缺少 MacBook 或笑脸杯 | 在提示词里明确列出签名道具 |
| 没有中英混排 | 明确要求 `bilingual labels (Chinese + English)` |
| 图太像 PPT 或流程图 | 强调 `hand-drawn editorial notebook style, not infographic` |
| 整体太商业/精致 | 降低饱和度要求，加 `slightly imperfect hand-drawn feel` |
| 比例不对 | 检查提示词里的比例参数是否正确写入 |
| Section header 太正式 | 要求 `small caps printed style with underline, not bold headers` |
| YC 太小/太大 | 调整为 `YC occupies 35-50% of the canvas` |

## 各布局类型专项检查

### IP Character Sheet
- [ ] 有全身站立 YC
- [ ] 有 ABOUT YC 标签列表
- [ ] 有 FAVORITE THINGS 道具图示
- [ ] 有 LIFE MODE 多场景
- [ ] 有 OUTFIT VIBES 服装变体
- [ ] 有 COLOR PALETTE
- [ ] 有 signature sticky note with quote

### Creative Workspace Panorama
- [ ] YC 坐在桌子前（不是站立）
- [ ] 桌上有 MacBook + 笑脸杯 + 笔记本
- [ ] 有多个 concept card panels
- [ ] 有顶部主题标题
- [ ] 有底部 tagline

### Social Media Card
- [ ] 场景简洁，不信息过载
- [ ] 有 1 句 signature quote（便条纸样式）
- [ ] 比例是 1:1 / 4:5 / 9:16 其中之一

## 迭代优先级

1. 角色识别问题（红发/眼镜）→ 必须重生成
2. 背景颜色问题 → 重生成
3. 缺少签名道具 → 重生成或局部编辑
4. 比例问题 → 重生成
5. 布局太满/太空 → 调整后重生成
6. 文字问题（错字/纯中文/纯英文）→ 局部编辑或重生成

## Sticker 贴图模式专项检查（默认模式）

- [ ] 背景是**纯白 #FFFFFF**（不是奶油白、不是纸纹、不是渐变阴影）
- [ ] 画风是**水彩铅笔/彩色铅笔轻涂松手绘**（不是高光全彩 anime，也不是纯黑线稿）
- [ ] YC 红发清晰可识别（这是唯一明显的颜色锚点）
- [ ] **只有一个 YC**，单主体，没有多场景/分格/步骤流
- [ ] 全图 0-3 个中文短词，无英文、无中英混排、无 section header
- [ ] 至少 50% 画面是空白
- [ ] 最多 1 个相关物件；无便利贴墙、无大"YC"logo、无书堆/笔筒/植物围一圈
- [ ] 无满天心形/星星/闪光装饰
- [ ] 像一张从笔记本剪下来贴在白纸上的小贴纸

**Sticker 失败信号（都是滑向海报的信号）**：
- 背景是奶油白/米白/有纸纹 → 重生成，强调 PURE WHITE #FFFFFF
- YC 画得太精致全彩高光 → 强调 loose watercolor colored-pencil sketch, not glossy anime
- 出现一圈道具/便利贴/书堆/大 logo → 删到只剩单角色 + 最多 1 物件
- 出现英文或中英混排 → 重生成，只要 0-3 个中文短词
- 出现多场景/箭头流程 → 那是 Simple 模式，压回单主体
- 没带参考图 → 补上贴纸参考图重生成（最常见的根因）

## Simple 普通模式专项检查

- [ ] 有 3-6 个步骤/场景串联
- [ ] 每步 YC 有不同动作
- [ ] 每步标注短（2-6 字）
- [ ] 步骤间有箭头或流动路径连接
- [ ] 没有重型面板边框
- [ ] 整体像一个温暖的视觉故事

**Simple 失败信号**：
- 变成 Rich 模式（多面板/section header）→ 去掉框和标题
- 步骤太多（>6）→ 精简到核心 3-4 步
- 文字太密 → 每步只保留最核心的 1 个标注

## 交付标准

**Rich**：有品味的创作者笔记页。温暖、有层次、信息完整。

**Simple**：温暖的视觉故事流。3-6 步讲清楚一件事。

**Sticker**：白底上一张水彩铅笔小贴纸。单角色、极少字、巨量留白，1 秒看懂、轻而干净。

三种模式都要满足：YC 有红发+眼镜。
