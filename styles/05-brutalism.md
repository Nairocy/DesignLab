# 05 · 粗野主义 Web Brutalism

> 把骨架暴露出来；对精致主义的坦率反动。
> 关键词：4px 黑描边 / 零模糊硬阴影 / 跑马灯 / 倾斜贴纸 / 巨型标题

- **适合**：创意机构、作品集、艺术项目、敢"吵"的品牌
- **不适合**：严肃商务、金融政务、温和的消费品
- **参考实现**：`../05-brutalism.html` · 截图 `../_shots/05-brutalism.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 底 | `#f4f2ec` |
| 墨 | `#101010` |
| 电蓝 | `#2500ff`（结构色：阴影/边框/引用线） |
| 荧光黄 | `#ffe600`（状态色：hover/高亮） |
| 字体 | 标题 `"Arial Black",Impact` 900；数据/标签 `Consolas` mono；正文 `"Microsoft YaHei"` 400 |
| 线条 | 4px 实线（主结构）；3px（贴纸/按钮） |

## 签名配方

### 无缝跑马灯（双份内容 + translateX(-50%)）
```css
.ticker{background:var(--ink);color:var(--yellow);overflow:hidden;white-space:nowrap}
.track{display:inline-block;animation:tick 26s linear infinite}
@keyframes tick{to{transform:translateX(-50%)}}
```
HTML 里把同一段文字放两份 `<span>`，位移 50% 即无缝。

### 零模糊硬阴影 + 按压
```css
.sticker{border:3px solid var(--ink);box-shadow:6px 6px 0 var(--ink);transform:rotate(7deg);background:#fff}
.btn{box-shadow:7px 7px 0 var(--blue);transition:transform .15s,box-shadow .15s}
.btn:hover{transform:translate(4px,4px);box-shadow:3px 3px 0 var(--blue)}  /* 按下=向影子方向位移 */
```

### 巨字 + 色块高亮
```css
h1{font-size:clamp(54px,10vw,140px);font-weight:900;line-height:1;letter-spacing:-.02em}
h1 mark{background:var(--blue);color:#fff;padding:0 .06em}
```

### 表格化特性行（编号暴露 + hover 整行变色）
```css
.feature{display:grid;grid-template-columns:110px 240px 1fr;gap:26px;padding:32px 12px;border-bottom:4px solid var(--ink)}
.feature:hover{background:var(--yellow)}
.feature .num{font-family:Consolas;letter-spacing:.2em}  /* [001] 样式 */
```

### mono 方括号 kicker
```css
.kicker{font-family:Consolas;letter-spacing:.26em}
.kicker::before{content:"[ ";color:var(--blue)}
.kicker::after{content:" ]";color:var(--blue)}
```

## 页面骨架
顶部跑马灯（黑底黄字）→ 4px 底线顶栏 → 巨字 hero（右上旋转贴纸、`mark` 色块、左色线引用式 lede）→ 四行表格特性 → 黑条页脚。

## 动效
跑马灯常驻（26s 匀速）；按钮按压 0.15s；行 hover 变色。都要"物理的、硬的"。

## 红线 / 翻车点
- "故意的乱"需要更狠的克制：层级、可点击性、移动端一条都不能少，否则只是没设计。
- 硬阴影位移必须和内容同一光源方向（右下），hover 反向位移会晕。
- 结构色（蓝）与状态色（黄）分工别混：蓝=阴影/边框/引用线，黄=hover/高亮。
