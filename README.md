# DesignLab · 前端设计风格学习图鉴

用一个练手项目回答一个问题：**同一份内容，换不同的视觉语言，会变成什么？**

同一套产品文案（虚构产品「拾光 SHIGUANG · 灵感记录应用」），用 15 种经典设计风格各实现一遍。
文字一字不差，变化的全是视觉语言——字体、色彩、空间、质感、动效。

## 目录结构

```
DesignLab/
├── index.html               图鉴首页（卡片导航 + 通用原则 + 延伸阅读）
├── 01-swiss.html            瑞士国际主义 Swiss Style
├── 02-editorial.html        杂志编辑风 Editorial
├── 03-luxury.html           暗调奢华 Luxury
├── 04-neumorphism.html      新拟态 Neumorphism
├── 05-brutalism.html        粗野主义 Brutalism
├── 06-cyberpunk.html        赛博朋克 Cyberpunk
├── 07-zen.html              和风侘寂 Wabi-sabi
├── 08-memphis.html          孟菲斯 Memphis
├── 09-bauhaus.html          包豪斯 Bauhaus
├── 10-neo-brutalism.html    新粗野主义 Neo-Brutalism
├── 11-pop-art.html          波普主义 Pop Art
├── 12-op-art.html           欧普主义 Op Art
├── 13-suprematism.html      至上主义 Suprematism
├── 14-constructivism.html   构成主义 Constructivism
├── 15-acid-graphics.html    酸性设计 Acid Graphics
├── styles/                  风格规范 md（写前端参考）
├── _shots/                  无头 Edge 验收截图
└── README.md                本文件（学习笔记）
```

15 个页面均为**零依赖单文件**，双击即可打开；右下角有「返回图鉴」胶囊。

## 写前端参考（styles/）

每个风格的设计 Token、签名 CSS 配方与红线整理在 `styles/`，写前端时按需取用：

- `styles/01-swiss.md` — 瑞士国际主义：栅格秩序
- `styles/02-editorial.md` — 杂志编辑风：衬线与阅读节奏
- `styles/03-luxury.md` — 暗调奢华：金 + 衬线 + 广字距
- `styles/04-neumorphism.md` — 新拟态：同色浮雕
- `styles/05-brutalism.md` — 粗野主义：硬骨架
- `styles/06-cyberpunk.md` — 赛博朋克：霓虹故障
- `styles/07-zen.md` — 和风侘寂：竖排留白
- `styles/08-memphis.md` — 孟菲斯：玩乐几何
- `styles/09-bauhaus.md` — 包豪斯：三原色构成
- `styles/10-neo-brutalism.md` — 新粗野主义：厚边 + 零模糊硬影
- `styles/11-pop-art.md` — 波普主义：网点 + 粗黑轮廓
- `styles/12-op-art.md` — 欧普主义：莫尔条纹视错觉
- `styles/13-suprematism.md` — 至上主义：纯几何 + 无限留白
- `styles/14-constructivism.md` — 构成主义：45° 斜带红黑海报
- `styles/15-acid-graphics.md` — 酸性设计：荧光 + 铬金属 + 噪点

## 统一内容源（15 页共用）

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

各页只改这些文字的**呈现方式**。个别风格有极少量装饰性文字（如刊号、报头跑马灯、章节题头、状态栏标签、图注），均为版式需要，不是内容差异。

## 五个观察透镜（对照时挨着看）

1. **字体**：衬线还是无衬线？字重和字距在传递什么情绪？
2. **色彩**：一共几个色？强调色占多少、用在哪？背景是纸还是黑？
3. **空间**：留白是奢侈还是拥挤？元素靠什么对齐：网格还是轴心？
4. **质感**：平面、浮雕还是纸纹？边界用线还是影子？
5. **动效**：有动画吗？快还是慢？它服务于什么状态？

---

## 15 个风格笔记

### 01 瑞士国际主义 Swiss / International Typographic Style
- **理念**：清晰、客观、理性；网格是宪法，排版是国王（1950s 苏黎世/巴塞尔）。
- **手法**：非对称栅格；Helvetica 式无衬线；左对齐右不齐；红=唯一信号色；数字（01–04）当锚点。
- **CSS 关键点**：`grid-template-columns:2fr 1fr` 非对称、实线表格化分栏、`::after` 红线、`font-feature-settings:"tnum"`。
- **场景**：企业官网、年报、机构页面。**翻车点**：对齐差 1px 就"不够瑞士"；网格不严格时风格立刻塌。

