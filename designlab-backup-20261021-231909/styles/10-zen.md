# 10 · 和风侘寂 Wabi-sabi

> 不完美、不对称、留白即「间」。
> 关键词：竖排题头 / 素纸 / 一笔墨圈 / 一枚朱印 / 大留白

- **适合**：茶室、民宿、文化品牌、随笔、个人主页
- **不适合**：功能密集、需要强调转化效率的页面
- **参考实现**：`../10-zen.html` · 截图 `../_shots/10-zen.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 素纸 | `#f6f2e8` + 纸纹点（`radial-gradient(rgba(51,49,43,.035) 1px,transparent 1px)` / `background-size:24px 24px`） |
| 墨 | `#33312b` |
| 次级 | `#8e8878` |
| 朱印红 | `#b23a2e`（全页唯一红，只用于印与数字） |
| 细线 | `#e0d9c8`（1px） |
| 字体 | `"Kaiti SC","KaiTi","STKaiti","Noto Serif SC","Songti SC",serif`（楷体优先） |
| 行高 | 2.1–2.3（"空气感"的来源） |

## 签名配方

### 竖排题头（左栏一列）
```css
.tate{writing-mode:vertical-rl;text-orientation:upright;border-right:1px solid var(--line);padding-right:34px}
.tate h1{font-size:clamp(28px,3.2vw,40px);font-weight:400;letter-spacing:.46em;line-height:1}
```
竖排只做装饰题头（品牌+标语）；正文一律保持横排。

### 一笔留缺的墨圈（enso，手绘 SVG）
```html
<svg viewBox="0 0 200 200" fill="none">
  <path d="M136 24 C 84 -2, 28 18, 14 64 C 0 110, 26 162, 76 178 C 122 192, 170 166, 180 122 C 186 96, 180 72, 164 52"
    stroke="#33312b" stroke-width="10" stroke-linecap="round" opacity=".88"/>
</svg>
```
首尾留缝（不闭合）+ 轻微 `rotate(-6deg)`——不追求圆满。

### 朱印
```css
.seal{display:inline-block;width:40px;height:40px;background:var(--accent);color:#fdf9ee;
  text-align:center;border-radius:3px;transform:rotate(-3deg);box-shadow:1px 1px 0 rgba(0,0,0,.12)}
```

### 四行细线特性（汉字数字）
```css
.feature{display:grid;grid-template-columns:80px 220px 1fr;gap:28px;padding:30px 8px;border-bottom:1px solid var(--line)}
.feature .num{font-size:20px;color:var(--accent)}  /* 一 二 三 四 */
```

## 页面骨架
细线顶栏 → 左竖排题头（标语 + 标题 + 朱印）｜右 520px 内容（enso 墨圈 + lede + 按钮）→ 四行细线特性 → 页脚。

## 动效
近乎无。只有链接 hover 的 0.4s 变红——连过渡都要"轻"。

## 红线 / 翻车点
- 正文保持横排，竖排仅装饰（可读性优先）。
- 行距一紧就失去"空气感"：line-height 别低于 2。
- 朱印红全页只一处；多了就变"喜庆"而不是"侘寂"。
