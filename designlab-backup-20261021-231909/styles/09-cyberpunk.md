# 09 · 赛博朋克 Cyberpunk

> 高技低生活的街头未来；霓虹、故障、监控感。
> 关键词：黑底霓虹 / 扫描线 / 故障字效 / HUD 四角括号 / 等宽字体

- **适合**：游戏、活动页、音乐潮牌、开发者彩蛋页
- **不适合**：长文阅读页、温和的商务场景
- **参考实现**：`../09-cyberpunk.html` · 截图 `../_shots/09-cyberpunk.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 底 | `#05050a`（比黑更冷） |
| 青 | `#00f0ff`（主信号） |
| 品红 | `#ff2d9b`（副信号/hover） |
| 黄 | `#f7e017`（点缀：代号数字） |
| 文字 | `#e8fbff` / 次级 `#7fa8b8` |
| 线 | `rgba(0,240,255,.35)` |
| 面板底 | `rgba(0,240,255,.045)` |
| 字体 | 全站 `Consolas,"Cascadia Mono"` 等宽；中文回退雅黑 |

## 签名配方

### 暗角 + 扫描线双层覆盖（灵魂）
```css
body::before{content:"";position:fixed;inset:0;pointer-events:none;z-index:49;
  background:radial-gradient(120% 90% at 50% 40%,transparent 55%,rgba(0,0,0,.55))}
body::after{content:"";position:fixed;inset:0;pointer-events:none;z-index:50;
  background:repeating-linear-gradient(0deg,rgba(255,255,255,.028) 0 1px,transparent 1px 3px)}
```
内容区和 `.wrap` 记得 `z-index:1`，别被盖住。

### 故障字效（双伪元素 + clip-path 分片 + steps(1) 闪现）
```css
.glitch{position:relative;display:inline-block}
.glitch::before,.glitch::after{content:attr(data-text);position:absolute;left:0;top:0;width:100%}
.glitch::before{text-shadow:-2px 0 var(--magenta);clip-path:inset(0 0 62% 0);animation:glitch-a 3.8s infinite steps(1)}
.glitch::after{text-shadow:2px 0 var(--cyan);clip-path:inset(58% 0 0 0);animation:glitch-b 3.8s infinite steps(1)}
```
HTML：`<span class="glitch" data-text="把灵感，">把灵感，</span>`。
故障只在 3.8s 周期里 ~15% 的时间闪现，其余透明——别常亮。

### HUD 四角括号
```css
.card{position:relative;border:1px solid var(--line);background:var(--panel)}
.card::before,.card::after{content:"";position:absolute;width:12px;height:12px;border-color:var(--cyan);border-style:solid}
.card::before{top:-1px;left:-1px;border-width:2px 0 0 2px}
.card::after{bottom:-1px;right:-1px;border-width:0 2px 2px 0}
```

### 霓虹按钮（外发光 + 内发光）
```css
.btn{border:1px solid var(--magenta);color:var(--magenta);
  box-shadow:0 0 14px rgba(255,45,155,.45),inset 0 0 14px rgba(255,45,155,.12);transition:.3s}
.btn:hover{background:var(--magenta);color:#05050a;box-shadow:0 0 28px rgba(255,45,155,.8)}
```

### 光标闪烁
```css
.blink{animation:blink 1.2s steps(2) infinite}
@keyframes blink{50%{opacity:0}}
```

## 页面骨架
HUD 状态条（`拾光 // SHIGUANG.OS` + `VER 2026.10 ▍`）→ 导航（brand 青色发光）→ hero（`> kicker _` + 故障标题 + 双霓虹按钮）→ 四块 HUD 面板（0x01–0x04）→ 页脚（`CYBERPUNK // EOF`）。

## 动效
blink 1–1.2s 步进闪烁（光标）；故障 3.8s 周期闪现；按钮 glow 0.3s。扫描线是静态覆盖层。

## 红线 / 翻车点
- 全部发光 = 全部不发光：高亮只给 1–2 处（青为主、品红为辅）。
- 长文阅读页别用；扫描线会和文字打架。
- 故障字只做在大标题的一个词上，正文不行。
