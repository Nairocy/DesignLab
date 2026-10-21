# 11 · 波普主义 Pop Art

> 把大众文化印成海报：网点、粗黑轮廓、对话框和俗艳四色，一切都在喊「看这里」。
> 关键词：Ben-Day 网点 / 4px 粗黑轮廓 / 四色重复 / 漫画气泡 / 星爆

- **适合**：活动页、潮牌、音乐节、食品饮料、面向年轻人的促销
- **不适合**：医疗金融、需要克制的高级感品牌、长文阅读站
- **参考实现**：`../11-pop-art.html` · 截图 `../_shots/11-pop-art.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 纸底 | `#fffdf5` |
| 墨 | `#111111`（轮廓与正文） |
| 红 | `#e8302a` |
| 黄 | `#ffd400` |
| 蓝 | `#1b4fd8` |
| 品红 | `#ff3d81` |
| 字体 | 标题 `"Arial Black","Arial Bold",Impact,"Microsoft YaHei","PingFang SC"`；正文 `"Helvetica Neue",Helvetica,Arial,"Microsoft YaHei","PingFang SC"` |
| 容器 | `max-width:1180px` · `padding:0 clamp(18px,4.2vw,46px)` |
| 轮廓 | `3px solid #111`（细件）/ `4px`（标题贴纸） |
| 硬影 | `3px 3px 0 #111`（按钮）/ `7px 7px 0 品红 + 14px 14px 0 墨`（双层贴纸） |

## 签名配方

### Ben-Day 网点底（波普的第一识别物）
```css
/* 品红网点 */
background:radial-gradient(circle,rgba(255,61,129,.5) 2.6px,transparent 2.8px) 0 0/15px 15px;
/* 墨色网点（浅一档） */
background:radial-gradient(circle,rgba(17,17,17,.24) 2.1px,transparent 2.3px) 0 0/13px 13px;
```
点半径 2.1–2.6px、网格 12–15px；点距太小会糊成灰面，太大就成波点布。

### 双层硬影标题贴纸
```css
.plate{display:inline-block;padding:.04em .16em .12em;border:4px solid var(--ink);
  background:var(--yellow);color:var(--ink);
  box-shadow:7px 7px 0 var(--magenta),14px 14px 0 var(--ink);transform:rotate(-1.7deg)}
.plate.p2{background:var(--red);color:var(--paper);box-shadow:7px 7px 0 var(--blue),14px 14px 0 var(--ink);transform:rotate(1deg)}
```
两层影（先彩色、后墨色）是「套印错版」的平替：一眼看出是印刷品而不是 UI。

### 四联重复版画（Warhol）
```css
.warhol{background:var(--ink);color:var(--paper)}
.warhol-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:3px;background:var(--ink)}
```
同一图形换四种底色重复四次，只在标题写「SAME IDEA — FOUR TIMES」。gap 用 3px 墨色缝，像印张拼版。

### 漫画气泡与星爆
```css
.hero-burst{position:absolute;width:118px;height:118px;transform-origin:50% 50%;
  animation:wobble 7s ease-in-out infinite}
.art-burst{transform-origin:388px 112px;animation:spin 64s linear infinite}
```
星爆用 SVG 多角星手绘；气泡尾巴用 CSS 三角。两者只给 1–2 处，多了就成贴纸墙。

### 跑马灯报头
顶部 `tick` 动画横条，写「POP ART SPECIAL / 四色印刷 / BEN-DAY DOTS」等版面信息——报纸刊头式装饰，允许，但不得改动正文文案。

## 页面骨架
跑马灯报头 → 顶栏 → hero（左侧双层硬影标题 + 右侧笔记本插画框 + 气泡 + 星爆 + 10¢ 贴纸）→ 黑底四联版画带 → 四色特性卡 → 页脚。

## 动效
`plateIn` / `frameIn` / `cardIn` / `panelIn` 入场（0.5–0.8s，带 rotate 落位）；`wobble` 7s 缓慢摇摆；`spin` 64s 极慢旋转。`prefers-reduced-motion` 全关。

## 红线 / 翻车点
- **四色配额**：红黄蓝品红各自有职责，别把四个色铺满整页——留白仍是纸。
- **轮廓不能省**：没有 3–4px 黑边，网点就变背景噪点，画面立刻散架。
- **网点只做底**：文字必须压在纯色块或纸上，压在网点上会花。
- **对比度**：黄底黑字 OK（≥10:1）；红底只能用白字且仅限大字（小字改黑底白字）。
- **插画风格统一**：全部走「粗线 + 平涂 + 网点」的漫画语言，混进写实或渐变图标就出戏。
