## for... in 遍历键
## for...of 遍历值
```javascript
var arr =['a','b','c'];
```
* for in 每次遍历的都是当前元素的下标
* for in 也可以用于遍历对象,遍历的是对象的键例如 name,age
* for of 每次遍历的都是当前元素
* for of  遍历对象的值

ng-repeat
* 用法1 group in gorups
* $index是指当前元素的下标,
* (key,value) in person   key 是对象的一个键,value是对象该键的值

# 编辑产品 源代码 [www.rar](https://leanote.com/api/file/getAttach?fileId=58608ac4b5a8580e45000003)
* 进入产品 product.controller.js, 点击进入产品的操作
* 在产品详情页,判断当前产品是新建产品还是编辑产品 product-edtail.controller.js

```javascript
 // product.controller.js
  $ionicActionSheet.show({
                    buttons: [
                        { text: '<b >查看产品</b>' },
                        { text: '<b>置顶</b>' },
                        { text: '<b>删除</b>' },
                        { text: '<b>重命名产品</b>' }
                    ],

                    titleText: '管理产品',
                    cancelText: '取消',
                    cancel: function() {
                      
                    },
                    buttonClicked: function(index) {
                        console.log(product);
                        switch (index) {
                        // 当点击 查看产品按钮,则跳转页面到产品详情,并传递产品组id,产品id
                            case 0:
                                $state.go('product-detail', { productID: key, groupID: groupID });
                                break;
                            case 2:
                                firebase.database().ref('products/' + groupID + '/products/' + key).remove();
                                break;
                            default:
                                break;
                        }
                        return true;

                    }

                });
            }
```
`product-detail.controller.js`
```javascript
// product-detail.controller.js
    var groupID= $stateParams.groupID;
    // 产品id有两种形式,如果为空.就是新建产品,如果传了,就是编辑产品
    var productID =$stateParams.productID;
    $scope.isNew =!productID;
    
    // 进入页面 
    // 当新建产品,则初始化产品数据,
    // 当编辑产品的时候,从服务器/数据库拉取当前产品的数据
    if($scope.isNew){
        $scope.product={name:'产品名字',images:[]};
    }else{
        firebase.database().ref('products/'+groupID+'/proudcts/'+productID).on('value',function(snapshot){
        $scope.product=snapshot.val();
        });
    }
    
    // 当保存产品的时候
    // 如果是新增产品,则将当前产品数据推送到产品组
    // 如果是编辑产品,则更新当前产品
    $scope.saveProduct=function(){
    if($scope.isNew){
        // 新增产品,推送产品
        firebase.database().ref('products/'+groupID+'/products').push($scope.product);
    }else{
        firebase.database().ref('products/'+groupID+'/products/'+productID).update($scope.product);
    }
    
    }
```


# 解决app的一些bug
* 有些页面切换没有动画
```javascript
// 通过注入 $ionicViewSwitcher 来设置页面跳转方向来解决没有动画的问题
    
 // index.controller.js
    $ionicViewSwitcher.nextDirection('forward'); // none,back

// product.js ,如果退出该页面之前,设置返回的方向
    $scope.$on('$ionicView.beforeLeave', function() {
            $ionicViewSwitcher.nextDirection('back');
        });


```

[百度](http://www.baidu.com)
# 视图生命周期 view viewcycle  和事件

 ## ionic原生配置 
 config.xml  配置app  [cordova config.xml配置详解](https://cordova.apache.org/docs/en/latest/config_ref/index.html)
 
 ## 插件的使用
* 白名单插件 [ionic whitelist](https://github.com/apache/cordova-plugin-whitelist)


 [www源码](https://leanote.com/api/file/getAttach?fileId=5860d84c3753af2cf3000000)
[config.xml](https://leanote.com/api/file/getAttach?fileId=5860d8883753af2cf3000001)