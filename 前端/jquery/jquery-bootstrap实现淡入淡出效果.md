#用jquery-bootstrap实现淡入淡出[源码]()

![](https://leanote.com/api/file/getImage?fileId=5834340cab6441366c00d8dc)


**提示该项目需要搭建sass ,typescript等自动化构建流程**


# 登陆界面


第1步 引入jquery，bootstrap,scss/css.scss,src/index.ts

* [bootstrap官网](http://v3.bootcss.com/getting-started/)
* jquery,bootstrap 可引用本地
* jquery.js先引入,bootstrap后引入,因为Boostrap依赖jquery

**index.html**
---
```html
<html>
<head>
<!-- 新 Bootstrap 核心 CSS 文件 -->
<link rel="stylesheet" href="http://cdn.bootcss.com/bootstrap/3.3.0/css/bootstrap.min.css">

<!-- 可选的Bootstrap主题文件（一般不用引入） -->
<link rel="stylesheet" href="http://cdn.bootcss.com/bootstrap/3.3.0/css/bootstrap-theme.min.css">

<!--引入编译后的css-->
<link href="css/css.css">
</head>

<body>
<!--  jquery本地-->
<script src="node_modules/jquery/dist/jquery.js"></script>

<!-- bootstrap-->
<script src="node_modules/bootstrap/dist/bootstrap/js/bootstrap.js"></script>

<!--引入编译后的typescript  src/index.ts-->
<script src="dist/index.js"></script>

</body>
</html>
```


第2步 编写第一个页面

```html
<!--登陆页面 全屏-->
<div class="page login">

<!-- 页面内容部分 竖直居中 -->
<div class="login-content">
    <!-- 登陆表单 --水平居中-->
      <div class="login-form">
        
        <input type="text" class="form-control">
        <input type="password" class="form-control">
      </div>
    </div>
  </div>

```

第3步. 登陆页面样式

css.scss
---
```scss

// 定义背景图片变量
$backgroundImage:url(//blackrockdigital.github.io/startbootstrap-stylish-portfolio/img/bg.jpg);


// body元素
body{
    // 登陆界面,显示全屏,背景图片
    .page.login{
        display:table;
        width:100%;
        height:100vh;
        background-image:$backgroundImage;// 将登陆界面作为变量使用,方便修改页面样式
    }
    // 竖直居中
    .login-content{
        display:table-cell;
        vertical-align:center;
    
        //登陆表单,水平居中
        .login-form{
            margin-left:auto;
            margin-right:auto;
        }
    }
}
```
第四步: 加入一颗小树苗
[css3 会跳舞的树](http://www.webhek.com/pure-css-dancing-tree)
* 将树苗的css放入_css3-tree.scss
* 并在css.scss中引入
* index.html在div.login.page元素中添加小树苗

_css3-tree.scss 

css.scss 引入_css3-tree.scss
---
```
@import  'css3-tree'; // 此时引入_css3-tree.scss而只会生成css.scss不会生成_css3-tree.css



```

第5步:  登陆界面淡入

src/index.ts
---
```typescript
$('.page').hide();//让所有页面隐藏

// 定义登陆界面
class Login{
        $el =$('.login.page');
    
     // 构造器 会在 new Login()的时候调用
     constructor() {
     // 登陆界面5秒淡入
        this.$el.fadeIn(5000);
     }

}
// 创建登陆界面
var loginPage = new Login();

```

第6步 登陆界面背景轮播

src/index.ts
---
```typescript
$('.page').hide();//让所有页面隐藏

// 定义登陆界面
class Login{
    // 登陆界面的jquery元素
    $el =$('.login.page');
    // 设置背景图片
    backgroundImages= [`https://www.lawyered.in/static/all_images/banner_images/banner_home1.4d06f0909844.jpg`
        , '//blackrockdigital.github.io/startbootstrap-stylish-portfolio/img/bg.jpg',
        `http://www.webhek.com/misc-res/unitethelovers/content/image/bg.jpg`];
     
     // 构造器 会在 new Login()的时候调用
     constructor() {
     // 登陆界面5秒淡入
        this.$el.fadeIn(5000);
        
        //调用背景轮播
        this.carouselBackground();
     }
     
     //背景轮播
    carouselBackground(){
    var index =0;//默认轮播图片下标是0;
    // 每隔10秒将背景修改一次,并且将图片下标+1
        setInterval(()=>{
            this.$el.css('backgroundImage',`url(${this.backgroundImages[index]})`);//修改图片的background-image属性来修改背景图片
            //如果图片到了数组末尾,就从0开始轮播,如果没有到数组的末尾就换下一张图片
            index = index==this.backgroundImages.length-1?0:++index;
            
        },10000);
    }
}

// 创建登陆界面
var loginPage = new Login();
```

第7步: 淡入淡出切换背景图片
src/index.ts
```typescript
$('.login.page').hide();

// 登陆界面
$('.page').hide();//让所有页面隐藏

// 定义登陆界面
class Login{
    // 登陆界面的jquery元素
    $el =$('.login.page');
    // 设置背景图片
    backgroundImages= [`https://www.lawyered.in/static/all_images/banner_images/banner_home1.4d06f0909844.jpg`
        , '//blackrockdigital.github.io/startbootstrap-stylish-portfolio/img/bg.jpg',
        `http://www.webhek.com/misc-res/unitethelovers/content/image/bg.jpg`];
     
     // 构造器 会在 new Login()的时候调用
     constructor() {
     // 登陆界面5秒淡入
        this.$el.fadeIn(5000);
        
        //调用背景轮播
        this.carouselBackground();
     }
     
     //背景轮播
    carouselBackground(){
    // 当前轮播的下标
        var index = 0;
        // 每10秒一组背景图片
        this.carouselId = setInterval(() => {
            // 10秒中的前3秒让背景消失
            this.$el.fadeOut(3000, () => {
                this.$el.css('backgroundImage', `url(${this.backgroundImages[index]})`);
                index = index == this.backgroundImages.length - 1 ? 0 : ++index;
                // 背景消失后3秒淡入,然后显示背景4秒**粗体**
                this.$el.fadeIn(3000);
            });

        }, 10000);
    }
}

// 创建登陆界面
var loginPage = new Login();
```


