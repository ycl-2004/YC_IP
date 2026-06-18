# QA Checklist — YC

## 通用必过项（三模式都要）
- [ ] YC 有红发（深红/酒红色）
- [ ] YC 有透明/细框圆眼镜（不是黑框）
- [ ] YC 参与了核心动作，不只是装饰
- [ ] 比例符合用户需求
- [ ] 带了参考图，没有照抄旧图的具体布局

角色识别失败（缺红发/眼镜）= 最高优先级，必须重生成：强调 `messy dark-red burgundy hair AND round clear-frame glasses — both mandatory`。

---

## Sample / Standard 默认模式专项

- [ ] 背景是**纯白 #FFFFFF**，不要整张奶油白/米白纸底
- [ ] 整体对齐 `assets/examples/simple/current-showcase/`：温暖手绘 chibi、中文短标注、中等信息密度
- [ ] 方法/观点被画成场景物件或具体动作，不是线框流程图
- [ ] YC 正在操作核心物件或参与核心动作，不是贴在旁边
- [ ] 角色周围没有白色矩形边框、截图底、贴纸残留底色
- [ ] 标注短、中文优先、可读；没有长段正文
- [ ] 没有重型面板边框 / section header（那会变成满版 editorial）
- [ ] 没有自动降成 Minimal，也没有自动升成 Rich

**Broad Concept Explainer（什么是 X）额外检查：**
- [ ] 只有一个核心隐喻，不是百科页
- [ ] 画面能看出“输入 → YC 操作/学习 → 输出”的关系
- [ ] 没有定义段落、分类列表、真实公司案例列表、底部总结条
- [ ] 中文短标注控制在 3-4 个左右

**Sample 失败信号：**
| 信号 | 解决 |
|------|------|
| 背景偏奶油白/纸色/灰底 | 重生成，强调 PURE WHITE #FFFFFF background |
| 太轻，像单个贴纸 | 用户没点名 Minimal 时，升回 Sample/current-showcase 密度 |
| 变成多面板 + section header | 去掉框和标题，回到手绘场景 |
| 文字太密 | 只保留最核心中文短标注 |
| 太像 PPT/流程图 | 强调 hand-drawn warm story, not infographic |
| 像百科教学卡片 | 压回一个中心隐喻：输入、YC 操作、输出 |
| YC 像贴纸贴上去 / 有白色边框 | 重生成或编辑去底，强调 character integrated into the scene |

---

## Minimal / Sticker 贴图模式专项（仅显式点名）

- [ ] 背景是**纯白 #FFFFFF**（不是奶油白、不是纸纹、不是渐变阴影）
- [ ] 画风是**水彩铅笔轻涂松手绘**（不是高光全彩 anime，也不是纯黑线稿）
- [ ] **只有一个 YC**，单主体，无多场景/分格/步骤流
- [ ] 全图 0-3 个中文短词，无英文、无中英混排、无 section header
- [ ] 至少 50% 留白
- [ ] 最多 1 个相关物件；无便利贴墙、无大"YC"logo、无书堆/笔筒/植物围一圈
- [ ] 无满天心形/星星/闪光
- [ ] 像从笔记本剪下来贴在白纸上的小贴纸

**Minimal 失败信号（都是滑向海报）：**
| 信号 | 解决 |
|------|------|
| 背景奶油白/纸纹 | 重生成，强调 PURE WHITE #FFFFFF |
| 画得太精致全彩高光 | 强调 loose watercolor colored-pencil sketch, not glossy anime |
| 一圈道具/便利贴/书堆/大 logo | 删到只剩单角色 + 最多 1 物件 |
| 出现英文或中英混排 | 重生成，只要 0-3 个中文短词 |
| 出现多场景/箭头流程 | 那是 Sample，压回单主体 |
| 没带参考图 | 补 `00-reference-sheet-watercolor` 重生成（最常见根因）|

---

## Rich 丰富模式专项（仅显式点名）

- [ ] 用户明确要求了 Rich / 完整海报 / IP 设定页 / 品牌全景 / 整页成品
- [ ] 画面是完整页面，而不是普通正文小图
- [ ] YC 红发和透明眼镜清楚可见
- [ ] 多区块有组织，但没有塞满长段文字
- [ ] 文字短、可读，不是密密麻麻的小字
- [ ] 背景是奶油白/轻纸感，整体温暖、有个人品牌气质
- [ ] 不像商业品牌 KV、PPT 信息图或通用 anime 海报

**Rich 失败信号：**
| 信号 | 解决 |
|------|------|
| 用户没明确点名 Rich | 降级到 Sample / Standard |
| 太像商业海报 / anime 拼贴 | 强调 warm hand-drawn editorial, personal creator brand, not glossy poster |
| 信息太满 | 减少区块，保留 3-6 个核心模块 |
| 文字太小太密 | 改成短标签和少量手写标题 |
| YC 不像主角 | 放大主视觉或增加 YC 在关键场景里的参与 |

---

## 迭代优先级
1. 角色识别（红发/眼镜）→ 必重生成
2. 模式是否被正确触发（Minimal / Rich 都必须显式点名）→ 不对就降级或重生成
3. 背景颜色（Minimal / Sample 要纯白；Rich 才可奶油白）→ 重生成
4. 信息密度（Sample 太轻或太密 / Minimal 太满 / Rich 太挤）→ 调整密度后重生成
5. 比例不对 → 检查提示词比例参数
6. 文字问题（错字/英文混入 Minimal、Sample 文字太密）→ 局部编辑或重生成

## 交付标准
- **Sample / Standard**：默认输出，对齐 current-showcase，白底、YC 参与核心动作、中文短标注、中等信息密度。
- **Minimal / Sticker**：显式点名才启用，白底一张水彩铅笔小贴纸，单角色、极少字、巨量留白，1 秒看懂。
- **Rich**：显式点名才启用的完整海报 / IP 设定页 / 品牌全景，区块清晰但不拥挤。
- 三者都要：YC 有红发+眼镜。
