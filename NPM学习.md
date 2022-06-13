谈及现代JavaScript语言，绕不开Node的学习，而Node的学习，绕不开npm包管理工具，今天小总结以下npm相关的东西

## 网站及已知的工具

首先上一盘硬菜——和node、npm、js相关的网站

* [npm中文文档](https://www.npmjs.cn/)
* [npmmirror 中国镜像站](https://www.npmmirror.com/)
* [npm 包搜索官网](https://www.npmjs.com/)
* [npm.io | NPM packages search engine](https://npm.io/)
* [Node.js 中文网 ](http://nodejs.cn/api/)

再上一盘小菜——我跟着敲项目用到的包/工具列表，供参考

- superagent   类似python的request
- slugify           元素大小写转换，字符替换工具
- nodemon      自动重启工具
- lubiuv           node 多线程 
- express        web框架
- morgan        express logger中间件，在 终端中打印请求路由，响应代码，响应时间信息（在express 的菜单resource中可以查看很多中间件）
- eslint         `npm install eslint prettier eslint-config-prettier eslint-plugin-prettier eslint-config-airbnb eslint-plugin-node eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react` 可以eslint官网查看具体的介绍
- dotenv
- mongoose    链接mongoDB的
- postman       api测试工具[Download Postman | Get Started for Free](https://www.postman.com/downloads/)



npm是包管理工具，那么就涉及到安装、删除、更新、查看等命令，下边进行一些汇总

| 功能描述                           | 语法命令                                                 |
| ---------------------------------- | -------------------------------------------------------- |
| 查看npm版本                        | `npm -V`                                                 |
| 更新npm到最新（稳定）              | `npm install npm@latest -g`                              |
| 更新npm到最新（测试）              | `npm install npm@next -g`                                |
| node初始化（不默认内容）           | `npm init`                                               |
| * * * * * * * * * * * * * * *      | * * * * * * * * * * * * * * *                            |
| 全局：安装一个包，终端加载它       | `npm install -g <package_name>`                          |
| 全局：更新一个包                   | `npm update -g <package>`                                |
| 全局：卸载一个包                   | `npm uninstall -g <package>`                             |
| * * * * * * * * * * * * * * *      | * * * * * * * * * * * * * * *                            |
| 本地：安装一个包，node加载它       | `npm install <package_name>`  涉及：--save  或--save-dev |
| 本地：安装一个包制定版本           | `npm i <package_name>@1.2.3`                             |
| 查看：项目装了哪些包               | 项目目录终端：`dir node_modules`                         |
| 卸载包并删除node_modules文件夹内容 | `npm uninstall <package>`                                |
| 卸载包并删除package.json引用内容   | `npm uninstall --save <package>`                         |
|                                    |                                                          |



## 需要重要理解

[参考原文](https://blog.csdn.net/juzipchy/article/details/65653683)

1. package.json中，`devDependencies` 节点下的模块是我们在开发时需要用的，比如项目中使用的 gulp ，压缩css、js的模块。这些模块在我们的项目部署后是不需要的，所以我们可以使用 --save-dev 的形式安装。

2. package.json中，`dependencies`是项目运行必须依赖的，像 express 这些模块是项目运行必备的，应该安装在 dependencies 节点下，所以我们应该使用 --save 的形式安装。

* 语法1：`npm install <package_name>` 

  1. 安装包到项目的node_modules文件夹中了

  1. 但是不会将这个包加入package.json的devDependencies或dependencies的引用中

  1. 别人下载你的程序，初始化时候不会下载这个包

* 语法2：`npm install -g <package_name>`

  1. 装到node的总的modules文件夹中了，

  1. 只能在终端中使用，并不能在node中使用

* 语法3：`npm install --save <package>`

  1. 安装模块到项目node_modules文件夹中了。

  2. 会将此包写入package.json的dependencies 节点。

  3. 运行 npm install 初始化项目时，会将包下载到项目目录下。

  4. 运行npm install --production或者注明NODE_ENV变量值为production时，会自动下载模块到node_modules目录中。

* 语法4：`npm install --save-dev <package>`

  1. 安装模块到项目node_modules文件夹中了。

  2. 会将此包写入package.json的devDependencies节点。

  3. 运行 npm install 初始化项目时，会将包下载到项目目录下。

  4. 运行npm install --production或者注明NODE_ENV变量值为production时，不会自动下载模块到node_modules目录中。

# package.json解读

## 字段说明

- `version` 表明了当前的版本。
- `name` 设置了应用程序/软件包的名称。
- `author`软件包作者名字。
- `description` 是应用程序/软件包的简短描述。
- `main` 设置了应用程序的入口点。
- `private` 如果设置为 `true`，则可以防止应用程序/软件包被意外地发布到 `npm`。
- `scripts` 定义了一组可以运行的 node 脚本。
- `dependencies` 设置了作为依赖安装的 `npm` 软件包的列表。
- `devDependencies` 设置了作为开发依赖安装的 `npm` 软件包的列表。
- `engines` 设置了此软件包/应用程序在哪个版本的 Node.js 上运行。
- `browserslist` 用于告知要支持哪些浏览器（及其版本）。
- `license`软件包的许可证。
- `repository`仓库位置

## package.json 中包版本 ~ 与 ^ 说明

package.json 中会记录很多包的版本号，前面大多出现 ^ 和 ~ 符号，表示某个包的版本号取值范围，包的版本号在这个范围之内都是可以的。

假定某个包的版本是 1.4.0

- ~1.4.0

  表示：>=1.4.0 && < 1.5.0

  说明：小版本不变，补丁号可以取最大值。

- ^1.4.0

  表示：>=1.4.0 && < 2.0.0

  说明：大版本号不变，小版本号可以取最大值。

- 1.4.0 

  表示：只能是1.4.0
