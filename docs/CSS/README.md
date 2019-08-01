# CSS入门

**CSS 概述：CSS 是什么？**

CSS代表级联样式表。CSS是一种标准的样式表语言，用于描述网页的表示(即布局和格式)。

- 样式定义如何显示 HTML 元素

- 样式通常存储在样式表中

- 把样式添加到 HTML 4.0 中，是为了解决内容与表现分离的问题

- 外部样式表可以极大提高工作效率

- 外部样式表通常存储在 CSS 文件中

- 多个样式定义可层叠为一

## 语法构成

```css
selector {declaration1; declaration2; ... declarationN }
```
选择器主要是需要改变样式的 HTML 元素。

每条声明是由一个属性和一个值组成。

属性（property）是希望设置的样式属性（style attribute），每个属性有一个值。属性和值被冒号分开

```css
div{
background:pink;
}
```

## 定位(Position)

position 属性指定了元素的定位类型，元素可以使用的top、bottom 、left 、right属性来定位，然而，这些属性单独是无法工作，必须先设定position属性

position 属性指定了元素的定位类型，它具有五个值：

- static

- relative

- fixed

- absolute

- sticky

元素可以使用的top、bottom 、left 、right属性来定位，然而，这些属性单独是无法工作，必须先设定position属性。他们也有不同的工作方式，这取决于定位方法

### static定位

HTML元素的默认值，即没有定位，元素出现在正常的流中

静态定位的元素不会受到 top, bottom, left, right影响

```css
div{
	width:100px;
	height: 100px;
	background-color: pink;
	position: static;
}
```

### fixed 定位

元素的位置相对于浏览器窗口是固定位置。

即使窗口是滚动的它也不会移动：

```css
div{
	width:100px;
	height: 100px;
	background-color: pink;
	position: fixed;
	top:40px;
}
```
::: warning 注意
Fixed 定位在 IE7 和 IE8 下需要描述 !DOCTYPE 才能支持。
Fixed定位使元素的位置与文档流无关，因此不占据空间。
Fixed定位的元素会和其他元素重叠
:::

### relative 定位

相对定位元素的定位是相对与其它正常位置的元素

```css
.box1, .box2{
	width:100px;
	height: 100px;
	background-color: pink;

}
.box2{
	position:relative;
	top:10px;
	left:30px;
}
```

### absolute 定位

绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那么它的位置相对于`<html>`
```
.box1, .box2{
	width:100px;
	height: 100px;
	background-color: pink;
	border: 2px solid #444;

}
.box2{
	position:absolute;
	top:40px;
	left:30px;
}
```

### sticky 定位

sticky 英文意思是粘贴，所以可以把它称之为粘性定位。

它基于用户的滚动位置来定位。

粘性定位的元素是依赖于用户的滚动，在 position:relative 与 position:fixed 定位之间切换。

它的行为就像相对定位，而当页面滚动超出目标区域时，它的表现就像fixed定位，它会固定在目标位置。

元素定位表现为在跨越特定阈值前为相对定位，之后为固定定位。

这个特定阈值指的是 top, right, bottom 或 left 之一，换言之，指定 top, right, bottom 或 left 四个阈值其中之一，才可使粘性定位生效。否则其行为与相对定位相同。

::: warning 注意
 Internet Explorer, Edge 15 及更早 IE 版本不支持 sticky 定位。 Safari 需要使用 -webkit- prefix
:::

```css

body{
	height: 2000px;
}
.box1, .box2{
	width:100px;
	height: 100px;
	background-color: pink;
	border: 2px solid #444;
}
.box2{
	position: -webkit-sticky; /* Safari */
    position: sticky;
    top:0px;
    background-color:pink;
    border: 2px solid #444;}
```

## 尺寸

CSS 尺寸 属性允许你控制元素的高度和宽度。同样，它允许你增加行间距

| 属性 | 描述 |
|--|--|
| height | 设置元素的高度 |
| line-height | 设置元素的最大高度 |
| max-width | 设置元素的最大宽度 |
| min-height | 设置元素的最小高度 |
| min-width | 设置元素的最小宽度 |
| width | 	设置元素的宽度 |

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title></title>
<style>
div{
max-width:10%;
background-color:pink;
}
</style>
</head>
<body>
	<div>设置div的最大宽度,设置div的最大宽度,设置div的最大宽度</div>
