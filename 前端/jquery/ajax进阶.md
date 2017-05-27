$
.ajax()

$.ajax()是所有ajax方法中最底层的方法,所有其他方法都是基于$.ajax()方法的封装。这个方法
只有一个参数,传递一个对象。

|参数|类型|说明|
|---|---|---|
|url|String|发送请求的地址|
|type|String|请求方式:POST或GET,默认为GET|
|Object|String|发送到服务器的对象|
|dataType |String| 返回数据类型,比如html,xml,json等|
|success|Function| 发送请求前可修改XML HttpRequest对象的函数|
data

>注意:对于data属性,如果是GET模式,可以使用之前所说的三种形式,如果是POST可以使用之前的两种形式。



$.ajax()
$.ajax()是所有ajax方法中最底层的方法,所有其他方法都是基于$.ajax()方法的封装。这个方法
只有一个参数,传递一个对象。

|参数|类型|说明|
|---|---|---|
|url|String|发送请求的地址|
|type|String|请求方式:POST或GET,默认为GET|
|Object|String| 发送到服务器的对象|
|dataType| String| 返回数据类型,比如html,xml,json等|
|success| Function |发送请求前可修改XML HttpRequest对象的函数|


jQuery - AJAX 表单序列化
表单序列化
使用表单序列化方法serialize(),会智能的获取指定表单内的所有元素,这样,在面对
大量表单元素时,会把表单元素内容序列化为字符串,然后再使用Ajax请求
```javascript
$.ajax({
'url':'demo.php',
'type':'POST',
'data':$('form').serialize(),
'success':function(response,status,xhr){
$('div').html(response);
}
//对于单选框或复选框 自动对单选框进行编码
$('div').html($('radio').serialize());
//对单选框或复选框进行解码
$('div').html(decodeURLComponent($('radio').serialize()));
JSON数据存数
var json = $('radio').serializeArray();
$('div').html(json[0].name + json[0].value);
```


jQuery - AJAX load() 方法
. jQuery load() 方法。
. jQuery对Ajax做了大量封装,我们使用起来比较方便,不需要去考虑浏览器的兼容性。对于封装的
方式,jQuery采用了三层封装:最底层的封装方法为:$.ajax(),而通过这层封装了第二层有三种方法:load()、$.get()
和$.post(),最高层是$.getScript()和$.getJSON()方法
load() 方法从服务器加载数据,并把返回的数据放入被选元素中。
语法

```javascript
$(selector).load(URL,data,callback);
```
必需的 URL 参数规定您希望加载的 URL。
可选的 data 参数规定与请求一同发送的查询字符串键/值对集合。
可选的 callback 参数是 load() 方法完成后所执行的函数名称。
例子:把示例文件 "demo_test.txt" 的内容加载到指定
的
<div> 元素中:
示例
示例文件("demo_test.txt")的内容:
```javascript
$("#div1").load("demo_test.txt");
<h2>jQuery and AJAX is FUN!!!</h2>
<p id="p1">This is some text in a paragraph.</p>
```