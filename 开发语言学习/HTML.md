HTML是一种标记语言，使用标签来包含内容[[WEB]]
标签：开始与结束一般成对出现
<！DOCTYPE html >
<html>

<head> </head>

<编码>

<title>   </title>

<body>  
<h1></h1>
<p> </p>
</body>

</html>
元素介绍：
-段落p 
-链接 a href
-图像src
-标题h1-6
-hr 创建分割线
-br 创建拆行
<!--这是一个注释-->

格式化标签
<b>	定义粗体文本
<em>	定义着重文字
<i>	定义斜体字
<small>	定义小号字
<strong>	定义加重语气
<sub>	定义下标字
<sup>	定义上标字
<ins>	定义插入字
<del>	定义删除字

HTML "计算机输出" 标签
标签	描述
<code>	定义计算机代码
<kbd>	定义键盘码
<samp>	定义计算机代码样本
<var>	定义变量
<pre>	定义预格式文本


HTML 引文, 引用, 及标签定义
标签	描述
<abbr>	定义缩写
<address>	定义地址
<bdo>	定义文字方向
<blockquote>	定义长的引用
<q>	定义短的引用语
<cite>	定义引用、引证
<dfn>	定义一个定义项目。


属性：
- HTML 元素可以设置**属性**
- 属性可以在元素中添加**附加信息**
- 属性一般描述于**开始标签**
- 属性总是以名称/值对的形式出现，**比如：name="value"**
	- class:类名属性
	- id:定义元素唯一ID
	- stytle：规定行内形式
	- title：描述元素额外信息 

关于换行符号的提醒：
	我们无法确定 HTML 被显示的确切效果。屏幕的大小，以及对窗口的调整都可能导致不同的结果。
	
	对于 HTML，您无法通过在 HTML 代码中添加额外的空格或换行来改变输出的效果。
	
	当显示页面时，浏览器会移除源代码中多余的空格和空行。所有连续的空格或空行都会被算作一个空格。需要注意的是，HTML 代码中的所有连续的空行（换行）也被显示为一个空格。


链接格式 

HTML超链接  超链接的几种形式 

- 链接形式 <b>使用
- <a href="url">链接文本</a>
- 
- 文本链接 <将文本转换为可点击链接>
- <a href="https://www.example.com">访问示例网站</a>
- 
- 图像链接 
- <a href="https://www.example.com">
		  <img src="example.jpg" alt="示例图片">
		  </a>
		  
-锚点链接 
<a href="#section2">跳转到第二部分</a> 需要在目标位置使用<a>元素定义标记 并用#引用
		<!-- 在页面中的某个位置 -->
		<a name="section2"></a>
		
-下载链接  <使用download属性>
<a href="document.pdf" download>下载文档</a>  

超链接属性 
	以下是 HTML 中创建链接的基本语法和属性：`<a>` 元素：创建链接的主要HTML元素是`<a>`（锚）元素。`<a>`元素具有以下属性：
	
	- `href`：指定链接目标的URL，这是链接的最重要属性。可以是另一个网页的URL、文件的URL或其他资源的URL。
	- 
	- `target`（可选）：指定链接如何在浏览器中打开。常见的值包括 `_blank`（在新标签或窗口中打开链接）和 `_self`（在当前标签或窗口中打开链接）。
	- 
	- `title`（可选）：提供链接的额外信息，通常在鼠标悬停在链接上时显示为工具提示。
	- 
	- `rel`（可选）：指定与链接目标的关系，如 nofollow、noopener 等。
	- ID属性  ID属性可以用来创建一个书签
	
	链接的 HTML 代码很简单，它类似这样：

	<a href="url">链接文本</a>


HTML head 元素
标签	描述
<head>	定义了文档的信息
<title>	    定义了文档的标题
<base>	定义了页面链接标签的默认链接地址
<link> 	定义了一个文档和外部资源之间的关系
<meta>	定义了HTML文档中的元数据
<script>	定义了客户端的脚本文件
<style>	定义了HTML文档的样式文件

**HTML 样式CSS**

*CSS (Cascading Style Sheets) 用于渲染HTML元素标签的样式*
*使用方式：内联、内部样式、外部引用；*
*example：样式属性、字体*

HTML图像 

HTML表格

HTML列表
无序列表
	<ul>  
	<li>Coffee</li>  
	<li>Milk</li>  
	</ul>
有序列表
	<ol>  
	<li>Coffee</li>  
	<li>Milk</li>  
	</ol>
自定义列表
	自定义列表不仅仅是一列项目，而是项目及其注释的组合。
	
	自定义列表以 <dl> 标签开始。每个自定义列表项以 <dt> 开始。每个自定义列表项的定义以 <dd> 开始。
	
	<dl>  
	<dt>Coffee</dt>  
	<dd>- black hot drink</dd>  
	<dt>Milk</dt>  
	<dd>- white cold drink</dd>  
	</dl>
HTML区块