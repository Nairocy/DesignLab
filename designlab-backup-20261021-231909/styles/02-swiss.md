# 02 · 瑞士国际主义 Swiss / International Typographic Style

> 清晰、客观、理性。网格是宪法，排版是国王。
> 关键词：非对称栅格 / 无衬线 / 严格左对齐 / 唯一信号红 / 数字锚点

- **适合**：企业官网、机构介绍、年报、数据与秩序感强的产品页
- **不适合**：需要温度、亲和、玩乐或奢华感的主题
- **参考实现**：`../02-swiss.html` · 截图 `../_shots/02-swiss.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 背景 | `#ffffff` |
| 文字 | `#0b0b0b` |
| 信号色 | `#e30613`（全页唯一强调色） |
| 次级灰 | `#6f6f6f` |
| 拉丁字体 | `Helvetica, Arial, sans-serif`；配 `font-feature-settings:"tnum"`（数字等宽） |
| 中文字体 | `"Microsoft YaHei UI","Microsoft YaHei"` |
| 容器 | `max-width:1200px; padding:0 44px` |
| 规则线 | 2px（版口线）/ 1px（分栏线），通体实线，不用阴影 |

## 签名配方（可直接抄）

### 非对称栅格 hero（2fr / 1fr）
```css
.hero{display:grid;grid-template-columns:2fr 1fr;gap:64px}
```
右侧列底部对齐（`justify-content:flex-end`），右下放正文与按钮。

### kicker：红字 + 拖尾横线
```css
.kicker{color:var(--red);font-size:12px;font-weight:700;letter-spacing:.3em;display:flex;align-items:center;gap:14px}
.kicker::after{content:"";width:52px;height:2px;background:var(--red)}
```

### 巨型标题：负字距
```css
h1{font-size:clamp(48px,7.4vw,92px);font-weight:700;line-height:1.04;letter-spacing:-.02em}
```

### 表格化四栏特性（外 2px、内 1px，数字当锚点）
```css
.features{display:grid;grid-template-columns:repeat(4,1fr);border-top:2px solid var(--ink);border-bottom:2px solid var(--ink)}
.feature{padding:26px 26px 52px;border-left:1px solid var(--ink)}
.feature:first-child{border-left:0;padding-left:0}
.feature .num{font-size:38px;font-weight:700;letter-spacing:-.03em}
```

### 按钮：直角实块，hover 变红
```css
.btn{background:var(--ink);color:#fff;padding:15px 32px;font-weight:700;letter-spacing:.1em;transition:background .2s}
.btn:hover{background:var(--red)}
```

## 页面骨架
顶栏（2px 底线）→ hero 左 2fr（kicker+h1）/ 右 1fr（底部对齐 lede+按钮）→ 四栏表格化特性 → 黑底反白页脚。右上角可点缀一个 52px 红方块（全页唯一装饰）。

## 动效
只有按钮的 `background` 过渡（0.2s）。不加入场动画——不用动效本身就是这个风格的一部分。

## 红线 / 翻车点
- 对齐差 1px 就"不够瑞士"：栅格必须严格，左对齐、右不齐是律法。
- 红色只做「信号」（kicker、hover、拖尾线、红方块），绝不进正文当装饰。
- 字号方向：大标题紧字距（负值）、小标签宽字距（0.2em+），别用反。
