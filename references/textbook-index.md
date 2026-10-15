# 教材详细知识点索引

## 第1章 网站开发入门
- 网站开发流程：确定主题→设计页面→效果图切片→设置站点→搭建结构层→搭建样式层→测试上传→网站推广→维护更新
- DW创建站点：站点→新建站点，设置站点名称和本地根文件夹
- 新建网页：文件→新建（Ctrl+N），保存Ctrl+S，预览F12
- HTML基本结构：`<!doctype html><html><head><meta charset="utf-8"><title></title><style>...</style></head><body>...</body></html>`

## 第2章 HTML标签与CSS样式基础
- HTML标签：h1-h6标题、p段落、br换行、hr水平线、ul/li无序列表、ol/li有序列表、img图像、a超链接、div容器
- 超链接路径：相对路径、target="_blank"新窗口
- CSS引入方式：内嵌样式（style标签）、行内样式（style属性）、链接样式（link标签）、导入样式（@import）
- CSS选择器：标签选择器、类选择器(.class)、id选择器(#id)、伪类选择器(a:link/a:hover/a:active/a:visited)
- 优先级：行内样式 > id选择器 > 类选择器 > 标签选择器
- 选择器嵌套：`#link1 a{}`表示id为link1的div中的a标签

## 第3章 文字在网页中的应用
- 文字属性：font-family、font-size、font-style、font-weight、color
- 段落属性：text-indent（首行缩进）、line-height（行高）、text-align（对齐）、text-decoration（修饰）、letter-spacing（字间距）
- 列表属性：list-style-type（符号类型）、list-style-image（图像符号）
- HTML符号：&nbsp;空格、&lt;<、&gt;>、&copy;©、&yen;¥

## 第4章 图像在网页中的应用
- 图像HTML：`<img src="images/1.jpg" width="400" height="300" alt="">`
- 图像CSS：border（边框）、float（环绕）、margin-right（间距）
- 背景CSS：background-color、background-image、background-repeat、background-position
- 图文混排：float:left图像居左文字环绕，float:right图像居右

### 案例一：做人做事的艺术（index.html）
- body背景：bg111.gif，font-size:14px
- #all：800px宽居中，6px #000 double边框，#FC9背景，padding:10px
- h1：36px黑体居中#f3300
- #all img：2px #ff3300 solid边框，float:left，margin-right:10px，padding:8px
- #all p：line-height:24px，text-indent:2em，楷体_GB2312

### 案例二：豌豆上的公主（tale.html）
- body：padding-top:30px，bg.gif背景，font-size:14px，color:#660033
- #content：width:80%居中，img1.jpg右下角不重复背景，#E9FBFF背景，6px double #FF0033边框
- h1,h5：text-align:center
- #content img：float:left，margin-right:10px
- p：text-indent:2em，line-height:2em

## 第5章 制作导航栏
- 纵向导航：ul/li + a标签
- 横向导航：li float:left，a display:block
- hover伪类：背景变色、边框变化
- 下拉菜单：display:none/block控制

## 第6章 表格在网页中的应用
- 表格：table/tr/td/th
- 合并：colspan跨列、rowspan跨行
- CSS：border-collapse合并边框

## 第7章 表单在网页中的应用
- 表单：form/input/select/textarea
- 常用input：text/password/radio/checkbox/submit/reset
- label关联表单元素

## 第8章 CSS标准流布局
- 盒子模型：content + padding + border + margin
- 块元素独占一行，行内元素并排
- 居中：margin:0 auto

## 第9章 CSS浮动布局
- float:left/right
- clear:both清除浮动
- 两栏布局：左栏float:left，右栏float:right

## 第10章 CSS定位布局
- position：static/relative/absolute/fixed
- 配合top/right/bottom/left
- z-index堆叠顺序
- overflow:hidden溢出隐藏

## 第11章 JavaScript应用
- script标签：`<script type="text/javascript">`
- function声明函数
- 窗口操作：window.close()
- 定时：setTimeout/setInterval

## 第12章 综合应用
- 完整结构：header头部 → main主体（浮动两栏） → footer底部
- 综合运用：浮动+定位+背景图
- 导航：a display:block + float:left + hover换背景图
