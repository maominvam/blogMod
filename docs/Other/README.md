# 文章

## 【全网唯一】Nodejs使用爬虫示例——刷博客浏览量

在开始之前记住，我们的一切操作全是在**电脑**上完成，手机无效哦~
你可以使用多个浏览器哦，但是别刷的太厉害，娱乐一下~，毕竟浏览量只是虚物，实力才是硬道理。

### 第一步：看效果

**先看效果：**

[可以点这里试一下](https://www.maomin.club/look)

然后你的浏览器会出现这个警告，点允许弹窗，就能弹出好几个窗口，或者你可以去设置直接允许弹窗。

最后你把所有的浏览记录清除掉。（因为浏览器的不同，我这就不示范了，相信一个程序员肯定会删浏览器记录，记住所有的浏览记录），

**每点上面那个示例链接一次，清除一次浏览记录。**


### 第二步：要源码
```js
console.log('加群QQ:716560543。私聊我发给你')
```

## HTML collection数组转换成正常的dom对象数组

HTML collection对象是一个类数组，如何将它转化为正常的数组，我们可以这样：

```js
var obj = document.getElementsByClassName('songlists')
```
上面的是HTML collection，下面是转化方法
```js
var arr = Array.prototype.slice.call(obj)
```
**OR**
```js
 [].slice.call(obj);
```
## 关于vue项目中axios跨域的解决方法（开发环境）
**1、在config文件中修改index.js**

```js
    proxyTable: {
      "/api":{
        target: 'https://www.baidu.com/muc/',//你需要跨域的url
        changeOrigin: true,
        pathRewrite: {
          '^/api': '/'
        }
      }
    },
```
**2、在config文件中修改dev.env.js**

```js
module.exports = merge(prodEnv, {
  NODE_ENV: '"development"',
  API_HOST:'/api/' //开发环境中加上这段关键，不然出错
})
```
**3、在config文件中修改prod.env.js**

```js
module.exports = {
  NODE_ENV: '"production"',
  API_HOST: 'https://www.baidu.com/muc/'//生产环境中加上这段关键，不然出错
}
```
**4、在你请求的端口之前加上**

```js
        this.$axios
          .get([
            '/api/captch/sent?phone' //这里需要在你请求的端口之前加上/api/.
          ])
          .then(response => {
            // success

          })
          .catch(error => {
            // error
            console.log(error)
          })
```




总结：
**这4步一步也不能少，谨记**

广告：
最后我自己创建一个QQ交流群。
IT各行各业的人都有，欢迎大家加入，
分享自己的心得体会。
QQ群：`716560543`

打扰了，请见谅~


## Vue-cookie的简单使用
**install**
```js
npm install vue-cookies --save
```
**main.js**
```js
import VueCookies from 'vue-cookies'
Vue.use(VueCookies)
```
**API:**

*设置*
```js
this.$cookies.set(keyName, time)
```
*获取*
```js
this.$cookies.get(keyName)    
```
*删除*

```js
this.$cookies.remove(keyName)
```
*查看一个cookie是否存在*

```js
this.$cookies.isKey(keyName)  
```
*获取所有cookie名称*

```js
this.$cookies.keys()
```

**示例**

*json对象*
```js
var user = { id:1, name:'Journal',session:'25j_7Sl6xDq2Kc3ym0fmrSSk2xV2XkUkX' };
this.$cookies.set('user',user);
// print user name
console.log(this.$cookies.get('user').name)
```
*过期时间
默认为1天*

|简写  |全名  |
|--|--|
| y | year|
|m|	month|
|d	|day|
|h	|hour|
|min	|minute|
|s	|second|
```js
this.$cookies.set("default_unit_second","input_value",1);         // 1秒之后
this.$cookies.set("token","GH1.1.1689020474.1484362313","60s");  // 60秒之后,
this.$cookies.set("token","GH1.1.1689020474.1484362313","30MIN");//30分钟之后 ,不区分大小写
this.$cookies.set('token',"GH1.1.1689020474.1484362313", new Date(2017,3,13).toUTCString());//某一天
this.$cookies.set("token","GH1.1.1689020474.1484362313", "Sat, 13 Mar 2017 12:25:57 GMT ");//某一时刻
this.$cookies.set("token","GH1.1.1689020474.1484362313", Infinity);  // 永不过期
this.$cookies.set("token","GH1.1.1689020474.1484362313", -1); //永不过期
```
## vue移动端 实现手机左右滑动入场动画

**app.vue**
```js
<template>
  <div id="app">
    <transition :name="transitionName">
      <keep-alive >
        <router-view v-if="$route.meta.keepAlive" class="Router"></router-view>
      </keep-alive>
    </transition >
    <transition :name="transitionName">
      <router-view v-if="!$route.meta.keepAlive"  class="Router"></router-view>
    </transition >
    <Play></Play>
  </div>
</template>
<script>import Play from './components/play'
export default {
  name: 'App',
  data () {
    return {
      transitionName: 'slide-left'
    }
  },
  watch: {
    '$route' (to, from) {
      // 切换动画
      let isBack = this.$router.isBack // 监听路由变化时的状态为前进还是后退
      if (isBack === true) {
        this.transitionName = 'slide-right'
        // from.meta.keepAlive = false
        // to.meta.keepAlive = true
      } else {
        // from.meta.keepAlive = true
        // to.meta.keepAlive = false
        // this.transitionName = 'slide-left'
        if (this.$route.path.split('/').length < 3) {
          this.transitionName = 'slide-fade'
        } else {
          this.transitionName = 'slide-left'
        }
      }
      this.$router.isBack = false
    }
  },
  components: {
    Play
  }
}
</script>

<style>
.Router {
  font-family: Roboto, Lato, sans-serif;
  position: absolute;
  width: 100%;
  height: 100%;
  padding-bottom: 60px;
  transition: all .377s ease;
  box-sizing: border-box;
  overflow: auto;
}
.slide-left-enter,
.slide-right-leave-active {
  opacity: 0;
  -webkit-transform: translate(100%, 0);
  transform: translate(100%, 0);
}

.slide-left-leave-active,
.slide-right-enter {
  opacity: 0;
  -webkit-transform: translate(-100%, 0);
  transform: translate(-100% 0);
}
.ovf {
  overflow: hidden;
}
.center {
  width: 95%;
  margin: 0 auto;
  overflow-y: hidden;
}
li {
  list-style: none;
}
</style>
```

**路由配置**

```js
    {
      path: '/playListDetail/:id',
      name: 'playListDetail',
      component: pather => require(['../components/playListDetail.vue'], pather),
      meta: {
        title: '歌单详情',
        keepAlive: true,
        isBack: false
      }
    },
```

**返回事件**

```js
 back () {
      this.$router.go(-1)
      this.$router.isBack = true
    }
```
## 关于Vue 移动端适配  （px2rem 插件将px转为rem）


**一、安装**
```js
npm install px2rem-loader  lib-flexible --save
```
**二、入口文件main.js加上**
```js
import 'lib-flexible/flexible.js'
```
**三、在index.html加上**
```html
 <meta name="viewport" content="width=device-width,initial-scale=1.0">
 <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```

**四、在build下的 utils.js中加上**
```js
const px2remLoader = {
loader: 'px2rem-loader',
options: {
remUnit: 37.5
}
}


function generateLoaders (loader, loaderOptions) {
const loaders = [cssLoader, px2remLoader]
if (loader) {
loaders.push({
loader: loader + '-loader',
options: Object.assign({}, loaderOptions, {
sourceMap: options.sourceMap
})
})
}
```
## node线上项目连接mysql出现 504 Gateway Time-Out
```js
var connection = mysql.createConnection({     
  host     : 'localhost',       
  user     : 'root',              
  password : '123456',       
  port: '3306',                   
  database: 'test'
});
```
一定别忘了加端口号 ↓
```
port: '3306',    
```
## 关于Nginx 重启时丢失nginx.pid文件

第一步、强行停止nginx进程
```
pkill -9 nginx
```
2、开启nginx进程
```
ps -ef | grep nginx
```
3、重新配置nginx.conf文件
```
nginx -c /etc/nginx/nginx.conf
```
## MYsql nodejs 出现错误之 Cannot enqueue Query after invoking quit.

不用connection.end()
```js
// connection.end();
```
## 图片上传转换成Base64，然后再转成 file 提交给后端

**图片上传代码转换成Base64**

```html
<input type="file" name="upimg" id='upimg'>

<script>
  window.onload = () => {
    let upDOM = document.getElementById('upimg')
    upDOM.addEventListener('change', (e) => {
      console.log(e)
      console.log(upDOM.files[0])
      var reader = new FileReader();
      reader.readAsDataURL(upDOM.files[0]);

      reader.onload = function (ie) {
        var Base64Val = this.result;
        console.log('Base64')

        console.log(Base64Val)
      }
    })
  }
</script>
```
**将Base64格式的图片转换成file提交给后端**

```js
  	 // Base64Val  base64格式的图片
      // fileName   生成文件的名字 （可自定义）

      var bytes=window.atob(Base64Val.split(',')[1]);
      var ab = new ArrayBuffer(bytes.length);  
      var ia = new Uint8Array(ab);  
      for (var i = 0; i < bytes.length; i++) {  
          ia[i] = bytes.charCodeAt(i);  
      }
      this[fileName] = new File( [ab] , fileName , {type : 'image/png'})
```





**OR**
```js
 new Blob([ab], {type : 'image/png'});
```
## js小效果之根据对应项目名跳转
```html
 <p><a href="http://192.168.2.61/pc/pc_MLMM/project.html?name=0">乳龄工程</a></p>
 <p><a href="http://192.168.2.61/pc/pc_MLMM/project.html?name=1">腹龄工程</a></p>
 <p><a href="http://192.168.2.61/pc/pc_MLMM/project.html?name=2">臀龄工程</a></p>
 <p><a href="http://192.168.2.61/pc/pc_MLMM/project.html?name=3">蜜龄工程</a></p>
 <p><a href="http://192.168.2.61/pc/pc_MLMM/project.html?name=4">康龄工程</a></p>
```

```js
var url='http://192.168.2.61/pc/pc_MLMM/project.html';
var obj=[
    {name:'?name=0'},
    {name:'?name=1'},
    {name:'?name=2'},
    {name:'?name=3'},
    {name:'?name=4'},
    {name:'?name=5'}
]
for (let i = 0; i < obj.length; i++) {
   if(url+obj[i].name==window.location.href){
       console.log(i)
       $('.click-b li').eq(i).addClass("ss").siblings().removeClass("ss");
       $('.wrap li').eq(i).addClass('show').siblings().removeClass('show')
   }
}
```
## html2canvans实现浏览器快速截图(这里有demo哦)
```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>html2canvas</title>
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.js"></script>
    <script src="https://cdn.jsdelivr.net/bluebird/latest/bluebird.js"></script>
    <script src="https://cdn.bootcss.com/html2canvas/0.5.0-beta3/html2canvas.js"></script>
    <!-- <script src="https://cdn.jsdelivr.net/npm/canvas2image@1.0.5/canvas2image.js"></script> -->
    <!-- <script src = "https://cdn.polyfill.io/v2/polyfill.min.js"></script> -->
    <style>
    *{
    	margin: 0;
    	padding: 0
    }
    #content{
    	width: 90%;
    	margin: 0 auto;
    	height: 300px;
    	text-align: center;
    	line-height: 300px;
    	border:1px solid #333;
    	box-sizing: border-box;
    }
    a {
        cursor: pointer;
        color: #333;
        text-decoration: underline;
    }
    </style>
</head>

<body>
    <div id="content" >
        <h1>hello html2canvas!</h1>
    </div>
    <script>
    $("#content").on("click", function(event) {
        event.preventDefault();
        var userAgent = navigator.userAgent;
        var isIE = userAgent.indexOf("compatible") > -1 && userAgent.indexOf("MSIE") > -1;
        html2canvas($('#content'), {
            allowTaint: true,
            taintTest: false,
            useCORS: true, //火狐浏览器添加项
            onrendered: function(canvas) {

                var image = canvas.toDataURL("image/png").replace("image/png", "image/octet-stream");
                var userAgent = navigator.userAgent;
                //判断是否是IE11
                debugger
                if (-1 !== userAgent.indexOf("Trident")) {
                    var arr = image.split(',');
                    var mime = arr[0].match(/:(.*?);/)[1];
                    var bstr = atob(arr[1]);
                    var n = bstr.length;
                    var u8arr = new Uint8Array(n);
                    while (n--) {
                        u8arr[n] = bstr.charCodeAt(n);
                    }
                    window.navigator.msSaveBlob(new Blob([u8arr], { type: mime }), "download.png");
                } else {
                    canvas.id = "mycanvas";
                    //生成base64图片数据
                    var dataUrl = canvas.toDataURL();
                    var newImg = document.createElement("img");
                    newImg.src = dataUrl;
                    var a = $("<a></a>").attr("href", dataUrl).attr("download", "img.png");
                    $("body").append(a); //火狐浏览器添加项
                    a[0].click();
                    a.remove();
                }
            }
        });
    });
    </script>
</body>

</html>
```
## select选择标签自定义下拉按钮
```html
<select>
<option value="" disabled selected style="display:none;">请选择时间</option>
</select>
```
```css
select{
	 appearance: none;
    -moz-appearance: none;
    -webkit-appearance: none;
    background: url(../images/go.png) no-repeat scroll 386px center transparent;
}
```
## 15个实用实用正则（小哥进来看看？）
```js
// 1 用户名正则
//用户名正则，4到16位（字母，数字，下划线，减号）
var uPattern = /^[a-zA-Z0-9_-]{4,16}$/;
console.log(uPattern.test("maomincoding"));//输出 true
// 2 密码强度正则
//密码强度正则，最少6位，包括至少1个大写字母，1个小写字母，1个数字，1个特殊字符
var pPattern = /^.*(?=.{6,})(?=.*\d)(?=.*[A-Z])(?=.*[a-z])(?=.*[!@#$%^&*? ]).*$/;
console.log("=="+pPattern.test("caibaojian#"));//输出 true
// 3 整数正则
//正整数正则
var posPattern = /^\d+$/;
//负整数正则
var negPattern = /^-\d+$/;
//整数正则
var intPattern = /^-?\d+$/;
console.log(posPattern.test("42"));//输出 true
console.log(negPattern.test("-42"));//输出 true
console.log(intPattern.test("-42"));//输出 true
// 4 数字正则
//正数正则
var posPattern = /^\d*\.?\d+$/;
//负数正则
var negPattern = /^-\d*\.?\d+$/;
//数字正则
var numPattern = /^-?\d*\.?\d+$/;
console.log(posPattern.test("42.2"));
console.log(negPattern.test("-42.2"));
console.log(numPattern.test("-42.2"));
// 5 Email正则
//Email正则
var ePattern = /^([A-Za-z0-9_\-\.])+\@([A-Za-z0-9_\-\.])+\.([A-Za-z]{2,4})$/;
console.log(ePattern.test("815682884@qq.com"));//输出 true
// 6 手机号码正则
//手机号正则
var mPattern = /^1[34578]\d{9}$/;
console.log(mPattern.test("15555555555"));//输出 true
// 7 身份证号正则
//身份证号（18位）正则
var cP = /^[1-9]\d{5}(18|19|([23]\d))\d{2}((0[1-9])|(10|11|12))(([0-2][1-9])|10|20|30|31)\d{3}[0-9Xx]$/;
console.log(cP.test("11010519880605371X"));//输出 true
// 8 URL正则
//URL正则
var urlP= /^((https?|ftp|file):\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
console.log(urlP.test("http://maomin.com"));//输出 true
// 9 IPv4地址正则
//ipv4地址正则
var ipP = /^(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$/;
//输出 true
console.log(ipP.test("115.28.47.26"));
// 十六进制颜色正则
//RGB Hex颜色正则
var cPattern = /^#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3})$/;
console.log(cPattern.test("#f8f8f8"));//输出 true
// 11 日期正则
//日期正则，简单判定,未做月份及日期的判定
var dP1 = /^\d{4}(\-)\d{1,2}\1\d{1,2}$/;
console.log(dP1.test("2017-05-11"));//输出 true
console.log(dP1.test("2017-15-11"));//输出 true
//日期正则，复杂判定
var dP2 = /^(?:(?!0000)[0-9]{4}-(?:(?:0[1-9]|1[0-2])-(?:0[1-9]|1[0-9]|2[0-8])|(?:0[13-9]|1[0-2])-(?:29|30)|(?:0[13578]|1[02])-31)|(?:[0-9]{2}(?:0[48]|[2468][048]|[13579][26])|(?:0[48]|[2468][048]|[13579][26])00)-02-29)$/;
console.log(dP2.test("2017-02-11"));//输出 true
console.log(dP2.test("2017-15-11"));//输出 false
console.log(dP2.test("2017-02-29"));//输出 false
// 12 QQ号码正则
//QQ号正则，5至11位
var qqPattern = /^[1-9][0-9]{4,10}$/;
console.log(qqPattern.test("815682884"));//输出 true
// 13 微信号正则
//微信号正则，6至20位，以字母开头，字母，数字，减号，下划线
var wxPattern = /^[a-zA-Z]([-_a-zA-Z0-9]{5,19})+$/;
console.log(wxPattern.test("maomin9761"));//输出 true
// 14 车牌号正则
//车牌号正则
var cPattern = /^[京津沪渝冀豫云辽黑湘皖鲁新苏浙赣鄂桂甘晋蒙陕吉闽贵粤青藏川宁琼使领A-Z]{1}[A-Z]{1}[A-Z0-9]{4}[A-Z0-9挂学警港澳]{1}$/;
console.log(cPattern.test("鲁B66666"));//输出 true
// 15 包含中文正则
//包含中文正则
var cnPattern = /[\u4E00-\u9FA5]/;
console.log(cnPattern.test("林俊杰"));//输出 true
```
## js小精华，你值得一看。（持续更新中）
```js
     // 数组去重
	// (1)
	let arr = [1,1,2,3,4];
	function fun(v) {
		return Array.from(new Set(v))
	}
	console.log(fun(arr)) //[1,2,3,4]
	// (2)
	let qc= [...new Set(arr)]
	console.log(qc) //[1,2,3,4]
	// 数组并集
	let arr0 = ['a','b','c'];
	let arr2 = ['c','d'];
	let a=new Set(arr0);
	let b=new Set(arr2);
	let bj = new Set([...a,...b]);
	console.log(bj);//{"a", "b", "c", "d"}
	// 数组交集
	let jj = new Set([...a].filter(x=>b.has(x)));
	console.log(jj);//{"c"}
	//数组差集
	let cj = new Set([...a].filter(x=>!b.has(x)));
	console.log(cj);//{"a", "b"}
	// 统计数组相同项的个数
	let arr6=['a','a','a','b','c','c'];
	let arr6obj=arr6.reduce(function(obj,name){
		obj[name]=obj[name]?++obj[name]:1;
		return obj;
	},{})
	console.log(arr6obj)//{a: 3, b: 1, c: 2}
	// 数组方法reduce()实现filter、map
	let arr7=[2,3,10];
	const arro=arr7.reduce(function(list,num){
		num=num*2;
		if(num>=20){
			list.push(num)
		}
		return list;
	},[])
	console.log(arro);//[20]
	// 字符串转换为数字
	let num1='1' * 1;
	console.log(typeof num1) //number
	// 使用Boolean过滤数组中的所有假值
	let jz=[0,null,false,NaN,1,2];
	const filter1=arr1=>arr1.filter(Boolean);
	console.log(filter1(jz))//[1,2]
	// 取整
	let num2=1.223;
	console.log(num2|0);//1
	// 判断奇偶
	let num3=3;
	console.log(!!(num3 & 1));//true
	//精确到指定位数(取小数第一位)
	let num4=6.222;
	console.log(num4.toFixed(1));//6.2
	// 解构
	let [rr,aa]=[1,2];
	console.log(rr);//1
	// 使用解构交换数值
	[rr,aa]=[aa,rr];
	console.log(rr);//2
	// 判断数据类型
	let ee=[1,12];
	let ongjj={
		name:'maomin'
	}
	function isType(arr) {
    	return Object.prototype.toString.call(arr)
	}
	console.log(isType(ee));//[object Array]
	console.log(isType(ongjj));//[object Object]
	// 字符串转化为对象
	let stringobj='{"id":0,"name":"张三","age":12}';
	let d3=JSON.parse(stringobj);
	console.log(d3)//{id: 0, name: "张三", age: 12}
	// 对象转化为字符串
	let objj={
		id:0,
		name:'maomin'
	}
	let d4=JSON.stringify(objj)
	console.log(d4);//{"id":0,"name":"maomin"}
	// 字符串转化为数组
	let stringww="a,b,c,d,e,f";
	console.log(stringww.split(","))//["a", "b", "c", "d", "e", "f"]
	// 数组转化为字符串
	let arr9=['l','o','v','e'];
	console.log(arr9.join('-'))
	//去除字符串指定符号
	var stre="a,b,c,d";
	function clear(str) {
		str = str.replace(/,/g, "");//取消字符串中出现的所有逗号
		return str;
	}
	console.log(clear(stre))//abcd
```
## 关于CSS预处理器less的使用（未完待续）
简单明了，直接上教程：

下面我们先大体了解些我接下来讲的less的功能特性：

 1. 属性
 2. 嵌套
 3. 混合方法
 4. 继承
 5. 导入
 6. 函数
 7. 其他

### 1、属性
（1）、值变量

```css
@dividerColor:#000;

div{
 	background: @dividerColor;
}

```

（2）、选择器变量

```css
@footer: .footer;

@{footer}{

}
```

（3）、属性变量

```css
@color:color;

div{
 @{color}:#000;
}
```

（4）、url 变量

```css
 @images:'../images' ;

 div{
    background:url('@{images}/img.png');
}
```
(5)、声明变量


 结构:   @name: { 属性: 值 ;};
 使用：@name();
```css
  @background: {background:red;};
  #main{
     @background();
}
```
(6)、变量运算

```css
@width:300px;
@color:#222;
div{
 width:@width-20;
 height:@width-20*5;
 margin:(@width-20)*5;
 color:@color*2;
 background-color:@color + #111;
}
```
(7) 、变量作用域

就近原则

```css
 @var: @a;
 @a: 100%;
 #wrap {
        width: @var;
        @a: 9%;
 }
```
(8) 、用变量去定义变量
```css
 @fnord:  "I am fnord.";
 @var:    "fnord";
 #wrap::after{
        content: @@var; //将@var替换为其值 content:@fnord;
      }
```
### 嵌套
（1）、& 的妙用

& ：代表的上一层选择器的名字，此例便是header。
```css
.big{
   .small{
	&:after{
	color:red;
}
	&_small{
	color:green;
	}
}
}
```
(2) 媒体查询

```css
div{
@media scress{
  @media (max-width:768px){
width:100px;
}
@media tv{
width:200px;
}
}


}
```
唯一的缺点就是 每一个元素都会编译出自己 @media 声明，并不会合并。

### 混合方法

(1)、无参数方法

```css
.card {
          background: #f6f6f6;
          -webkit-box-shadow: 0 1px 2px rgba(151, 151, 151, .58);
          box-shadow: 0 1px 2px rgba(151, 151, 151, .58);
      }
#wrap{
        .card();
      }
```
(2)、默认参数方法

```css
 .border(@a:10px,@b:50px,@c:30px,@color:#000){
          border:solid 1px @color;
          box-shadow: @arguments;//指代的是 全部参数
      }
      #main{
          .border(0px,5px,30px,red);//必须带着单位
      }
```
（3）、方法中的匹配模式

```css
#main{
.csser(left,50px,#999);
}
.csser(top，@width:20px,@color:#000){
border-color:transparent transparent @color  transparent;
}
```
(4) 、方法的命名空间


```css
      #card(){
          background: #723232;
          .d(@w:300px){
              width: @w;

              #a(@h:300px){
                  height: @h;//可以使用上一层传进来的方法
                  width: @w;
              }
          }
      }
      #wrap{
          #card > .d > #a(100px); // 父元素不能加 括号
      }
      #main{
          #card .d();
      }
      #con{
          //不得单独使用命名空间的方法
          //.d() 如果前面没有引入命名空间 #card ，将会报错

          #card; // 等价于 #card();
          .d(20px); //必须先引入 #card
      }
```
 - 在 CSS 中`>` 选择器，选择的是 儿子元素，就是 必须与父元素 有直接血源的元素。
  - 在引入命令空间时，如使用 `>` 选择器，父元素不能加 括号。
  - 不得单独使用命名空间的方法 必须先引入命名空间，才能使用 其中方法。
  - 子方法 可以使用上一层传进来的方法
(5)、方法的条件筛选

```css
    #card{

        // and 运算符 ，相当于 与运算 &&，必须条件全部符合才会执行
        .border(@width,@color,@style) when (@width>100px) and(@color=#999){
            border:@style @color @width;
        }

        // not 运算符，相当于 非运算 !，条件为 不符合才会执行
        .background(@color) when not (@color>=#222){
            background:@color;
        }

        // , 逗号分隔符：相当于 或运算 ||，只要有一个符合条件就会执行
        .font(@size:20px) when (@size>50px) , (@size<100px){
            font-size: @size;
        }
    }
    #main{
        #card>.border(200px,#999,solid);
        #card .background(#111);
        #card > .font(40px);
    }
```
 - 比较运算有： > >= = =< <。
  - = 代表的是等于
  - 除去关键字 true 以外的值都被视为 false：

  (6)、数量不定的参数


```css
   	.boxShadow(...){
          box-shadow: @arguments;
    }
   .textShadow(@a,...){
          text-shadow: @arguments;
      }
   #main{
          .boxShadow(1px,4px,30px,red);
          .textShadow(1px,4px,30px,red);
      }
```
  (7)、方法使用important！

```css
.border{
          border: solid 1px red;
          margin: 50px;
      }
      #main{
          .border() !important;
      }
```
## 关于vue项目中搜索节流的实现

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190627103158201.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)


