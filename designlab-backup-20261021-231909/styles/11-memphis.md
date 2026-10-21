# 11 · 孟菲斯 Memphis

> 1981 米兰；对极简的嬉皮笑脸式反叛，装饰无罪。
> 关键词：点阵底 / 漂浮几何 / 贴纸卡 / 撞色 / 摇摆动画

- **适合**：电商活动、年轻品牌、播客、派对风页面
- **不适合**：严肃商务、金融、需要沉稳气质的内容
- **参考实现**：`../11-memphis.html` · 截图 `../_shots/11-memphis.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 底 | `#fbf2e2` + 点阵（`radial-gradient(rgba(23,19,14,.07) 1.5px,transparent 1.5px)` / `background-size:30px 30px`） |
| 墨 | `#17130e`（所有边框/阴影） |
| 粉 | `#ff5d8f`（主） |
| 蓝 | `#4d7cfe` |
| 青 | `#23c9b4` |
| 黄 | `#ffd23f`（高亮块） |
| 字体 | `"Trebuchet MS","Arial Rounded MT Bold","Microsoft YaHei"`（圆润感），标题 800 |
| 边框 | 全站 3px；硬阴影永远是实心墨色 |

## 签名配方

### 摇摆的漂浮几何（波浪/圆环/三角/十字，SVG）
```css
.shape{position:absolute;pointer-events:none;animation:wiggle 6s ease-in-out infinite}
@keyframes wiggle{0%,100%{transform:rotate(-7deg)}50%{transform:rotate(7deg)}}
```
各自 `animation-delay` 用负值错峰（-1.2s / -2s / -3.4s）。形状总数 ≤6 个。

### 贴纸卡（硬阴影 + hover 微旋）
```css
.card{background:#fff;border:3px solid var(--ink);border-radius:18px;box-shadow:6px 6px 0 var(--ink);transition:transform .2s,box-shadow .2s}
.card:hover{transform:translate(-2px,-2px) rotate(-1deg);box-shadow:8px 8px 0 var(--ink)}
```

### 药丸按钮（按下往影子方向走）
```css
.btn{background:var(--pink);color:#fff;border:3px solid var(--ink);border-radius:999px;box-shadow:5px 5px 0 var(--ink);transition:transform .15s,box-shadow .15s}
.btn:hover{transform:translate(-2px,-2px);box-shadow:7px 7px 0 var(--ink)}
.btn:active{transform:translate(2px,2px);box-shadow:2px 2px 0 var(--ink)}
```

### 高亮 mark 微旋
```css
h1 mark{background:var(--yellow);border-radius:10px;padding:0 .12em;display:inline-block;transform:rotate(-1.5deg)}
```

### 波浪下划线 hover
```css
nav a:hover{text-decoration:underline wavy var(--pink) 2px;text-underline-offset:7px}
```

## 页面骨架
顶栏（黄圆点 brand）→ hero（4 个漂浮几何 + 药丸 kicker + 双色按钮）→ 四张白贴纸卡（各色药丸编号 + 小几何 motif）→ 3px 顶线页脚。

## 动效
wiggle 6s 摆动（形状）；卡片 hover 平移+微旋；按钮按压。幅度都要小（≤7deg / ≤8px）。

## 红线 / 翻车点
- 不设"配额"会变幼儿园：固定四色、形状 ≤6 个、运动幅度要小。
- 点阵底密度别调大（30px 格起步）。
- 一张卡一个主色，别在同一卡上堆三色。
