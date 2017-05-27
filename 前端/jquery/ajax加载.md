.
jQuery load() 方法。
. jQuery对Ajax做了大量封装,我们使用起来比较方便,不需要去考虑浏览器的兼容性。对于封装的
方式,jQuery采用了三层封装:最底层的封装方法为:$.ajax(),而通过这层封装了第二层有三种方法:load()、$.get()
和$.post(),最高层是$.getScript()和$.getJSON()方法
. load() 方法从服务器加载数据,并把返回的数据放入被选元素中。

```javascript
$(selector).load(URL,data,callback);
```
必需的 URL 参数规定您希望加载的 URL。
可选的 data 参数规定与请求一同发送的查询字符串键/值对集合。
可选的 callback 参数是 load() 方法完成后所执行的函数名称。
例子:把示例文件 "demo_test.txt" 的内容加载到指定
的
```javascript
<div> 元素中:
```
示例
示例文件("demo_test.txt")的内容:
```html
$("#div1").load("demo_test.txt");
<h2>jQuery and AJAX is FUN!!!</h2>
<p id="p1">This is some text in a paragraph.</p>
```