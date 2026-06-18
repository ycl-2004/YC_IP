# 使用示例

> 三种模式：**Sample / Standard（默认，对齐当前 examples）/ Minimal 或 Sticker 或贴图纸（极简贴纸，仅显式点名）/ Rich（满版 editorial，仅显式点名）**。
> 不指定模式时，skill 默认走 Sample / Standard。Minimal 和 Rich 都必须明确点名才启用。
> **每次生图都建议附一张对应模式的参考图**（见仓库 `assets/examples/`），纯文字 prompt 不够稳。
> 当前 Sample 成品风格基准在 `assets/examples/simple/current-showcase/`；封面版看 `assets/examples/cover/`；1:1 社媒样例看 `assets/examples/social/`。

---

## 基础用法

### 配图策略（shot list，不生图）

```text
Use $YC_IP 先不要生图。
分析下面这篇文章，输出 shot list。
每张图写清楚：段落位置、主题、核心意思、用哪个模式、YC 在做什么、建议比例、建议标注词。

<粘贴文章>
```

### 文章正文配图（默认 Sample）

```text
Use $YC_IP 为下面这篇文章配几张图，默认 Sample 风格，对齐当前 examples。

<粘贴文章>
```

### 指定比例

```text
Use $YC_IP 画一张 1:1 图，主题「专注写作」，YC 托腮看着合上的笔记本，当前 Sample 风格。
```

```text
Use $YC_IP 生成一张 9:16 的竖版图，关于「每天进步一点点」的感悟，保持当前 Sample 风格。
```

---

## Sample / Standard（默认，最常用）

### 一个概念 / 情绪

```text
Use $YC_IP 画一张「灵感来了」的图：YC 抬手去接一个飘下来的小灯泡，白底，中文短标注，对齐当前 examples。
```

### 社媒单图

```text
Use $YC_IP 1:1 社媒单图，YC 坐着喝咖啡，感觉专注又有点 chill，白底，当前 Sample 风格。
```

### 文章封面 / 标题图（Sample 封面版）

```text
Use $YC_IP 给这篇文章做个 16:9 封面，标题「我是怎么搭出个人 IP 的」。
一个 YC hero 放一侧 + 一行手写标题 + 白底，干净不堆元素。
```

---

## Minimal / Sticker（仅显式点名：极简贴纸）

### 一个极简概念

```text
Use $YC_IP 明确使用 Minimal / 贴图纸，画一张「专注写作」的极简贴纸图：单个 YC，最多一个笔记本，纯白底，几乎不写字。
```

### 太满 → 压回 Minimal

```text
Use $YC_IP 这张太满像海报了。重生成 Minimal / Sticker：单角色、白底、删掉周围道具和标注、留白多。记得带贴纸参考图。
```

---

## Sample 方法图（流程 / 对比）

### 流程 / 步骤

```text
Use $YC_IP 把这个学习方法画成 16:9 场景图：把方法变成可操作的物件，YC 正在里面操作，纯白背景，对齐当前 examples。
```

### Before / After

```text
Use $YC_IP 16:9，左边「用之前」一团乱，右边「用之后」清爽，YC 在中间，当前 Sample 风格。
```

### 内容支柱故事流（音乐创作）

```text
Use $YC_IP 16:9，展示创作流程：情绪 → 歌词 → 旋律 → 编曲 → 录音 → 分享，YC 每步做不同动作，当前 Sample 风格。
```

---

## Rich 丰富（仅显式点名：完整海报 / IP / 品牌 / 整页成品）

### IP 自我介绍

```text
Use $YC_IP 明确使用 Rich 模式，生成 16:9 YC IP 介绍图。
展示 YC 是谁、关注什么主题、有什么特点（ABOUT YC、FAVORITE THINGS、LIFE MODE）。
```

### 品牌生态地图

```text
Use $YC_IP 明确使用 Rich 模式，生成 21:9 超宽 YC 品牌生态图，YC 居中，5大内容支柱环绕四周。
```

---

## 知识讲解（按复杂度选模式）

### 一个概念（默认 Sample）

```text
Use $YC_IP 画一张图解释「复利」：YC 正在把小星星贴到一条慢慢翘起来的曲线上，标注「时间 / 坚持」。
```

### 需要分步的原理（默认 Sample）

```text
Use $YC_IP 16:9 讲「什么是递归」：YC 把一个盒子打开里面还是一个小盒子，分几步表示层层调用。
```

---

## 编辑和修复

### 去掉多余文字

```text
Use $YC_IP 帮我编辑这张图，去掉左上角的多余文字，其他保持不变。
```

### 角色识别修复

```text
Use $YC_IP 重新生成。角色必须有：蓬松深红发色 + 透明圆框眼镜。其他构图保持一样。
```

### 调整比例

```text
Use $YC_IP 把上面这张图的概念重新生成一版 9:16 竖版的，保持同样模式。
```
