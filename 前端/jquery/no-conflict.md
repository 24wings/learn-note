jQuery - noConflict() 方法
* 如何在页面上同时使用 jQuery 和其他框架?

------jQuery 和其他 JavaScript 框架
jQuery 使用 $ 符号作为 jQuery 的简写。如果其他 JavaScript 框架也使用 $ 符号作为简写怎么办?
其他一些 JavaScript 框架包括:
* MooTools
* Backbone
* Sammy
* Cappuccino
* Knockout
* JavaScript
* MVC
* Google Web Toolkit
* Google Closure
* Ember
* Batman
* Ext

------其中某些框架也使用 $ 符号作为简写(就像 jQuery),如果您在用的两种不同的框架正在使用相同的简
写符号,有可能导致脚本停止运行。jQuery 的团队考虑到了这个问题,并实现了 noConflict() 方法。
. jQuery noConflict() 方法
-------noConflict() 方法会释放会 $ 标识符的控制,这样其他脚本就可以使用它了。
实例:可以通过全名替代简写的方式来使用 jQuery:
```javascript
$.noConflict();
jQuery(document).ready(function(){
jQuery("button").click(function(){
jQuery("p").text("jQuery 仍在运行!");
});
```