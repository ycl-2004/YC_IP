# 使用示例

> 三种模式：**Sticker 贴图（默认，白底水彩小贴纸）/ Simple 普通（多步场景流）/ Rich 丰富（满版 editorial，仅 IP/品牌用）**。
> 不指定模式时，skill 会按"一件事 → Sticker / 多步过程 → Simple / 整页成品 → Rich"自动判断，默认偏轻。
> **每次生图都建议附一张对应模式的参考图**（见仓库 `assets/examples/`），纯文字 prompt 不够稳。

---

## 基础用法

### 配图策略（shot list，不生图）

```text
/yc-personal-ip 先不要生图。
分析下面这篇文章，输出 shot list。
每张图写清楚：段落位置、主题、核心意思、用哪个模式、YC 在做什么、建议比例、建议标注词。

<粘贴文章>
```

### 文章正文配图（默认 Sticker）

```text
/yc-personal-ip 为下面这篇文章配几张图，默认贴纸风（白底干净、一张讲一件事）。

<粘贴文章>
```

### 指定比例

```text
/yc-personal-ip 画一张 1:1 的贴纸图，主题「专注写作」，YC 托腮看着合上的笔记本。
```

```text
/yc-personal-ip 生成一张 9:16 的竖版图，关于「每天进步一点点」的感悟，保持贴纸风。
```

---

## Sticker 贴图（默认，最常用）

### 一个概念 / 情绪

```text
/yc-personal-ip 画一张「灵感来了」的贴纸图：YC 抬手去接一个飘下来的小灯泡，白底，几乎不写字。
```

### 社媒单图

```text
/yc-personal-ip 1:1 贴纸图，YC 坐着喝咖啡，感觉专注又有点 chill。单角色，留白多。
```

### 文章封面 / 标题图（Sticker 封面版）

```text
/yc-personal-ip 给这篇文章做个 16:9 封面，标题「我是怎么搭出个人 IP 的」。
一个 YC hero 放一侧 + 一行手写标题 + 白底，干净不堆元素。
```

---

## Simple 普通（多步 / 对比）

### 流程 / 步骤

```text
/yc-personal-ip 用 simple 模式把这个学习方法画成 16:9 的流程图，3-5 步，箭头连接。
```

### Before / After

```text
/yc-personal-ip simple 模式，16:9，左边「用之前」一团乱，右边「用之后」清爽，YC 在中间。
```

### 内容支柱故事流（音乐创作）

```text
/yc-personal-ip simple 模式，16:9，展示创作流程：情绪 → 歌词 → 旋律 → 编曲 → 录音 → 分享，YC 每步做不同动作。
```

---

## Rich 丰富（仅 IP / 品牌 / 整页成品）

### IP 自我介绍

```text
/yc-personal-ip rich 模式，16:9 YC IP 介绍图。
展示 YC 是谁、关注什么主题、有什么特点（ABOUT YC、FAVORITE THINGS、LIFE MODE）。
```

### 品牌生态地图

```text
/yc-personal-ip rich 模式，21:9 超宽 YC 品牌生态图，YC 居中，5大内容支柱环绕四周。
```

---

## 知识讲解（按复杂度选模式）

### 一个概念（Sticker）

```text
/yc-personal-ip 画一张贴纸图解释「复利」：YC 旁边一条慢慢翘起来的小曲线，标注「时间 / 坚持」。
```

### 需要分步的原理（Simple）

```text
/yc-personal-ip simple 模式 16:9 讲「什么是递归」：YC 把一个盒子打开里面还是一个小盒子，分几步表示层层调用。
```

---

## 编辑和修复

### 去掉多余文字

```text
/yc-personal-ip 帮我编辑这张图，去掉左上角的多余文字，其他保持不变。
```

### 角色识别修复

```text
/yc-personal-ip 重新生成。角色必须有：蓬松深红发色 + 透明圆框眼镜。其他构图保持一样。
```

### 太满 → 压回贴纸

```text
/yc-personal-ip 这张太满像海报了。重生成成 sticker：单角色、白底、删掉周围道具和标注、留白多。记得带贴纸参考图。
```

### 调整比例

```text
/yc-personal-ip 把上面这张图的概念重新生成一版 9:16 竖版的，保持同样模式。
```