</body>
</html>
```

## 外边距(Margin)

外边距指的是围绕在元素边框的空白区域，可以通过margin属性来设置外边距，它接受任何长度单位、百分数值甚至负值

| 值 | 描述 |
|--|--|
| auto | 设置浏览器的边距，这样做的结果会依赖于浏览器 |
| length | 定义一个固定的margin（使用像素，pt，em等） |
| % | 定义一个使用百分比的边距 |

::: warning 注意：
 margin可以使用负值，重叠的内容
:::

### 单边外边距属性

```css
p {
background-color: pink;
margin-top:100px;
margin-bottom:100px;
margin-right:50px;
margin-left:50px;
}
```
### 值复制

通过值复制，不用重复地键入这对数字

如果缺少左外边距的值，则使用右外边距的值

如果缺少下外边距的值，则使用上外边距的值

如果缺少右外边距的值，则使用上外边距的值


```css
margin:25px 50px 75px 100px;
```

::: tip 表示：
上边距为25px、右边距为50px、下边距为75px、左边距为100px
:::

```
margin:25px 50px 75px;
```
::: tip 表示：
上边距为25px、左右边距为50px、下边距为75px
:::

```
margin:25px 50px;
```
::: tip 表示：
上下边距为25px、左右边距为50px
:::

```
margin:25px;
```
::: tip 表示：
所有的4个边距都是25px
:::

### 所有的CSS边距属性
| 属性 | 描述 |
|--|--|
| margin | 简写属性，在一个声明中设置所有外边距属性 |
| margin-bottom | 设置元素的下外边距 |
| margin-left | 设置元素的左外边距 |
| margin-right | 设置元素的右外边距 |
| margin-top | 设置元素的上外边距 |

## 填充（Padding）

元素的内边距指的是在边框和内容区之间，通过padding属性定义元素边框与元素内容之间的空白区域

### 单边内边距属性

通过使用下面四个单独的属性，分别设置上、右、下、左内边距：

- padding-top

- padding-right

- padding-bottom

- padding-left

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Document</title>
<style type="text/css">
p
{
background-color: pink;
padding-top:25px;
padding-bottom:25px;
padding-right:50px;
padding-left:50px;
}
</style>
</head>
<body>
<p>HTML中文网</p>
</body>
</html>
```
### 值复制：

通过值复制，不用重复地键入这对数字

``` css
padding:25px 50px 75px 100px;
```

上填充为25px、右填充为50px、下填充为75px、左填充为100px

```css
padding:25px 50px 75px;
```

上填充为25px、左右填充为50px、下填充为75px

```css
padding:25px 50px;
```

上下填充为25px、左右填充为50px

```css
padding:25px;
```
所有的填充都是25px

### 所有的CSS填充属性

|属性|说明 |
|--|--|
| padding | 使用简写属性设置在一个声明中的所有填充属性 |
| padding-bottom | 设置元素的底部填充 |
| padding-left | 设置元素的左部填充 |
| padding-right | 设置元素的右部填充 |
| padding-top | 设置元素的顶部填充 |

## 背景(Backgrounds)

CSS Backgrounds(背景)属性是用于定义HTML元素的背景，本节给大家简单介绍一下css 背景属性使用和所呈现的效果。


CSS 背景属性用于定义HTML元素的背景

CSS 属性定义背景效果:

- background-color

- background-image

- background-repeat

- background-attachment

- background-position


### 背景颜色：background-color

background-color属性可为元素设置背景色，这个属性接受任何合法的颜色值

``` css
 body{
 	background-color:pink;
 }
```


### 背景图片：background-image###

background-image 属性描述了元素的背景图像，默认情况下，背景图像进行平铺重复显示，以覆盖整个元素实体

```css
body{
	background-image:url("images/33.jpg");
}
```
### 背景重复：background-repeat###

属性值 repeat 导致图像在水平垂直方向上都平铺，就像以往背景图像的通常做法一样。repeat-x 和 repeat-y 分别导致图像只在水平或垂直方向上重复，no-repeat 则不允许图像在任何方向上平铺

水平方向上

```css
body{
	background-repeat: repeat-x;
}
```
垂直方向上
```
body{
	background-image:url("images/Image 16.jpg");
	background-repeat: repeat-y;
}
```

### 背景图像是否固定：background-attachment

- scroll：背景图片随页面的其余部分滚动。这是默认    

- fixed：背景图像是固定的    

- inherit：指定background-attachment的设置应该从父元素继承   

设置图像是随页面滚动的

```css
body{
	height: 5000px;
	background-image:url("images/Image 16.jpg");
	background-repeat: no-repeat;
	background-attachment:scroll;
}

```

