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

&emsp;样式表允许以多种方式规定样式信息. 样式可以规定在单个HTML元素中, 在HTML页的头元素中, 或在一个外部CSS文件中. 甚至可以咋同一个HTML文档内部引用多个外部样式表.
&emsp;一般情况下, 优先级如下: <br>
&emsp; **(内联样式)Inline style > (内部样式) Internal style sheet > (外部样式) External style sheet > 浏览器默认样式** <br>

&emsp;假设我们有一个css文件, 代码如下:
```css
h3 {
	color:blue;
}
```
&emsp;我们有一个html代码如下:
```html
<head>
    <!-- 外部样式 style.css -->
    <link rel="stylesheet" type="text/css" href="style.css"/>
    <!-- 设置：h3{color:blue;} -->
    <style type="text/css">
      /* 内部样式 */
      h3{color:green;}
    </style>
</head>
<body>
    <h3>显示绿色，是内部样式</h3>
</body>
```
> 这种情况下, h3 显示为绿色, 用的内部样式的设置

**注意:** 如果外部样式放在内部样式的后面, 则外部样式将覆盖内部样式, 具体例子如下: 
```html
<head>
    <!-- 设置：h3{color:blue;} -->
    <style type="text/css">
      /* 内部样式 */
      h3{color:green;}
    </style>
    <!-- 外部样式 style.css -->
    <link rel="stylesheet" type="text/css" href="style.css"/>
</head>
<body>
    <h3>显示蓝色，是外部样式</h3>
</body>
```
## CSS背景

CSS 背景属性用于定义 HTML 元素的背景.

CSS 属性定义背景效果:

* background-color
* background-image
* background-repeat
* background-repeat
* background-attachment
* background-position

### 背景颜色

&emsp;background-color 属性定义了元素的背景颜色.
&emsp;页面背景颜色使用在body的选择器中.

例子如下:
```css
body {background-color:#b0c4de;}
```
> CSS中, 颜色值通常以一下方式定义:<br>
	&emsp;* 十六进制 -> 例如 `#ff0000`<br>
	&emsp;* RGB -> 例如 `rgb(255,0,0)`<br>
	&emsp;* 颜色名称 -> 例如 `red`

### 背景图像

&emsp;background-image 属性描述了元素的背景图像.

&emsp;默认情况下, 背景图像进行平铺重复显示, 以覆盖整个元素实体 例子如下:
```css
body {background-image:url('paper.gif');}
```

### 背景图像 - 水平或垂直平铺

&emsp;默认情况下 backgropund-image 属性会在页面的水平或者垂直方向平铺.

&emsp;一些图像如果在水平方向与垂直方向平铺, 这样看起来很不协调.

&emsp;因此, 应该设置相应的平铺模式, 使得页面展示起来更加协调, 代码如下:

```css
body
{
	background-image:url('gradient2.png');
	background-repeat:repeat-x;
}
```
### 背景图像 - 设置定位与平铺

> &emsp;要让背景图像不影响文本的排版
	<br> 如果不想让图像平铺, 我们可以使用 background-repeat属性
```css
body
{
	background-image:url('img_tree.png');
	background-repeat:no-repeat;
}
```

&emsp;上面的例子中, 背景图像与文本显示在同一个位置, 为了让页面排版更加的合理, 不影响文本的阅读, 我们可以改变图像的位置.

&emsp;我们可以利用`background-position` 属性改变图像在背景中的位置 例子如下:
```css
body
{
	background-image:url('img_tree.png');
	background-repeat:no-repeat;
	background-position:right top;
}
```
### 背景 - 简写属性

&emsp;在上面的例子中, 我们可以看到页面的背景颜色通过很多的属性进行控制. 为了简化这些属性的代码, 我们可以将这些属性合并在同一个属性中. 背景颜色的简写属性为 `background` :

```css
body {
	background:#ffff00 url('img_tree.png') no-repeat right top;
}
```
**注意:** 当使用简写属性时, 属性值的顺序为:

* background-color
* background-image
* background-repeat
* background-attachment
* background-position

当使用 `background-attachment:fixed` 属性时, 图像不会随着页面的其他部分滚动.

## CSS Text(文本)
### 文本颜色
&emsp;颜色属性被用来设置文字的颜色.
&emsp;颜色是通过CSS最经常的指定:

* 十六进制值 -> #FF0000
* 一个RGB值 -> RGB(255,0,0)
* 颜色的名称 -> red

&emsp;一个网页的背景颜色是指在主体内的选择:
```css
body {color:red;}
h1 {color:#00ff00;}
h2 {color:rgb(255,0,0);}
```
> 对于W3C标准的CSS：如果你定义了颜色属性，你还必须定义背景色属性。<br>
	**`color`这个属性用来设置文本的颜色**

### 文本的对齐方式

&emsp;文本排列属性是用来设置文本的水平对齐方式
&emsp;文本可居中或对齐到左或右, 两端对齐.
&emsp;当`text-align`设置为`justify`, 每一行被展开的宽度相等, 左, 右外边距是对齐的.
```css
h1 {text-align:center;}
p.date {text-align:right;}
p.main {text-align:justify;}
```
### 文本修饰
&emsp;`text-decoration` 属性用来设置或删除文本的装饰.
&emsp; 从设计的角度看 `text-decoration`属性主要是用来删除链接的下划线:
```css
a {text-decoration:none;}
```
当然, 也可以以如下方式装饰文字:
```css
h1 {text-decoration:overline;}
h2 {text-decoration:line-through;}
h3 {text-decoration:underline;}
```
> 注意: 不建议强调不是链接的文本, 因为这回混淆用户

### 文本转换

&emsp;文本转换属性是用来指在一个文本中的大写和小写字母.
&emsp;可用于所有字句变成大写或小写字母, 或每个单词的首字母大写. 例子如下:
```css
p.uppercase {text-transform:uppercase;}
p.lowercase {text-transform:lowercase;}
p.capitalize {text-transform:capitalize;}
```
### 文本缩进
&emsp;文本缩进属性是用来指文本的第一行的缩进.
```css
p {text-indent:50px;}
```
### 其他属性
**指定字符之间的空间 -> `letter-spacing:3px;` 或 `letter-spacing:-3px;`**

**指定行与行之间的空间 -> `ling-height:70%;`**

**设置元素的文本方向 -> `direction:rtl;(从右到左书写方向)`**

**增加单词之间的空间 -> `word-spacing:30px;`**

**在元素内禁用文字不换行(即取消自动换行) -> `white-space:nowrap;`**

**垂直对齐图像 -> `vertical-align:text-top;` 或 `vertical-align:text-bottom`**

**添加文本阴影 -> `text-shadow:2px 3px #FF0000;`**

## CSS 字体


