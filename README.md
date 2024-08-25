# css_practice

## 一般的语法规则是
```css
选择器 {

	属性1:值1;
	属性2:值2;
}
```
> 选择器通常是我们需要改变样式的HTML元素
	每条声明由一个属性和一个值组成
	CSS 声明总是以分号结束, 声明总是用大括号括起来

## CSS id 和 class

### id 和 class 选择器
&emsp;如果我们需要再HTML元素中设置CSS样式, 我们需要在元素中设"id" 和 "class" 选择器

### id选择器
&emsp;id 选择器可以为标有特定id的HTML元素指定特定的样式

&emsp;HTML元素以id属性来设置id选择器, CSS中id选择器以 **#** 来定义

&emsp;下面的样式规则应用于元素属性 id="para1"

```css

#para1 {
	text-align:center;
	color:red;
}
```
<b style="background-color:white; color:black">id 属性不能以数字开头, 数字开头的id在特定的浏览器中不起作用</b>

### class 选择器

&emsp;class 选择器用于描述一组元素的样式, class选择器有别于id选择器, class可以在多个元素中使用

&emsp;calss 选择器在 HTML 中以class属性表示, 在 CSS 中, 类选择器以一个点 `.` 表示

```css

.center{
	text-align:center;
}
/* html 标签中应该写成 class="center" */

p.center{
	text-align:center;
}
/* html 所有p标签有center类的元素居中*/
```
上面是一个让所有拥有 center 类的HTML元素全部居中

```html

<p class="class1 class2 class3"></p>
<!--多个class选择器可以用空格分开-->
```
> 注意, 类名的第一个字符也不可以使用数字. 因为无法在特定的浏览器中起作用 (Mozilla 和 Firefox)

## CSS 创建

&emsp;当读到一个样式表时, 浏览器会根据样式表来格式化HTML文档

### 如何插入样式表

&emsp;一共有三种方法插入样式表:

* 外部样式表 external style sheet
* 内部样式表 internal style sheet
* 内联样式 inline style

### 外部样式表

&emsp;当样式需要应用于很多页面时, `外部样式表` 是理想的选择, 在使用外部样式表的情况下, 我们可以通过改变`一个文件`来改变整个站点的外观. 每个页面使用 &lt;link&gt;标签链接到样式表.
```html
<head>
	<link rel="stylesheet" type="text/css" href="css_file_location.css">
</head>
```
&emsp;浏览器会从我们提供的css文件地址读取样式声明, 并根据它来格式文档.
外部样式表可以在任何文本编辑器中进行编辑. 文件不能包含任何html标签. 样式表应该以`.css`扩展名进行保存
> 注意: `margin-left:20px` 上面的`20`与`px`之间不可以用空格分开

### 内部样式表

&emsp;当单个文档需要特殊的样式时, 就应该使用内部样式表. 我们可以使用`<style>`标签在文档头部定义内部样式表, 例如:
```html
<head>
	<style>
		hr {
			color:sienna;
		}
		p {
			margin-left:20px;
		}
		body {
			background-image:url("images/back40.gif");
		}
	</style>
</head>
```

### 内联样式

&emsp;由于要将表现和内容混杂在一起, **内联样式表会损失掉样式表的许多优势**. 所以这种方法我们要慎用, 例如当样式仅仅需要在一个元素上应用一次时.

&emsp;要使用内联样式, 我们需要在相关的标签内使用内联样式 `style` 属性. Style属性可以包含任何css属性.
```html
<p style="color:sienna;margin-left:20px">这是一个段落。</p>
```
### 多重样式

> &emsp; 如果某些属性在不同的样式表中被同样的选择器定义, 那么属性值将从`更具体的样式表`中被继承
例如, 外部样式表拥有针对h3选择器的三个属性:
```css
h3 {
    color:red;
    text-align:left;
    font-size:8pt;
}
```
&emsp;而内部样式表拥有针对h3选择器的两个属性:
```css
h3 {
    text-align:right;
    font-size:20pt;
}
```
&emsp; 加入我们拥有内部样式表的这个页面的同时与外部样式表链接, 那么h3得到的样式是:
```css
color:red;
text-align:right;
font-size:20pt;
```
**即颜色属性将被继承于外部样式表, 而文字排列, 和字体尺寸会被内部样式表中的规则取代.**

### **多重样式优先级**

