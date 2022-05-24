## 学习中遇到的包：
* electron-reloader
* electron-packager
* nodemon //自动重启
* fluent-ffmpeg   ffmpeg   ffprob  其中ffpeg需要下载，并配置环境路径[新版ffmpeg小白安装配置PATH路径指南_topia_csdn的博客-CSDN博客_ffmpeg path](https://blog.csdn.net/topia_csdn/article/details/110110774)
* 

## 已经制作

| name               | function                             | 学习源     | 用到modules                                                  |
| ------------------ | ------------------------------------ | ---------- | ------------------------------------------------------------ |
| 直接拉网页成客户端 | 把远程网页固化下来                   | 官网doc    |                                                              |
| SysTop             | 一个监测CPU的软件                    | bili       | nodemon <br />electron-log <br />node-os-utils  //获取cpu及内存数据 |
| image压缩          | 图片压缩软件                         | bili       | imagemin、<br />imagemin-mozjpeg、<br />imagemin-pngquant、<br />slash |
| 获取video长度      | 通过ipcRenderer获得video长度         | bili       | ffmpeg<br />fluent-ffmpeg                                    |
| todo list          | 通过ipcRenderer 再两个独立窗口间通信 | bli        | 增加todo，删除所有todo                                       |
| 视频转换器         |                                      | bili60开始 |                                                              |





安装node：https://nodejs.org

验证：node --version





安装electron  ` npm install electron -g`

验证electron：`electron -v`



升级electron：`npm update electron -g`

卸载electron：`npm uninstall electron`



热更新需要安装：`npm install --save-dev electron-reloader`

main.js 中加入热加载

`const reloader = require('electron-reloader')`

`reloader(module)`



至少三个文件

* package.json:用于配置electron工程的
* index.js  相当于electron桌面应用入口点
* index.html: 用于主窗口UI页面文件





electron事件：

- 原生事件，调用API
- web事件，



closed：窗口关闭

window-all-closed：所有窗口关闭

activate：窗口激活后触发事件



特性：

- 支持多窗口应用,每一个窗口都会有自己独立的JavaScript上下文
- 过屏幕API整合桌面系统的特性,与本地开发语言编写的桌面应用的效果类似.
- 支持获取本地计算机特性，如电源状态
- 支持阻止操作系统进入省电模式,对于一些演示文稿类的应用非常有用.
- 支持创建托盘应用
- 支持创建菜单和菜单项.
- 支持为应用增加全局键盘快捷键
- 支持汇报程序崩溃
- 支持之定义的Dock菜单项
- 支持操作系统通知.
- 支持为应用程序创建启动安装器



打包：`electron-packager .` 

安装: `npm install electron-packager -g`





![image-20220508225147117](.\笔记素材图\electron原理)

![qianhzi](.\笔记素材图\electron学习前置条件.png)



![image-20220513002542189](.\笔记素材图\ipc通信.png)

![image-20220513160821971](.\笔记素材图\menu.png)

### electron 自动重启：安装 `npm i -D nodemon`

json中配置dev这行：

```json
"scripts": {
        "start": "electron .",
        "dev": "nodemon --exec electron ."
    },
```

终端中启动：

```shell
npm run dev
```



看到了41集，bug logger 软件制作[【Udemy付费课程】Electron From Scratch：使用 JavaScript 构建流行桌面应用程序（中英文字幕）_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1kY411w7Xo?p=41&spm_id_from=pageDriver)