我们经常会遇到这种需求，现在我们在使用百度搜索的时候他们的思想也是
根据防抖节流而实现的，至于用防抖还是节流根据自己需求。



```html
<template>
 <input type="text"   v-model.trim="sse">
</template>
<script>
const delay = (function () {
  let timer = 0
  return function (callback, ms) {
    clearTimeout(timer)
    timer = setTimeout(callback, ms)
  }
})()
export default {
	name :  'search',
	watch : {
		sse () {
	 delay(() => {
        this.search()
      }, 500)
},
methods ：{
	search () {
        this.$axios
          .get([url])
          .then(response => {
            // success
          })
          .catch(error => {
            // error
            alert('失败！')
          })
}
}
}
}

</script>


```
## 关于vue打包上线遇到的坑
打包上线经常会经常遇到路径找不到，页面空白，那么下面我们就解决一下。

**第一步、先找到config目录的index.js**

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019062710222433.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
改成如上图红框标注所示

**第二步、找到build下的utils.js文件**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190627102448821.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
加上如上图红框所示代码


**最后我自己创建一个QQ交流群。
IT各行各业的人都有，欢迎大家加入，
分享自己的心得体会。
QQ群：716560543**
## 关于webstorm更换主题
现在我们前端使用编辑器，只要用习惯就好，不过这里推荐使用webstorm,因为被称为,'js神器'的称号，不是白说的。
接下来我们来看下怎么引入主题。

