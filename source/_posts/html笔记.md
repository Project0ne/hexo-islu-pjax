---
title: HTML笔记
date: 2020-09-14 00:00:00
img: 'https://files.islu.cn/article /html.jpg'
author: 卢慧军
abbrlink: 47785
top: false
toc: true
mathjax: true
summary: 常用HTML标签解释及应用(写Markdown文章时也可用)
categories: HTML
tags:
  - HTML
  - 常用HTML标签解释及应用
keywords: HTML5命名规范,CSS3命名规范,前端web开发命名规范,符合SEO规范,html,html常用标签
---
# HTML的笔记(上)
## 什么是HTML
HTML：Hyper  Text  Markup  Language(超级文本标签语言)

## HTML页面结构
有两部分组成：
### 文档类型声明
作用：告诉浏览器使用的是HTML的哪个版本
`语法：在网页的最顶端编写：`
`<!doctype  html>`
### HTML页面部分
作用：表示页面的开始和结束
`语法：在文档类型声明的下面编写一对<html>标记`
`<html></html>`
Html标签里面有两个标签，分别是
+ `<head></head>`
作用：表示网页的头部
+ `<body></body>`
作用：表示网页的身体，以后页面中所有的要显示的内容，都要写在body标签里
## HTML语法
### 标记语法
标记又叫标签或者元素，在网页中表示一些功能，必须使用<>括起来，标记分为两大类
#### 封闭类型标记
也叫双标记，必须成对出现，有开始和结束标签。
`语法：<标记>内容</标记>`
eg:`<html>` `<head>` `<body>` `<title>` `<p>` `<b>` `<s>`
`<u>` `<i>` `<sup>` `<sub>` `<h1>~<h6>` `<pre>`
#### 非封闭标记
也叫单标记，或空标记，只有一个标记组成，即表示开始也表示结束。
`语法：<标记>或者<标记/>`
eg:`<!doctype html>` `<meta>` `<br>` `<hr>`
### 标签的嵌套
在一个标签中，出现另外一个标签，从而形成层叠关系，里面的标签又称为“子标签”，外面的标签又称为“父标签”
推荐写法：
	在子元素前，使用一个Tab缩进，表示层级关系
### 注释
不会在页面中显示，只是让程序员方便读代码
`语法：<!--注释的内容-->`

<font color=red>注意：注释标签不能嵌套，也不能出现在其他标记结构中</font>>

eg:`<head   <--错误的注释  -->>`
### `<head>` 中的内容
+ 指定网页的编码格式
`<meta  charset=”utf-8”>`
+ 指定网页的标题
`<title>捞月亮的渔夫</title>`
## 网页中的文本：
### 特殊字符的处理
需要一些<font color=red>转义字符</font>来表示特殊的符号
```html
&nbsp; 	表示一个空格
&lt;    表示一个<
&gt;   	表示一个>
&copy;  表示©
&yen;  	表示 ¥
<br>	表示回车或换行
```
### 文本的样式
```html
<b></b>		 	加粗
<i></i> 	 	 斜体
<u></u>			下划线
<s></s>			删除线
<sub></sub> 	下标
<sup></sup>		上标
```
## 标题元素
作用：在页面中以醒目的方式显示文本
`<h1>这是一级标签</h1>`<h1>这是一级标签</h1>
`<h2>这是二级标签</h2>`<h2>这是二级标签</h2>
`<h3>这是三级标签</h3>`<h3>这是三级标签</h3>
`<h4>这是四级标签</h4>`<h4>这是四级标签</h4>
`<h5>这是五级标签</h5>`<h5>这是五级标签</h5>
`<h6>这是六级标签</h6>`<h6>这是六级标签</h6>
## 标签的属性和值
允许通过属性对标签进行修饰

#### 属性

+ align
  作用：标记内容的水平对齐方式

`语法：`

属性必须声明在开始标签中

`<标签 属性名=”属性值”></标记>`

多个属性之间用空格隔开

`<标签属性名=”属性值”属性名=”属性值”></标记>`
`eg:<h1>~<h6>、<p>`

#### 取值
+ left 左对齐
+ center居中对齐
+ right右对齐
eg:`<h1 align="center">骆驼祥子</h1>`
<h1 align="center">骆驼祥子</h1>

### 段落元素

表示一段文字,独占一行

`标签：<p></p>`
### 预格式化

保留HTML代码中的回车和空格

