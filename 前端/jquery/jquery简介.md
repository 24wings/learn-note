#
# 简介
本章带你jquery入门,有三个知识板块
* visual studio code　的代码演示
* jquery简介
* jquery选择器
* jquery事件






#
# jquery选择器

选择器是支持开发者所熟悉的css语法,快速且轻松的对页面进行设置。

常用jquery选择器分成以下三大类:

* 基本选择器 \(\#id,.className,element... ,群组选择器\)

* 层次选择器 \(sel空格sel2 ,sel1&gt;sel2 , sel+sel2, sel1~sel2\)

* 祖先元素与后代元素
* 父元素与子元素
* 指定元素的下一个元素
* 父元素与子元素
* 指定元素后面所有的兄弟元素

* 属性选择器 例如:a\[title\]

* 过滤选择器

### 层级选择器

| css/jquery通用选择器 | 选择功能 |
| :--- | :--- |
| sel1 sel2 | 后代 |
| sel1&gt;sel2 | 子选择器,指定元素的下一个元素 |
| sel1+sel2 | 兄弟节点选择器,指定元素的下一个元素 |
| sel1~sel2 | 所有兄弟节点选择器，指定元素后面所有的兄弟元素 |

### jquery其他方法

| 方法 | 功能 |
| :--- | :--- |
| find\(\) | 后代元素 |
| children\(\) | 子选择器 |
| next\(\) | 兄弟节点选择器 |
| nextAll\(\) | 兄弟节点选择器,指定元素后面所有的兄弟 |




