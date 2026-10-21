# 10 · 新粗野主义 Neo-Brutalism

> 对「精致而模糊」的正面反叛：界面像一张张贴纸摞在方格纸上，用纯黑厚边和零模糊实影制造物理厚度。
> 关键词：纯黑厚边 / 零模糊实影 / 高饱和撞色 / 方格纸 / 按压式触觉

- **适合**：独立产品、开发者工具、创意工作室、活动页、个人品牌
- **不适合**：严肃金融政务、需要低调奢华的品牌、长文阅读站
- **参考实现**：`../10-neo-brutalism.html` · 截图 `../_shots/10-neo-brutalism.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 纸底 | `#fdf8ea`（暖白，不是冷灰） |
| 墨 | `#000000`（纯黑，不用 #111 / #1a1a1a） |
| 主强调 | `#ffd93d`（黄，只给主按钮与标题高亮块） |
| 撞色板 | `#ff5f9e` 粉 / `#5ad2ff` 青 / `#c8f54a` 青柠 / `#b79bff` 紫 / `#ff8a4c` 橙 |
| 字体 | 标题 `"Arial Black", Impact, "Microsoft YaHei", sans-serif`；正文 `"Segoe UI","PingFang SC","Microsoft YaHei",Arial`；编号/小标签 `Consolas, monospace` |
| 容器 | `max-width:1160px` · `padding:0 40px`（小屏 22px） |
| 边框 | 主体 `3px solid #000`；导航/细件 `2px solid #000` |
| 硬影 | 按钮 `7px 7px 0 #000`；卡片 `8px 8px 0 #000`；小件 `4px 4px 0 #000` |
| 圆角 | 一律 0（返回胶囊除外，那是导航件） |

**红线：页面上不允许出现任何 blur、渐变、半透明表面。** 深度只能来自「实色偏移」和「黑边」。

## 签名配方

### 方格纸可见网格（整页底层）
```css
body{
  background:#fdf8ea;
  background-image:
    repeating-linear-gradient(0deg,rgba(0,0,0,.055) 0 1px,transparent 1px 34px),
    repeating-linear-gradient(90deg,rgba(0,0,0,.055) 0 1px,transparent 1px 34px);
}
```
网格让页面像草稿纸，是「结构可见」的直接表达；34px 一格，线用 5% 黑，别加深到抢内容。

### 厚边 + 零模糊实影（风格的定义性一招）
```css
.card{border:3px solid #000;box-shadow:8px 8px 0 #000;background:#fff}
.btn{border:3px solid #000;box-shadow:7px 7px 0 #000}
```
`box-shadow` 的第三个参数（blur）必须是 0、颜色必须不透明。一旦写成 `0 8px 20px rgba(0,0,0,.2)` 就变回了普通卡片，风格立刻消失。

### 按压式触觉（按下时向影子方向压进去）
```css
.btn:hover{transform:translate(-3px,-3px);box-shadow:10px 10px 0 #000}
.btn:active{transform:translate(4px,4px);box-shadow:2px 2px 0 #000}
```
位移与阴影必须同向（右下）。hover 是「抬离纸面」，active 是「按回纸面」——这一对动作就是触感来源。

### 每卡一色的撞色系统
```css
.card.c1{background:#ff5f9e}
.card.c2{background:#5ad2ff}
.card.c3{background:#ffd93d}
.card.c4{background:#b79bff}
.card p{color:#000;font-weight:500}   /* 撞色底上一律黑字，保证对比度 */
```
撞色只铺在**容器**上，不铺正文；四个色块把「四个特性」自然分组成四个区。

### 标题高亮块（黄底 + 黑边 + 实影 + 微旋转）
```css
h1 em{
  font-style:normal;display:inline-block;background:#ffd93d;
  border:3px solid #000;box-shadow:7px 7px 0 #000;
  padding:0 .1em;transform:rotate(-1.6deg);
}
```
高亮不是一个色块背景，而是一张「贴上去的纸」——有边、有影、有角度。

### 贴纸与星形装饰
```css
.sticker{position:absolute;transform:rotate(9deg);background:#c8f54a;
  border:3px solid #000;box-shadow:6px 6px 0 #000}
```
星形用 SVG polygon 手绘（12 角），填充撞色 + 4px 黑描边；装饰件同样要遵守「厚边 + 硬影」。

## 页面骨架
顶栏（品牌方块标 + 描边导航）→ hero（方格纸底 + 贴纸 + 星形 + 引导 chip + 超大标题 + 高亮 em + 双按钮）→ 2×2 撞色卡片墙（描边 SVG 图标 + 黑色编号块 + 标题 + 一句描述）→ 黑底信息带 → 页脚（白底 + 描边标签）。

## 动效
入场 `pop`（0.55s，`cubic-bezier(.2,.7,.35,1)`，卡片错峰 0.08s）；hover 抬升 / active 压入（0.12–0.14s）。全部只动 `transform` 与 `box-shadow`，不动布局。`prefers-reduced-motion` 全关。

## 红线 / 翻车点
- **模糊即破功**：任何 blur、渐变、半透明卡片、柔和阴影都会把这套语言打回「普通平面设计」。
- **厚边要统一**：2px（细件）与 3px（主体）两档就够，混用四五种粗细会像手滑。
- **撞色只给容器**：正文、图标、按钮文字保持纯黑；把荧光色铺到正文上直接不可读。
- **对比度验收**：粉/青/黄/紫底配黑字均 ≥ 7:1；若改用浅色系撞色必须重测。
- **按压方向必须与影子同向**：hover 往左上抬、active 往右下压，反了就「卡片在飞」。
- **小屏**：`<=880px` 卡片转单列，贴纸从绝对定位改为文档流、星形隐藏，否则会压住标题。
