---
name: web-design-course
description: 网页设计与制作课程辅助Skill。基于教材《网页设计案例教程（HTML5+CSS3+JavaScript）》（杨松主编，航空工业出版社），Dreamweaver CC环境。支持扫描版PDF渲染读取、章节页码快速定位、按教材代码复刻案例。当用户提到网页设计作业、DW操作、HTML/CSS代码、学习通作业、网站开发等场景时使用。
---

# 网页设计与制作课程辅助

本Skill基于教材《网页设计案例教程（HTML5+CSS3+JavaScript）》（杨松主编），覆盖12章内容，辅助完成课程作业。

## 适用场景

- 学习通"网页设计与制作"课程作业
- Dreamweaver CC网页制作
- HTML5 + CSS3 网页代码编写
- 按教材案例复刻网页

## 核心工作流

### 1. 章节快速定位（避免每次从第一章扫描）

- 教材为**扫描版 PDF，无文字层**，`get_text()` 恒返回空，不能靠文字提取定位。
- 页码换算规律（已多组数据验证，恒定可靠）：

```
PDF 物理页码 = 书内印刷页码 + 10
书内印刷页码 = PDF 物理页码 - 10
```

- 用户说出某章/某案例 → 直接换算 PDF 页 → 渲染该页视觉读取，无需从第一章逐页扫描。
- 各章起始页与全部案例页码见 [references/section-locator.md](references/section-locator.md)。

### 2. 扫描版 PDF 读取方法

- 用 PyMuPDF（`import pymupdf`）打开 PDF，取 0 基索引 `(PDF页码 - 1)`。
- `page.get_pixmap(matrix=Matrix(2,2), alpha=False)` 渲染为高清图片，再视觉识别其中的 HTML/CSS 代码。
- 图片过大导致读取超时，降低 `Matrix` 缩放比例重渲染。

### 3. 作业制作与交付流程

1. 按教材代码构建**独立站点文件夹**（`images/` 子目录 + HTML 文件）。
2. 浏览器截图验证，包含默认与 `:hover` 状态，与教材效果图逐项核对。
3. 打包为 zip，放桌面"网页基础作业"文件夹；按需要单独或整章打包。

## 教材结构（12章）

| 章 | 标题 | 核心内容 | 掌握状态 |
|---|---|---|---|
| 1 | 网站开发入门 | 开发流程、DW站点创建、HTML基本结构 | 用户明确不做 |
| 2 | HTML标签与CSS样式基础 | 常用标签、CSS引入方式、选择器 | 已学 |
| 3 | 文字在网页中的应用 | 字体属性、段落属性、列表样式 | 已学 |
| 4 | 图像在网页中的应用 | 图像大小/边框/对齐、图文混排、背景图 | 已学 |
| 5 | 制作导航栏 | 纵向/横向导航、图像背景、下拉菜单 | 已完成 |
| 6 | 表格在网页中的应用 | 表格标签、合并单元格、CSS控制表格 | 已完成 |
| 7 | 表单在网页中的应用 | input/select/textarea、CSS美化表单 | 待做 |
| 8 | CSS标准流布局 | 盒子模型、标准流、居中 | 待做 |
| 9 | CSS浮动布局 | float、clear、两栏布局 | 待做 |
| 10 | CSS定位布局 | position、relative/absolute、z-index | 待做 |
| 11 | JavaScript的应用 | script标签、函数、窗口操作 | 待做 |
| 12 | 综合应用 | 婚礼策划机构完整首页 | 待做 |

## 已验证的案例技术

### 导航栏（第5章 + 仿京东素材）

- 纵向导航：`<nav>` + 块级 `<a>`，`:hover` 变色。
- 横向导航：`float:left` 横向排列，统一宽度与行高。
- 带图像效果横向导航：`background` 引用菜单背景图，`:hover` 切换按钮图（menuBg.jpg / menu_ok.jpg）。
- 下拉菜单：`<ul><li><ul>` 嵌套，子菜单 `display:none`，`:hover` 时 `display:block`。
- 仿京东侧边分类：分类块 + 灰色标题栏 + 白色子项。
- 圆角按钮导航：深蓝横条，`:hover` 显示白色圆角按钮图（menu.png）。

### 表格（第6章）

- 基本标签：`<table><tr><td><th>`，标题用 `<caption>`。
- 合并单元格：`colspan` 跨列、`rowspan` 跨行。
- 边框合并：`border-collapse:collapse`，避免相邻边框变两倍。
- 隔行变色：给单数行 `<tr>` 加类名（如 `row`），统一设置背景色。
- 跨月/非本期数据：加类名（如 `nouse`）设灰底，`:hover` 用伪类变色。
- 表格居中：`margin:0 auto`。

## 素材处理规范

- **缺失图片的等效替代**：教材引用的素材（如 `image/title.gif`）资源包未提供时，用 CSS 等效背景（如深灰 `background-color`）还原效果，并在注释中说明。
- **真实素材优先**：用户提供真实图片后，替换早期占位图并重做验证。
- **压缩包处理**：
  - Windows：zip 用 `Expand-Archive`；rar 用 WinRAR（`Rar.exe x`）。
  - Linux：无 root 权限时，下载 RARLAB 静态 `unrar` 放 `~/.local/bin`；`rarfile` 库仅能列目录，解压仍需外部 unrar。
- **含准确中文文字的图片**：优先采用无字底图 + HTML 原生 DOM 文字，避免图内文字错字。

## 代码风格规范

- HTML5 doctype：`<!doctype html>`
- 编码：`<meta charset="utf-8">`
- 内嵌CSS写在`<head>`的`<style type="text/css">`中
- 基础结构：`<html><head>...</head><body>...</body></html>`
- 块居中：`margin:0 auto;`
- 首行缩进：`text-indent:2em;`

## 快速参考

- [references/textbook-index.md](references/textbook-index.md) - 12章详细知识点索引
- [references/section-locator.md](references/section-locator.md) - 章节/案例精确页码定位（PDF页=书页码+10）
- [examples/](examples/) - 作业示例代码

## 使用规则

1. 作业必须严格按教材步骤和代码完成，拒绝脱离教材的自由发挥。
2. 资源包与教材不符时，以教材内容为准替换；缺素材用 CSS 等效还原。
3. 每个作业提交站点文件夹压缩包，交付前截图验证。
4. 定位章节优先使用页码换算公式，不重复扫描全书。
