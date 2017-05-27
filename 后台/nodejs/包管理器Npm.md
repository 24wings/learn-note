N
odejs 是通过扩展V8引擎,让Javascript拥有访问服务器接口,从而实现Javascript服务器端编程.

### 安装Nodejs

windows　安装[Nodejs官网](https://nodejs.org/en/)　下载右侧最新版本
安装好的Nodejs分为两个部分 Node命令和Npm 命令

### node命令

一般当我们下载完成node之后都会运行`node --version`查看nodejs的版本,这里的$表示linux下的bash窗口,在windows下的用户无需输入

```bash
$ node -v #　node　的版本 与 --version
$ node xxxx.js # node 运行 xxxx.js
```

### npm命令行

这里我们介绍一些npm 的基本使用方式

```bash
# npm初始化一个项目配置文件 package.json
npm init
npm init -y #自动初始化
#npm 安装依赖包到　package.json的devdependencs上
npm i xxxx --save
#npm 安装包到开发环境下
npm i xxxx --save-dev
#npm 安装所有项目的依赖包
npm i
#npm 只安装生产环境的包
npm i --prodction
# 安装package到全局下/即nodejs的安装文件夹下的lib/node_modules　可以全局访问
npm i http-server -g
```




