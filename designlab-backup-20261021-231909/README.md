# DesignLab · 前端设计风格学习图鉴

用一个练手项目回答一个问题：**同一份内容，换不同的视觉语言，会变成什么？**

同一套产品文案（虚构产品「拾光 SHIGUANG · 灵感记录应用」），用 10 种经典设计风格各实现一遍。
文字一字不差，变化的全是视觉语言——字体、色彩、空间、质感、动效。

## 目录结构

```
DesignLab/
├── index.html              图鉴首页（卡片导航 + 通用原则 + 延伸阅读）
├── 02-swiss.html           瑞士国际主义 Swiss Style
├── 03-editorial.html       杂志编辑风 Editorial
├── 04-luxury.html          暗调奢华 Luxury
├── 06-neumorphism.html     新拟态 Neumorphism
├── 07-brutalism.html       粗野主义 Brutalism
├── 09-cyberpunk.html       赛博朋克 Cyberpunk
├── 10-zen.html             和风侘寂 Wabi-sabi
├── 11-memphis.html         孟菲斯 Memphis
├── 12-bauhaus.html         包豪斯 Bauhaus
├── 13-neo-brutalism.html    新粗野主义 Neo-Brutalism（可切深浅主题）
├── styles/                 风格规范 md（写前端参考）
├── _shots/                 无头 Edge 验收截图
└── README.md               本文件（学习笔记）
```

10 个页面均为**零依赖单文件**，双击即可打开；右下角有「返回图鉴」胶囊。

## 写前端参考（styles/）

每个风格的设计 Token、签名 CSS 配方与红线整理在 `styles/`，写前端时按需取用：

- `styles/02-swiss.md` — 瑞士国际主义：栅格秩序
- `styles/03-editorial.md` — 杂志编辑风：衬线与阅读节奏
- `styles/04-luxury.md` — 暗调奢华：金 + 衬线 + 广字距
- `styles/06-neumorphism.md` — 新拟态：同色浮雕
- `styles/07-brutalism.md` — 粗野主义：硬骨架
- `styles/09-cyberpunk.md` — 赛博朋克：霓虹故障
- `styles/10-zen.md` — 和风侘寂：竖排留白
- `styles/11-memphis.md` — 孟菲斯：玩乐几何
- `styles/12-bauhaus.md` — 包豪斯：三原色构成
- `styles/13-neo-brutalism.md` — 新粗野主义：硬边线框（含双主题）

## 统一内容源（10 页共用）

| 部位 | 文案 |
|---|---|
| 品牌 | 拾光 SHIGUANG |
| 导航 | 功能 / 定价 / 关于 |
| 引导语 | 灵感记录，轻如羽毛 |
| 标题 | 把灵感，留在拾光 |
| 简介 | 一闪而过的想法最珍贵。拾光帮你随手捕捉、自动整理，让每一次创作都从从容容。 |
| 按钮 | 立即体验 / 了解更多 |
| 特性 1 | 一秒捕捉 — 打开即写，灵感不过夜。 |
| 特性 2 | 多端同步 — 手机、平板与桌面，实时同步。 |
| 特性 3 | 极简专注 — 只保留纸与笔的纯粹。 |
| 特性 4 | 全平台 — 网页版随时可用，无需安装。 |
| 页脚 | © 2026 拾光 SHIGUANG · 保留所有权利 |

各页只改这些文字的**呈现方式**。个别风格有极少量装饰性文字（如刊号 NO.07、章节题头、跑马灯重复文案、状态栏标签），均为版式需要，不是内容差异。

## 五个观察透镜（对照时挨着看）

1. **字体**：衬线还是无衬线？字重和字距在传递什么情绪？
2. **色彩**：一共几个色？强调色占多少、用在哪？背景是纸还是黑？
3. **空间**：留白是奢侈还是拥挤？元素靠什么对齐：网格还是轴心？
4. **质感**：平面、玻璃、浮雕还是纸纹？边界用线还是影子？
5. **动效**：有动画吗？快还是慢？它服务于什么状态？

---

## 10 个风格笔记