### 02 杂志编辑风 Editorial
- **理念**：网页当印刷刊物编排，阅读节奏优先（Vogue / Esquire 气质）。
- **手法**：居中报头 + 粗细双线；双栏通版；首字下沉；四栏"小文章"竖线分隔；衬线字体（Georgia / 宋体）。
- **CSS 关键点**：`::first-letter` 首字下沉、双线用 `border-top:3px + border-bottom:1px` 叠加、`grid:7fr/5fr`。
- **场景**：博客、专栏、内容平台。**翻车点**：衬线字号过小会糊；分栏线过深抢正文。

### 03 暗调奢华 Luxury
- **理念**：昂贵感 = 稀有 + 克制；金色只在一个地方发光。
- **手法**：深黑底 + 暖金；居中纪念性构图；广字距；罗马数字与菱形分隔符；缓慢流光。
- **CSS 关键点**：`background-clip:text` 金渐变文字、`letter-spacing:.24em+`、`@keyframes sheen` 流光。
- **场景**：奢侈品、酒店、高端服务。**翻车点**：金用多了就俗；黑底留白不足会变"土豪金"。

### 04 新拟态 Neumorphism
- **理念**：从同一种材质里"挤"出的接口，像捏一块软塑料。
- **手法**：背景 = 表面同色；一明一暗双向柔影；按压时影子翻转为内嵌。
- **CSS 关键点**：`box-shadow:9px 9px 20px #c5ccd9,-9px -9px 20px #fff`、`:active` 切换 `inset` 阴影。
- **场景**：仪表盘、面板组件。**翻车点**：对比度天然偏低（NN/g 明确警示过无障碍）——文字层级别指望影子，要用颜色/字重补。

### 05 粗野主义 Web Brutalism
- **理念**：把骨架暴露出来；对精致主义的坦率反动。
- **手法**：4px 黑描边 + 零模糊硬阴影；跑马灯；倾斜贴纸；巨型标题；hover 按压位移。
- **CSS 关键点**：`box-shadow:7px 7px 0 #2500ff` 硬阴影、`@keyframes tick` + `translateX(-50%)` 无缝跑马灯。
- **场景**：创意机构、作品集、艺术项目。**翻车点**："故意的乱"需要更狠的克制——层级、可点击性、移动端一条都不能少，否则只是没设计。

### 06 赛博朋克 Cyberpunk
- **理念**：高技低生活的街头未来；霓虹、故障、监控感。
- **手法**：黑底霓虹（青/品红/黄）；暗角 + 扫描线双层；标题故障分片；HUD 四角括号；等宽字体。
- **CSS 关键点**：`repeating-linear-gradient` 扫描线、双伪元素 + `clip-path:inset()` glitch、`text-shadow` 色散。
- **场景**：游戏、活动页、音乐潮牌。**翻车点**：全部发光 = 全部不发光——高亮留给 1–2 处；长文阅读页别用。

### 07 和风侘寂 Wabi-sabi
- **理念**：不完美、不对称、留白即「间」。
- **手法**：竖排题头；素纸底 + 纤维点；一笔留缺的墨圈；朱印是全页唯一的红。
- **CSS 关键点**：`writing-mode:vertical-rl` + `text-orientation:upright`、点阵纸纹 `radial-gradient`、SVG 手绘墨圈。
- **场景**：茶室、民宿、文化品牌、随笔。**翻车点**：竖排是装饰不是正文（正文保持横排）；行距一紧就失去"空气感"。

### 08 孟菲斯 Memphis
- **理念**：1981 米兰；对极简的嬉皮笑脸式反叛，装饰无罪。
- **手法**：点阵底 + 漂浮波浪/圆环/三角（缓慢摇摆）；贴纸卡片（硬阴影 + hover 微旋转）；四色点彩。
- **CSS 关键点**：点阵底 `radial-gradient + background-size`、`@keyframes wiggle`、硬阴影 + hover 位移。
- **场景**：电商活动、年轻品牌、播客。**翻车点**：不设"配额"会变幼儿园——固定四色、形状 ≤6 个、运动幅度要小。

