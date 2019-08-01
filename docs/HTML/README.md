# HTML入门

HTML 教程- (HTML5 标准)

超文本标记语言（英语：HyperText Markup Language，简称：HTML）是一种用于创建网页的标准标记语言！

您可以使用 HTML 来建立自己的 WEB 站点，HTML 运行在浏览器上，由浏览器来解析。

在本教程中，您将学习如何使用 HTML 来创建站点。

HTML 很容易学习！相信您能很快学会它！

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>HTML中文网(html.cn)</title>
</head>
<body>
    <h1>我的第一个标题</h1>
    <p>我的第一个段落。</p>
</body>
</html>
```
## 表格

表格是由 `<table>` 标签来定义，每个表格的行由 `<tr>` 标签定义，每行被分割为若干单元格由 `<td>` 标签定义。数据单元格可以包含文本、图片、列表、段落、表单、水平线、表格等等

```html
<body>
    <table border="1" border-collapse: collapse>
        <caption>个人信息</caption>
        <tr>
            <td>ID</td>
            <td>姓名</td>
            <td>年龄</td>
            <td>分数</td>
        </tr>
        <tr>
            <td>1</td>
            <td>张三</td>
            <td>18</td>
            <td>90</td>
        </tr>
        <tr>
            <td>2</td>
            <td>李四</td>
            <td>20</td>
            <td>88</td>
        </tr>
    </table>
</body>
```
## 列表

HTML 支持有序、无序和定义列表。其中，无序列表默认使用粗体圆点（典型的小黑圆圈）进行标记；有序列表默认使用数字进行标记。

**有序列表**
```html
<ol>
    <li>篮球</li>
    <li>羽毛球</li>
    <li>足球</li>
    <li>乒乓球</li>
</ol>
```
**无序列表**

```html
<ul>
    <li>篮球</li>
    <li>羽毛球</li>
    <li>足球</li>
    <li>乒乓球</li>
</ul>
```
**定义列表**

```html
<dl>
<dt>Coffee</dt>
<dd>*Black hot drink</dd>
<dt>Milk</dt>
<dd>*White cold drink</dd>
</dl>
```
## 表单

表单是一个包含表单元素的区域。表单元素是允许用户在表单中输入内容，指的是不同类型的 input 元素、复选框、单选按钮、提交按钮等等。表单是一个包含表单元素的区域。
表单元素是允许用户在表单中输入内容,比如：文本域(`textarea`)、下拉列表、单选框(`radio-buttons`)、复选框(`checkboxes`)等等。
表单使用表单标签  `<form>` 来设置的，下面就来好好介绍一下HTML 表单元素。

**form元素**

```html
<form>
.
input 元素
.
</form>
```
**input元素**

| 类型 | 描述 |
|--|--|
| text | 定义常规文本输入 |
| radio | 定义单选按钮输入（选择多个选择之一） |
| submit | 定义提交按钮（提交表单） |
| password | 定义密码字段的输入 |
| checkbox | 定义多选按钮输入 |

```html
<form>
用户名：<input type="text">
密码：<input type="password">
</form>
```
**单选与多选**

```html
<form>
单选：<input type="radio" name="sex" value="male">男
<input type="radio" name="sex" value="female">女<br>
多选：<input type="checkbox" name="subject" value="Math">数学
     <input type="checkbox"  name="subject" value="English">英语
</form>
```
**提交**

```html
<form>
<input type="text">
<input type="submit" name="submit">
</form>
```
**HTML Form 属性**

| 属性 | 描述 |
|--|--|
| action | 指向何处提交表单的地址（URL） |
| enctype | 指被提交数据的编码（默认：url-encoded） |
| method | 指在提交表单时所用的 HTTP 方法（默认：GET） |
| name   | 指识别表单的名称 |
| target   | 指 action 属性中地址的目标 |
| novalidate   | 指浏览器不验证表单 |
| accept-charset    | 指在被提交表单中使用的字符集 |
| autocomplete   | 指浏览器应该自动完成表单 |

**表单中的GET与POST的使用**

当表单提交的数据是是被动的，并且没有敏感信息可采用GET的方式提交

如果表单正在更新数据，或者是包含敏感信息时就可以用POST方式，因为它安全性更高

## 链接

HTML 使用超级链接与网络上的另一个文档相连。几乎可以在所有的网页中找到链接。点击链接可以从一张页面跳转到另一张页面。
HTML使用标签 `<a>`来设置超文本链接。

超链接可以是一个字，一个词，或者一组词，也可以是一幅图像，您可以点击这些内容来跳转到新的文档或者当前文档中的某个部分。

当您把鼠标指针移动到网页中的某个链接上时，箭头会变为一只小手。

在标签`<a>` 中使用了href属性来描述链接的地址。

默认情况下，链接将以以下形式出现在浏览器中：

1.一个未访问过的链接显示为蓝色字体并带有下划线。

2.访问过的链接显示为紫色并带有下划线。

3.点击链接时，链接显示为红色并带有下划线。

注意：如果为这些超链接设置了 CSS 样式，展示样式会根据 CSS 的设定而显示。

```html
<a href="">访问vam的金豆之路</a>
```
**target属性**

使用 target 属性，你可以定义被链接的文档在何处显示。

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>HTML中文网(html.cn)</title> 
</head>
<body>

<a href="https://www.html.cn/" target="_blank">访问HTML中文网!</a>

<p>如果你将 target 属性设置为 "_blank", 链接将在新窗口打开。</p>

</body>
</html>
```
**id属性**