### 02 瑞士国际主义 Swiss / International Typographic Style
- **理念**：清晰、客观、理性；网格是宪法，排版是国王（1950s 苏黎世/巴塞尔）。
- **手法**：非对称栅格；Helvetica 式无衬线；左对齐右不齐；红=唯一信号色；数字（01–04）当锚点。
- **CSS 关键点**：`grid-template-columns:2fr 1fr` 非对称、实线表格化分栏、`::after` 红线、`font-feature-settings:"tnum"`。
- **场景**：企业官网、年报、机构页面。**翻车点**：对齐差 1px 就"不够瑞士"；网格不严格时风格立刻塌。

### 03 杂志编辑风 Editorial
- **理念**：网页当印刷刊物编排，阅读节奏优先（Vogue / Esquire 气质）。
- **手法**：居中报头 + 粗细双线；双栏通版；首字下沉；四栏"小文章"竖线分隔；衬线字体（Georgia / 宋体）。
- **CSS 关键点**：`::first-letter` 首字下沉、双线用 `border-top:3px + border-bottom:1px` 叠加、`grid:7fr/5fr`。
- **场景**：博客、专栏、内容平台。**翻车点**：衬线字号过小会糊；分栏线过深抢正文。

### 04 暗调奢华 Luxury
- **理念**：昂贵感 = 稀有 + 克制；金色只在一个地方发光。
- **手法**：深黑底 + 暖金；居中纪念性构图；广字距；罗马数字与菱形分隔符；缓慢流光。
- **CSS 关键点**：`background-clip:text` 金渐变文字、`letter-spacing:.24em+`、`@keyframes sheen` 流光。
- **场景**：奢侈品、酒店、高端服务。**翻车点**：金用多了就俗；黑底留白不足会变"土豪金"。

### 06 新拟态 Neumorphism
- **理念**：从同一种材质里"挤"出的接口，像捏一块软塑料。
- **手法**：背景 = 表面同色；一明一暗双向柔影；按压时影子翻转为内嵌。
- **CSS 关键点**：`box-shadow:9px 9px 20px #c5ccd9,-9px -9px 20px #fff`、`:active` 切换 `inset` 阴影。
- **场景**：仪表盘、面板组件。**翻车点**：对比度天然偏低（NN/g 明确警示过无障碍）——文字层级别指望影子，要用颜色/字重补。

### 07 粗野主义 Web Brutalism
- **理念**：把骨架暴露出来；对精致主义的坦率反动。
- **手法**：4px 黑描边 + 零模糊硬阴影；跑马灯；倾斜贴纸；巨型标题；hover 按压位移。
- **CSS 关键点**：`box-shadow:7px 7px 0 #2500ff` 硬阴影、`@keyframes tick` + `translateX(-50%)` 无缝跑马灯。
- **场景**：创意机构、作品集、艺术项目。**翻车点**："故意的乱"需要更狠的克制——层级、可点击性、移动端一条都不能少，否则只是没设计。

### 09 赛博朋克 Cyberpunk
- **理念**：高技低生活的街头未来；霓虹、故障、监控感。
- **手法**：黑底霓虹（青/品红/黄）；暗角 + 扫描线双层；标题故障分片；HUD 四角括号；等宽字体。
- **CSS 关键点**：`repeating-linear-gradient` 扫描线、双伪元素 + `clip-path:inset()` glitch、`text-shadow` 色散。
- **场景**：游戏、活动页、音乐潮牌。**翻车点**：全部发光 = 全部不发光——高亮留给 1–2 处；长文阅读页别用。

### 10 和风侘寂 Wabi-sabi
- **理念**：不完美、不对称、留白即「间」。
- **手法**：竖排题头；素纸底 + 纤维点；一笔留缺的墨圈；朱印是全页唯一的红。
- **CSS 关键点**：`writing-mode:vertical-rl` + `text-orientation:upright`、点阵纸纹 `radial-gradient`、SVG 手绘墨圈。
- **场景**：茶室、民宿、文化品牌、随笔。**翻车点**：竖排是装饰不是正文（正文保持横排）；行距一紧就失去"空气感"。