### 09 包豪斯 Bauhaus
- **理念**：形式追随功能；基本几何 + 原色构成（1919 魏玛）。
- **手法**：红黄蓝只做形状不做渐变；正交构成；竖排题头栏；几何图案与功能一一对应。
- **CSS 关键点**：`clip-path:polygon()` 三角形、`border-radius:999px 999px 0 0` 半圆、`writing-mode` 竖排。
- **场景**：设计工作室、展陈、教育机构。**翻车点**：几何形状要有构图职责，不能沦为贴纸；原色面积配比失衡会显廉价。

### 10 新粗野主义 Neo-Brutalism
- **理念**：对"精致而模糊"的正面反叛——界面像一张张贴纸摞在方格纸上，用纯黑厚边和零模糊实影造物理厚度（Gumroad 2021 改版把它推成主流）。
- **手法**：纯黑 3px 厚边 + `box-shadow:8px 8px 0 #000`（blur 必须为 0）；粉/青/黄/紫每卡一色；方格纸可见网格；贴纸与星形手绘 SVG；按钮 hover 抬离纸面、active 压回影子。
- **CSS 关键点**：`box-shadow` 第三参数 0、`repeating-linear-gradient` 双层画网格、`transform:translate()` 与阴影同步缩小做按压、撞色容器一律配黑字。
- **场景**：独立产品、开发者工具、创意工作室、活动页。**翻车点**：一旦出现 blur/渐变/半透明卡片，风格立刻退回普通平面设计；撞色侵入正文就不可读；按压方向与影子不同向会"卡片在飞"。

### 11 波普主义 Pop Art
- **理念**：把大众文化印成海报（1960s，Lichtenstein 的漫画网点 / Warhol 的四联版画）；俗艳即态度。
- **手法**：Ben-Day 网点底（`radial-gradient` 2.1–2.6px + 12–15px 网格）；4px 黑轮廓；双层硬影标题贴纸（彩色 + 墨色套印）；Warhol 式四色重复版画；漫画气泡 + 星爆 + 跑马灯报头。
- **CSS 关键点**：`radial-gradient(circle,rgba(17,17,17,.24) 2.1px,transparent 2.3px) 0 0/13px 13px`、`box-shadow:7px 7px 0 var(--magenta),14px 14px 0 var(--ink)`、`repeating-linear-gradient` 报头。
- **场景**：活动页、潮牌、音乐节、饮品促销。**翻车点**：四色要有配额，否则糊成彩纸堆；网点只做底，文字压上去会花；轮廓一省就散架。

### 12 欧普主义 Op Art
- **理念**：静止的画面看着在动（1960s，Vasarely / Riley）；视觉冲击全由线条密度与走向制造。
- **手法**：两组同心圆圆心偏移 4–5% 造莫尔条纹；棋盘格（`repeating-conic-gradient`）；3px/7–10px 条纹带；条纹遮罩标题字；波浪线装饰带。
- **CSS 关键点**：`repeating-radial-gradient(circle at 50% 50%,…0 1.6px,transparent 1.6px 9px)`、`background-clip:text` + `-webkit-text-stroke` 保住字形、`repeating-conic-gradient(…0 25%,transparent 0 50%) 0 0/16px 16px`。
- **场景**：展览海报、音乐视觉、概念产品。**翻车点**：正文压密条纹 3 秒致晕；一页只留两处错觉；点缀色只许一个；必须 `prefers-reduced-motion`。

### 13 至上主义 Suprematism
- **理念**：1915 年马列维奇的《黑方块》——剥到只剩形与色，让几何体在无垠白底上漂浮。
- **手法**：绝对定位纯色形体（方块/圆/长条/十字），角度 17°/-12°/-28°/34° 各不相同；无阴影无描边无渐变；26–40s 极慢漂移（位移 4–10px）；1px 细线代替卡片。
- **CSS 关键点**：`position:absolute` + 独立 `rotate`、`@keyframes drift-*` 长周期 `ease-in-out infinite`、形体总面积 <25%。
- **场景**：艺术机构、建筑事务所、出版、先锋品牌。**翻车点**：形体超过 25% 就退化成几何插画；加一层柔影就变成拟物；原色超过四枚立刻俗。

