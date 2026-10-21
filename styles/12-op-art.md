# 12 · 欧普主义 Op Art

> 静止的页面看着在动：同心圆、棋盘与条纹以不同频率叠在一起，眼睛自己造出波纹。
> 关键词：莫尔条纹 / 同心圆 / 棋盘格 / 条纹遮罩字 / 极简双色

- **适合**：展览海报、音乐视觉、概念产品、编辑型专题
- **不适合**：需要长时间阅读的正文页、老年用户为主的界面（视错觉会引起不适）
- **参考实现**：`../12-op-art.html` · 截图 `../_shots/12-op-art.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 纸底 | `#f5f5f3` |
| 墨 | `#0a0a0a` |
| 强调 | `#2b5cff`（只给主按钮与极小标记） |
| 正文 | `#3c3c38` |
| 次级 | `#6a6a64` |
| 细线 | `rgba(10,10,10,.14)` |
| 字体 | `"Futura","Avenir Next","Century Gothic","Helvetica Neue",Helvetica,Arial,"Microsoft YaHei"`；小标签 `ui-monospace,"SFMono-Regular",Menlo,Consolas` |
| 容器 | `max-width:1240px` · `padding:0 48px` |

## 签名配方

### 双同心圆系统（莫尔条纹的来源）
```css
background:repeating-radial-gradient(circle at 50% 50%,var(--ink) 0 1.6px,transparent 1.6px 9px);
background:repeating-radial-gradient(circle at 54% 46.5%,var(--ink) 0 1.6px,transparent 1.6px 9px);
```
两组同心圆圆心偏移 4–5%，叠在一起就产生旋转感——**偏移量是唯一的调节旋钮**，偏太多成两个圆、偏太少不动。

### 棋盘格
```css
background:repeating-conic-gradient(var(--ink) 0 25%,transparent 0 50%) 0 0/16px 16px;
```
`repeating-conic-gradient` 一行就能出棋盘；16px 一格，缩小到 7px 变细网格，用于小面积装饰。

### 条纹遮罩字（标题的第二次震动）
```css
h1 .striped{
  background-image:repeating-linear-gradient(90deg,var(--ink) 0 3px,transparent 3px 10px);
  -webkit-background-clip:text;background-clip:text;
  color:transparent;-webkit-text-fill-color:transparent;-webkit-text-stroke:.018em var(--ink);
}
```
3px 实条 + 7px 空隙；补 `text-stroke` 保住字形轮廓，否则小字会碎。

### 条纹分隔带
```css
.band{height:16px;border-top:1px solid var(--hair);border-bottom:1px solid var(--hair);
  background-image:repeating-linear-gradient(90deg,var(--ink) 0 3px,transparent 3px 13px)}
```
横贯全宽的节奏线，替代普通 `<hr>`；密度变了，页面呼吸就变了。

## 页面骨架
顶栏（无底线，仅细线）→ hero（左文右图：标题一半实心一半条纹 + 莫尔圆盘 + 棋盘块）→ 条纹带 → 四列特性（细竖线分隔，无卡片）→ 波浪线装饰 → 页脚。

## 动效
只有 `breathe`（极缓慢的透明度呼吸）与 `dim`；hover 时条纹背景位移一格。整页刻意近乎静止——动得越多，错觉越弱。

## 红线 / 翻车点
- **正文绝不压在条纹上**：密条纹上的小字 3 秒致晕，文字区必须纯色底。
- **一页只留两处错觉**：同心圆 + 棋盘足够；再多就成视觉噪音。
- **点缀色只能一个**：欧普的张力来自黑白对比，彩色一多就退化成普通海报。
- **必须支持 reduced-motion**：前庭功能敏感人群会因动效不适，这不是可选项。
- **条纹宽度统一**：3px 实 + 7–10px 空，一套到底；混用不同频率会显脏。
