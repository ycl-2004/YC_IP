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

## 交付标准

好图应该让读者第一眼觉得：「这是一个有品味的年轻创作者的内容」，而不是「这是一张 AI 生的模板图」。

温暖、有个性、有 YC 的标志、信息清晰但不说明书 — 这四点都满足才算合格。