### 背景定位：background-position

可以利用 background-position 属性改变图像在背景中的位置，它有四个值分别为：left、right、top、bottom。可以通过这些值改变图像背景位置

```css
body{
	height: 5000px;
	background-image:url("images/Image 16.jpg");
	background-repeat: no-repeat;
	background-position: right top;
}

```
### CSS背景属性


|属性|描述 |
|--|--|
| background |  简写属性，作用是将背景属性设置在一个声明中 |
| background-color | 设置元素的背景颜色 |
| background-image | 把图像设置为背景 |
| background-position | 设置背景图像是否及如何重复 |
| background-repeat | 设置元素的顶部填充 |
| background-attachment  | 背景图像是否固定或者随着页面的其余部分滚动 |

## 边框(Border)

元素的边框是围绕元素内容和内边距的一条线或者多条线 ,它允许设置元素边框的样式、宽度和颜色

### 边框样式

border-style属性用来定义边框的样式

border-style的值：

|属性|描述 |
|--|--|
| none |  默认无边框 |
| dotted | 定义一个点状边框 |
| dashed	 | 定义一个虚线边框 |
| solid | 定义实线边框 |
| double | 定义两个边框。 两个边框的宽度和 border-width 的值相同 |
| groove  | 定义3D沟槽边框 |
| ridge | 定义3D脊边框 |
| inset  | 定义一个3D的嵌入边框 |
| outset  | 定义一个3D突出边框 |



```html
<p style="border-style:none;">
   none:无边框
</p>
<p style="border-style:dotted;">
   dotted：点状边框
</p>
<p style="border-style:dashed;">
    dashed: 虚线边框
</p>
<p style="border-style:solid;">
    solid: 实线边框
</p>
<p style="border-style:double;">
    double: 两个边框
</p>
<p style="border-style:groove;">
    groove: 3D沟槽边框
</p>
<p style="border-style:ridge;">
    ridge: 3D脊边框
</p>
<p style="border-style:inset;">
    inset:3D的嵌入边框
</p>
<p style="border-style:outset;">
    outset:3D突出边框
</p>
```
### 边框宽度

border-width 属性可以为边框指定宽度

指定宽度的两种方法：直接指定数值、或者关键字（thick、medium（默认值）、thin）

```html
<p style="border-style:none;border-width: thick;">
   none:无边框
</p>
<p style="border-style:dotted;border-width: thick;">
   dotted：点状边框
</p>
<p style="border-style:dashed;border-width: thick;">
    dashed: 虚线边框
</p>
<p style="border-style:solid;border-width: thick;">
    solid: 实线边框
</p>

```

### 边框颜色：

border-color 属性可以设置边框的颜色，可以使用任何类型的颜色值

```html
<p style="border-style:none;border-color:pink;">
   none:无边框
</p>
<p style="border-style:dotted;border-color:pink;">
   dotted：点状边框
</p>
<p style="border-style:dashed;border-color:pink;">
    dashed: 虚线边框
</p>
<p style="border-style:solid;border-color:pink;">
    solid: 实线边框
</p>
```
::: warning 注意
   如果未声明边框颜色，则与文本颜色相同；若元素中没有任何文本，则边框颜色就是其父元素的文本颜色
:::

### 单独设置边框：

```css
p{  width:100px;
			height: 100px;
			border-left-style: dotted;
			border-top-style: dashed;
			border-right-style:solid;
			border-bottom-style:ridge;
			border-left-color:#F9AFF1;
			border-top-color:#FF97FE;
			border-right-color:#E35CF1;
			border-bottom-color:#C319F6;

}

```
### CSS边框属性
|属性|描述 |
|--|--|
| border|简写属性，用于把针对四个边的属性设置在一个声明。 |
| border-style|用于设置元素所有边框的样式，或者单独地为各边设置边框样式。|
| border-width|简写属性，用于为元素的所有边框设置宽度，或者单独地为各边边框设置宽度。|
| border-color|简写属性，设置元素的所有边框中可见部分的颜色，或为 4 个边分别设置颜色。|
| border-bottom|简写属性，用于把下边框的所有属性设置到一个声明中。|
| border-bottom-color|设置元素的下边框的颜色。|
| border-bottom-style |设置元素的下边框的样式。|
| border-bottom-width| 设置元素的下边框的宽度。|
| border-left|简写属性，用于把左边框的所有属性设置到一个声明中。 |
| border-left-color| 设置元素的左边框的颜色。|
| border-left-color| 设置元素的左边框的颜色。|
| border-left-style| 设置元素的左边框的样式。|
| border-left-width| 设置元素的左边框的宽度。|
| border-right| 简写属性，用于把右边框的所有属性设置到一个声明中。|
| border-right-color| 设置元素的右边框的颜色。|
| border-right-style| 设置元素的右边框的样式。|
| border-right-width| 设置元素的右边框的宽度。|
| border-top| 简写属性，用于把上边框的所有属性设置到一个声明中。|
| border-top-color| 设置元素的上边框的颜色。|
| border-top-style| 设置元素的上边框的样式。|
| border-top-width| 设置元素的上边框的宽度。|