下面有一个网站，这个网站的名字叫

http://www.themesmap.com/

这个网站是JetBrains全系列主题下载,支持:InteliJ IDEA, PhpStorm, PyCharm, RubyMine, WebStorm and AppCode.
选择自己喜欢的主题下载，

然后我们打开编辑器，这里我汉化了（英文没那么好）

打开如下图所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019062709174990.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)

你会看到一个方案，对这就是主题引入之后所能看到的，接下来引入主题，点击右边的小齿轮图标，之后，点击最后一个选择项，导入选择方案。会打开一个本地文件目录。
选择你刚才下好的文件，确定，然后你就可以在方案框里找到你引入的主题了。
点击确定就ok了


到最后呢，推荐大家一个绿柔主题，为什么呢，我在那个网站上没找到这么好的主题。分享给大家

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190627092226768.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)

链接: https://pan.baidu.com/s/13ojPrbX0bin_j9mBK-HaNQ
提取码: 9984

谢谢大家


**最后我自己创建一个QQ交流群。IT各行各业的人都有，欢迎大家加入，分享自己的心得体会。
QQ群：716560543**
## 关于vue cli 使用iview 自定义主题遇到的坑
定制主题，这里讲变量覆盖
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190627095008326.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
当你老老实实的把上面文档中的代码一一复制粘贴到项目文件中时，发现了还没装less,所以你就

```
npm install less –save
npm install less-loader –save
```
结果呢
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019062709485752.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)

下面我们来解决他
我们找到项目根目录下build下的utils.js文件，把原来的（跟下面代码差不多）改成下面所示。
```
  return {
    css: generateLoaders(),
    postcss: generateLoaders(),
    less: generateLoaders('less',{ javascriptEnabled: true }),
    sass: generateLoaders('sass', { indentedSyntax: true }),
    scss: generateLoaders('sass'),
    stylus: generateLoaders('stylus'),
    styl: generateLoaders('stylus')
  }
```
运行就ok了


**最后我自己创建一个QQ交流群。IT各行各业的人都有，欢迎大家加入，分享自己的心得体会。
QQ群：716560543**
## 微信小程序—开关
wxml
```html
wxml：

 <view >
  <button  class="show" bindtap="onChangeShowState">{{showView?'隐藏':'显示'}}</button>
 </view>
 <view class="hide{{showView?'show':''}}">
      <text class="text">我是被隐藏控件</text>
 </view>
 ```
 wxss
```css
wxss:

.hide{
 display: none;
}
.show{
 display: block;
}
```
js
```js
Page({
  data: {
    showView: true
  },
  onLoad: function (options) {
    showView: (options.showView == "true" ? true : false)
  }
  , onChangeShowState: function () {
    var that = this;
    that.setData({
      showView: (!that.data.showView)
    })
  }
})
```

另一种方式：

wxml
```html
 <image src="{{showView?'http://192.168.2.61/wap/rm/images/select.png':'http://192.168.2.61/wap/rm/images/selected.png'}}"  bindtap="onChangeShowState"></image>

```
js
```js
showView:true;
onChangeShowState: function () {
   var that = this;
   that.setData({
     showView: (!that.data.showView)
   })
 }

```
## 点击其他地方关闭
```html
      <div class="fc">
        <div class="fc_box">
          <div class="fc_c">
            <p class="fc_t ovf"><span>预约挂号</span><span>只显示可预约</span></p>
            <div class="fc_b">
                <div><span >解放军总医院</span><span>皮肤科</span><img src="images/shou.png" alt=""></div>
                <ul class="fc_b1">
                  <li>
                    <p>4月24号（周三）上午</p>
                    <p class="kyy">可预约</p>
                  </li>
                  <li>
                    <p>4月24号（周三）下午</p>
                    <p class="ym">约满</p>
                  </li>
                  <li>
                    <p>4月25号（周四）上午</p>
                    <p class="kyy">可预约</p>
                  </li>
                </ul>
                <div><span>泰安市中医医院 </span><span>皮肤科</span><img src="images/shou.png" alt=""></div>
                <ul class="fc_b2">
                  <li>
                    <p>4月27号（周六）上午</p>
                    <p class="ym">约满</p>
                  </li>
                  <li>
                    <p>4月27号（周六）下午</p>
                    <p class="ym">约满</p>
                  </li>
                </ul>
            </div>
          </div>
        </div>
      </div>
  <div class="foot">
    <div class="foot_b main  ovf">
      <div><img src="images/gz.png" alt=""><p>关注</p></div>
      <div>
        <p class="yy">预约就诊</p>
        <p class="zx"><a href="chat.html">咨询医生</a></p>
      </div>
    </div>
  </div>
```

```css
.fc{ position: fixed; width: 100%; height: 100%; top: 0; bottom:0; left: 0; right:0; background: rgba(17, 17, 17, 0.35); z-index: 1000; display: none; max-width: 640px; }
.fc_box { width: 100%; height: 62%; z-index: 100; max-width: 640px; position: fixed; padding: 0.6rem 0.5rem 0 0.6rem; bottom: 0; animation: myfirst 0.5s; background: #ffffff; -webkit-animation: myfirst 0.5s; }
@keyframes myfirst { from { height: 0; } to { height: 62%; } }
.h { transition: height 1s linear; animation: mytwo 1s !important; -webkit-animation: mytwo 1s !important; -webkit-transition: height 1s linear; -moz-transition: height 1s linear; -ms-transition: height 1s linear; -o-transition: height 1s linear; }
@keyframes mytwo { from { height: 62%; } to { height: 0; } }
.fc_t span:nth-child(1){ color: #101010; font-size: 0.7rem; }
.fc_t span:nth-child(2){ float: right; color: #666666; margin-top:0.1rem; padding-left:0.8rem; background: url('../images//w1.png')no-repeat left center; background-size:14%; }
.fc_b div{ margin: 0.9rem 0; }
.fc_b div span:nth-child(1){ background: url('../images/dian.png')no-repeat left center; background-size:6%; padding-left:0.7rem; margin-right:0.3rem; }
.fc_b div img{ float: right; width: 4%; margin-top:0.3rem; }
.fc_b1 { border-bottom:1px solid #eaeaea; }
.fc_b li{ overflow: hidden; margin:1rem 0; }
.fc_b li p:nth-child(1){ float: left; margin-top:0.2rem; }
.fc_b li p:nth-child(2){ float: right; width: 17%; font-size: 0.55rem; }
.kyy{ border-radius:24px; background: #2e7ced; color: #fff; text-align: center; padding: 0.18rem 0; }
.ym{ border-radius:24px; background: #cacaca; color: #fff; text-align: center; padding: 0.15rem 0; }
.foot{ position: fixed; bottom: 0;  max-width: 640px; padding:0.2rem 0; z-index: 100; background: #fff; width: 100%; }
.foot_b div:nth-child(1) { float: left; width: 30%; text-align: center; }
.foot_b div:nth-child(1) img { width: 23%; margin: auto; }
.foot_b div:nth-child(1) p{ font-size: 0.5rem; margin-top:0.2rem; }
.foot_b div:nth-child(2) { float: left; width: 70%; margin-top:0.1rem; }
.foot_b div:nth-child(2) p{ float: left; width: 50%; text-align: center; padding: 0.4rem 0; color: #fff; }
.foot_b div:nth-child(2) p:nth-child(1){ background-color: #6eb0fa; border-radius: 36px 0px 0px 36px; }
.foot_b div:nth-child(2) p:nth-child(2){ background-color: #2e7ced; border-radius: 0px 36px 36px 0px; }
.foot_b div:nth-child(2) p:nth-child(2) a{ color: #fff; }
```

```js
$(".yy").click(function(){
  $(document).bind('mousewheel', function (event, delta) {
  return false;
  });
  $(".fc").show();
  $(".fc_box").removeClass("h");
})
 document.addEventListener("click", function(e){
 var target = event.target;
 if (target.className=="fc"){
  $(document).unbind('mousewheel');
  $(".fc").hide();
  $(".fc_box").addClass("h");
 }
 })
```
## 平滑滚动到顶部
添加类名
**top**

```js
    // 平滑滚动到顶部
    var scrollTopSmooth = function (position) {
        if (!window.requestAnimationFrame) {
            window.requestAnimationFrame = function (cb) {
                return setTimeout(cb, 10);
            };
        }
        var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
        var step = function () {
            var distance = position - scrollTop;
            scrollTop = scrollTop + distance / 5;
            if (Math.abs(distance) < 1) {
                window.scrollTo(0, position);
            } else {
                window.scrollTo(0, scrollTop);
                requestAnimationFrame(step);
            }
        };
        step();
    }
    $backToTop = document.querySelector('.top')
    $backToTop.addEventListener('click', function () {
        scrollTopSmooth(0);
    }, false);
```
## Vue cli之全家桶搭建项目
一般项目都会用到这几个，这里不在详细介绍概念，只是简单的使用。


### 一、搭建cli

**1.事先安装好cnpm(淘宝镜像)**

```js
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

 **2.cnpm install -g vue-cli**

全局安装vue脚手架工具。（下载一次就好）

**3.vue init webpack your_project_name**

创建一个脚手架项目（每次创建需要）

eg:这时在命令行中有需要你填的信息{
你的项目名；
你的项目描述；
还有你想是否下载的插件（y/n）；
}

**4.使用 npm run dev来运行项目**

就这样，一个简单的vue开发项目模板就这样下载完成了。

eg：
 i 是install 的简写。
全局安装依赖：

```js
cnpm i   依赖名
```

局部安装依赖：
```js
cnpm i -D  依赖名
```

### 二、vue-router
一般事先安装模板时，已经安装上了。
可以查看package.json中。
如果没有安装

```js
cnpm i -D vue-router
```
安装好之后，在src目录中会生成一个router目录，里面放着index.js，
一般有两种配置
第一种：
```js
import Vue from 'vue';
import Router from 'vue-router';
Vue.use(Router);
export default new Router({
    routes: [
// 一进入就显示页面
        {
            path: '/',
            redirect: '/index'
        },
        {
            path: '/',
            component: pather => require(['../components/common/bodys.vue'], pather),
            meta: { title: '主体' },
            children:[
                {
                    path: '/index',
                    component: pather => require(['../components/page/index.vue'], pather),
                    meta: { title: '系统首页' }
                },
                {
                    path: '/biaoge',
                    component: pather => require(['../components/page/biaoge.vue'], pather),
                    meta: { title: '基础表格' }
                },
                {
                    path: '/Tab',
                    component: pather => require(['../components/page/Tab.vue'], pather),
                    meta: { title: 'tab选项卡' }
                },
                {
                    path: '/jibenbiaodan',
                    component: pather => require(['../components/page/jibenbiaodan.vue'], pather),
                    meta: { title: '基本表单' }
                },
                {
                    path: '/fuwenben',
                    component: pather => require(['../components/page/fuwenben.vue'], pather),
                    meta: { title: '富文本编辑器' }
                },
                {
                    path: '/bianjiqi',
                    component: pather => require(['../components/page/bianjiqi.vue'], pather),
                    meta: { title: 'markdown编辑器' }    
                },
                {
                    path: '/shangchuan',
                    component: pather => require(['../components/page/shangchuan.vue'], pather),
                    meta: { title: '文件上传' }   
                },
                {
                    path: '/scharts',
                    component: pather => require(['../components/page/scharts.vue'], pather),
                    meta: { title: 'schart图表' }
                },
                {
                    path: '/tuozhuai',
                    component: pather => require(['../components/page/tuozhuai.vue'], pather),
                    meta: { title: '拖拽列表' }
                },
                {
                    path: '/quanxianceshi',
                    component: pather => require(['../components/page/quanxianceshi.vue'], pather),
                    meta: { title: '权限测试', permission: true }
                }             
            ]
        },
        {
            path: '/login',
            component: pather => require(['../components/page/login.vue'], pather)
        },

        {
            path: '/cuowu404',
            component: pather => require(['../components/page/cuowu404.vue'], pather)
        },
        {
            path: '/cuowu403',
            component: pather => require(['../components/page/cuowu403.vue'], pather)
        },
        {
            path: '*',
            redirect: '/404'
        }
    ],
// 去掉#号
mode:"history"
})

```
第二种：

```js
import Vue from 'vue'
import Router from 'vue-router'
import HelloWorld from '@/components/HelloWorld'
Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'HelloWorld',
      component: HelloWorld
    }
  ]
})
```

### 三、axios
先安装

```js
cnpm i -D axios
```

然后在main.js写入

```js
import axios from 'axios'

Vue.prototype.$axios = axios
```
这样就可以在组件中使用axios 获取数据了

```js
    loadData(){
            this.$axios.get(['https://free-api.heweather.com/v5/weather?city=qingdao&key=1b47b16e4aa545eaa55a66f859ac0089'])
                .then((response) => {
                    // success
                    console.log(response.data);
                })
                .catch((error) => {
                    //error
                    console.log(error);
                })
        },
```

### 四、vuex
**1、安装**

```js
cnpm i -D vuex
```
**2、然后需要手动创建一个文件夹store在src目录当中，
接着在store文件夹中创建store.js**
例：
```js
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)

export default new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment: state => state.count++,
    decrement: state => state.count--,
  }
})
```
**3、然后在main.js引入注册**

```js
import Vuex from 'vuex'
import store from './store/store'

