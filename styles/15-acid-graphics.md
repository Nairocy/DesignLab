# 15 · 酸性设计 Acid Graphics

> 后网络的锐舞海报：荧光色在纯黑里发光，铬金属球和失真字体一起把屏幕变成一台坏掉的显示器。
> 关键词：荧光三色 / 液态铬 / 透视网格 / 噪点颗粒 / 色散字

- **适合**：电子音乐、潮流服饰、游戏、Web3、面向 Z 世代的品牌活动
- **不适合**：政务医疗金融、严肃 B 端后台、需要长文阅读的官网
- **参考实现**：`../15-acid-graphics.html` · 截图 `../_shots/15-acid-graphics.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 底 | `#08080c`（外层）/ `#0b0b12`（区块） |
| 酸性绿 | `#ccff00` |
| 品红 | `#ff00c8` |
| 电青 | `#00fff0` |
| 紫 | `#7b2bff` |
| 正文 | `#f2f3f8`，次级 `#d8d8e0` |
| 细线 | `rgba(255,255,255,.14)` |
| 字体 | 标题 `"Arial Black",Impact,"PingFang SC","Microsoft YaHei"`；正文 `"Segoe UI","Helvetica Neue","PingFang SC"`；小标签 `Consolas,"Courier New",monospace` |
| 容器 | `max-width:1180px` · `padding:0 40px` |

## 签名配方

### 荧光光球（背景的体积）
```css
.orb{position:absolute;border-radius:50%;opacity:.5;will-change:transform}
.orb-a{width:44vw;height:44vw;top:-13vw;left:-9vw;
  background:radial-gradient(circle at 50% 50%,rgba(204,255,0,.62) 0%,rgba(204,255,0,.34) 26%,rgba(150,200,0,.14) 50%,rgba(204,255,0,0) 72%);
  animation:drift 32s ease-in-out infinite}
```
每颗球是 4 段 rgba 渐变 + 整体 opacity .5；`vw` 定尺寸保证任意屏都够大。三颗（绿/品红/青）分别占据三个角。

### 液态铬（hero 的主角）
```css
background:conic-gradient(from 200deg,#0c0d12 0%,#8f98ad 10%,#f6f9ff 17%,#454b59 27%,
  #0b0c10 38%,#b9c3d6 48%,#5f6676 57%,#111218 68%,#cfd8e8 78%,#6b7386 88%,#0c0d12 100%);
```
`conic-gradient` 的明暗跳变就是金属反射；配合 `border-radius:50%` 与内阴影，立即得到铬球。

### 透视网格地面
```css
.grid-floor{position:absolute;left:50%;bottom:-18vh;width:220vw;height:72vh;
  transform:translateX(-50%) perspective(340px) rotateX(76deg);transform-origin:center bottom;
  background-image:linear-gradient(rgba(0,255,240,.2) 1px,transparent 1px),
                   linear-gradient(90deg,rgba(0,255,240,.2) 1px,transparent 1px);
  background-size:64px 64px}
```
`perspective(340px) + rotateX(76deg)` 把平面网格压成地面；网格线透明度 ≤.2，否则抢内容。

### 噪点颗粒层
```css
.grain{position:fixed;inset:-25%;z-index:4;pointer-events:none;opacity:.055;
  background-image:url("data:image/svg+xml,...feTurbulence type='fractalNoise'...")}
```
内联 SVG `feTurbulence` 生成噪声（无外部图片）；opacity 5.5% 恰好盖住渐变断层又不脏。

### 色散字（chromatic aberration）
```css
text-shadow:3px 0 0 rgba(255,0,200,.55), -3px 0 0 rgba(0,255,240,.45);
```
左右各偏移 3px 的品红/青色散，模拟镜头色差；偏移超过 4px 会变成重影。

## 页面骨架
顶栏（荧光描边方块标）→ hero（超大色散标题 + 右侧铬球 + 荧光绿主按钮 + LIQUID CHROME 标签）→ 跑马灯信息带 → `FEATURES/04`（描边卡 + 荧光图标 + 右下角 SYSTEM ONLINE 状态）→ 页脚（mono 字 + ACID GRAPHICS / 15）。

## 动效
`drift-a/b/c` 光球漂浮（28–36s）、`grid-run` 网格缓慢滚动、`jitter` 标题微抖、`blob` 变形。全部 ≥25s 或幅度 ≤2px，`prefers-reduced-motion` 全关。

## 红线 / 翻车点
- **正文不许荧光**：荧光绿/品红只做装饰、描边、按钮底；正文用 `#f2f3f8`，否则黑底荧光字读三行就花。
- **黑要够黑**：底 `#08080c` 起，用 `#1a1a22` 当底会立刻显脏。
- **光球 opacity ≤.55**：太亮会盖掉文字；球只做环境光，不做主体。
- **网格线 ≤.2 透明度**：超过就变成 80 年代 synthwave，不是 acid。
- **噪点必须 fixed 且 pointer-events:none**：否则会拦截点击、滚动时抖动。
- **色散只给主标题**：全站都用 text-shadow 会整体发虚。
