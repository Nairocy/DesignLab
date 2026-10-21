# 13 · 新粗野主义 Neo-Brutalism

> 粗野主义的可用化分支：保留直角、硬边、硬阴影的态度，把配色系统化、可读性拉满。
> 关键词：3px 硬边 / 双层硬阴影 / 撞色系统 / 瀑布微旋 / 像素角标 / 双主题

- **适合**：个人品牌站、创意工作室、作品集、多子站/多产品（每站一色当标签）
- **不适合**：严肃政务金融；圆润亲和型品牌
- **参考实现**：`../13-neo-brutalism.html` · 截图 `../_shots/13-neo-brutalism.png`（及 `-dark.png`）
- **内核来源**：与 nairocy.com 主站同构（含"主题驱动卡片变色"约定）

## 设计 Token

| 项 | 浅色 | 深色（`html[data-theme="dark"]`） |
|---|---|---|
| 底 | `#f4f5fa` | `#0d0f1a` |
| 卡片 | `rgba(255,255,255,.92)` | `rgba(22,26,43,.92)` |
| 文字 | `#1a1d29` | `#e8eaf2` |
| 次级 | `#5b6072` | `#9aa2b8` |
| 结构线 | `#373b52` | `#5b6478` |
| 硬影 | `rgba(0,0,0,.35)` | `rgba(0,0,0,.65)` |

撞色板（每卡一色，三件套 = 主色 / 深色边框版 / 半透明投影）：
```css
--c-1:#ff6b35; --c-1-dark:#9a3412; --c-1-soft:rgba(255,107,53,.38);   /* 橙 */
--c-2:#7c5cff; --c-2-dark:#5b21b6; --c-2-soft:rgba(124,92,255,.38);   /* 紫 */
--c-3:#0ea5e9; --c-3-dark:#075985; --c-3-soft:rgba(14,165,233,.38);   /* 蓝 */
--c-4:#00c2a8; --c-4-dark:#0f766e; --c-4-soft:rgba(0,194,168,.38);    /* 青 */
```
字体：`'Segoe UI','Helvetica Neue','PingFang SC','Microsoft YaHei'`；标签/小件用 `Consolas`。

## 签名配方

### 卡片三件套：直角 + 3px 硬边 + 双层硬阴影
```css
.card.c1{--c:var(--c-1);--c-dark:var(--c-1-dark);--acc-soft:var(--c-1-soft)}
.card{--border-c:var(--c-dark);--accent-text:var(--c-dark);
  border:3px solid var(--border-c);
  box-shadow:4px 4px 0 var(--shadow-hard),8px 8px 0 var(--acc-soft)}
.card:hover{transform:translate(-4px,-4px);rotate:0deg;
  box-shadow:8px 8px 0 var(--shadow-hard),12px 12px 0 var(--acc-soft)}
html[data-theme="dark"] .card{--border-c:var(--c);--accent-text:var(--c)}  /* 深色换亮边 */
```
第二层"主色半透明影"是辨识度来源（黑色只做底味）。

### 瀑布挂画：微旋转 + 错落
```css
.card{rotate:-.8deg}                  /* 各卡 ±0.5~0.8deg 不等 */
.card.c2{margin-top:1.3rem}
.card:hover{rotate:0deg}              /* hover 摆正 */
```
用独立 `rotate` 属性（与 `transform` 入场动画互不冲突）。

### 像素角标（hover 显现）
```css
.card::before,.card::after{content:"";position:absolute;width:14px;height:14px;background:var(--c);
  opacity:0;transform:scale(.5);transition:opacity .18s,transform .18s}
.card::before{top:-9px;right:-9px}
.card::after{bottom:-9px;left:-9px}
.card:hover::before,.card:hover::after{opacity:1;transform:scale(1)}
```

### 描边大字背景
```css
.outline-text{color:transparent;-webkit-text-stroke:1px var(--outline);
  font-family:Consolas;font-size:clamp(76px,12.5vw,162px);white-space:nowrap;user-select:none;pointer-events:none}
```

### 双主题切换（原生 JS + localStorage）
```js
var root = document.documentElement;
try { var saved = localStorage.getItem('designlab-theme'); if (saved) root.setAttribute('data-theme', saved); } catch (e) {}
btn.addEventListener('click', function () {
  var next = root.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
  root.setAttribute('data-theme', next);
  try { localStorage.setItem('designlab-theme', next); } catch (e) {}
});
```
变量全部走 `:root` / `html[data-theme="dark"]` 两套；正文/卡片加上 `transition:background .3s,color .3s` 让切换顺滑。

### 错峰入场
```css
@keyframes pop-in{from{opacity:0;transform:translateY(22px)}to{opacity:1;transform:none}}
.card{animation:pop-in .8s cubic-bezier(.22,.61,.36,1) both}
.card:nth-child(1){animation-delay:.05s}   /* 依次 +0.1s */
```

## 页面骨架
顶栏（brand + 主题按钮，均 3px 硬边）→ hero（描边大字背景 + 硬边 chip + `em` 高亮块 + 双按钮）→ 2×2 卡片墙（描边 SVG 图标 + 色号 tag + 标题 + 链接）→ 居中页脚（3px 顶线）。

## 动效
pop-in 入场（0.8s 错峰）；卡片 hover 位移+摆正+角标显现；按钮按压位移；主题切换 0.3s 变色。

## 红线 / 翻车点
- 硬阴影位移要和 border 宽度、hover 位移同向配套（右下），否则视觉上"卡片会飞"。
- 撞色只给边框/标签/链接三处，侵入正文就乱。
- 深色主题别忘了把边框从深色版切到亮色版，否则"黑边埋进黑底"。
- 直角是信仰：radius 一律 0（像素角标也是方的）。