### 11 孟菲斯 Memphis
- **理念**：1981 米兰；对极简的嬉皮笑脸式反叛，装饰无罪。
- **手法**：点阵底 + 漂浮波浪/圆环/三角（缓慢摇摆）；贴纸卡片（硬阴影 + hover 微旋转）；四色点彩。
- **CSS 关键点**：点阵底 `radial-gradient + background-size`、`@keyframes wiggle`、硬阴影 + hover 位移。
- **场景**：电商活动、年轻品牌、播客。**翻车点**：不设"配额"会变幼儿园——固定四色、形状 ≤6 个、运动幅度要小。

### 12 包豪斯 Bauhaus
- **理念**：形式追随功能；基本几何 + 原色构成（1919 魏玛）。
- **手法**：红黄蓝只做形状不做渐变；正交构成；竖排题头栏；几何图案与功能一一对应。
- **CSS 关键点**：`clip-path:polygon()` 三角形、`border-radius:999px 999px 0 0` 半圆、`writing-mode` 竖排。
- **场景**：设计工作室、展陈、教育机构。**翻车点**：几何形状要有构图职责，不能沦为贴纸；原色面积配比失衡会显廉价。

### 13 新粗野主义 Neo-Brutalism（内核同构 nairocy.com 主站）
- **理念**：粗野主义的可用化分支——保留直角、硬边、硬阴影的态度，但把配色系统化、可读性拉满；从"反精致"进化为"另一种精致"。
- **手法**：3px 实边框 + 零模糊硬阴影（默认 4px/8px 双层：黑色 + 主色半透明；hover 涨到 8px/12px 并位移 -4px）；每卡一色撞色系统；卡片瀑布式微旋转（±0.8°），hover 摆正；像素角标（::before/::after，14px，hover 显现）；错峰入场。
- **CSS 关键点**：CSS 变量双主题（html[data-theme] 切换 + 原生 JS + localStorage 持久化）；rotate 独立属性与 transform 入场动画互不冲突；深色主题下边框从深色版换亮色版。
- **场景**：个人品牌站、创意工作室、作品集；多子站/多产品尤其合适（每站一色当标签）。**翻车点**：硬阴影位移要和边框宽度、hover 位移同向配套，否则视觉上"卡片会飞"；撞色只给边框/标签/链接三处，侵入正文就乱；深色主题别忘换边框色，否则黑边埋进黑底。
- **另注**：本页默认浅色主题，右上角按钮可切深色——顺带演示"主题驱动卡片变色"的约定。

---

## 通用原则速查（10 页共同底线）

1. **8pt 间距节奏**：间距取 8 的倍数，秩序从数字开始。
2. **字阶而非孤立的字号**：3–4 级，级差 ≥1.25 倍。
3. **对比度是红线**：正文 ≥ 4.5:1（新拟态尤其危险）。
4. **一页一强调色**：强调色只给"行动"，不给装饰。
5. **对齐有系统**：要么网格，要么轴心，别"差不多对齐"。
6. **动效服务状态**：入场 ≤ 1s、缓动自然；优先动 transform / opacity。
7. **留白即层级**：空白本身在引导视线。
8. **无障碍底线**：`prefers-reduced-motion`、focus 可见、点击区 ≥ 44px（10 页已内置）。

## 参考资料（检索于 2026-10-04）

- Tilda Education — Popular Web Design Styles: <https://tilda.education/en/web-design-styles>
- Kevin Liu's Wiki — Website Design Styles（风格适用场景与翻车点对照表）: <https://wiki.kevinliu.biz/wiki/design/website-design-styles>
- Web Design Lookbook（Swiss / Brutalism 视觉研究）: <https://webdesignlookbook.webflow.io/>
- UI Style Guide — 67 Interactive Design Styles: <https://www.uistyleguide.com/>
- Figma — Top Web Design Trends 2026: <https://www.figma.com/resource-library/web-design-trends/>
- Fireart Studio — Web Design Trends 2026（Tactile Brutalism）: <https://fireart.studio/blog/the-best-web-design-trends/>
- ui-ux-stylepedia（50+ 风格交互合集，开源可读源码）: <https://github.com/sailesh-01/ui-ux-stylepedia>

## 复用提示

- 全局替换「拾光 / SHIGUANG」与表格里的几段文案，页面即刻变你自己的产品页；
- 每个文件顶部都有注释标明风格名，便于对号入座；
- 右下角"返回图鉴"胶囊位于 `</body>` 前最后一行，不需要就直接删。
