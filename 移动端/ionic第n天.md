# 今天的源代码

# 第一步产品的数据
含义| 属性名字| 数据类型 
-|-
 产品名字|name | string
 价格 | price | number
 产品描述| summary |string
 图片| images | string[]


## 双向数据绑定产品的产品描述

```html
<!--在product-detail.html的icon-content底部的上面加入双向绑定产品详情 -->

   <textarea ng-model="product.summary" rows="10" placeholder="产品描述" cols="" style="    width: 100%;
    
    font-size: 17px;"></textarea>
```
[product-detail.html](https://leanote.com/api/file/getAttach?fileId=585de64cab644175ca00115f)



##  第二步产品图片布局
* product-detail.html
* styles.css

```html
  <div class="row product-images">
            <div class="col col-20 addImage"></div>
            <div class="col col-20"></div>
            <div class="col col-20"></div>
            <div class="col col-20"></div>
        </div>
```

```css
.product-images {
    padding-left: 4.5%;
}

.product-images .col-20 {
    padding-bottom: 20%;
    margin-right: 5%;
    background: yellow;
}

.product-images .addImage {
    background: url(../img/ion-plus.png) no-repeat;
    background-size: cover;
}
```
![](https://leanote.com/api/file/getImage?fileId=585debd5ab644175ca0011d4);




# 第三步用户添加产品图片 
文件名 | 链接 
-|-
js/product-detail.js|[第三步product-detail.controller.js](https://leanote.com/api/file/getAttach?fileId=585df595ca968075cb000001) 
templates/product-detail.html  |[第三步product-detail.html](https://leanote.com/api/file/getAttach?fileId=585df595ca968075cb000002)
test.video |[test.mp4](https://leanote.com/api/file/getAttach?fileId=585df792ab64417326001274)
<video src="https://leanote.com/api/file/getAttach?fileId=585df792ab64417326001274" autoplay style="width:100%;" loop></video>


<video src="https://leanote.com/api/file/getAttach?fileId=585df8dfab644173260012a9" autoplay style="width:100%" loop></video>

* 编写文本框以及点击回调事件,让用户可以选取图片   product-detail.html
* 将选中的图片解析成base64格式.并加入product.images数组 呈现在界面上  product-detail.js

```html
<!-- 当前文本框被选择新的文件,就触发增加产品的行为-->
<input type="file"  id="addProductImageInput"  onchange="angular.element(this).scope().addProductImage(this)  ">

<!-- 点击加号 则触发 input文本框 -->
<div class="row">
<!-- 加号-->
<div class="col col-20 addProduct" onclick="document.querySelector('#addProductImageInput').click()">
</div>
</div>

```

* [FileReader API](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader)
```js
// 获取选取的文件
    $scope.addProductImage=function(fileInput){
        var file = fileInput.files[0];
        //  调试输出console.log(file.name);
        var reader =  new FileReader();
//  读取文件成功后的回调函数
        reader.onload=function(event){
// 拿到读取后的数据
var base64Data = event.target.result;
    // 将图片推送入产品的图片组里; 如果出现undefined错误,记得初始化产品图片数组为空数组
        $scope.product.images.push(base64Data);
}
// 开始读取文件
reader.readAsDataURL(file);
    }
```

product-detail.html
```html
    <div class="col col-20" ng-repeat=" image in product.images" style="background:url({{image}}) no-repeat;background-size: cover;"></div>
```


![](https://leanote.com/api/file/getImage?fileId=585dfdccab644175ca001394)
### 错误原因
答: 没有$scope.addProductImageInput函数


# 第四步:用firebase 管理上传产品图片

[firebase storage 上传文件](https://firebase.google.com/docs/storage/web/upload-files)

```javascript
 $scope.addProductImage = function(fileInput) {
            var file = fileInput.files[0];
            firebase.storage().ref("img/" + Math.random() + file.name).put(file)
                .then(function(rtn) {
                    $scope.$apply(function() {
                        $scope.product.images.push(rtn.a.downloadURLs[0]);
                    })
                })


        }
```

 重构路由参数封装
 * app.js 配置产品详情的路由封装
 ```javascript
// 指定进入哪个产品组的哪一个产品 
  .state('product-detail', {
            url: '/product-detail/:groupID/:productID',
            templateUrl: 'templates/product-detail.html',
            controller: 'productDetailCtrl'
        });
```

产品的数据结构

* group
    *  name
    *  createDt
    *  products:[]
        * name
        * price
        * images
        * summary

# 最终www目录代码

[www.rar](https://leanote.com/api/file/getAttach?fileId=58606e12ab64417326003bbb)
 
 

 
 

