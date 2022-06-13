1. 跟着敲代码

2. 跟着解决问题

3. 多思考

   

   # 课程用到的包

   * superagent   类似python的request
   * slugify           元素大小写转换，字符替换工具
   * nodemon      自动重启工具
   * postman       api测试工具[Download Postman | Get Started for Free](https://www.postman.com/downloads/)
   * lubiuv           node 多线程 
   * express        web框架
   * morgan        express logger中间件，在 终端中打印请求路由，响应代码，响应时间信息（在express 的菜单resource中可以查看很多中间件）
   * eslint         `npm install eslint prettier eslint-config-prettier eslint-plugin-prettier eslint-config-airbnb eslint-plugin-node eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react` 可以eslint官网查看具体的介绍
   * dotenv
   * mongoose    链接mongoDB的

```shell
$ E:\D-drive-61125\Node学习及练习> node
Welcome to Node.js v16.13.0.
Type ".help" for more information.
> const name="jack"
undefined
> name
'jack'
> 7+3
10
> .exit
```

node下，点tab键，可以看到全局变量

`_`可以带入上次结果，例如,输入function的名字+.后，点tab可以看到具体函数属性

```shell
> 3*8
24
> _+6
30
> _/5
6

//如
String.+Tab
```

nodejs的特性：`同步synchronous`     `异步asynchronous`  `阻塞blocking`

## npm查看包有无过时的

```shell
npm outdated
//返回如：
Package  Current  Wanted  Latest  Location              Depended by
express   4.17.3  4.18.1  4.18.1  node_modules/express  Node学习及练习

//升级
npm update XXXXX
```

### **查看全局已安装**
查看全局已安装（-g 的意思是 global 全局的意思）

```$ npm ls -g```

会发现，会把包的所有依赖也显示出来

加上层级控制显示深度：--depth 0

`$ npm ls -g --depth 0`

这样就只会查到安装的包，并不会查到包的依赖。

**查看项目中已安装**
查看当前项目已安装包（项目跟目录必须有 package.json 文件）

`$ npm ls`

同样也是会把所有包的依赖显示出来。同上，加上 --depth 0 就好了。

`$ npm ls --depth 0`

**如果只想显示生产环境依赖的包**
`$ npm ls --depth 0 --prod`

**只显示开发环境依赖的包**
`$ npm ls --depth 0 --dev`

————————————————
版权声明：本文为CSDN博主「勇敢的阿呆」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_41664096/article/details/121797260



## 流：

可读、可写、双工、转换

![image-20220526234125242](.\笔记素材图\4stream.png)

# 导入模块系统解析

![moudle system](.\笔记素材图\module-system.png)

loading

![loading](.\笔记素材图\loadingmoudle.png)

wrapping

![wrapping](.\笔记素材图\wrapping moudle.png)

execution 没得讲，跳过

return

![image-20220527002256850](.\笔记素材图\export moudle.png)

# Express

* 很小的node框架，高抽象
* 流行的node框架