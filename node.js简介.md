**当浏览器地址栏输入**[www.baidu.com](http://www.baidu.com/)**，敲下回车会发生什么？**

1. 利用DNS域名解析系统进行域名解析，将域名解析成IP

   因为域名只是一个别名，计算机只认识IP，所以需要DNS解析一下（如果有端口号需要识别端口号，否则进入默认端口：http协议默认端口号是80，https默认端口号是443）

2. 查找ip对应的主机服务器

   如果是第一次访问该服务器，会向网络供应商（移动、联通...）请求

3. TCP的三次握手，经过三次在客户端和服务器之间传递报文，建立连接

4. 发起http请求，请求入口文件，后端接收到请求相关信息，返回入口文件

5. 解析入口文件，同时如果有资源请求继续发送http请求...

6. 过程中如果碰到css文件，js文件，需要去加载外部文件

7. 1. 加载css，渲染html结构
   2. 加载js
   3. 执行js的逻辑，有ajax请求，再次去服务器请求数据
   4. 通过数据刷新DOM

8. 文件渲染完成（TCP的四次挥手，断开连接）









**认识node.js**

### [https://nodejs.org/](https://nodejs.org/en/)

### <http://nodejs.cn/>

![img](00-笔记_files/Image.gif)

### Node是一个基于 Chrome V8 引擎的 JavaScript 运行环境（服务器端的浏览器）

### Node.js 的包管理器 npm，是全球最大的开源库生态系统



**引擎 engine是什么？**

浏览器中有一种东西叫内核，浏览器有很多种：chrome、firefox、百度浏览器、qq浏览器.....，但是内核现在流行的只有几种：



| **内核** | **浏览器**          | **Cool** |              |
| -------- | ------------------- | -------- | ------------ |
| trident  | IE                  | -ms-     | microsoft    |
| webkit   | safari、chrome(l)   | -webkit- | apple/google |
| blink    | chrome(h)、opera(h) |          | google       |
| presto   | opera(l)            | -o-      | opera        |
| gecko    | firefox             | -mz-     | mozilla      |



内核里有引擎：渲染引擎（渲染dom结构）、脚本引擎（运行脚本语言）

脚本引擎最流行的就是chrome V8引擎，快、高效



**一、node历史**

Ryan Dahl 

![img](00-笔记_files/Image [1].gif)

​    他的工作是用C/C++写高性能Web服务。对于高性能，异步IO、事件驱动是基本原则，但是用C/C++写就太痛苦了， 于是这位仁兄开始设想用高级语言开发Web服务。他评估了很多种高级语言，发现很多语言虽然同时提供了同步IO和异步IO，但是开发人员一旦用了同步IO，他们就再也懒得写异步IO了，所以，最终，Ryan瞄向了JavaScript。

​    在2009年，Ryan正式推出了基于JavaScript语言和V8引擎的开源Web服务器项目，命名为Node.js

### **二、node.js能做哪些事**

1. 处理文件与数据库
2. 与互联网进行沟通，以标准化的格式处理请求并发送回答（处理客户端请求）
3. 用来执行编译 CSS 预编译语言、预编译、压缩、混淆 JS、压缩图片、reload、deploy 等工程化任务

### **三、node.js的优点**

1. 处理高并发场景性能更高

   Java 1G 服务器 每个客户端连接耗费2M资源 1024=2^10

   node 1G 服务器 动态分配

2. 采用事件驱动、异步编程，为网络服务而设计

3. 轻量高效，运行速度是PHP的86倍

4. 包和模块

5. 便于前端学习

6. 适用于I/O密集型的应用，不适用于CPU密集型的应用

**注意：NodeJS不是语言，是运行环境！！**

### **四、使用node.js**

##### **安装**

> node官网 [https://nodejs.org](https://nodejs.org/)

> node中文网 [http://nodejs.cn](http://nodejs.cn/)

node -v //查看版本，检测安装是否成功

##### **运行**

node index //文件名，后缀.js可写可不写

### node

### 1+1 //进入node环境后执行js代码，跟在chrome的console里写代码基本一致

### **五、node.js模块**

##### **核心模块**

​    os、fs、http等

##### **自定义模块（CommonJS规范）**

   module.exports、require

##### **第三方模块**

​    gulp等，需要在命令行中执行 npm install 模块名称

​        模块之间不能循环依赖

npm 

在安装Node的时候会安装npm ，这是Node的包管理工具，node package manager

包：就是被封装好打包上传的工具，我们只需要下载安装就可以立即使用

npm可以对这些node的包、模块进行宏观的管理，例如下载、卸载、更新...

npm拥有最大的开源网站：[https://www.npmjs.com](https://www.npmjs.com/)



我们需要npm init先来创建一个package.json文件，加上-y指全部使用默认配置项

我们通过npm install 模块 来安装模块，缩写：npm i 模块,默认的会安装到目录中的node_modules；如果没有这个文件夹，会自动创建

卸载的话就是npm unintsall 模块名

全局安装 -g（全写上是--global）,全局安装之后，在任意的文件夹都可以访问到

在本地（当前目录上）安装（大多是包）不需要加-g，可以--save指的是保存在本地的package.json里



因为npm在是国外服务器，所以下载速度比较慢，所以可以使用cnpm（淘宝国内镜像）来下载

下载cnpm：

npm install -g cnpm --registry=[https://registry.npm.taobao.org](https://registry.npm.taobao.org/)

**注意，cnpm不是真正的npm，下载的资源来自与taobao服务器，下载到的东西和npm下载的是不一样;cnpm 不一定能使用list、info等等操作**



yarn



| npm                              | yarn                          |
| -------------------------------- | ----------------------------- |
| npm install                      | yarn add                      |
| npm init -y                      | yarn init -y                  |
| npm install --save [package]     | yarn add [package]            |
| npm install --save-dev [package] | yarn add [package] [--dev/-D] |
| npm install -g [package]         | yarn global add [package]     |





nvm 

管理node版本

- nvm v 查看nvm的版本
- nvm list 查看当前安装过的node版本
- nvm install 8.10.0 安装8.10.0的node
- nvm use  8.10.0  切换使用8.10.0 的node



node_modules和package.json

工程化：开始使用一些自动化工具来帮助我们构建项目。

我们可以通过npm init来创建package.json文件，这个文件可以来管理我们的项目依赖的包的信息

devDependencies是开发依赖，也就是只在开发的时候使用的包 --save-dev （-D），depedencies是我们打包的时候依然使用的包--save （-S）

**这个文件还有一个好处，就是使我们的项目有辨识性，我们在某些情况下，需要将项目提交给某个地方或者共享给某人，这个时候我们不需要提交node——modules文件夹，只需要在那个地方执行npm install 就可以安装package.json里所有的包，使我们的项目可以继续运行**