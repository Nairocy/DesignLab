# 09 · 包豪斯 Bauhaus

> 形式追随功能；基本几何 + 原色构成（1919 魏玛）。
> 关键词：三原色 / 圆三角方半圆 / 正交构成 / 竖排题头栏

- **适合**：设计工作室、展陈、教育机构、宣言型页面
- **不适合**：需要柔和或奢华气质的内容
- **参考实现**：`../09-bauhaus.html` · 截图 `../_shots/09-bauhaus.png`

## 设计 Token

| 项 | 值 |
|---|---|
| 底 | `#f4f1ea`（暖白） |
| 墨 | `#101010` |
| 红 | `#d92b2b`（方形） |
| 蓝 | `#1f4ed8`（三角） |
| 黄 | `#f2c200`（圆） |
| 字体 | `"Arial","Helvetica Neue",Helvetica,"Microsoft YaHei"`（几何无衬线） |
| 结构线 | 3px 实线 |
| 形状 | 圆/三角/方/半圆——**每种形状绑定一个功能**，不是随机贴纸 |

## 签名配方

### 纯 CSS 基本形
```css
.sh-circle{border-radius:50%;background:var(--yellow)}
.sh-tri{clip-path:polygon(50% 4%,96% 96%,4% 96%);background:var(--blue)}
.sh-square{background:var(--red)}
.sh-half{border-radius:999px 999px 0 0;background:var(--ink)}   /* 半圆 */
```

### 三栏 hero：竖排题头栏 + 内容 + 几何板
```css
.hero{display:grid;grid-template-columns:64px minmax(0,1fr) 330px;gap:44px}
.rail{writing-mode:vertical-rl;text-orientation:upright;border-right:3px solid var(--ink);padding-right:22px;letter-spacing:.46em}
.shapes{display:grid;grid-template-columns:1fr 1fr;grid-auto-rows:104px;gap:16px}
```

### 方形红点 kicker
```css
.kicker{display:flex;align-items:center;gap:12px;font-weight:700;letter-spacing:.32em}
.kicker i{width:13px;height:13px;background:var(--red);display:block}
```

### 四格特性：形随机能（同一套形状缩小复用）
```css
.feature .motif{width:26px;height:26px}   /* m-circle / m-tri / m-square / m-half */
.features{display:grid;grid-template-columns:repeat(4,1fr);border-top:3px solid var(--ink)}
.feature{padding:32px 26px 56px;border-left:1px solid var(--ink)}
```

## 页面骨架
3px 底线顶栏 → hero 三栏（竖排 SHIGUANG 题头｜红点 kicker + 巨型标题 + 按钮｜2×2 几何板）→ 四格特性（四几何形对应四功能）→ 黑条页脚。

## 动效
无。只有按钮 hover 变色（黑→红 / 描边→黄底）。静态海报感。

## 红线 / 翻车点
- 几何形状要有"构图职责"（对应功能/分区），不能沦为随机贴纸。
- 原色面积配比失衡会显廉价：黄色圆（视觉最重）别给太大；红蓝黄只用色块不用渐变。
- 形状只用四个基础形，别引入第五种。
