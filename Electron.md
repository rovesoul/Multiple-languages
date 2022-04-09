安装node：https://nodejs.org

验证：node --version





安装electron  ` npm install electron -g`

验证electron：`electron -v`



升级electron：`npm update electron -g`

卸载electron：`npm uninstall electron`





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