### 14 构成主义 Constructivism
- **理念**：1920s 苏联海报（Rodchenko / Lissitzky）——红黑双色、对角动线、粗窄体大字，版面像一台运转的机器。
- **手法**：1750px 宽 45° 红斜带切开版面（负半宽高居中 + `rotate(-45deg)`）；斜置红色大色块海报（3px 边 + 14px 硬影）；竖排编号；红细线替代卡片；箭头指向 CTA。
- **CSS 关键点**：`.band{transform:rotate(-45deg);transform-origin:center}` + `margin:-H/2 0 0 -W/2`、`@keyframes bandIn` 沿带轴滑入、`writing-mode:vertical-rl` 竖排数字。
- **场景**：展览、戏剧、演出、工业品牌。**翻车点**：出现第三种彩色就破年代感；斜带太短会像一条红线；容器不 `overflow:hidden` 会横向滚动。

### 15 酸性设计 Acid Graphics
- **理念**：后网络的锐舞海报（2019+）——荧光色在纯黑里发光，铬金属球与失真字体把屏幕变成一台坏掉的显示器。
- **手法**：`conic-gradient` 液态铬球；三颗荧光光球（绿/品红/青，`radial-gradient` 四段 + opacity .5）；`perspective(340px) rotateX(76deg)` 透视网格地面；内联 SVG `feTurbulence` 噪点；3px 色散字。
- **CSS 关键点**：`conic-gradient(from 200deg,#0c0d12,#8f98ad 10%,#f6f9ff 17%,…)`、`.grid-floor{transform:translateX(-50%) perspective(340px) rotateX(76deg)}`、`text-shadow:3px 0 0 rgba(255,0,200,.55),-3px 0 0 rgba(0,255,240,.45)`。
- **场景**：电子音乐、潮流服饰、游戏、Z 世代品牌。**翻车点**：正文不许荧光；光球 opacity ≤.55；网格线 ≤.2 透明度；噪点层必须 `fixed + pointer-events:none`；色散只给主标题。

---

## 通用原则速查（15 页共同底线）

1. **8pt 间距节奏**：间距取 8 的倍数，秩序从数字开始。
2. **字阶而非孤立的字号**：3–4 级，级差 ≥1.25 倍。
3. **对比度是红线**：正文 ≥ 4.5:1（新拟态、酸性设计尤其危险）。
4. **一页一强调色**：强调色只给"行动"，不给装饰（波普/酸性是刻意的例外，但配额要写死）。
5. **对齐有系统**：要么网格，要么轴心，别"差不多对齐"。
6. **动效服务状态**：入场 ≤ 1s、缓动自然；优先动 transform / opacity。
7. **留白即层级**：空白本身在引导视线。
8. **无障碍底线**：`prefers-reduced-motion`、focus 可见、点击区 ≥ 44px（15 页已内置）。

## 参考资料（检索于 2026-10-04 / 部分补充于 2026-10-21）

- Tilda Education — Popular Web Design Styles: <https://tilda.education/en/web-design-styles>
- Kevin Liu's Wiki — Website Design Styles（风格适用场景与翻车点对照表）: <https://wiki.kevinliu.biz/wiki/design/website-design-styles>
- Web Design Lookbook（Swiss / Brutalism 视觉研究）: <https://webdesignlookbook.webflow.io/>
- UI Style Guide — 67 Interactive Design Styles: <https://www.uistyleguide.com/>
- Figma — Top Web Design Trends 2026: <https://www.figma.com/resource-library/web-design-trends/>
- Fireart Studio — Web Design Trends 2026（Tactile Brutalism）: <https://fireart.studio/blog/the-best-web-design-trends/>
- ui-ux-stylepedia（50+ 风格交互合集，开源可读源码）: <https://github.com/sailesh-01/ui-ux-stylepedia>
- NN/g — Neobrutalism: Definition and Best Practices: <https://www.nngroup.com/articles/neobrutalism/>
- neobrutalism.com — What is neobrutalism?: <https://neobrutalism.com/docs>

## 复用提示

- 全局替换「拾光 / SHIGUANG」与表格里的几段文案，页面即刻变你自己的产品页；
- 每个文件顶部都有注释标明风格名，便于对号入座；
- 右下角"返回图鉴"胶囊位于 `</body>` 前最后一行，不需要就直接删。