`语法：<pre></pre>`
### 网页中的图像

用于表示网络中任意资源(图片、视频、音频、文件)的位置（或路径）

URL：统一资源定位符(Uniform Resource Locator)
#### 路径的表现形式：
##### 1.绝对路径：从文件所在的最高级目录开始查找所经过的路径
##### 2.相对路径从当前文件位置出开始查找所经过的路径
```
相对路径口诀：
			同目录，直接用（直接填写图片名）
			子目录，先进入，再使用
			<img src="1/1.jpg" >
			父目录，先返回，再使用
			../表示返回上一级目录
```
#### 图像的标签：
`<img>`
1. src(必须属性)：要显示的图片的url（相对/绝对）
2. width：设置图片宽度，单位是px或%
3. height：设置图片高度，单位是px或%
4. alt：鼠标移至图片时显示的文字
5. title：图片加载不出来时显示的文字
### 超链接
`语法：<a></a>`
#### 属性：
+ href：
	链接到那个地址
	此属性，必须有，如果没有此属性：`<a>标签将不具有超链接的功能<a href="http://www.baidu.com">百度一下</a>`
	
+ target：
指定打开新网页的方式

取值：
	1._self：默认值，在当前的标签页中打开新网页
	2._blank：在新标签页中打开新网页
#### 超链接的其他用法：
##### 1.资源下载
让链接的href等于.rar或者.zip即可
`<a  href=”1.zip”>点我下载</a>`
##### 2.电子邮件链接
`<a  href=”mailto:邮箱地址”>联系我们</a>`
`<a href="mailto:2831843232@qq.com">`
##### 3.锚点就是网页中的一个记号，通过超链接可以迅速到达记号所在的位置.
实现步骤：
>第一步：定义锚点
>>方式一：使用任意标签的id属性定义锚点
>>
>>>`<h1  id=”锚点名字”>化妆品区域</h1>`
>
>>方式二：使用a标签的name属性，定义锚点
>>
>>>`<a  name=”锚点名字”>化妆品区域</a>`
>
>第二步：链接到锚点
>
>>`<a  href=”#锚点名字”>化妆品</a>`
##### 4、返回顶部
`<a  href=”#”>返回顶部</a>`

### 块级元素和行内元素
#### 块级元素

在网页中独占一行，可以设置宽高

`比如<h1>~<h6>,<p>，<hr>，<table>、div、ul、ol、li、pre、tr、td、form`
#### 行内元素

和其他元素在一行显示,大部分行内元素不可以设置宽高

`<a>,<img><b><s><u><i><sub><sup>,<span>`
`可以设置宽高的行内元素有：<img>  input;`
`<span>:处理同一行文本的不同形式`
### 列表
作用：按照从上到下的方式来显示所有的数据，并且在数据前添加一些标识
#### 列表的组成

由列表类型和列表项组成

##### 1.列表类型：
有序列表:`<ol></ol>`    ---Order list
无序列表：`<ul></ul>`   ---Unorder list
##### 2.列表项：
用于表示列表中的数据：`<li></li>`     ---List  item
```html
语法：<ol>
		<li>篮球</li>
		<li>足球</li>
		<li>排球</li>
		<li>台球</li>
	  </ol>
```
#### 列表属性：
##### 有序列表在属性：
+ type
作用：指定列表标识的类型

+ 取值：
	+ 1：按数字排列，默认值
	+ a:按小写字母排列
	+ A：按大写字母排列
	+ i:按小写罗马数字排列
	+ I：按大些罗马字母排列
+ start
	作用：指定起始编号从几开始，是数字
##### 无序列表的属性：
+ type：
作用：指定列表标识的类型
+ 取值：
	+ disc  默认值，实心圆
	+ circle  空心圆
	+ square  实心方块
	+ none   不显示标识（最常用）
##### 列表的嵌套
在一个列表项中又出现了一个列表

被嵌套的列表只能出现在`<li>`中，不能乱放
<img src="https://cdn.jsdelivr.net/gh/isome/ialoe-article@master/HTML笔记/li嵌套.png">
##### 定义列表：
通常用对某个名词的解释

语法：

`<dl></dl>`  -----definition  list(定义列表)

`<dt></dt>` 定义要解释的名词

`<dd></dd>` 表示定义列表中对名字的解释内容
```html
格式：
	<dl>
		<dt>《水浒传》</dt>
		<dd>中国四大名著</dd>
	</dl>
```
### 结构标记
作用：用于描述整个网页的结构，提升标记的语义性

