# QA Checklist — YC

## 必过项

- [ ] YC 有红发（深红/酒红色）
- [ ] YC 有透明/细框圆眼镜
- [ ] YC 参与了场景的核心动作，不只是装饰
- [ ] 背景是奶油白/米白（不是纯白）
- [ ] 包含 MacBook（带心形贴纸）或笑脸杯（工作/创意场景）
- [ ] 有中英混排标注
- [ ] 比例符合用户需求
- [ ] 布局类型与内容匹配
- [ ] 没有复刻旧图的具体布局

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

## Minimal 极简模式专项检查

- [ ] 背景是**纯白**（不是奶油白！）
- [ ] 全图最多 2-5 个中文词
- [ ] 无英文文字
- [ ] 至少 50% 画面是空白
- [ ] YC 是简化线稿风（不是精致全彩 anime）
- [ ] 只用了一种强调色（橙或红）
- [ ] 无心形/星星/闪光等装饰
- [ ] 无签名道具（除非道具本身是隐喻）
- [ ] 一个核心隐喻，去掉所有文字后画面仍然完全可理解

**Minimal 失败信号**：
- 背景是奶油白/米白 → 重生成，强调 PURE WHITE
- YC 画得太精致/全彩 → 强调 simple black line sketch style
- 出现英文 → 重生成，只要中文
- 文字超过 5 个词 → 删减
- 出现心形/星星装饰 → 重生成，强调 NO decorative elements
- 出现 MacBook/笑脸杯等签名道具 → 去掉，除非道具是隐喻本身

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

**Minimal**：白纸上的一个想法。1 秒看懂核心意思，画面极致干净。

三种模式都要满足：YC 有红发+眼镜。