id属性可用于创建在一个HTML文档书签标记。
提示: 书签是不以任何特殊的方式显示，在HTML文档中是不显示的，所以对于读者来说是隐藏的。
实例

```html
<a id="tips">有用的提示部分</a>
<a href="#tips">访问有用的提示部分</a>
```

## 属性

HTML 标签可以拥有属性，属性提供了有关 HTML 元素的更多的信息。它总是以名称/值对的形式出现，比如：name="value"。

| 属性 | 含义 |
|--|--|
| class | 元素的类名 |
| id | 元素的唯一id |
| style | 元素的行内样式 |
| title   | 元素的额外信息 |

注意：属性和属性值对大小写不敏感，但最好还是以小写的形式去写；属性值应该始终被包括在引号内，双引号是最常用的，不过使用单引号也没有问题。

## 图像

我们可以通过`<img>`标签在HTML文档中显示图像。`<img>`标签是一个空标签，只包含属性，并且没有闭合标签。

```html
<img src="url">
```

**替换文本属性Alt**

alt 属性用来为图像定义一串预备的可替换的文本，替换文本属性的值是用户定义的

```html
<img src="1.jpg" alt="cat">
```

## 框架

通过使用框架，你可以在同一个浏览器窗口中显示不止一个页面。每份HTML文档称为一个框架，并且每个框架都独立于其他的框架。

**框架标签（iFrame）**
```html
<iframe src="http://www.html.cn/"></iframe>
```

| 属性 | 值 | 描述 |
|--|--|--|
| frameborder | 1，0 | 表示是否显示框架周围的边框 |
| height | px | 表示 iframe 的高度 |
| width | px | 表示 iframe 的宽度 |
| name   | frame_name |表示iframe 的名称 |
| scrolling   | yesnoauto |规定是否在 iframe 中显示滚动条 |
| src   | URL |规定在 iframe 中显示的文档的 URL。 |
| srcdoc| HTML_code |在 `<iframe>` 中显示的页面的 HTML 内容 |
| marginheight  | px |定义 iframe 的顶部和底部的边距 |
| marginwidth   | px |定义 iframe 的左侧和右侧的边距 |

```html
<iframe src="http://www.html.cn" width="450px" height="300px"></iframe>
```

## 速查列表

**HTML 基本文档**
```html
<!DOCTYPE html>
<html>
<head>
<title>文档标题</title>
</head>
<body>
可见文本...
</body>
</html>
```

**基本标签（Basic Tags）**
```html
<h1>最大的标题</h1>
<h2> . . . </h2>
<h3> . . . </h3>
<h4> . . . </h4>
<h5> . . . </h5>
<h6>最小的标题</h6>
 
<p>这是一个段落。</p>
<br> （换行）
<hr> （水平线）
<!-- 这是注释 -->
```

**文本格式化（Formatting）**
```html
<b>粗体文本</b>
<code>计算机代码</code>
<em>强调文本</em>
<i>斜体文本</i>
<kbd>键盘输入</kbd> 
<pre>预格式化文本</pre>
<small>更小的文本</small>
<strong>重要的文本</strong>
 
<abbr> （缩写）
<address> （联系信息）
<bdo> （文字方向）
<blockquote> （从另一个源引用的部分）
<cite> （工作的名称）
<del> （删除的文本）
<ins> （插入的文本）
<sub> （下标文本）
<sup> （上标文本）
```

**链接（Links）**
```html
普通的链接：<a href="http://www.example.com/">链接文本</a>
图像链接： <a href="http://www.example.com/"><img src="URL" alt="替换文本"></a>
邮件链接： <a href="mailto:webmaster@example.com">发送e-mail</a>
书签：
<a id="tips">提示部分</a>
<a href="#tips">跳到提示部分</a>
```

**图片（Images）**
```html
<img src="URL" alt="替换文本" height="42" width="42">
```

**样式/区块（Styles/Sections）**
```html
<style type="text/css">
h1 {color:red;}
p {color:blue;}
</style>
<div>文档中的块级元素</div>
<span>文档中的内联元素</span>
```

**无序列表**
```html
<ul>
    <li>项目</li>
    <li>项目</li>
</ul>
```

**有序列表**
```html
<ol>
    <li>第一项</li>
    <li>第二项</li>
</ol>
```

**定义列表**
```html
<dl>
  <dt>项目 1</dt>
    <dd>描述项目 1</dd>
  <dt>项目 2</dt>
    <dd>描述项目 2</dd>
</dl>
```

**表格（Tables）**
```html
<table border="1">
  <tr>
    <th>表格标题</th>
    <th>表格标题</th>
  </tr>
  <tr>
    <td>表格数据</td>
    <td>表格数据</td>
  </tr>
</table>
```

**框架（Iframe）**
```html
<iframe src="demo_iframe.htm"></iframe>
```

**表单（Forms）**
```html
<form action="demo_form.php" method="post/get">
<input type="text" name="email" size="40" maxlength="50">
<input type="password">
<input type="checkbox" checked="checked">
<input type="radio" checked="checked">
<input type="submit" value="Send">
<input type="reset">
<input type="hidden">
<select>
<option>苹果</option>
<option selected="selected">香蕉</option>
<option>樱桃</option>
</select>
<textarea name="comment" rows="60" cols="20"></textarea>
 
</form>
```
**实体（Entities）**
```html
&lt; 等同于 <
&gt; 等同于 >
&#169; 等同于 ©
```