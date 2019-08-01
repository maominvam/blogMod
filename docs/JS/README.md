# JS 入门

JavaScript 是 Web 的编程语言。

所有现代的 HTML 页面都使用 JavaScript。

JavaScript 非常容易学。

## JavaScript 用法

HTML 中的脚本必须位于 `<script>` 与 `</script>` 标签之间。
脚本可被放置在 HTML 页面的 `<body>` 和 `<head>` 部分中。

**内部的js**
```html
<head>
<script>
function myFunction()
{
    document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
}
</script>
</head>
```
**外部的js**
```js
<script src="myScript.js"></script>
```
## JavaScript 输出
- 使用 window.alert() 弹出警告框。

- 使用 document.write() 方法将内容写到 HTML 文档中。

- 使用 innerHTML 写入到 HTML 元素。

- 使用 console.log() 写入到浏览器的控制台。
**使用 window.alert()**
```html
<!DOCTYPE html>
<html>
<body>
<script>
window.alert(5 + 6);
</script>
<h1>我的第一个页面</h1>
<p>我的第一个段落</p>
</body>
</html>
```
**操作 HTML 元素**
```html
<!DOCTYPE html>
<html>
<body>
<p id="demo">我的第一个段落</p>
<script>
document.getElementById("demo").innerHTML = "HTML中文网";
</script>
</body>
</html>
```
**写到 HTML 文档**
```html
<!DOCTYPE html>
<html>
<body>
<p>我的第一个段落。</p>
<script>
document.write(Date());
</script>
</body>
</html>
```
**写到控制台**

浏览器中使用 F12 来启用调试模式， 在调试窗口中点击 "Console" 菜单。
```html
<!DOCTYPE html>
<html>
<body>
<script>
a = 5;
b = 6;
c = a + b;
console.log(c);
</script>
</body>
</html>
```
## JavaScript 语法


JavaScript 是一个脚本语言。
它是一个轻量级，但功能强大的编程语言。

**JavaScript 字面量**

字符串（String）字面量 可以使用单引号或双引号:
```js
document.getElementById("demo").innerHTML = 'John Doe';
```
表达式字面量 用于计算：
```js
document.getElementById("demo").innerHTML = 5 * 10;
```
数组（Array）字面量 定义一个数组：

```js
[40, 100, 1, 5, 25, 10]
```
对象（Object）字面量 定义一个对象：

```js
{firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}
```
函数（Function）字面量 定义一个函数：

```js
function myFunction(a, b) { return a * b;}
```
**JavaScript 变量**

在编程语言中，变量用于存储数据值。
JavaScript 使用关键字 var 来定义变量， 使用等号来为变量赋值：

```js
<script>
var length;
length = 6;
document.getElementById("demo").innerHTML = length;
</script>
```
变量可以通过变量名访问。在指令式语言中，变量通常是可变的。字面量是一个恒定的值。

注意：变量是一个名称。字面量是一个值。

**JavaScript 操作符**

JavaScript使用 算术运算符 来计算值:

```js
document.getElementById("demo").innerHTML = (5 + 6) * 10;
```
JavaScript使用赋值运算符给变量赋值：

```js
var x, y, z;
x = 5;
y = 6;
z = (x + y) * 10;
document.getElementById("demo").innerHTML = z;
```

JavaScript语言有多种类型的运算符：

| 属性 |实例| 描述 |
|--|--|--|
| 赋值，算术和位运算符 |  =  +  -  *  / |在 JS 运算符中描述 |
| 条件，比较及逻辑运算符  | ==  != <  > |在 JS 比较运算符中描述 |

**JavaScript 语句**

在 HTML 中，JavaScript 语句向浏览器发出的命令。

语句是用分号分隔：

```js
x = 5 + 6;
y = x * 10;
```
**JavaScript 关键字**

JavaScript 关键字用于标识要执行的操作。

和其他任何编程语言一样，JavaScript 保留了一些关键字为自己所用。

var 关键字告诉浏览器创建一个新的变量：

```js
var x = 5 + 6;
var y = x * 10;
```
JavaScript 同样保留了一些关键字，这些关键字在当前的语言版本中并没有使用，但在以后 JavaScript 扩展中会用到。

JavaScript 关键字必须以字母、下划线_或美元符（$）开始。
后续的字符可以是字母、数字、下划线或美元符（数字是不允许作为首字符出现的，以便 JavaScript 可以轻易区分开关键字和数字）。


以下是 JavaScript 中最重要的保留字（按字母顺序）：

|  | |  | |
|--|--|--|--|
|abstract|	else|	instanceof|	super
|boolean|	enum|	int|	switch
|break|	export|	interface|	synchronized
|byte|	extends|	let|	this
|case|	false|	long|	throw
|catch|	final|	native|	throws
|char|	finally|	new|	transient
|class|	float|	null|	true
|const|	for|	package|	try
|continue|	function|	private|	typeof
|debugger|	goto|	protected|	var
|default|	if|	public|	void
|delete|	implements|	return|	volatile
|do|	import|	short|	while
|double|	in|	static|	with
**JavaScript 注释**

不是所有的 JavaScript 语句都是"命令"。双斜杠 // 后的内容将会被浏览器忽略：

```js
// 我不会执行
```
**JavaScript 数据类型**

JavaScript 有多种数据类型：数字，字符串，数组，对象等等：

```js
var length = 16;// Number 通过数字字面量赋值
var points = x * 10;// Number 通过表达式字面量赋值
var lastName = "Johnson";// String 通过字符串字面量赋值
var cars = ["Saab", "Volvo", "BMW"];// Array  通过数组字面量赋值
var person = {firstName:"John", lastName:"Doe"};// Object 通过对象字面量赋值
```
**数据类型的概念**

编程语言中，数据类型是一个非常重要的内容。

为了可以操作变量，了解数据类型的概念非常重要。

如果没有使用数据类型，以下实例将无法执行：
```js
16 + "Volvo"
```
**JavaScript 函数**

JavaScript 语句可以写在函数内，函数可以重复引用：
引用一个函数 = 调用函数(执行函数内的语句)。

```js
function myFunction(a, b) {
   return a * b; // 返回 a 乘以 b 的结果
}
```

**JavaScript 字母大小写**

JavaScript 对大小写是敏感的。

当编写 JavaScript 语句时，请留意是否关闭大小写切换键。

函数 getElementById 与 getElementbyID 是不同的。

同样，变量 myVariable 与 MyVariable 也是不同的。

**JavaScript 字符集**

JavaScript 使用 Unicode 字符集。

Unicode 覆盖了所有的字符，包含标点等字符。

**JavaScript 语句**

JavaScript 语句是发给浏览器的命令。

这些命令的作用是告诉浏览器要做的事情。


未完待续......
