# 04 · 暗调奢华 Luxury / High-end

> 昂贵感 = 稀有 + 克制。金色只在一个地方发光。
> 关键词：近黑暖调 / 暖金 / 居中纪念性构图 / 广字距 / 缓慢流光

- **适合**：奢侈品、酒店、高端服务、纪念性官网
- **不适合**：高频交互工具、信息密集型页面
- **参考实现**：`../04-luxury.html` · 截图 `../_shots/04-luxury.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 底 | `#0d0c0a`（近黑暖调） |
| 金 | `#c9a55a`（主）/ `#e8cf8e`（亮）/ `#8f6f2e`（深，渐变端点） |
| 文字 | `#ece6da`（暖白） |
| 次级 | `#9a8f7a` |
| 金线 | `rgba(201,165,90,.22)`（1px 分隔线） |
| 字体 | 标题 `Georgia…serif`；正文 `"Microsoft YaHei"` 300 字重，行高 2.2 |
| 容器 | `max-width:1080px; padding:0 48px; text-align:center`（全居中） |

## 签名配方

### 背景顶部一抹金光
```css
body{background-image:radial-gradient(1200px 520px at 50% -8%,rgba(201,165,90,.09),transparent 60%)}
```

### 金渐变品牌字 + 流光
```css
.monogram{
  background:linear-gradient(100deg,#8f6f2e 0%,#e8cf8e 38%,#f8ecc2 50%,#e8cf8e 62%,#8f6f2e 100%);
  background-size:220% 100%;-webkit-background-clip:text;background-clip:text;color:transparent;
  animation:sheen 8s linear infinite;
}
@keyframes sheen{to{background-position:220% 0}}
```

### 菱形分隔 + 渐隐金线
```css
.rule{display:flex;align-items:center;justify-content:center;gap:18px;color:var(--gold);font-size:9px}
.rule::before,.rule::after{content:"";width:120px;height:1px}
.rule::before{background:linear-gradient(90deg,transparent,var(--gold))}
.rule::after{background:linear-gradient(90deg,var(--gold),transparent)}
```
HTML 里放 `◆`。

### 幽灵按钮（hover 才有金）
```css
.btn{border:1px solid var(--gold);color:var(--gold-2);padding:15px 46px;letter-spacing:.36em;text-indent:.36em;transition:all .5s}
.btn:hover{background:linear-gradient(100deg,#8f6f2e,#e8cf8e,#8f6f2e);color:#211a0c;border-color:transparent}
```

### 入场：极慢浮现
```css
@keyframes fade-up{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:none}}
.hero>*{animation:fade-up 1.6s cubic-bezier(.16,.84,.44,1) both}  /* 依次 +0.15s 递增 delay */
```

## 页面骨架
居中导航（广字距）→ EST. 行（`EST. MMXXVI · 灵感记录`）→ 金渐变巨字 → 小字 SHIGUANG → ◆ 分隔 → h1 → lede → 双按钮 → 四栏特性（罗马数字 I–IV）→ 页脚。

## 动效
金字流光 8s；入场 1.6s 缓浮（错峰 0.15s）；按钮 hover 0.5s——一切都"慢"。

## 红线 / 翻车点
- 金用多了就俗：金色只给品牌字、罗马数字、按钮边框三处。
- 留白不足会变"土豪金"：深底上元素要少、间距要大。
- 正文别用衬线小字（看不清），用细黑体 300；中央构图别塞真实长文。
