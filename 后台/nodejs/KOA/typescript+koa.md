本
文将引导创建一个自动化编译运行的typescript+koa+mongoose的项目.
重点将放在以下几个细节处
* gulpFile.js 中实现自动化编译运行typescript,监听文件改动,自动编译运行js脚本
* mongoose 配合对象接口实现数据类型


#1. 初始化项目
###1.1 初始化项目配置文件package.json
```bash
$ npm init -y
$ cnpm i @types/koa koa koa-views @types/koa-views koa-static @types/koa-static koa-router @types/koa-router koa-bodyparser @types/koa-bodyparser --save

```



项目根目录下添加typescript配置文件 tsconfig.json
```json
{
"compilerOptions": {
"target": "es6",
"module": "commonjs",
"typeRoots": [
"node_modules/@types"
],
"moduleResolution": "node",
"sourceRoot": "src",
"outDir": "dist"
}
}
```


gulpFile.js实现自动化编译运行流程
```javascript
cnpm i gulp gulp-typescript-compiler gulp-
concat gulp-typescript gulp-uglify gulp-rename gulp-nodemon
typescript --save

```



```javascript

import koa = require('koa');
import path = require('path');
import bodyparser = require('koa-bodyparser');
import staticServer = require('koa-static');
import {carRouter} from './routes';

import Router = require('koa-router');
import views = require('koa-views');



var app = new koa();
app.use(async(ctx,next)=>{
var start= new Date().getTime();
await next();
var time = new Date().getTime() - start;
console.log(`${ctx.method} ${ctx.path} ${time}ms`);
});


app.use(staticServer(path.resolve(__dirname, '../public')));
app.use(staticServer(path.resolve(__dirname, '../node_modules')));

app.use(bodyparser());
app.use(views(path.resolve(__dirname,'../views'),{
map:{
html:'swig'
}
}));

// 路由
var router = new Router();
router.use('/car',carRouter.routes());
router.use('/car',carRouter.allowedMethods());
app.use(router.routes());
app.use(router.allowedMethods());
app.listen(4000,()=>{
console.log('server running on 4000');
});
```