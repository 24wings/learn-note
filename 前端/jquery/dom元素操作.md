#
#Unit02　
本章节主要内容Dom操作事件
基础的Dom css操作


#
## 基础DOM和CSS操作

>在javaScript中,DOM不但内容庞大繁杂,而且我们开发的过程中需要考虑更多的兼
容性,扩展性。在jQuery中,已经将最常用的DOM操作方法进行了有效封装,并且
不需要考虑浏览器的兼容性。


|方法 |说明|
|---|---|
|html()| 获取元素中HTML内容|
|html(value)| 设置元素中HTML内容|
|text()| 获取元素中文本内容|
|text(value) |设置元素中文本内容|
|val()| 获取表单中的文本内容|
|val(value)| 获取表单中的文本内容|




元素属性操作

|方法| 说明|
|---|---|
|attr(key) |获取某个元素key属性的属性值|
|attr(key,value) |设置某个元素key属性的属性值|
|attr({key1:value,key2:value}) |设置某个元素多个key属性的值|
|attr(key,function(index,value){}) |设置某个元素key通过fn来设置|
|removeAttr()| 删除某个元素的属性|


元素样式操作

|方法| 说明|
|---|---|
|css(name)| 获取某个元素行内的CSS样式|
|css(name,value) |设置某个元素行内的CSS样式|
|css(name,function(index,value))| 设置某个元素行内的CSS样式|
|css({name1:value,name2:value})| 设置某个元素行内多个CSS样式|
|addClass(class)| 给某个元素添加一个CSS类|
|addClass(class1 class2 class3)| 给某个元素添加多个CSS类|
|removeClass(class) |删除某个元素的一个CSS类|
|removeClass(class1 class2 class3) 删除某个元素的多个CSS类|
|toggleClass(class)| 来回切换默认样式和指定样式|
|toggleClass(class,switch)| 来回切换样式的时候设置切换频率|
|toggleClass(functon(){})| 通过匿名函数设置切换的规则|
|toggleClass(function(){},switch)| 匿名函数切换时也可以设置频率|
|hasClass() |样式选择器|


内外边距和边框尺寸方法

|方法|说明|
|---|---|
|innerWidth()|获取元素宽度,包含内边距padding|
|innerHeight()|获取元素高度,包含内边距padding|
|outerWidth()|获取元素宽度,包含边框border和内边距padding|
|outerHeight()|获取元素高度,包含边框border和内边距padding|
|outerWidth(true)|获取元素宽度,包含边框border和内边距和外边距|
|outerHeight(true) |获取元素高度,包含边框border和内边距和外边距|



内部插入节点方法

|方法|说明|
|---|---|
|append(content)|向指定元素内部后面插入节点content|
|append(function(index,html){})| 使用匿名函数向指定元素后面插入节点|
|appendTo(content)| 将指定元素移入到指定元素content内部后面|
|prepend(content)| 向指定元素content内部的前面插入节点|
|prepend(function(index,html){})| 使用匿名函数向指定元素内部的前面插入节点|
|prepentTo(content)| 将指定元素移入到指定元素content内部前面|


外部插入节点方法

|方法|说明|
|---|---|
|after(content)|向指定元素外部后面插入节点content|
|after(function(index,html){ })|使用匿名函数向指定元素外部后面插入节点
|before(content)|向指定元素外部前面插入节点content
|before(function(index,html){})| 使用匿名函数向指定元素外部前面插入节点|
|insertAfter(content)|将指定元素移入到指定元素content外部后面|
|insertBefore(content)|将指定元素移入到指定元素content外部前面



包裹节点

|方法|说明|
|---|---|
|wrap(html) |向指定元素包裹一层html节点|
|wrap(Element)| 向指定元素包裹一层原生的DOM节点|
|wrap(function(index,html){})| 用匿名函数向指定元素包裹一层自定义内容|
|unwrap() |移除一层指定元素包裹的内容|
|wrapAll(html) |用html将所有元素包裹到一起|
|wrapAll(Element) |用DOM对象将所有元素包裹到一起|
|wrapInner(html) |向指定元素的子元素包裹|
|wrapInner(Element)| 向指定元素的子元素包裹|
|wrapInner(function(){})| 向指定元素的子元素包裹|

