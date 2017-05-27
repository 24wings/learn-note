.
jQuery get() 和 post() 方法用于通过 HTTP GET 或 POST 请求从服务器请数据。

#### HTTP 请求:GET vs POST

----GET - 从指定的资源请求数据
----POST - 向指定的资源提交要处理的数据

```javascript
//GET方式接收的PHP
$('div').load('demo.php?url=wanviv');
//传递data则为POST方式
$('div').load('demo.php,{“url”:”wanviv”});
```
>(GET 基本上用于从服务器获得(取回)数据。注释:GET 方法可能返回缓存数据。
POST 也可用于从服务器获取数据。不过,POST 方法不会缓存数据,并且常用于
连同请求一起发送数据。)



. $.post() 方法通过 HTTP POST 请求从服务器上请求数据。
. : jQuery post() (URL,data,callback);
回调函数: function(response,status,xhr){}
属性名 说明
responseText 作为响应主体被返回的文本
responseXML 如果响应主体是text/xml,则返回包含响应数
据的XML DOM文档
status 响应的HTTP状态
statusText HTTP状态的说明
如果成功返回数据,那么xhr对象的statusText属性则返回“OK”字符串,除了OK
的状态字符,statusText还提供了一系列其他的值,如下:


####Post请求
方法通过 HTTP POST 请求从服务器上请求数据。
$.post()
jQuery post() (URL,data,callback);
回调函数: function(response,status,xhr){}

|属性|含义|
|---|---|
|responseText| 作为响应主体被返回的文本|
|responseXML| 如果响应主体是text/xml,则返回包含响应数据的XML DOM文档|
|status| 响应的HTTP状态|
|statusText |HTTP状态的说明|

>如果成功返回数据,那么xhr对象的statusText属性则返回“OK”字符串,除了OK
的状态字符,statusText还提供了一系列其他的值,如下:

|HTTP状态码| 说明|
|---|---|
|200:OK |服务器成功返回了页面|
|400:Bad Request| 语法错误导致服务器不识别|
|401:Unauthorized| 请求需要用户验证|
|404:Not found |指定的URL在服务器上找不到|
|500:Internet Server Error| 服务器遇到意外错误,无法完成请求|
|503:ServiceUnavailable| 由于服务器过载或维护导致无法完成请求|



####Get与Post方法的区别

jQuery - AJAX get() 和 post() 方法
* load()方法是局部方法,因为它需要一个包含元素的jQuery对象作为前缀,而$.get()和
$.post是全局方法,无需指定某个元素,通过回调函数返回结果。
* 对于用途而言,load()适合做静态文件的异步获取,而对于需要传递参数到服务器页
面$.get()和$.post()更加适合。
$.get()方法有4个参数,前面三个参数和load()一样,多了一个第四参数type,即服务器
* 返回的内容格式:包含xml,html,script,json和text.第一个参数为必选参数,其他为可选参数。


下面的例子使用 $.get() 方法从服务器上的一个文件中取回数据:
示例文件("demo.php")的内容:

```html
<h2>jQuery and AJAX is FUN!!!</h2>
<p id="p1">This is some text in a paragraph.</p>
$("button").click(function(){
$.get("demo_test.php",function(data,s
tatus){
alert("Data: " + data + "\nStatus: " +
status);
});
});
```


#####post请求
$.post() 方法通过 HTTP POST 请求从服务器上请求数据。
. 语法:
$.post(URL,data,callback);
必需的 URL 参数规定您希望请求的 URL。
可选的 data 参数规定连同请求发送的数据。
可选的 callback 参数是请求成功后所执行的函数名。
下面的例子使用 $.post() 连同请求一起发送数据:
示例文件("demo.php")的内容:
```html
<h2>jQuery and AJAX is FUN!!!</h2>
<p id="p1">This is some text in a paragraph.</p>
```

```javascript
$("button").click(function(){
$.post("demo_test_post.php",
{
name:"Donald Duck",
city:"Duckburg"
},
function(data,status){
alert("Data: " + data + "\nStatus: "
+ status);
});
});
```
|方法|说明|
|---|---|
|$.getJSON()| 返回JSON数据|
|$.getScript()|加载Script文件|

.语法
```javascript
//获取JSON数据
$.getJSON(“test.json”,function(response,status,xhr){
alert(response[0]);
});
```
```javascript
//加载script文件
$.getJScript(“test.js”);
});
```