如
何安装
安装程序

NodeJS提供了一些安装程序，都可以在nodejs.org这里下载并安装。

Windows系统下，选择和系统版本匹配的.msi后缀的安装文件。Mac OS X系统下，选择.pkg后缀的安装文件。
编译安装

Linux系统下没有现成的安装程序可用，虽然一些发行版可以使用apt-get之类的方式安装，但不一定能安装到最新版。因此Linux系统下一般使用以下方式编译方式安装NodeJS。

确保系统下g++版本在4.6以上，python版本在2.6以上。

从nodejs.org下载tar.gz后缀的NodeJS最新版源代码包并解压到某个位置。

进入解压到的目录，使用以下命令编译和安装。
```bash
$ ./configure
$ make
$ sudo make install
```
如何运行

打开终端，键入node进入命令交互模式，可以输入一条代码语句后立即执行并显示结果，例如：
```bash
$ node
> console.log('Hello World!');
Hello World!
```
如果要运行一大段代码的话，可以先写一个JS文件再运行。例如有以下hello.js。
```bash
function hello() {
console.log('Hello World!');
}
hello();
```
写好后在终端下键入`node hello.js`运行，结果如下：
```bash
$ node hello.js
Hello World!
```
#####权限问题

在Linux系统下，使用NodeJS监听80或443端口提供HTTP(S)服务时需要root权限，有两种方式可以做到。

一种方式是使用sudo命令运行NodeJS。例如通过以下命令运行的server.js中有权限使用80和443端口。一般推荐这种方式，可以保证仅为有需要的JS脚本提供root权限。
```bash
$ sudo node server.js
```
另一种方式是使用chmod +s命令让NodeJS总是以root权限运行，具体做法如下。因为这种方式让任何JS脚本都有了root权限，不太安全，因此在需要很考虑安全的系统下不推荐使用。
```bash
$ sudo chown root /usr/local/bin/node
$ sudo chmod +s /usr/local/bin/node
```