## 颜色(Color)

色彩 Color

|属性 | 版本| 继承性| 描述|
|--|--|--|--|
|color|CSS1|有|指定颜色。请参阅 颜色值|
|opacity|CSS3|无|定义元素的不透明度|

## 字体(Fonts)

CSS 字体属性定义文本的字体系列、大小、加粗、风格（如斜体）和变形（如小型大写字母）

### CSS字体系列：

在 CSS 中，有两种不同类型的字体系列名称：

- 通用字体系列：拥有相似外观的字体系统组合（比如 "Serif" 或 "Monospace"）

- 特定字体系列 ： 具体的字体系列（比如 "Times" 或 "Courier"）

### 设置字体系列

font-family 属性用于设置文本的字体系列。

font-family 属性应该设置几个字体名称作为一种"后备"机制，如果浏览器不支持第一种字体，他将尝试下一种字体。

::: warning 注意
   如果字体系列的名称超过一个字，它必须用引号，如Font Family："宋体"，多个字体系列是用一个逗号分隔指明
:::

```css
h1{pfont-family:"Times New Roman", Times, serif;}
```

### 设置字体样式

    主要是用于指定斜体文字的字体样式属性

    这个属性有三个值：

    - normal：正常显示文本

    - italic：以斜体字显示的文字

    - oblique：文字向一边倾斜（和斜体非常类似，但浏览器不太支持）

```html
<style type="text/css">
	h1{
		font-style: normal;
	}
	h2{
		font-style:italic;
	}
	h3{
		font-style:oblique;
	}
	</style>
</head>
<body>
	<h1>This is a heading</h1>
	<h2>This is a heading</h2>
	<h3>This is a heading</h3>
</body>

```
### 设置字体大小：

    font-size 属性设置文本的大小。

    font-size 值可以是绝对或相对值。

    - 绝对值：将文本设置为指定的大小不允许用户在所有浏览器中改变文本大小（不利于可用性），绝对大小在确定了输出的物理尺寸时很有用

    例：像素（px）

    - 相对大小：相对于周围的元素来设置大小允许用户在浏览器改变文本大小

    例：em

    1em 等于当前的字体尺寸，如果一个元素的 font-size 为 16 像素，那么对于该元素，1em 就等于 16 像素。在设置字体大小时，em 的值会相对于父元素的字体大小改变。

```html

<style type="text/css">
	.p1{
		font-size:16px;
	}
	.p2{
		font-style:1em;
	}
	</style>
</head>
<body>
	<p class="p1">This is a heading</p>
	<p class="p2">This is a heading</p>

</body>
```
### 设置字体加粗：

font-weight 属性设置文本的粗细。

使用 bold 关键字可以将文本设置为粗体。

关键字 100 ~ 900 为字体指定了 9 级加粗度。如果一个字体内置了这些加粗级别，那么这些数字就直接映射到预定义的级别，100 对应最细的字体变形，900 对应最粗的字体变形。数字 400 等价于 normal，而 700 等价于 bold。

如果将元素的加粗设置为 bolder，浏览器会设置比所继承值更粗的一个字体加粗。与此相反，关键词 lighter 会导致浏览器将加粗度下移而不是上移。

```html

<style type="text/css">
	.p1{
		font-weight:bold;
	}
	.p2{
		font-weight:700;
	}
	</style>
</head>
<body>
	<p class="p1">This is a heading</p>
	<p class="p2">This is a heading</p>

</body>
```

### 所有CSS字体属性

|Property|描述|
|--|--|
|font|在一个声明中设置所有的字体属性|
|font-family|指定文本的字体系列|
|font-size|指定文本的字体大小|
|font-style|指定文本的字体样式|
|font-variant|以小型大写字体或者正常字体显示文本。|
|font-weight|指定字体的粗细。|

## 文本(Text)

