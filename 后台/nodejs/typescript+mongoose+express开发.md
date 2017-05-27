前端的技术日益更新,而所有技术中,typescript无异于未来的标准。
所以本文将使用typescript来编写express+mongoose的应用

自动化流程gulpFile.js
```javascript
var gulp = require("gulp");
var tsc = require("gulp-typescript-compiler");
var ts = require('gulp-typescript');
var nodemon = require("gulp-nodemon");
/** gulp-bootstrap  */

var gulp = require('gulp');


var tsProject = ts.createProject('tsconfig.json');

gulp.task("default", ["compile", "watch",
    "nodemon"
]);


gulp.task("watch", function () {

    return gulp.watch(["./src/**/*.ts"], ["compile"]);

});


gulp.task("compile", function () {
    return gulp.src('src/**/*.ts')
        .pipe(tsProject())
        .pipe(gulp.dest('build'));

});

gulp.task("nodemon", function () {
    nodemon({
        script: "build/www",
        // exec: ' ', // set DEBUG=*,-not_this &node --debug
        env: {
            'NODE_ENV': 'production'
        }

    });
});
```

有了自动化流程
我们开始设计目录结构
```html
-  src
------views 视图层
------models 数据层
------routes 路由层
-----middlewares 中间件
app.ts   app的核心
config.ts  app的配置
route.ts 路由
www.ts 　程序的入口
```

##如何配置数据层,让数据有实体类型
在models下新建一个admin.model.ts
```typescript
import mongoose = require('mongoose');

// 系统管理员名字
var adminSchema = new mongoose.Schema({

    name: String,
    avatar: String,
    password: String,
    gender: String,
    email: String,
    signature: String,
    createDt: { type: Date, default: Date.now },
    updateDt: { type: Date, default: Date.now },

});


export interface IAdmin extends mongoose.Document {
    avatar: string;
    name: string;
    password: string;
    gender: string;
    email: string;
    signature: string;

}

export var adminModel = mongoose.model<IAdmin>('Admin', adminSchema);
```
在models创建index.ts文件    

----------


```typescript
import mongoose = require('mongoose');

mongoose.connect('mongodb://118.89.38.111/wanviv');

export { IAdmin, adminModel } from './admin';
```


