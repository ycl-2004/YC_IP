# 参考图分类（生图时怎么用）

参考图只锁三件事：**①YC 长相 ②画风渲染 ③信息密度**。锁完不照抄构图——每次从当前内容重想画面。

## simple/current-showcase/（默认成品风格基准）
`current-showcase/` 复制自仓库外层 `examples/images/`，是当前 README/gallery 里希望最终输出对齐的成品风格基准。

- 默认生成路径看这里：Sample / Standard。
- 需要判断“最终效果像不像当前 example”时，看这里。
- 产出要贴近 `current-showcase/` 的密度、白底、手绘线条、角色参与感和中文标注方式。
- `current-showcase/` 是结果 benchmark，不是构图模板；每次仍然要按当前内容重想场景。

### 按 topic 选择 primary reference

每次先读 `../../references/reference-routing.md`，再扫描本目录选择与主题、比例、情绪和信息密度相符的真实 asset。不要固定使用某一张图。`07-noise-filter.png` 仍是安全的单角色、白底、单场景机制图 fallback，但不是通用默认。

所有 reference 都只锁角色、渲染、留白和密度；必须为当前内容重新设计构图。`character-reference/` 九宫格只在角色连续两次漂移时作为第二张修复参考，不能作为普通 Sample 的唯一风格锁。

## sticker/（Minimal / Sticker 显式模式用）
- **`00-reference-sheet-watercolor.png` = canonical 画风锁。每张 Minimal / Sticker 固定带这一张，别换。** 它锁住"白底水彩铅笔松手绘"这个画风，是 Minimal 不跑成海报的命门。
- `01-08-*.png`：动作姿势库（坐着用笔记本、托腮思考、拿杯子…）。**只作构思参考**——想画某个动作先翻它找最接近的，不当画风锁。
- `outfit-01~09.png`：服装变体参考。**只作构思参考**，不当画风锁。

> Minimal / Sticker 生图 = 永远带 00；红发/眼镜不稳时再加 `character-reference/` 九宫格一起带。

## simple/（Sample 方法类参考）
01-07 是基础方法类例图（流程流、桌面场景、before/after 等）。08-11 是推荐的方法类成品样例：

- `08-idea-press-machine.png`：把混乱想法压成作品。
- `09-trust-bridge.png`：用证据、作品、反馈铺出信任桥。
- `10-purpose-sort-machine.png`：按学习 / 创作 / 发布分拣输入素材。
- `11-one-source-many-outputs.png`：一个素材输出文章 / 视频 / 音乐等多种表达。

做方法类图时优先参考 08-11 的思路：方法要变成场景物件，YC 在里面操作；不要画成线框流程图，也不要把角色贴成带白边的小贴纸。

## cover/（封面版）
`01-sticker-cover-tiny-win.png` 是 16:9 封面样例：一个 YC hero + 一行中文标题 + 白底。封面默认对齐 Sample，不自动升级成 Rich。

## social/（社媒比例）
`01-social-1x1-tiny-win.png` 是 1:1 社媒样例，用同一套视觉语言转方图。社媒单图默认对齐 Sample，避免塞成海报。

## character-reference/（长相锁，跨模式）
01-07 九宫格 = YC 长相锁。注意它是**全彩 anime，只能锁长相、锁不了 Sample/水彩画风**。Broad Concept 默认不要带九宫格；只有连续两次角色识别失败时才作为第二张参考，并明确禁止复制网格和多角色。`05/06/07-pose-library-*` 是动作构思库。

## rich/（已不在默认路径）
仅"整页 IP 介绍/品牌全景设定页"这类极少数场景手动启用时才参考。日常忽略。
