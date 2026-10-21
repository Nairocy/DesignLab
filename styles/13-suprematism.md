# 13 · 至上主义 Suprematism

> 1915 年马列维奇的《黑方块》：把世界剥到只剩形与色，让几何体在无垠白底上漂浮。
> 关键词：纯几何 / 无限留白 / 原色四枚 / 无阴影无描边 / 极慢漂移

- **适合**：艺术机构、建筑事务所、出版、先锋品牌、展览海报
- **不适合**：信息密集型产品页、需要强 CTA 转化的电商
- **参考实现**：`../13-suprematism.html` · 截图 `../_shots/13-suprematism.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 底 | `#f4f1e8`（象牙白，不用纯白） |
| 墨 | `#0d0d0d` |
| 红 | `#c8102e` |
| 土黄 | `#e8b800` |
| 群青 | `#1a3a8f` |
| 细线 | `rgba(13,13,13,.2)` |
| 字体 | `"Century Gothic","Futura","Avenir Next","Trebuchet MS","Microsoft YaHei"`，字重 300–500 |
| 容器 | `padding: clamp(22px,5vw,64px)`，内容区最宽 1320px |

## 签名配方

### 漂浮形体（本风格的全部装饰）
```css
.shape{position:absolute;display:block;pointer-events:none;z-index:1}
/* 纯色、无阴影、无描边；只有圆需要 border-radius */
.s-cross{bottom:30%;right:38%;width:clamp(56px,6.6vw,90px);aspect-ratio:1;transform:rotate(34deg)}
```
形体的角度是「手放上去的」：17° / -12° / -28° / 34°，每个都不一样，绝不正交对齐。

### 极慢漂移
```css
@keyframes drift-a{0%,100%{transform:rotate(17deg) translate(0,0)}50%{transform:rotate(19.5deg) translate(-4px,7px)}}
.s-black{animation:drift-a 34s ease-in-out infinite}
.s-red{animation:drift-b 26s ease-in-out infinite}
.s-ochre{animation:drift-c 40s ease-in-out infinite}
```
26–40s 一轮、位移 4–10px、旋转 ±2–3°。**慢到几乎察觉不到**才对——快了就成动画贴纸。

### 无装饰分栏
```css
.rule{border-top:1px solid var(--line)}
```
特性区不用卡片、不用底色，只用 1px 细线分四栏；「没有容器」本身就是至上主义的禁欲。

### 巨大留白
hero 高度 ≥70vh，形体总面积不超过版面 25%。留白不是空，是构图的一部分——删掉留白，风格立刻消失。

## 页面骨架
顶栏（文字导航，无底边）→ hero（左侧小方块 + 引导语 + 大字标题 + 简介 + 黑底按钮；右侧漂浮几何组）→ 细线 → 四栏特性（每栏顶部一个小几何组合图标）→ 页脚（底部三色小方块收尾）。

## 动效
`fade-up` 入场（0.5s 透明度 + 位移）；5 个形体各自 26–40s 漂移。`prefers-reduced-motion` 全关。

## 红线 / 翻车点
- **形体必须克制**：占版面 >25% 就从「至上主义」退化成几何插画页。
- **不许有阴影/渐变/纹理**：形体是纯色块，加一层柔影就变 2010 年的拟物风。
- **原色最多四枚**：黑白 + 红黄蓝，第五种颜色一出现就俗。
- **小屏收敛**：`overflow:hidden` + 形体缩小或隐藏，否则绝对定位会撑出横向滚动条。
- **字体别抢戏**：几何无衬线、字重细、字距大；粗黑标题会把形体压死。
