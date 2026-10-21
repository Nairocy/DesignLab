# 14 · 构成主义 Constructivism

> 1920s 苏联海报的动员感：红黑两色、45° 斜带、粗窄体大字，版面像一台正在运转的机器。
> 关键词：红黑双色 / 45° 斜带 / 粗窄体 / 竖排编号 / 海报块

- **适合**：展览、戏剧、音乐演出、政治/社会议题、工业品牌
- **不适合**：母婴、甜品、需要温柔感的服务；也不适合多语言长文案
- **参考实现**：`../14-constructivism.html` · 截图 `../_shots/14-constructivism.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 纸底 | `#e9e1d0`（旧纸米色） |
| 红 | `#c8102e`（唯一彩色） |
| 墨 | `#141414` |
| 米白 | `#f4efe2` |
| 字体 | 标题 `"Oswald","Impact","Arial Narrow","Haettenschweiler","Microsoft YaHei"`；正文 `"Helvetica Neue",Helvetica,Arial,"Microsoft YaHei"` |
| 容器 | `max-width:1240px` · `padding:0 clamp(20px,4.2vw,52px)` |
| 边框 | `3px solid #141414` |
| 硬影 | `14px 14px 0 #141414`（海报块）/ `9px 9px 0`（小件） |

## 签名配方

### 45° 宽斜带
```css
.band{position:absolute;display:block;transform:rotate(-45deg);transform-origin:center}
.band-a{width:1750px;height:190px;left:72%;top:58%;margin:-95px 0 0 -875px}
.band-a i{display:block;width:100%;height:100%;background:var(--red);animation:bandIn 1.3s cubic-bezier(.16,.86,.3,1) both}
```
用「超长条 + 负半宽高居中 + rotate(-45deg)」画对角线，比 `clip-path` 更稳；`bandIn` 让它沿带轴滑入。

### 斜置海报块（hero 的视觉锤）
```css
.plate{border:3px solid var(--ink);box-shadow:14px 14px 0 var(--ink);transform:rotate(4deg)}
```
红色大色块 + 超细描边 + 大偏移硬影，内部放巨大数字或字母，整块相对页面倾斜 3–6°。

### 竖排编号
```css
.num{writing-mode:vertical-rl;text-orientation:upright}
```
特性编号拆成「0 / 1」两行竖排（或竖直渲染），是俄式排版的标志性细节。

### 粗窄体 + 红黑分工
标题全大写 Oswald/Impact（窄体），正文回到常规黑体且字号偏小——**大字喊、小字说**，对比就是动员感。

## 页面骨架
顶栏（红菱形 + 品牌 + 细线导航）→ hero（左上斜置标题 + 红色大色块海报 + 45° 斜带贯穿 + 箭头指向按钮）→ 白底/米底分隔 → `04 MANIFESTO` 大数字 + 竖排编号的四栏特性（红细线分隔）→ 页脚（黑底红字）。

## 动效
`bandIn`（1.3s，斜带沿轴滑入）、`rise`（文字块错位归位）、`plateIn`（海报块落下）。`prefers-reduced-motion` 全关。

## 红线 / 翻车点
- **只有红黑白**：加入第三种彩色（哪怕一点蓝）立刻失去 1920s 苏联海报的年代感。
- **斜带必须够长**：1750px 级别；短条只会像一条红线，不会形成「版面被切开」的力量。
- **小屏裁切**：斜带超宽，容器必须 `overflow:hidden`，否则横向滚动条。
- **字号对比夸张**：标题 100px+ 与正文 14px 并存；字号接近就变成普通复古风。
- **硬影方向固定右下**：海报块与按钮同向，反了会显得「贴纸浮起来」。
