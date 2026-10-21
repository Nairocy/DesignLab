# 02 · 杂志编辑风 Editorial / Magazine

> 网页当印刷刊物编排，阅读节奏优先。
> 关键词：衬线 / 居中报头 / 粗细双线 / 首字下沉 / 竖线分栏

- **适合**：博客、专栏、内容平台、品牌故事长页
- **不适合**：工具型、功能密集型界面
- **参考实现**：`../02-editorial.html` · 截图 `../_shots/02-editorial.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 纸色 | `#f7f2e8`（米白纸） |
| 墨色 | `#211d17` |
| 次级 | `#6f6757` |
| 分栏线 | `#d8cebb`（1px） |
| 强调色 | `#9e2b25`（暗红，仅给编号/kicker/hover） |
| 字体 | `Georgia,"Times New Roman","Songti SC","SimSun",serif`；行高 1.85–2.05 |
| 容器 | `max-width:1160px; padding:0 44px` |

## 签名配方

### 居中报头 + 粗细双线
```css
.masthead .name{font-size:clamp(44px,6vw,68px);font-weight:700;letter-spacing:.34em;text-indent:.34em}
.rule-double{height:5px;border-top:3px solid var(--ink);border-bottom:1px solid var(--ink)}
```
（letter-spacing 后加等值 text-indent 抵消末字右侧间隙，居中才正。）

### 双栏通版 7fr / 5fr
```css
.spread{display:grid;grid-template-columns:7fr 5fr;gap:56px}
```

### 首字下沉
```css
.lede::first-letter{float:left;font-size:56px;line-height:.82;padding:8px 12px 0 0;font-weight:700;color:var(--accent)}
```

### 四栏"小文章"：竖细线分栏 + 汉字数字
```css
.features{display:grid;grid-template-columns:repeat(4,1fr)}
.feature + .feature{border-left:1px solid var(--rule);padding-left:24px}
.feature .num{font-size:26px;font-style:italic;font-weight:700;color:var(--accent)}
```
编号用「一 二 三 四」（或斜体罗马），别用阿拉伯数字。

### 栏目导航：居中、竖线分隔
```css
nav.cats{display:flex;justify-content:center}
nav.cats a{padding:0 24px;border-right:1px solid var(--rule)}
nav.cats a:last-child{border-right:0}
```

## 页面骨架
meta 行（刊名 + NO.07 / 2026）→ 居中报头（拾光 / SHIGUANG）→ 粗细双线 → 栏目导航 → 7:5 双栏通版（左 kicker+h1，右首字下沉正文+按钮）→ 双线 → 四栏小文章 → 双线 → 版权行。

## 动效
无入场动画；hover 仅颜色过渡（0.3s）。纸面是静的。

## 红线 / 翻车点
- 衬线中文字号别小于 13px（宋体小字发糊）。
- 分栏线过深会抢正文——用 `#d8cebb` 级别的淡线。
- 双线、竖线、留白都服务"阅读节奏"，不是装饰堆料；刊号等"版面文字"越少越好。