Vue.use(Vuex)

new Vue({
  el: '#app',
  router,
  store,
  components: { App },
  template: '<App/>'
})
```
比如在headers.vue使用vuex

```html
<template>
    <div class="headers">
     <p>{{count}}</p>
     <button @click="increment">+</button>
     <button @click="decrement">-</button>
    </div>
</template>
<script>
import { mapState } from 'vuex'
export default {
  name: 'headers',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
        increment(){
          this.$store.commit('increment')
        },
        decrement(){
          this.$store.commit('decrement')
        }
  },
    computed:{
        count(){
            return this.$store.state.count
        },
    }

}
</script>
<style scoped lang="scss" >
</style>

```

### 五、sass
**1、需要安装sass**
    (1)安装node-sass
    (2)安装sass-loader
    (3)安装style-loader 有些人安装的是 vue-style-loader 其实是一样的！
```js
cnpm install node-sass --save-dev
cnpm install sass-loader --save-dev  
cnpm install style-loader --save-dev
```

**2、接着需要更改build文件夹下面的webpack.base.config.js**

```js
'use strict'
const path = require('path')
const utils = require('./utils')
const config = require('../config')
const vueLoaderConfig = require('./vue-loader.conf')

function resolve (dir) {
  return path.join(__dirname, '..', dir)
}



module.exports = {
  context: path.resolve(__dirname, '../'),
  entry: {
    app: './src/main.js'
  },
  output: {
    path: config.build.assetsRoot,
    filename: '[name].js',
    publicPath: process.env.NODE_ENV === 'production'
      ? config.build.assetsPublicPath
      : config.dev.assetsPublicPath
  },
  resolve: {
    extensions: ['.js', '.vue', '.json'],
    alias: {
      'vue$': 'vue/dist/vue.esm.js',
      '@': resolve('src'),
    }
  },
  module: {
    rules: [
      {
        test: /\.vue$/,
        loader: 'vue-loader',
        options: vueLoaderConfig
      },
      {
        test: /\.js$/,
        loader: 'babel-loader',
        include: [resolve('src'), resolve('test'), resolve('node_modules/webpack-dev-server/client')]
      },
      {
        test: /\.(png|jpe?g|gif|svg)(\?.*)?$/,
        loader: 'url-loader',
        options: {
          limit: 10000,
          name: utils.assetsPath('img/[name].[hash:7].[ext]')
        }
      },
      {
        test: /\.(mp4|webm|ogg|mp3|wav|flac|aac)(\?.*)?$/,
        loader: 'url-loader',
        options: {
          limit: 10000,
          name: utils.assetsPath('media/[name].[hash:7].[ext]')
        }
      },
      {
        test: /\.(woff2?|eot|ttf|otf)(\?.*)?$/,
        loader: 'url-loader',
        options: {
          limit: 10000,
          name: utils.assetsPath('fonts/[name].[hash:7].[ext]')
        }
      },
      { //从这一段上面是默认的！不用改！下面是没有的需要你手动添加，相当于是编译识别sass!
        test: /\.scss$/,
        loaders: ["style", "css", "sass"]
      }
    ]
  },
  node: {
    // prevent webpack from injecting useless setImmediate polyfill because Vue
    // source contains it (although only uses it if it's native).
    setImmediate: false,
    // prevent webpack from injecting mocks to Node native modules
    // that does not make sense for the client
    dgram: 'empty',
    fs: 'empty',
    net: 'empty',
    tls: 'empty',
    child_process: 'empty'
  }
}

```

**3、在你需要使用sass的地方写入即可**
```html
 <style lang="scss" scoped="" type="text/css">
 $primary-color: #333;
   body {
        color: $primary-color;
       }
</style>
```

### 六、vue UI库
这里已著名的Element组件库为例
https://element.eleme.cn/#/zh-CN/component/carousel

**1、安装**

```js
npm i element-ui -S
```
**2、使用**
在main.js写入
```js
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'

Vue.use(ElementUI)
```
**3、然后在组件使用就可以了**
例：轮播图

```html
<template>
  <el-carousel indicator-position="outside">
    <el-carousel-item v-for="item in 4" :key="item">
      <h3>{{ item }}</h3>
    </el-carousel-item>
  </el-carousel>
</template>

<style>
  .el-carousel__item h3 {
    color: #475669;
    font-size: 18px;
    opacity: 0.75;
    line-height: 300px;
    margin: 0;
  }

  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }

  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }
</style>
```


总结：就这么多了，有什么疑问欢迎添加微信：maomin9761
## 远程服务器Linux错误 ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES）

```js
vi /etc/my.cnf
```
在[mysqld]后面任意一行添加“skip-grant-tables”

```js
service mysqld restart
```

```js
mysql
```

```js
flush privileges;
```

```js
grant all privileges on *.* to root@'%' identified by '123456' with grant option;
```

```js
quit;
```

```js
service mysqld restart
```
## 关于Node.js 链接mysql超时处理（默认8小时）

**备注：这是在pm2配置node环境下，超过8小时mysql自动关闭的情况下出现的解决方法:**







**1、封装mysql.js**

```js
var mysql = require('mysql');
var connection = {
    host: '',//主机名
    user: '',//用户名
    password: '',//密码
    database: ''//数据库
}


// 用于保存数据连接实例
var db = null;

var pingInterval;

// 如果数据连接出错，则重新连接
function handleError(err) {
    logger.info(err.stack || err);
    connect();
}

// 建立数据库连接
function connect() {
    if (db !== null) {
        db.destroy();
        db = null;
    }

    db = mysql.createConnection(connection);
    db.connect(function (err) {
        if (err) {
            logger.info("error when connecting to db,reConnecting after 2 seconds:", err);
            setTimeout(connect, 2000);
        }
    });
    db.on("error", handleError);

    // 每个小时ping一次数据库，保持数据库连接状态
    clearInterval(pingInterval);
    pingInterval = setInterval(() => {
        console.log('ping...');
        db.ping((err) => {
            if (err) {
                console.log('ping error: ' + JSON.stringify(err));
            }
        });
    }, 3600000);
}

connect();
module.exports = db;
```

**2、在server.js引入以下代码就能用了**

```
var connection = require('./mysql');
```
## vue-router传参需要注意的问题
**router1页面跳到router2页面并带参数**
router1.vue
```html
<template>  
   <div class>    
   <button @click="tiao">tiao</button>  
   </div>
