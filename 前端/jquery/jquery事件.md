#
##Jquery事件

>在JavaScript课程学习中,我们掌握了很多使用事件,常用的
事件有click、dblclick、mousedown、mouseup、mousemove、
mouseover、mouseout、change、submit、keydown等
事件处理程序指的是当 HTML 中发生某些事件时所调用的方法。术语
由事件“触发”(或“激发”)经常会被使用。 )

|方法 |说明|
|---|---|
|bind() |绑定一个或多个事件|
|unbind()| 删除全部事件|
|unbind('click')| 删除click事件|
|unbind('click',fn)| 删除单个事件的某个函数|


## 基础事件
jQuery基础事件


|方法 |说明|
|---|---|
|mouseover()|鼠标滑入|
|mouseout()|鼠标离开|
|mouseenter()|鼠标滑入|
|mouseleave()|鼠标离开|
|keydown(event.keyCode)|键盘按下,返回键码|
|keyup(event.keyCode)|键盘弹起,返回键码|
|keypress(event.charCode)|返回字符编码|
|focus()|光标激活|
|blur()|光标丢失|
|focusin()|光标激活,子元素有效|
|focusout()|光标丢失,子元素有效|