CSS 文本属性可定义文本的外观。 通过文本属性，您可以改变文本的颜色、字符间距，对齐文本，装饰文本，对文本进行缩进

|属性|描述|
|--|--|
|color|设置文本颜色|
|direction|设置文本方向|
|letter-spacing|设置字符间距|
|line-height|设置行高|
|text-align|对齐元素中的文本|
|text-indent|缩进元素中文本的首行|
|text-shadow|设置文本阴影|
|text-transform|控制元素中的字母|
|unicode-bidi|设置或返回文本是否被重写|
|vertical-align|设置元素中空白的处理方式|
|white-space|向文本添加修饰|
|word-spacing|设置字间距|

## 文本装饰(Text Decoration)

|属性|描述|
|--|--|
|text-decoration|简写属性。定义元素文本装饰|
|text-decoration-line|定义元素文本装饰线条位于文本的哪个位置|
|text-decoration-color|指定元素文本装饰线条的颜色|
|text-decoration-style|定义元素文本装饰线条的形状|
|text-decoration-skip|定义元素文本装饰线条必须跳过内容中的哪些部分|
|text-underline-position|定义元素装饰线的位置|
|text-shadow|设置文本阴影|

## 书写模式(Writing Modes)

|属性|描述|
|--|--|
|direction|检索或设置文本流的方向|
|unicode-bidi|用于同一个页面里存在从不同方向读进的文本显示。与 <' direction '> 属性一起使用|
|writing-mode|设置或检索对象的内容块固有的书写方向|

## 列表样式(List)

CSS 列表样式可以设置不同列表项标记的有序列表，不同列表项标记的无序列表或者是设置列表的标记为图像。

- 设置不同列表项标记的有序列表
- 设置不同列表项标记的无序列表
- 设置列表项标记为图像

```html
<style>
ul.a {list-style-type:circle;}
ul.b {list-style-type:square;}
ol.c {list-style-type:upper-roman;}
ol.d {list-style-type:lower-alpha;}
</style>
</head>
<body>
<p>无序列表实例:</p>
<ul class="a">
  <li></li>
</ul>
<ul class="b">
  <li></li>
</ul>
<p>有序列表实例:</p>
<ol class="c">
  <li></li>
</ol>
<ol class="d">
  <li></li>
</ol>
```
**简写列表样式**

为简单起见，可以将 3 个列表样式属性合并为一个方便的属性：`list-style`

|属性|描述|
|--|--|
|list-style|简写属性。用于把所有用于列表的属性设置于一个声明中|
|list-style-image|将图象设置为列表项标志。|
|list-style-position|设置列表中列表项标志的位置。|

## 表格(Table)

table属性通过改变表格的边框，内边距，文本的对齐方式以及颜色来使表格变得更加美观

**表格边框**

```html
<table border="1">
	<tr>
		<td>示例一</td>
		<td>示例一</td>
		<td>示例一</td>
	</tr>
	<tr>
		<td>示例二</td>
		<td>示例二</td>
		<td>示例二</td>
	</tr>
</table>
```

**折叠边框**
```html
<style>
table,tr,td{
	border: 1px solid #ccc;
}
table{
	border-collapse:collapse;

}
</style>
</head>

<body>
<table>
	<tr>
		<td>示例一</td>
		<td>示例一</td>
		<td>示例一</td>
	</tr>
	<tr>
		<td>示例二</td>
		<td>示例二</td>
		<td>示例二</td>
	</tr>
</table>
```
**CSS Table 属性**

|属性|描述|
|--|--|
|border-collapse|设置是否把表格边框合并为单一的边框。|
|border-spacing|设置分隔单元格边框的距离。|
|caption-side|设置表格标题的位置。|
|empty-cells|设置是否显示表格中的空单元格|
|table-layout|设置显示单元、行和列的算法。|


## 内容(Content)

**内容 Content**

|属性|描述|
|--|--|
|content|用来和:after及:before伪元素一起使用，在对象前或后显示内容|
|counter-increment|设定当一个selector发生时计数器增加的值|
|counter-reset|将指定selector的计数器复位|
|quotes|设置或检索对象内使用的嵌套标记|

## 浮动 (Float)

Float会使元素向左或向右移动，其周围的元素也会重新排列，常常用于图像，但它在布局时也一样非常有用

CSS 中所有的浮动属性


|属性|描述|值|
|--|--|--|
|clear|指定不允许元素周围有浮动元素。|left、right、both、none、inherit |
|float|指定一个盒子（元素）是否可以浮动。|left、right、none、inherit|

**未完待续......**