</template>
<script>
 export default
 {  
   name: "router1",  
   components: {},
   data() {    return {};  },
   computed: {},  
   watch: {},  
   methods: {    
     tiao() {      
       this.$router.push({        name: "router2",
       //path: '/router2',如果写这行代码会出错。paramB始终是undefined，        
       // 通过查阅文档，终于找到原因，那是因为路由的params对象使用，必须要通过路由名来调用路由，而不同通过path来调用，而query对象则没有这个要求。        params: {          paramA: "a"        },        query: {          paramB: "b"        }      });   
      }
      },
     };
  </script><style lang='scss' scoped></style>
```
router2.vue

```html
<template>  
<div class>    
<p @click="get">get</p>  
</div></template>
<script>
export default {  
  name: "router2",  
  components: {},  
  data() {    return {};  },  
  computed: {},  
  watch: {},  
  methods: {    
    get(){      console.log(this.$route.query.paramB, this.$route.params.paramA);    
   }  
  },
  };
  </script><style lang='scss' scoped></style>
```
## 你所不知道的...扩展符
**...扩展符这是es6新增的。**

1、该运算符主要用于函数调用。

```js
function add(a,b)
{    console.log(a+b);}
const arr=[1,2];
add(...arr);//3
```

2、合并数组

```js

const arr1=[1,2];
const arr2=[3,4];
const arr3=[...arr1,...arr2];
console.log(arr3);//[1,2,3,4]
```
3、将一个数组的内容添加到另一个数组的尾部

```js
const arr4=[0,1,2];
const arr5=[3,4,5];
arr4.push(...arr5);
console.log(arr4);//[0,1,2,3,4,5]
```
4、扩展运算符将字符串转为真正的数组

```js
const arrstr=[...'mao'];
console.log(arrstr);//["m", "a", "o"]
```
5、简化求出一个数组最大元素的写法。

```js
console.log(Math.max(...[14, 3, 77]))//77
```
6、将字符串转化为数组；

```js
const str = 'abcde';
const arr6 = [...str];
console.log(arr6);//["a", "b", "c", "d", "e"]
```
7、函数传参(解构赋值)

```js
const ar=[1,2];
function add1(...ar) {    console.log(ar[0]+ar[1])}add1(...ar);//3复
```
8、apply，apply第一个参数对象，第二个参数数组.

```js
let arrr = [1, 2];
function addr(x, y) {    sum = x + y;    return sum;}
let sumr = addr.apply(addr, arrr);console.log(sumr) // 3
```
## 函数柯里化与class类

**函数柯里化**

是把接收多个参数的函数变换成接收一个单一参数（最初函数的第一个参数）的函数，并返回接受剩余的参数而且返回结果的新函数的技术。
```js
function add(x) {    return function (y) {        console.log(x+y);    }}
add(1)(2);//3
```
**class类**
```js
class Person{
  //定义了一个名字为Person的类    
  constructor(name,age){
    //constructor是一个构造方法，用来接收参数    
    this.name = name;//this代表的是实例对象    
    this.age=age;
  }
    say (){
      //这是一个类的方法，注意千万不要加上function    
      return "我的名字叫" + this.name+"今年"+this.age+"岁了";
    }
  }
    const obj=new Person("maomin",22);console.log(obj.say());//我的名字叫maomin今年22岁了
```
## 关于props实现双向绑定

首先我们学过props知道，这是父组件传给子组件的一个属性，只能单向的父组件传给子组件，而不能够子组件改变父组件的值。下面我们将会实现props双向绑定的功能。

**父组件**

pare.vue

```html
<template>  
  <div class>    
     <child :a="msg" @get="post"></child>  
   </div>
   </template>
   <script>
    import child from "./child.vue";
     export default {
      name: "pare",
      components: {    child  },
      data() {    return {      msg: "maomin"    };  },  
      computed: {},   
      watch: {},  
      methods: {      
         post(data){
           this.msg=data;  
           console.log(this.msg)//happy,birthday!      
       }  },
       };
      </script>
     <style scoped></style>



```
**子组件**

child.vue

```html
<template>
 <div class>   
 <p>{{a}}</p>  
 </div>
</template>
<script>
export default {  
name: "child",  
components: {},  
props: ["a"],  
data() {    return {        msg:"happy,birthday!"    };  },  
computed: {},  watch: {      a(){          this.msg=this.a      }  },  
methods: {  },  //生命周期 - 挂载完成（可以访问DOM元素）  
mounted() {       this.$emit('get',this.msg)  },};
</script>
<style  scoped></style>

```
## 关于Vuex的简单使用（看这篇就够了）

**1、安装vuex**
```js
npm i vuex
```
**2、在main.js里进入并且使用vuex**

```js
import Vuex from 'vuex'
Vue.use(Vuex)
```
**3、在src文件目录下创建store目录，目录下创建store.js文件**
```js
import Vue from 'vue'
import Vuex from 'vuex'Vue.use(Vuex);
export default new Vuex.Store({  
  state: {     },  
  mutations: {    },  
  getters:{     },   
  actions: {}
})

```
**4、需要在main.js配置**
```js
import store from './store/store'
new Vue({  store,  render: h => h(App)}).$mount('#app');
```

**5、接下来分析vuex中各项模块的功能**

**（1）state**

vuex中的数据源，我们需要保存的数据就保存在这里，可以在页面通过 this.$store.state来获取我们定义的数据；

store.js

```js
export default new Vuex.Store({
  state: {    
    count: 0,    
    data:[],   
    num:[1,2,4]  
  }
  })
```

view.vue

```html
<template>
 <p>{{count}}</p>
 <p>{{num}}</p>
</template>
<script>
import { mapState,mapGetters,mapMutations } from 'vuex'//这里是使用了辅助函数，分别对应state、getters、mutations.
computed:{
  ...mapState(['num']) , //...是es6的拓展符，这样可以直接访问到num.        
  count(){return this.$store.state.count //也可以用这种方法        
},
}</script>

```

**(2) mutations**

如果需要修改state中的值唯一的方法就是提交mutation来修改.

store.js

```js
export default new Vuex.Store({
  mutations: {    
    increment: state => state.count++,    
    decrement: state => state.count--,    
    get: state => console.log(state.data),    
    ff(state, b) {      console.log(state.count+=b)    }  
  },
})
```

view.vue

```html
<template>
     <button @click="increment">+</button>     <button @click="decrement">-</button>     <button @click="get">get</button>     <button @click="ff">+10</button>
</template>
<script>
methods:{
        increment(){ this.$store.commit('increment')},        
        ff(){          this.$store.commit('ff',10) },        
        decrement(){this.$store.commit('decrement')},        
        get(){          this.$store.commit('get')}
}
</script>
```
**（3）getters**

就是从state中派生出状态，比如将state中的某个状态进行过滤然后获取新的状态

store.js

```js
export default new Vuex.Store({
getters:{    
  filter(state) { const a=state.num.length;
    for (let i = 0; i < a; i++){
      if (state.num[i] < 3){ console.log(state.num[i]) }     
     }    
    }  
  },
})
```

view.vue

```html
<template>
    <p @click="getter">getters</p>
</template>
<script>
methods:{
      getter(){        this.$store.getters.filter;      },
}
</script>
```
**(4) actions**

actions就是mutation的加强版，它可以通过commit mutations中的方法来改变状态，最重要的是它可以进行异步操作。

store.js

```js
export default new Vuex.Store({
 actions: {
   asyncInrement(context){
     return new Promise(resolve => {  setTimeout(() => { context.commit('increment');resolve(); }, 1000)
   });
  }
 }
})
```
view.vue

```html
<template>
     <button @click="action">+1</button>
</template>
<script>
methods:{
      action() {          this.$store.dispatch('asyncInrement').then(() => {          console.log(this.$store.state.count);      })},
}

</script>
```
**6、module模块**

项目比较复杂的时候，数据全部写在一个state ，将会使我们的文件显得太过于臃肿，而且不易维护，那怎么办呢？
vuex为我们提供了module这样一个模块的概念

store.js

```js
const moduleA = {
  state: { /*data**/ },
  mutations: { /**方法**/ },
  actions: { /**方法**/ },
  getters: { /**方法**/ }
}

const moduleB = {
  state: { /*data**/ },
  mutations: { /**方法**/ },
  actions: { /**方法**/ }
  getters: { /**方法**/ }
}


export default new Vuex.Store({
  modules: {
    a: moduleA,
    b: moduleB
  }
})

//在模块内部使用
state.count //这种使用方式和单个使用方式样，直接使用就行

//在组件中使用
store.state.a.count //先找到模块的名字，再去调用属性
store.state.b.count //先找到模块的名字，再去调用属性
```

view.vue
```html
<template>
    <p @click="get"></p>
</template>
<script>
    methods:{
    get(){
        this.$store.state.a.count
        }
}

</script>
```
## 教你用VS code 生成vue-cli代码片段

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190529171912826.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
可以自定义设置名字：name.json

```js
{
	"Print to console": {
		"prefix": "vue",
		"body": [
			"<template>",
			"<div class='$2'>$5</div>",
			"</template>",
			"",
			"<script>",
			"",
			"export default {",
			"name:'',",
			"components: {},",
			"data() {",
			"return {",
			"",
			"};",
			"},",
			"computed: {},",
			"watch: {},",
			"methods: {",
			"",
			"},",
			"//生命周期 - 创建完成（可以访问当前this实例）",
			"created() {",
			"",
			"},",
			"//生命周期 - 挂载完成（可以访问DOM元素）",
			"mounted() {",
			"",
			"},",
			"beforeCreate() {}, //生命周期 - 创建之前",
			"beforeMount() {}, //生命周期 - 挂载之前",
			"beforeUpdate() {}, //生命周期 - 更新之前",
			"updated() {}, //生命周期 - 更新之后",
			"beforeDestroy() {}, //生命周期 - 销毁之前",
			"destroyed() {}, //生命周期 - 销毁完成",
			"activated() {}, //如果页面有keep-alive缓存功能，这个函数会触发",
			"}",
			"</script>",
			"<style lang='scss' scoped>",
			"$4",
			"</style>"
		],
		"description": "Log output to console"
	}
}
```
## css圣杯布局与双飞翼布局

## 圣杯布局

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>圣杯布局</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        body {
            min-width: 600px;
        }

        header,
        footer {
            text-align: center;
            width: 100%;
            background-color: #bbbbbb;
        }

        .text {
            text-align: center;
            line-height: 200px;
            font-size: 40px;
            color: #fff;
        }

        .bd {
            overflow: hidden;
            padding: 0 200px 0 200px;
        }

        .main {
            float: left;
            width: 100%;
            height: 200px;
            background-color: #ddd;
        }

        .left {
            /* opacity: 0.5; */
            float: left;
            width: 200px;
            height: 200px;
            background-color: #da4242;
            /* 产生布局效果的属性 */
            margin-left: -100%;
            position: relative;
            left: -200px;
        }

        .right {
            /* opacity: 0.5; */
            float: left;
            width: 200px;
            height: 200px;
            background-color: #4ddef1;
            /* 产生布局效果的属性 */
            margin-left: -200px;
            position: relative;
            left: 200px;
        }
    </style>
</head>

<body>
    <header>圣杯布局</header>
    <div class="bd">
        <div class="main text">
            main
        </div>
        <div class="left text">
            left
        </div>
        <div class="right text">
            right
        </div>
    </div>
    <footer>footer</footer>
</body>

</html>
```

### 双飞翼布局

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>双飞翼布局</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        header,
        footer {
            text-align: center;
            width: 100%;
            background-color: #bbbbbb;
        }

        .text {
            text-align: center;
            line-height: 200px;
            font-size: 40px;
            color: #fff;
        }

        .bd {
            overflow: hidden;
        }

        .main {
            float: left;
            width: 100%;
            height: 200px;
            background-color: #ddd;
        }

        .main-content {
            margin: 0 200px;
        }

        .left {
            float: left;
            width: 200px;
            height: 200px;
            background-color: #da4242;
            /* 产生布局效果的属性 */
            margin-left: -100%;
        }

        .right {
            float: left;
            width: 200px;
            height: 200px;
            background-color: #4ddef1;
            /* 产生布局效果的属性 */
            margin-left: -200px;
        }
    </style>
</head>

<body>
    <header>双飞翼布局</header>
    <div class="bd">
        <div class="main text">
            <div class="main-content">main</div>
        </div>
        <div class="left text">
            left
        </div>
        <div class="right text">
            right
        </div>
    </div>
    <footer>footer</footer>
</body>

</html>
```
## js小效果之获取验证码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>验证码</title>
    <style>
    .get{
        cursor: pointer;
    }
    .reset{
        display: none;
    }
    .reset span{
        color:red;
    }
    </style>
</head>
<body>
    <input type="text"><button>确定</button>
    <p class="get">获取验证码</p>
    <p class="reset">重新获取验证码<span>10</span>s</p>
</body>
<script>
function $(el) {
    return document.querySelector(el);
}
let val="";
let timer=null;
function stop() {
    clearInterval(timer);
    timer=null;
}
$(".get").onclick=function(){
    this.style.display="none";
    $(".reset").style.display="block";
    var chars = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K',
    'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'];
    function generateMixed(n) {
    var res = "";
    for(var i = 0; i < n; i++) {
       var id=Math.ceil(Math.random() * 35);
       res +=chars[id];
       }
       return res;
    }
    var num1=generateMixed(4);
    val=num1;
    alert(num1);
    var i=10;
    timer=setInterval(() => {
        i--;
        $(".reset span").innerText=i;
        if(i===0){
            stop();
            $(".reset").style.display="none";
            $(".get").style.display="block";
        }
    }, 1000);
}
$("button").onclick=function(){
    console.log(val);
    if(val!=$("input").value){
        console.log("输入错误");
        $("input").value="";
        return;
    }
}
</script>
</html>
```
## 记住这几个git命令就够了

git clone:  下载初始化

git add:添加

git commit -m ‘ ’ :提交 带消息

git push：推送

git pull： 拉取

## 当你遇到Error: ER_TRUNCATED_WRONG_VALUE_FOR_FIELD: Incorrect string value:

```
Error: ER_TRUNCATED_WRONG_VALUE_FOR_FIELD: Incorrect string value: '\xE6\x88\x91\xE4\xBB\xAC...' for column 'content' at row 1
```
这种原因是字符集编码导致的。

**1、验证字符集**

首先进入mysql：

```
mysql  -u root -p
```
进入之后输入以下：

```
show variables like '%character%';
```
这里是输入命令之后的视图：
```
mysql> show variables like '%character%';
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8mb4                    |
| character_set_connection | utf8mb4                    |
| character_set_database   | latin1                     |
| character_set_filesystem | binary                     |
| character_set_results    | utf8mb4                    |
| character_set_server     | latin1                     |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
8 rows in set (0.01 sec)

```
你会看到| character_set_server     | latin1                     |
就是这个character_set_server等于latin1导致的错误，需要手动改文件

**2、进入my.cnf**

```
vim /etc/my.cnf
```
编辑my.cnf
在[mysqld]下面

```
character-set-client-handshake = FALSE
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci
init_connect='SET NAMES utf8mb4'

```

**3、重启mysql.**

```
service mysql restart
```

**4、再次登录mysql，查看字符集**

```
mysql> show variables like '%character%';
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8mb4                    |
| character_set_connection | utf8mb4                    |
| character_set_database   | utf8mb4                    |
| character_set_filesystem | binary                     |
| character_set_results    | utf8mb4                    |
| character_set_server     | utf8mb4                    |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
8 rows in set (0.01 sec)
```
出现以上视图你就成功一半了

5、**为什么成功一半呢?**

需要把已经建立好的数据库和表格全部重新建吧**

## js实现上传头像（看了你就懂，相信我）

**效果图：**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190523092218668.png)
**html:**
```html
    <div class="tx ovf">
        <div class="tit">头像</div>
        <div class="ovf tx-img"><img src="" alt="">
            <div class="upload-b"><span>修改头像</span><input type="file" class="upload1"></div>
        </div>
    </div>
```
**css:**

```css
	.ovf{overflow: hidden;}
    .tit { float: left; width: 50px; margin-top: 39px; font-size: 0.9vw; color: #999999; }
    .tx{ margin-top:44px; }
    .tx img{ width: 90px; height: 90px; border-radius:50%; margin-right:30px;border: 1px solid #fca89d; }
    .tx span{ border: solid 1px #fca89d; color: #fca89d; font-size: 16px; padding: 10px; cursor: pointer; }
    .upload1 { position: absolute; right:0; }
    .tx img{ float: left; }
    .tx input{ width: 86%; opacity: 0; }
    .upload-b { float: left; margin-top:36px; position: relative; }
```
**js：**

```js
$(".upload1").change(function(){
    	var file=this.files[0];
    	readFile(file);
    	});
    function readFile(file) {
        // 新建阅读器
        var reader = new FileReader();
        // 根据文件类型选择阅读方式
        switch (file.type){
        case 'image/jpg':
        case 'image/png':
        case 'image/jpeg':
        case 'image/gif':
        reader.readAsDataURL(file);
        break;
        }
        // 当文件阅读结束后执行的方法
        reader.addEventListener('load',function () {
        // 如果说让读取的文件显示的话 还是需要通过文件的类型创建不同的标签
        switch (file.type){
        case 'image/jpg':
        case 'image/png':
        case 'image/jpeg':
        case 'image/gif':
        console.log(reader.result);
        $(".tx-img img").attr("src",reader.result);
        break;
        }
        });
        }
```
## 原生js实现图片单张上传及批量上传

**效果图：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190523090622399.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>pc图片上传</title>
    <style>
    .up{ display: inline-block; vertical-align: middle; border:1px solid #eaeaea;box-sizing: border-box; text-align: left; margin-right: 20px;
    margin-bottom: 20px; width:240px; height: 240px; }
    .tips{color: #999999;text-align: center;position: absolute;bottom:0;left: 96px;}
    .Input{ position: relative; width: 240px; height: 240px; background: url(add.png)no-repeat center center; }//这里的图片背景源文件在下面。
    .on{ position: relative; display: inline-block; text-align: left; margin-right: 20px; margin-bottom: 20px; width: 240px; height: 240px; display: none; position: relative; overflow: hidden; line-height: 200px; }
    /*新增加的img*/
    .on img{ width: 100%; height: auto; position: absolute; left: 0; right: 0; top: 0; bottom: 0; margin:auto; }
    .on div{position: absolute; height: 40px;width: 100%;bottom: 12px;z-index: 10;text-align: center;}
    .on div p:nth-child(1){ float: left; width: 50%; line-height: 40px; font-size: 14px; cursor: pointer; color: #666666; background-color: #f4f4f4; }
    .on div p:nth-child(2){ cursor: pointer; float: left; width: 50%; font-size: 14px; color: #666666; line-height: 40px; background-color: #f8f8f8; }
    .up input{ width: 240px; height: 240px; opacity: 0; }
    .button{ margin-top: 30px; }
    /*批量上传*/
    .button .set{ display: inline-block; width: 216px; height: 36px; background:url(btn_upload_off.png); background-size: 100% 100%; }
    .set input{ width: 216px; height: 36px; opacity: 0; }
    .submit{width: 100px;  text-align: center; margin-top: 20px; border: 1px solid #333333; padding: 10px 0; border-radius: 4px;}
	</style>
</head>
<body>
    <section id="content">
        <ul class="baohan">
            <li class="up">
                <div class="Input">
                    <input type="file" name="" class="fileinput">
                    <p class="tips">添加图片</p>
                </div>
                <div class="on">
                    <div>
                        <p>排序</p>
                        <p class="del">删除</p>
                    </div>
                </div>
            </li>
            <li class="up">
                <div class="Input">
                    <input type="file" name="" class="fileinput" ">
                    <p class="tips">添加图片</p>
                </div>
                <div class="on">
                    <div>
                        <p>排序</p>
                        <p class="del">删除</p>
                    </div>
                </div>
            </li>
            <li class="up">
                <div class="Input">
                    <input type="file" name="" class="fileinput" ">
                    <p class="tips">添加图片</p>
                </div>
                <div class="on">
                    <div>
                        <p>排序</p>
                        <p class="del">删除</p>
                    </div>
                </div>
            </li>
            <div class="button">
                <div class="set"><input type="file" name="" multiple="multiple" id="piliang"></div>
            </div>
            <div class="submit">提交</div>
        </ul>
    </section>
</body>
<script src="https://unpkg.com/jquery@3.4.1/dist/jquery.js"></script>
<script>
$(document).ready(function(){
	$(".fileinput").change(function(){
		var file=this.files[0];
		readFile(file,$(this).parent().siblings(".on"));
	});
	$(".on").mouseover(function(){
		$(this).children("div").show();
	});
	$(".on").mouseout(function(){
		$(this).children("div").hide();
	});
	$(".del").click(function () {
          $(".on>div").hide();
          $(this).parent().parent().hide();
          $(this).parent().parent().siblings(".Input").show();
          $(this).parent().siblings("img").remove()
          $(".fileinput").val("");


    });
    var on =document.querySelector(".on");
//    需要把阅读的文件传进来file element是把读取到的内容放入的容器
    function readFile(file,element) {
//        新建阅读器
        var reader = new FileReader();
//        根据文件类型选择阅读方式
        switch (file.type){
            case 'image/jpg':
            case 'image/png':
            case 'image/jpeg':
            case 'image/gif':
                reader.readAsDataURL(file);
                break;
        }
//        当文件阅读结束后执行的方法
        reader.addEventListener('load',function () {
//            如果说让读取的文件显示的话 还是需要通过文件的类型创建不同的标签
            switch (file.type){
                case 'image/jpg':
                case 'image/png':
                case 'image/jpeg':
                case 'image/gif':

                    var img = document.createElement('img');
                    img.src = reader.result;
                    element.append(img);
                    element.siblings(".Input").hide();
                    element.show();
                    break;
            }
        });
    }
 // 批量上传
    var piliang = document.querySelector('#piliang');
    var on = $('.on');
    piliang.addEventListener('change',function () {
       for (var i = 0;i < this.files.length;i++){
           var file = this.files[i];
           on.eq(i).children(".cha").next().remove();
           readFile(file,on.eq(i));
       }

    });
//  
var on = $(".on");
$(".submit").click(function () {
  for (var i = 0; i < 10; i++) {
    console.log(on[i].childNodes.length);
    if (on[i].childNodes.length==6){
     alert("上传成功");
     return
    }else{
      alert("上传照片不足十张");
      $(".next").attr("href","javascript:void(0)");
      return;
    }

  }
});

});
</script>
</html>
```
**这是源文件背景：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190523090823361.png)
## js基础之数组方法

```js
var arr1=[1,2,3,4];
	var a1=arr1.pop();
	console.log(a1);//4
	console.log(arr1);// [1, 2, 3]
	/*
	pop() 方法将删除 arrayObject 的最后一个元素，把数组长度减 1，并且返回它删除的元素的值。如果数组已经为空，则 pop() 不改变数组，并返回 undefined 值。
	*/
	var arr2=[1,2,3,4];
	var a2=arr2.shift();
	console.log(a2);//1
	console.log(arr2)//2, 3, 4
	/*
	如果数组是空的，那么 shift() 方法将不进行任何操作，返回 undefined 值。请注意，该方法不创建新数组，而是直接修改原有的 arrayObject。
	*/
	var arr3=[1,2,3,4];
	var a3=arr3.splice(3,1);
	console.log(a3);//4
	console.log(arr3);//[1, 2, 3]
	// 该方法会改变原始数组。
	// splice(index,howmany,item1,.....,itemX)
	// index	必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。
	// howmany	必需。要删除的项目数量。如果设置为 0，则不会删除项目。
	// item1, ..., itemX	可选。向数组添加的新项目。
	var arr4=[1,2,3,4];
	var a4=arr4.slice(2,3);
	console.log(a4);//3
	console.log(arr4);//[1,2,3,4]
	// 该方法并不会修改数组，而是返回一个子数组
	// slice(start,end)
	// start	必需。规定从何处开始选取。如果是负数，那么它规定从数组尾部开始算起的位置。也就是说，-1 指最后一个元素，-2 指倒数第二个元素，以此类推。
	// end	可选。规定从何处结束选取。该参数是数组片断结束处的数组下标。如果没有指定该参数，那么切分的数组包含从 start 到数组结束的所有元素。如果这个参数是负数，那么它规定的是从数组尾部开始算起的元素。
	var arr5=[1,2,3,4];
	var a5=arr5.join();
	console.log(a5);
	// 将数组转化为字符串
	// 把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。
	// join(),括号里面为自定义分隔符，不填默认为逗号。这与toString()方法相同。
```
## 微信小程序之自定义底部导航栏


### 一、 在目录下创建文件如下图：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019051716324676.png)
**tabbar.js：**

```js
// pages/tabbar/tabbar.js
const app = getApp();
Component({
  /**
   * 组件的属性列表
   */
  properties: {
      tabbar: {
        type: Object,
        value: {
           "backgroundColor": "#ffffff",
           "color": "#333",
           "selectedColor": "#fca89d",
           "borderStyle": "white",
            "list": [{
                 "pagePath": "/pages/index/index",
                 "text": "首页",
                 "iconPath": "http://192.168.2.61/wap/rm/images/in.png",
                 "selectedIconPath": "http://192.168.2.61/wap/rm/images/ined.png"
               },
               {
                 "pagePath": "/pages/mry/mry",
                 "text": "美容院",
                 "iconPath": "http://192.168.2.61/wap/rm/images/mei.png",
                 "selectedIconPath": "http://192.168.2.61/wap/rm/images/meied.png"
               },
               {
                 "pagePath": "/pages/shop/shop",
                 "text": "商城",
                 "iconPath": "http://192.168.2.61/wap/rm/images/shop.png",
                 "selectedIconPath": "http://192.168.2.61/wap/rm/images/shoped.png"
               },
               {
                 "pagePath": "/pages/mine/mine",
                 "text": "我的",
                 "iconPath": "http://192.168.2.61/wap/rm/images/min.png",
                 "selectedIconPath": "http://192.168.2.61/wap/rm/images/mined.png"
               }
             ],

        }
      }
  },

  /**
   * 组件的初始数据
   */
  data: {

  },

  /**
   * 组件的方法列表
   */
  methods: {

  }
})

```
**tabbar.json:**

```js
{
  "component": true,
  "usingComponents": {

  }
}
```
**tabbar.wxml:**

```html
<!--pages/tabbar/tabbar.wxml-->
<view class="tabbar_box {{isIphoneX?'iphoneX-height':''}}" style="background-color:{{tabbar.backgroundColor}}">
    <block wx:for="{{tabbar.list}}" wx:key="{{item.pagePath}}">
        <navigator wx:if="{{item.isSpecial}}" class="tabbar_nav" hover-class="none" url="{{item.pagePath}}" style="color:{{tabbar.selectedColor}}" open-type="navigate">
            <view class='special-wrapper'>
                <image class="tabbar_icon" src="{{item.iconPath}}"></image>
            </view>
            <image class='special-text-wrapper'></image>
            <text class="txt">{{item.text}}</text>
        </navigator>
        <navigator wx:else class="tabbar_nav" hover-class="none" url="{{item.pagePath}}" style="color:{{item.selected ? tabbar.selectedColor : tabbar.color}}" open-type="switchTab">
            <image class="tabbar_icon" src="{{item.selected ? item.selectedIconPath : item.iconPath}}"></image>
            <text class="txt">{{item.text}}</text>
        </navigator>
    </block>
</view>

```
**tabbar.wxss:**

```css
/* pages/tabbar/tabbar.wxss */
.tabbar_box { display: flex; flex-direction: row; justify-content: space-around; position: fixed; bottom: 0; left: 0; z-index: 999; width: 100%; height: 98rpx; box-shadow: 0 0 2px rgba(0, 0, 0, 0.1); }
.tabbar_box.iphoneX-height { padding-bottom: 66rpx; }
.tabbar_nav { flex: 1; display: flex; flex-direction: column; justify-content: center; align-items: center; font-size: 20rpx; height: 100%; position: relative; }
.tabbar_icon { width: 40rpx; height: 40rpx; margin:7rpx 0; }
.special-wrapper .tabbar_icon { width: 84rpx; height: 84rpx; }
.special-text-wrapper { width: 45rpx; height: 45rpx; }
.txt{font-size: 26rpx;}
```

###  二、然后需要在以下全局文件做下修改

**app.js:**

```js
//app.js
App({
   onLaunch: function () {
     // 隐藏自带的tabbar
     wx.hideTabBar();
   },

       editTabbar: function () {
           let tabbar = this.globalData.tabBar;
           let currentPages = getCurrentPages();
           let _this = currentPages[currentPages.length - 1];
           let pagePath = _this.route;
           (pagePath.indexOf('/') != 0) && (pagePath = '/' + pagePath);
           for (let i in tabbar.list) {
             tabbar.list[i].selected = false;
             (tabbar.list[i].pagePath == pagePath) && (tabbar.list[i].selected = true);
           }
           _this.setData({
             tabbar: tabbar
           });
         },
         globalData: {
           systemInfo: null, //客户端设备信息
           userInfo: null,
           tabBar: {
             "backgroundColor": "#ffffff",
             "color": "#333",
             "selectedColor": "#fca89d",
             "borderStyle": "white",
             "list": [{
                 "pagePath": "/pages/index/index",
                 "text": "首页",
                 "iconPath": "http://192.168.2.61/wap/rm/images/in.png",
                 "selectedIconPath": "http://192.168.2.61/wap/rm/images/ined.png"
               },
               {
                 "pagePath": "/pages/mry/mry",
                 "text": "美容院",
                 "iconPath": "http://192.168.2.61/wap/rm/images/mei.png",
                 "selectedIconPath": "http://192.168.2.61/wap/rm/images/meied.png"
               },
               {
                 "pagePath": "/pages/shop/shop",
                 "text": "商城",
                 "iconPath": "http://192.168.2.61/wap/rm/images/shop.png",
                 "selectedIconPath": "http://192.168.2.61/wap/rm/images/shoped.png"
               },
               {
                 "pagePath": "/pages/mine/mine",
                 "text": "我的",
                 "iconPath": "http://192.168.2.61/wap/rm/images/min.png",
                 "selectedIconPath": "http://192.168.2.61/wap/rm/images/mined.png"
               }
             ],
           }
         }
})
```
**app.json:**

```js
 "tabBar": {
    "backgroundColor": "#ffffff",
    "color": "#333",
    "selectedColor": "#fca89d",
    "borderStyle": "white",
    "list": [
      {
        "pagePath": "pages/index/index"
      },
      {
        "pagePath": "pages/mry/mry"
      },
      {
        "pagePath": "pages/shop/shop"
      },
      {
        "pagePath": "pages/mine/mine"
      }
    ]
  }
```

### 三 、需要引入的tabbar,如index.wxml

**index.wxml:**

```html
<tabbar tabbar="{{tabbar}}"></tabbar>
```
**index.json:**

```js
{
    "usingComponents": {
      "tabbar": "/component/tabbar/tabbar"
    }
}
```
**index.js：**

```js
const app = getApp()；
Page({
  data: {
    tabbar: {},
    },
  onLoad: function () {
     app.editTabbar();
  }
    })
```


最后，
效果图：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190517164211228.png)

## pm2基本命令

```
$ pm2 logs
```
显示所有进程日志

```
$ pm2 stop all
```
停止所有进程

```
$ pm2 restart all
```

重启所有进程

```
$ pm2 reload all
```

 0秒停机重载进程 (用于 NETWORKED 进程)

```
$ pm2 stop 0
```
停止指定的进程

```
$ pm2 restart 0
```
 重启指定的进程

```
$ pm2 startup
```
产生 init 脚本 保持进程活着

```
$ pm2 web
```
运行健壮的 computer API endpoint

```
$ pm2 delete 0
```
杀死指定的进程

```
$ pm2 delete all
```
杀死全部进程

## nginx反向代理之端口配置
**cd /etc/nginx/**

**vim nginx.conf**
```
 server {
        listen       80 default_server;
        listen       [::]:80 default_server;
        server_name  域名;
        listen 443 ssl;
        root         /usr/share/nginx/html;
        ssl_certificate cert/1_www.maomin.club_bundle.crt;
        ssl_certificate_key cert/2_www.maomin.club.key;
        ssl_session_timeout 5m;
        # Load configuration files for the default server block.
        // include /etc/nginx/default.d/*.conf;
       location / {
                root /root/www/;
                index index.html index.htm;
        }
        location /chat/ {
        proxy_pass http://内网:3001/;
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
        location /upload/ {
        proxy_pass http://内网:8083/;
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
		error_page 404 /404.html;
            location = /40x.html {
        }

        error_page 500 502 503 504 /50x.html;
            location = /50x.html {
        }
        }

```
## nginx环境下配置https域名

拿到的证书分两个文件，一个是xxx.crt，一个是xxx.key，分别对应公钥和私钥。

1.假设我们的nginx安装目录是：/usr/local/nginx/，在目录下创建一个新目录，姑且命名为cert，把两个证书文件扔到此目录下。

2.编辑conf目录下的nginx.conf文件

3.如果只想让网站支持https访问，那么在server_name下面插入两行，添加两行内容：

```
listen 443;
ssl on;
```
4.如果想让网站兼容http和https访问，那么在server_name下面插入一行，添加一行内容：

```
listen 443 ssl
```
5.在root /home...（项目路径）下面再插入三行，添加内容：

```
ssl_certificate cert/xxx证书文件名1.crt;
ssl_certificate_key cert/xxx证书文件名2.key;
ssl_session_timeout 5m;
```
6.编辑完成后，保存退出，执行命令**nginx -t**，测试下我们修改后的配置文件语法是否正确，如果正确将会输出如下提示：

7.然后继续执行命令，**nginx -s reload**，重新加载配置文件。执行后，在浏览器中输入https的网址进行访问，如果地址栏边上有个小锁的标志，则证明升级成功，恭喜自己吧！
## vue基础之slot插槽

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>slot插槽</title>
</head>
<body>
    <div id="app">
        <my-component>
            <p>vue</p>
        </my-component>
        <my-component1>
            <p slot="p1">p1</p>
            <p slot="p2">p2</p>
        </my-component1>
    </div>
</body>
<script src="vue.js"></script>
<script>
//匿名插槽
    Vue.component("my-component",{
        template:"<div><slot></slot></div>"
    })
//具名插槽
    Vue.component("my-component1",{
        template:"<div><slot name='p1'></slot><slot name='p2'></slot></div>"
    })
    let vm = new Vue({
        el:"#app"
    })
</script>
</html>
```
## vue基础之组件同级传递

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>同级传递</title>
</head>
<body>
    <div id="app">
        <son1></son1>
        <son2></son2>
    </div>
</body>
<script src="./vue.js"></script>
<script>
    let nullVm=new Vue();
    var vm=new Vue({
        el:"#app",
        components:{
            "son1":{
                data(){
                    return {
                        mes:[1,2]
                    }
                },
                template:"<p @click='get'>send</p>",
                methods: {
                    get(){
                        nullVm.$emit("s1",this.mes)
                    }
                },
            },
            "son2":{
                template:"<p><p>",
                mounted(){
                    // let that=this;
                    nullVm.$on("s1",function (params) {
                        console.log(params)
                    })
                },
            }
        }
    })
    /*
一般同级传递都是指的是子组件与子组件之间的传递，因为父亲只有一个，那就是Vue实例。
如果想把son1的数据传给son2,
这里需要创建一个空实例Vue对象,然后利用事件方法$emit("自定义参数名"，"需要传递的数据")，
然后将空对象这个$emit(),整体写在函数内。这样他的数据就会传出去了。谁来接受呢？另一个同级组件需要用钩子函数mounted，这个钩子函数的意思是初始化页面完成后，再对html的dom节点进行一些需要的操作。
在mounted钩子函数内，用空实例Vue对象调用$on("上一个组件的自定义参数名"，"回调函数")。
    */
</script>
</html>
```
## vue基础之组件子传父

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>子传父</title>
</head>
<body>
    <div id="app">
        <son @get="getson"></son>
        <global @glo="getglo"></global>
    </div>
</body>
<script src="./vue.js"></script>
<script>
    Vue.component("global",{
        data:function (){
         return {
             mes:"我是全局组件"
         }
        },
        template: "<p @click='post'>全局组价</p>",
        methods:{
            // post:()=>{
            //     this.$emit("glo", this.mes)
            // },
            post: function(){
                console.log(this)
                this.$emit("glo", this.mes)
            }
        }
    })
    let vm=new Vue({
        el:"#app",
        data:{
            mes:""
        },
        components:{
            "son":{
                data:function(){
                    return {
                        mesSon:"I am son"
                    }
                },
                template:"<p @click='send'>局部组件</p>",
                methods: {
                    send:function(){
                        this.$emit("get",this.mesSon)
                    }
                },
            }
        },
        methods: {
            getson:function(data){
                console.log(data);
            },
            getglo:function(data){
                console.log(data);
            }

        },

    })
/*
首先子组件包括全局组件，局部组件。
如何将子组件的数据传递给父组件，这里用到子组件的一个事件属性。$emit
$emit 必须在事件中使用。有两个参数，第一个参数是事件名，第二个参数是子组件的数据，也就是需要传的数据。
然后，父组件怎样才能接收到子组件传过来的数据呢？需要在实例中绑定一个函数，这个函数的参数值就是子组件传过来的数据。
最后将子组件放到挂载点中。（这里要注意一点，在子组件中封装的事件函数为自定义事件，需要在子组件中绑定）


*/
</script>
</html>
```
## vue基础之组件父传子

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>父传子</title>
</head>
<body>
    <div id="app">
        <son :q1="d1" :q2="d2"></son>
        <global :box1="e"></global>
    </div>
</body>
<script src="./vue.js"></script>
<script>
    Vue.component("global",{
        props:['box1'],
        template:"<p>{{box1}}</p>"
    })
    let vm=new Vue({
        el:"#app",
        data:{
            d1:"1",
            d2:"2",
            e:"3"
        },
        components:{
            "son":{
                data:function(){
                    return {
                        mes:"hello"
                    }
                },
                props:['q1','q2'],
                template:"<p>{{q1}}</p>"
            }
        }
    })
    /*
    在子组件内定义一个属性props,他的值是一个数组。数组值随便定义
    是用来接受父组件的数据的，然后用：，也就是bind,绑定这个数组值=父组件需要传的数据
    */
</script>
</html>
```
## 微信小程序之支付
**wxml**

```html
<button bindtap='zfclick'>支付</button>
```
**index.js**

```js
// 第一次签名
// const stringA = "appid=****&attach=支付测试&body=紫薯OR红薯&mch_id=***&nonce_str=0VDpjwNyCHVHWVNe&notify_url=http://www.weixin.qq.com/wxpay/pay.php&openid=odtBs5SY7xRZ_vwDpw01anLnhg8o&out_trade_no=20190422352&spbill_create_ip=172.16.30.242&total_fee=1&trade_type=JSAPI";

// const stringSignTemp = stringA + "&key=***"; //注：key为商户平台设置的密钥key
// const sign = MD5(stringSignTemp).toUpperCase() = "106413A77D104A9A8F9E701D0AD50D1F"; //注：MD5签名方式
Page({

  /**
   * 页面的初始数据
   */
  data: {

  },
  zfclick: function () {
    // 请求支付
    wx.requestPayment(
      {
        'timeStamp': '1555912632.057',            //时间戳
        'nonceStr': 'zAyit9jhBk0ivgOX',          //随机串  
        'package': 'prepay_id=wx29082620893785cd4ba91ed32347390556',
        'signType': 'MD5',
        'paySign': '******',                     //签名
        'success': function (res) {
          console.log("支付成功");
          console.log(res);
        },
        'fail': function (res) {
          console.log(res);
        },
        'complete': function (res) { }
      })
  },

  /**
   * 生命周期函数--监听页面加载
   */
  onLoad: function (options) {
    // 获取登陆的openid
    wx.login({
      success: function (res) {
        console.log(res)
        if (res.code) {
          //发起网络请求
          wx.request({
            url: 'https://api.weixin.qq.com/sns/jscode2session',
            data: {
              appid: '***',
              secret: '10161c9b673dfd0f0425082cda890eca',
              js_code: res.code,
              grant_type: 'authorization_code'
            },
            success(v) {
              console.log(v)
            }
          })
        } else {
          console.log('登录失败！' + res.errMsg)
        }
      }
    });
    // 请求下单
    // wx.request({
    //   url: 'https://api.mch.weixin.qq.com/pay/unifiedorder',


    // })
  }
})



```
## js小效果之聊天界面检测输入状态

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>检测输入状态</title>
</head>
<body>
    <p style="display:none">正在输入</p>
    <input type="text">
</body>
<script>
var timer=null;
function $(el){ return document.querySelector(el) }
$("input").onkeyup=function(e){
    if(e.keyCode==8){
        $("p").style.display="none";
    }
    else{
        clearInterval(timer);
        $("p").style.display="block";
        setInterval(hide,5000);
      }
}
function hide(){
    $("p").style.display="none";
}
</script>
</html>
```
## 关于防抖与节流的应用方案

**防抖**：一段时间完成一个操作；

**节流**：定时完成操作。

### 应用场景：

**防抖**：

1、seach搜索联想，用户在不断输入输入值时，用防抖来节约请求资源。

2、windows触发resize的时候，不断的调整浏览器窗口大小会不断的触发这个事件，用防抖来让其只触发这一次。

3、防止重复提交。

**节流**：

1、鼠标不断点击触发，mousedown(单位时间内只触发一次)。

2、监听滚动事件，比如是否滑到底部自动加载更多，用throttle。


```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>防抖与节流</title>
        <style>
            .container{width: 400px;height: 200px;background: #ccc;text-align: center;font-size: 25px;line-height: 200px;}
        </style>
    </head>
    <body>
        <div class="container"></div>
    </body>
    <script>
    var count=1;
    var container=document.querySelector(".container");
    function getUser() {
        this.innerHTML= count++;
    }
    // container.onmousemove=demo(getUser,1000,true);//防抖
    container.onmousemove = time(getUser, 1000);//节流
// *****************************************************************
//防抖
    function demo(fn,wait,buber) {
        var timer;
        return function () {
            clearTimeout(timer);
            if(buber){
                var callNow=!timer;
                timer=window.setTimeout(function () {
                    timer=null
                },wait);
                if(callNow){
                    fn.apply(this);
                }
            }
            else{
                clearTimeout(timer);
                timer = window.setTimeout(fn.bind(this), wait);
            }
        }
    }
// 节流
    function time(fn,wait){
        var pp=0;//参照物
        return function () {
            var now= + new Date();//1970 1 1 到现在的毫秒数
            if(now-pp>wait){
                fn.apply(this);
                pp=now
            }
        }
    }
    </script>
    </html>
```
## node 操作mysql数据库


http://static.runoob.com/download/websites.sql
这是实例 websites.sql文件
### 1、安装node的mysql服务
```
npm install mysql
```
******************************
以下代码全是在test.js中，输入下面命令：

```
node test.js
```
*******************************************************
### 2、链接到sql

```js
var mysql      = require('mysql');
var connection = mysql.createConnection({
  host     : 'localhost',
  user     : 'root',
  password : '123456',
  database : 'test'
});

connection.connect();

connection.query('SELECT 1 + 1 AS solution', function (error, results, fields) {
  if (error) throw error;
  console.log('The solution is: ', results[0].solution);
});
```
### 3、查询数据

```js
var mysql  = require('mysql');  

var connection = mysql.createConnection({     
  host     : 'localhost',       
  user     : 'root',              
  password : '123456',       
  port: '3306',                   
  database: 'test'
});

connection.connect();

var  sql = 'SELECT * FROM websites';
//查
connection.query(sql,function (err, result) {
        if(err){
          console.log('[SELECT ERROR] - ',err.message);
          return;
        }

       console.log('--------------------------SELECT----------------------------');
       console.log(result);
       console.log('------------------------------------------------------------\n\n');  
});

connection.end();
```
### 4、插入数据

```js
var mysql  = require('mysql');  

var connection = mysql.createConnection({     
  host     : 'localhost',       
  user     : 'root',              
  password : '123456',       
  port: '3306',                   
  database: 'test'
});

connection.connect();

var  addSql = 'INSERT INTO websites(Id,name,url,alexa,country) VALUES(0,?,?,?,?)';
var  addSqlParams = ['菜鸟工具', 'https://c.runoob.com','23453', 'CN'];
//增
connection.query(addSql,addSqlParams,function (err, result) {
        if(err){
         console.log('[INSERT ERROR] - ',err.message);
         return;
        }        

       console.log('--------------------------INSERT----------------------------');
       //console.log('INSERT ID:',result.insertId);        
       console.log('INSERT ID:',result);        
       console.log('-----------------------------------------------------------------\n\n');  
});

connection.end();
```
### 5、更新数据

```js
var mysql  = require('mysql');  

var connection = mysql.createConnection({     
  host     : 'localhost',       
  user     : 'root',              
  password : '123456',       
  port: '3306',                   
  database: 'test'
});

connection.connect();

var modSql = 'UPDATE websites SET name = ?,url = ? WHERE Id = ?';
var modSqlParams = ['菜鸟移动站', 'https://m.runoob.com',6];
//改
connection.query(modSql,modSqlParams,function (err, result) {
   if(err){
         console.log('[UPDATE ERROR] - ',err.message);
         return;
   }        
  console.log('--------------------------UPDATE----------------------------');
  console.log('UPDATE affectedRows',result.affectedRows);
  console.log('-----------------------------------------------------------------\n\n');
});

connection.end();
```
### 6、删除数据

```js
var mysql  = require('mysql');  

var connection = mysql.createConnection({     
  host     : 'localhost',       
  user     : 'root',              
  password : '123456',       
  port: '3306',                   
  database: 'test'
});

connection.connect();

var delSql = 'DELETE FROM websites where id=6';
//删
connection.query(delSql,function (err, result) {
        if(err){
          console.log('[DELETE ERROR] - ',err.message);
          return;
        }        

       console.log('--------------------------DELETE----------------------------');
       console.log('DELETE affectedRows',result.affectedRows);
       console.log('-----------------------------------------------------------------\n\n');  
});

connection.end();
```
## 允许远程链接mysql，开放3306端口

### 1、云服务器下安全组，开放3306端口。

去你自己的服务器下的安全组添加允许3306端口。
### 2、配置mysql

首先为了保险起见。

请先检查是否开启了3306端口，下图是已经开启了。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190416220616390.png)

（1）如果开启了，可以直接跳到第二步。
```
vi /etc/mysql/mysql.conf.d/mysqld.cnf
```
将bind-address = 127.0.0.1注销​

（2）依次完成，123456是你自己的密码。

```
mysql -u root -p
```

```
 grant all privileges on *.* to 'root'@'%' identified by '123456';
```

```
flush privileges;​
```
## 云服务器linux系统安装mysql数据库

CentOS7默认数据库是mariadb,配置等用着不习惯,因此决定改成mysql,但是CentOS7的yum源中默认好像是没有mysql的。为了解决这个问题，我们要先下载mysql的repo源。

### 1.下载mysql的repo源

```
wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
```

### 2.安装mysql-community-release-el7-5.noarch.rpm包

```
sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
```

### 3.安装mysql

```
sudo yum install mysql-server
```

根据提示安装就可以了,不过安装完成后没有密码,需要重置密码

### 4.重置mysql密码

```
mysql -u root
```

登录时有可能报这样的错：ERROR 2002 (HY000): Can‘t connect to local MySQL server through socket ‘/var/lib/mysql/mysql.sock‘ ：
使用下面的命令：
```
sudo chown -R root:root /var/lib/mysql
```

### 5、重启mysql服务

```
service mysqld restart
```

### 6、接下来登录重置密码

```
	mysql -u root  //直接回车进入mysql控制台
mysql > use mysql;
mysql > update user set password=password('123456') where user='root';
mysql > exit;
```
## 本地安装MySql压缩包


https://dev.mysql.com/downloads/file/?id=484900
这里我们需要下载Mysql的社区版，这才是我们要用的。![在这里插入图片描述](https://img-blog.csdnimg.cn/20190416212918148.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
下载完成后，解压文件夹。

### 1、配置环境变量
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019041621340272.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
点击环境变量。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190416213425912.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
在path字段后新建解压后的路径，确定就OK了。
### 2、在安装根目录自动生成data文件夹
进入安装根目录下的bin目录下，打开命令行工具，执行命令：
```
mysqld --initialize-insecure --user=mysql
```
这时在根目录下生成data文件夹。
### 3、安装myaql
依旧是在bin文件目录下使用命令：

```
mysqld -install
```
下载安装成功后会有提示。

### 4、启动mysql服务

```
mysql -u root -p
```

这时默认是没有密码的，直接回车。
### 5、设置密码
分别依次输入以下命令：
```
ALTER USER 'root'@'localhost' IDENTIFIED BY 'password' PASSWORD EXPIRE NEVER;
```

```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';`
```

```
FLUSH PRIVILEGES;
```

### 6、退出

```
quit
```
## 教你如何用网页开发桌面应用

这里我们需要用的nw.js
https://nwjs.io/
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190415134618416.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
最好下载sdk版本。
下载完之后，解压打开
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190415134757632.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
图中的app文件夹是我自己创建的，你也需要自己创建一个，里面放你项目文件，另外创建一个
package.json文件
###################################################################
name：这个app的名称，可以随便取一个~
main：代表app的入口文件，我们这里用的是index.html，就是当app启动的时候第一个页面是什么。
version：版本号，一般于后续版本升级使用。
window：对窗口进行设置。
height：高度，单位像素。
width：宽度，单位像素。
show：当程序一点击运行的时候是否直接把窗口显示出来。
title：窗口标题，当入口页面的title标签为空的时候就使用这个属性来当做窗口的标题。
toolbar：是否启用工具条。
frame：是否使用边框，也就是含有最小化，关闭等按钮的边框。
resizable：是否可以调整窗口大小。
icon：窗口的图标，也是在快速启动栏显示的图标。
transparent：窗口背景是否透明。
#############################################################################
package.json
{
        "name":  "first  app",
        "main":  "index.html",
        "version":  "1.0",
        "window":  {
                "height":  300,
                "width":  360,
                "show":  true,
                "title":  "first  app",
                "toolbar":  true,
                "frame":  true,
                "resizable":false,
                "icon":  "./icon.png",
                "transparent":false
        }
}


然后将这些项目文件压缩成app.zip的压缩文件，将其更改为app.nw文件。将app.nw从app中粘贴到根目录中，
然后 打开命令行工具
例：
copy /b "E:\myweb\maomin\nwjs\nw.exe"+"E:\myweb\maomin\nwjs\app.nw"   "E:\myweb\maomin\nwjs\app.exe"

这里只是一个例子，按自己的存放的路径来。

合并完成后会在根目录看见一个名叫app.exe的文件。

接着你需要下载一个名叫Enigma Virtual Box的软件。
https://enigmaprotector.com/en/aboutvb.html
打开它，选中app.exe
然后将你刚才下好的nw.js里原始文件（除去你自己生成和创建的文件）。拖到下面的大方框中，Add,点击process.
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190415135729271.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)

## 微信小程序支付

```html
<view class="container">
    <input type="text" bindinput="getOrderCode" style="border:1px solid #ccc;"  />
    <button bindtap="pay">立即支付</button>
</view>
```

```js
Page({
  data: {
    txtOrderCode: ''
  },
  pay: function () {
    var ordercode = this.data.txtOrderCode;
    wx.login({
      success: function (res) {
        if (res.code) {
          wx.request({
            url: 'https://www.yourdomain.com/pay',
            data: {
              code: res.code,//要去换取openid的登录凭证
              ordercode: ordercode
            },
            method: 'GET',
            success: function (res) {
              console.log(res.data)
              wx.requestPayment({
                timeStamp: res.data.timeStamp,
                nonceStr: res.data.nonceStr,
                package: res.data.package,
                signType: 'MD5',
                paySign: res.data.paySign,
                success: function (res) {
                  // success
                  console.log(res);
                },
                fail: function (res) {
                  // fail
                  console.log(res);
                },
                complete: function (res) {
                  // complete
                  console.log(res);
                }
              })
            }
          })
        } else {
          console.log('获取用户登录态失败！' + res.errMsg)
        }
      }
    });
  },
  getOrderCode: function (event) {
    this.setData({
      txtOrderCode: event.detail.value
    });
  }
})
```
## 获取微信小程序code

```html
<button bindtap='g'>点击</button>
```

```js
//index.js
//获取应用实例
const app = getApp()

Page({
  // 登录
  g:()=>{
    wx.login({
      success: res => {
        // ------ 获取凭证 ------
        var code = res.code;
        if (code) {
          console.log('获取用户登录凭证：' + code);
          // ------ 发送凭证 ------
          wx.request({
            url: 'https://api.weixin.qq.com/sns/jscode2session',
            data: { code: code },
            method: 'POST',
            header: {
              'content-type': 'application/json'
            },
            success: function (res) {
              if (res.statusCode == 200) {
                console.log("获取到的openid为：" + res.data)
                // that.globalData.openid = res.data
                wx.setStorageSync('openid', res.data)
              } else {
                console.log(res.errMsg)
              }
            },
          })
        } else {
          console.log('获取用户登录失败：' + res.errMsg);
        }
      }
    })
  }


})
```

## 教你如何用网页开发APP


用到的工具：**HBuilderX app开发版**

### 1.首先你得网站必须是上线的，然后明确这一点后，点击打开HBuilderX。在文件里找到新建项目，选择wap2App,将下面信息填写完整，然后创建。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190415133804469.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)

### 2.默认打开如下界面：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190415134126942.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)

### 按着箭头的方向一直填写下去,然后，点击云打包

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019041513425715.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190415134329975.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)

 **打包之后，下方会出现下载链接，只能下5次。这样就下好APP了。**





## 教你如何在云服务器上安装并配置web服务器（这里以nginx服务器为例，操作系统linux）

**这里以git bash 工具为例，当然你可以直接用puTTY或者Xshell链接到服务器，用FileZilla 上传文件。**


### **一、连接服务器**

```
ssh  root@你的远程ip地址。
```


### 二、查看版本

```
uname -a
```
### 三、安装nginx(1) ，这一步可以直接跳过，现在nginx可以直接yum install nginx安装，如果这样安装不了，就得先进行这一步
```
yum install epel-release
```
### 四、安装nginx(2)

```
yum install nginx
```
### 五、检查是否安装成功

```
nginx -V
```


### 六、配置web服务器
```
1.进入根目录，输入cd  /etc/nginx/
2.输入 ls，查看文件
3.输入nginx -t ，找到文件
4.vim nginx.conf，打开文件
5.如果你的主机上没有vim,可以输入命令yum  install  vim
```

#### （1）.更改参数（这里最关键）

1.user nginx 改为 user root
2.找到路径并改为以下格式 （这里根目录/root/www/文件夹需要你自己创建，我推荐用FileZilla链接服务器自己在root下创建就可以了，当然你可以不用取名www。）
```
http > server > location / {
	root /root/www/;
	index index.html index.htm;
}
```


（你可以用下面这些命令更改参数）
```
:set nu 视图模式
i 编辑模式
esc 退出编辑模式
:wq 保存退出
```

#### （2）进入 nginx.conf

```
vim nginx.conf
```



#### （3）查看是否存在该文件夹

```
cd /root/www/
pwd
```


***********************

#### （4）上传网站到服务器（同样我推荐这里用FileZilla链接服务器，自己在www文件夹下,创建一个`index.html`就可以了，下面是单纯在`git bash`命令行下创建的，如果你不怕麻烦的话，可以用下面的方法）

提供scp工具
```
yum install openssh-client
```
```
logout
```
退出服务器

```
scp -r 你的本地项目路径 root@你的服务器ip:/root/www/
```

上传文件到服务器（请在你的本地项目文件目录内打开git bash）

ssh  root@你的远程ip地址。
远程连接到服务器

cd /root/www/

ls查看是否存入文件

#### （5）开启nginx 服务

开启nginx服务

```
ps -ef | grep nginx
```

停止nginx 服务

```
nginx -s stop
```

查看进程
```
nginx -t
```

查看文件

```
cat /etc/nginx/nginx.conf
```

重新加载nginx

```
nginx -s reload
```
## 教你如何上线web项目，简单易学~

**1**、![在这里插入图片描述](https://img-blog.csdnimg.cn/20190402103950891.png)
可以选择阿里云、腾讯云提供商。

**2**、把项目上传到服务器
需要用到ftp软件，

**3**、需要用到xshell链接服务器，进行node等环境安装（全是在xshell内操作，以Linux为例）
```
yum install epel-release
yum install npm nodejs
node -v
```

**4**、接下来可以在xshell内vim命令行操作（以Linux为例）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190402110531342.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)

**5**、如果你觉得每次输命令node app.js很麻烦：

```
npm install -g pm2
pm2 start app.js
```

(网上也有很多命令)
## 截取指定字符前后字符串

```html
<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <title>分割字符串</title>
</head>
<body>
        <input type="text" class="int">
    　　<button onclick="getStr()">截取</button>
</body>
<script type="text/javascript">
    var int=document.querySelector('.int');
    function getStr() {
        var string=int.value;
        if(string.indexOf("省")>-1){
        var str="省";
        var str_before = string.split(str)[0];
        var str_after = string.split(str)[1];
        console.log('前：' + str_before + ' - 后：' + str_after);
        }
        else if(string.indexOf("自治区")>-1){
        var str1="自治区";
        var str_before = string.split(str1)[0];
        var str_after = string.split(str1)[1];
        console.log('前：' + str_before + ' - 后：' + str_after);
        }
    }
</script>
</html>
```
## this秒懂版

```js
// this指向
// 1.指向全局变量window
var a = 1;

function func() {
    var a = 2;
    console.log(this.a);
}
func(); //2
// 2.指向调用它的对象(funx()中的this只对直属上司（直接调用者obj）负责，不管有多少个。)
var b = 3;

function funx() {
    console.log(this.b);
}
var obj = {
    b: 4,
    funx
}
obj.funx(); //4

var aa = 15

function test() {
    console.log(this.aa)
}
var obj = {
    aa: 2,
    test
}
var obj0 = {
    aa: 3,
    obj
}
obj0.obj.test()
// 3.可以将其传给一个变量，并且一样调用它
var d = 1

function test() {
    console.log(this.d)
}
var obj = {
    d: 2,
    test
}
var testCopy = obj.test
testCopy();
// 4.call(),命令指向谁
var e = 7;

function test1() {
    console.log(this.e)
}
var obj = {
    e: 8,
    test1
}
var testCopy = obj.test1
testCopy.call(obj);
// 5.指向构造函数实例化对象
var e = 9;

function Fu(e) {
    this.e = e
}
var rr = new Fu(10);
console.log(rr.e);
// 6.箭头函数中的this在函数定义的时候就已经确定，它this指向的是它的外层作用域this的指向。
var u = 11;
var test = () => {
    console.log(this.u);
}
var obj = {
    u: 18,
    test
}
obj.test();
```
## JS获取ip地址

```
<script src="http://pv.sohu.com/cityjson?ie=utf-8"></script>
<script> console.log(returnCitySN["cip"]+','+returnCitySN["cname"]) </script>
```
## 前端几个实用的小工具，解压就能使用~

链接: https://pan.baidu.com/s/1bpitVMtfmJ8AxSKDWVX1Bw

提取码: z9kx

欢迎下载哦~

有疑问可以加我QQ:815682884

## 靠谱的webstorm GIT操作

**第一步：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311105230129.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
**第二步：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311105257819.png)
**第三步：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311105316616.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
**第四步：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311105334835.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
**第五步：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311105351278.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
**第六步：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311105603109.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
**第七步：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311105409402.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
**第八步：**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311105426570.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MDQ1NjQ1,size_16,color_FFFFFF,t_70)
第九步：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311105450927.png)
好了，去git库看看你新上传的文件吧！！！

## webpack编译配置（一）



**1.创建一个空文件夹。**

**2.命令行：**

```
npm init(回车)
npm install --save-dev webpack（创建库）
```

**3.创建**

一个index.html文件（文件中需要引入处理后的js文件[假设bundle.js]）、main.js(需要被处理的js文件)、

webpack.config.js文件（配置文件）{
module.exports = {
    entry: './main.js',
    output: {
        filename: 'bundle.js'
	//这里的bundle.js默认放在dist文件里
    }
};

}

配置文件中需要添加很多模块（这里就不列举了。官网文档中有）

**4.命令行：webpack**

(执行)

```
npm init

cnpm i -D webpack

|-- index.html
|-- main.js
|-- show.js
|-- webpack.config.js


cnpm i -D style-loader css-loader

cnpm i -D webpack-dev-server
cnpm i -D webpack-cli

webpack-dev-server
webpack-dev-server --open


"scripts": {
    "dev": "webpack-dev-server --open",
    "build": "webpack -p"
  }
```
## less之考拉

先创建一个less文件，拖入考拉，即可自动编译。

http://koala-app.com/index-zh.html

这是考拉的网址。

http://lesscss.cn/

这是less学习的网址。
