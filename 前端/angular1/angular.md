#环境和开发工具
使用nodejs和npm 进行包管理和服务器
[nodejs](https://nodejs.org/zh-cn/)

使用vs code开发IDE
[vs code](https://www.visualstudio.com/en-us/products/code-vs.aspx)
vs code 常用功能
* 格式化代码
* 转到代码定义位置

使用Git和SourceTree管理代码
[Git的GUI工具](https://git-scm.com/download/gui/win)
[sourceTree]()

#angular2框架开发
 angular2官网[angular.cn](angular.cn)
按照官网将package.json,tsconfig.json,typings.json,systemjs.config.js

其中
 ```javascript
 //system.config.js,将app作为程序入口指定为main.js 并且将其他组件映射成简短的名字
 var packages = {
    'app':                        { main: 'main.js',  defaultExtension: 'js' },
    'rxjs':                       { defaultExtension: 'js' },
    'angular2-in-memory-web-api': { main: 'index.js', defaultExtension: 'js' },
  };


##第一步:启动应用程序
文件清单
* index.html
* main.ts
* app.module
* app.component
* page.component


```javascript
//index.html是angular官网的index.html,额外加入jquery和bootstrap
<script src="//cdn.bootcss.com/jquery/3.0.0/jquery.js"></script>


//main.ts 启动应用程序
import {platformBrowserDynamic} from '@angular/platform-browser-dynamic';
import {AppModule} from './app.module';

window['$'].ajax(
    {
        methond:'GET',
        url:'web-site.json',
        success:function(data){
            window['websiteData']=data;
            window['pages']= data.pages;
            window['nav']=data.nav;
            platformBrowserDynamic().bootstrapModule(AppModule);
        }
}
);

//app.module.ts
import {NgModule} from '@angular/core';
import {CommonModule} from '@angular/common';
import {BrowserModule} from '@angular/platform-browser';
import {FormsModule} from '@angular/forms';

import {AppComponent} from './app.component';


@NgModule({
    imports:[CommonModule,BrowserModule,FormsModule],
    declarations:[AppComponent],
    bootstrap:[AppComponent]
})
export class AppModule{}

//app.component.ts
import {Component, OnInit} from '@angular/core';

@Component({
    selector: 'my-app',
    template: 'this is AppComponent'
})
export class AppComponent implements OnInit {
    ngOnInit(){

    }
}

//app.routing.ts
import { Routes, RouterModule } from '@angular/router';
import {PageComponent} from './page.component';

const appRoutes: Routes = [
  {
    path:"",
    redirectTo:"sign-in",
    pathMatch:'full'

  },
  { path: '**', 
  component: PageComponent,
  pathMatch:'full' 

}
];

export const appRoutingProviders: any[] = [];
export const routing = RouterModule.forRoot(appRoutes);
```
文件清单完成,运行 npm run start 可以看见页面内容 this is app component的字体


##第二步:安装express 并配置静态文件服务器
```nodejs
//重新配置angular的时候记得将express重新加入package.json
npm install express --save

//创建文件 server.js  仿照heroku dev 上的项目https://github.com/heroku/node-js-getting-started.git
var express = require('express');
var app = express();

app.use(express.static(__dirname+'/'));

app.set('port',process.env.PORT||5000);

app.listen(app.get('port'),function(){
    console.log('app server listening on',app.get('port'));
})

```
运行node server




##最后一步:上传到heroku
创建.gitigore文件 文件内容
```python
#不上传node_modules文件夹
node_modules
```
添加Procfile
```javascript
web: node server.js
```
仿照heroku给的案例配置服务器


 ```nodejs
 ```