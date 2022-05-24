1. 跟着敲代码
2. 跟着解决问题
3. 多思考

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

npm查看包有无过时的

```shell
npm outdated
//返回如：
Package  Current  Wanted  Latest  Location              Depended by
express   4.17.3  4.18.1  4.18.1  node_modules/express  Node学习及练习

//升级
npm update XXXXX
```

node 多线程 lubiuv