# 06 · 新拟态 Neumorphism

> 从同一种材质里"挤"出来的接口，像捏一块软塑料。
> 关键词：同色表面 / 双向柔影 / 按压凹陷 / 大圆角

- **适合**：仪表盘、控制面板、单主题小工具页
- **不适合**：高密度信息页；强无障碍要求场景（对比度天然偏低，NN/g 点名过）
- **参考实现**：`../06-neumorphism.html` · 截图 `../_shots/06-neumorphism.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 表面 = 背景 | `#e8ecf3`（关键：同色） |
| 暗影 | `#c5ccd9` |
| 亮影 | `#ffffff` |
| 文字 | `#3d4657` / 次级 `#7b8598` |
| 强调 | `#4f5dcc`（只给图标、数字、文字强调） |
| 字体 | `"Segoe UI","Microsoft YaHei UI","Microsoft YaHei"` |
| 圆角 | 18–24px（大圆角，直角会破功） |

## 签名配方

### 三套阴影变量（核心）
```css
:root{
  --raise:9px 9px 20px var(--sh-dark),-9px -9px 20px var(--sh-light);          /* 凸起（大） */
  --raise-sm:6px 6px 14px var(--sh-dark),-6px -6px 14px var(--sh-light);       /* 凸起（小） */
  --press:inset 5px 5px 11px var(--sh-dark),inset -5px -5px 11px var(--sh-light); /* 凹陷 */
}
```

### 按压反馈（灵魂：凸起 ⇄ 凹陷切换）
```css
.btn{border-radius:18px;background:var(--bg);box-shadow:var(--raise);transition:box-shadow .35s,transform .2s}
.btn:active{box-shadow:var(--press);transform:none;color:#3d48a8}
```
所有可点元素都必须有 `:active` 凹陷态，否则"软塑料"出不来。

### 凹陷圆槽里嵌数字
```css
.dot{width:58px;height:58px;border-radius:50%;box-shadow:var(--press);color:var(--accent);
     display:flex;align-items:center;justify-content:center;text-shadow:1px 1px 1px #fff}
```

### 文字"压印"效果
```css
h1{text-shadow:1px 1px 1px #fff,-1px -1px 2px rgba(120,132,155,.35)}
```

## 页面骨架
凸起面板式导航（radius 22，整条一体）→ 居中 hero（凹陷药丸 chip + 压印大标题 + 双凸起按钮）→ 四张凸起卡片（各含凹陷圆槽数字）→ 页脚。

## 动效
过渡集中在 box-shadow / transform（0.35s）——"按压"就是动效的全部；hover 只有 1–3px 浮起。

## 红线 / 翻车点
- 对比度是先天病：文字层级别指望影子，要用颜色/字重补；正文别浅于 `#7b8598`。
- 表面色必须 = 背景色；换任何一色都会"漏气"。
- 圆角要大（18–24px）；到处是柔和影子时，页面别塞太多元素，会糊成一坨。