#### 常用的语义标记
1. `<header></header>`
作用：定义网页或某部分内容的头部
2. `<nav></nav>`
作用：定义网页的导航链接部分
3. `<section></section>`
作用：表示网页的主体内容
4. `<article></article>`
作用：定义与文字描述相关的内容
5. `<aside></aside>`
作用：定义页面中侧边栏的信息
6. `<footer></footer>`
作用：定义某区域的底部信息
###### 他们的本质都是div标签`<div></div>`：表示块区元素，独占一行，用于表示一个区域。是H5新增的语义化新标签
### 表格
表格是由单元格按照从左到右，从上到下的顺序排列而成的。
#### 标签
表格：`<table></table>
行：`<tr></tr>` ----table  row 表示一行
列或单元格：<td></td> ----table   data  表示一个单元格
```html
表格的写法：
<table>
	<tr>							行必须写在表里面
		<td></td>单元格必须写在row里面
		<td></td>
	</tr>
	<tr></tr>
</table>
```
#### 表格的属性：
+ table的属性:
	+ width
	设置表格的宽度，单位是px或%
	+ height
	设置表格的高度，单位是px或%
	+ align
	设置表格的水平对齐方式
	left/center/right
	+ border
	设置表格的边框宽度，默认值是0，没有单位
	+ bgcolor
	设置背景颜色，取值为对应颜色的英文
	+ cellspacing
	表示单元格的外边距，就是单元格与单元格之间的距离
	+ cellpadding
	设置单元格的内边距，就是单元格与内容的距离

+ tr的属性：
	+ align
	设置当前行里面内容的水平对齐方式
		+ 取值：left/center/right
	+ valign
	设置当前行里面内容的垂直对齐方式
		+ 取值：top(顶部)middle(居中)/bottom（底部）
	+ bgcolor：
	设置该行的背景颜色
+ td的属性：
	+ width,设置单元格的宽度
	+ height
	+ align
	+ valign
	+ bgcolor
	+ colspan:  跨列
	+ rowspan：跨行
###### 被跨掉的单元格必须删除
#### 可选标记
+ 表格的标题：`<caption></caption>`必须写在`<table>`标签的第一行，一个表格只能有一个标题
+ 所有的`<td>`标签都可以被`<th>`标签替换，table header内容的标题
+ 行分组可以将连续的几个行，划分到一个组中，进行统一的管理。
	+ 表头行分组`<thead></thead>`表格中最上面的一行或几行，进行分组，就可以将这一行放在`<thead>`标签里
	+ 表尾行分组`<tfoot></tfoot>`表格中最后一行进行分组的话，可以放在`<tfoot>`标签中
	+ 表主体行分组`<tbody></tbody>`可以将若干个行，放在`<tbody>`中,进行统一设置
###### 注意：若不对table中的数据进行分组，默认都在<tbody>中
	+ 表格的嵌套被嵌套的表格必须写在`<td>`里面.


### 表单

#### 作用

1. 提供可以与用户***\*交互\****的可视化界面
2. 收集用户信息并提交给服务器

#### 标签

`<table></table>`

#### 属性

1. action	作用：定义表单内容被提交到哪个服务器里，后面跟url	
2. method  作用：定义表单数据的提交方式
   + 作用：定义表单数据的提交方式
   + 取值：
     1. get默认是get
     2. post

#### 可视化控件

+ 分类

  1. input元素
  2. textarea 多行文本域元素
  3. select和option选项框元素
  4. 其他元素

+ Input元素

  + 作用：在页面中提供各种各样的输入控件

  + 语法：`<input>或者<input />`

  + 属性：

    1. type    指定创建输入控件的类型

       + 取值

         1. text  文本框

         2. password 密码框

         3. submit  提交按钮

         4. reset  重置按钮

         5. radio  单选框(单选框需要分组才能使用

            使用name属性分组，让两个单选框的name值一致即可)

         6. checkbox 多选框

         7. file  文件选择框(用于上传文件)

    2. value    指定控件的值

    3. placeholder    占位符，默认显示在控件上的文本

    4. readonly    只能看，不能改，没有值

    5. disabled    禁用控件，没有值

  + 表单辅助标签

    + `<input type=”checkbox” id=”login”>`
    + `<label  for=”login”>下次自动登录</label>`
